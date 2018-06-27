---
title: Aggiornamento incrementale in Power BI Premium
description: Informazioni su come abilitare set di dati molto grandi nel servizio Power BI Premium.
author: christianwade
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 04/30/2018
ms.author: chwade
LocalizationGroup: Premium
ms.openlocfilehash: 1b6a3c35abeff33e2fb1e0fecdc5c2a5c88e1530
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2018
ms.locfileid: "34298183"
---
# <a name="incremental-refresh-in-power-bi-premium"></a>Aggiornamento incrementale in Power BI Premium

L'aggiornamento incrementale abilita set di dati molto grandi nel servizio Power BI Premium, con i seguenti vantaggi:

- **Gli aggiornamenti sono più veloci.** È sufficiente aggiornare i dati che sono stati modificati. Ad esempio, è sufficiente aggiornare gli ultimi 5 giorni di un set di dati di 10 anni.

- **Gli aggiornamenti sono più affidabili.** Ad esempio non è necessario mantenere connessioni con esecuzione prolungata a sistemi di origine volatili.

- **Il consumo di risorse risulta ridotto.** L'aggiornamento di una quantità di dati inferiore riduce l'uso complessivo di memoria e altre risorse.

## <a name="how-to-use-incremental-refresh"></a>Come usare l'aggiornamento incrementale

I criteri di aggiornamento incrementale sono definiti in Power BI Desktop e vengono applicati dopo essere stati pubblicati nel servizio Power BI.

Per iniziare, attivare l'aggiornamento incrementale nelle funzionalità di anteprima.

![Opzioni - Funzionalità di anteprima](media/service-premium-incremental-refresh/preview-features.png)

### <a name="filter-large-datasets-in-power-bi-desktop"></a>Filtrare grandi set di dati in Power BI Desktop

I set di dati di grandi dimensioni, che contengono anche miliardi di righe, potrebbero non essere gestibili in Power BI Desktop, che in genere è limitato dalle risorse disponibili nel PC desktop dell'utente. Questi set di dati vengono in genere filtrati al momento dell'importazione, per poter essere usati in Power BI Desktop. Questo vale anche se si usa l'aggiornamento incrementale.

#### <a name="rangestart-and-rangeend-parameters"></a>Parametri RangeStart e RangeEnd

Per sfruttare l'aggiornamento incrementale nel servizio Power BI, il filtro deve essere applicato usando i parametri di data/ora di Power Query con i nomi riservati e con distinzione maiuscole/minuscole **RangeStart** e **RangeEnd**.

Nell'Editor di Power Query selezionare **Gestisci parametri** per definire i parametri con valori predefiniti.

![Gestisci parametri](media/service-premium-incremental-refresh/manage-parameters.png)

Dopo aver definito i parametri è possibile applicare il filtro, selezionando l'opzione di menu **Filtro personalizzato** per una colonna.

![Filtro personalizzato](media/service-premium-incremental-refresh/custom-filter.png)

Verificare che vengano filtrate righe in cui il valore della colonna *è dopo o uguale a* **RangeStart** e *prima di* **RangeEnd**.

![Filtra righe](media/service-premium-incremental-refresh/filter-rows.png)

> [!TIP]
> Il tipo di dati dei parametri deve essere data/ora, ma è possibile convertirli in modo da soddisfare i requisiti dell'origine dati. Ad esempio, la funzione Power Query seguente converte un valore data/ora per renderlo simile a una chiave surrogata di tipo intero con formato *aaaammgg*, comune nei data warehouse. La funzione può essere chiamata dal passaggio di applicazione del filtro.
>
> `(x as datetime) => Date.Year(x)*10000 + Date.Month(x)*100 + Date.Day(x)`

Selezionare **Chiudi e applica** nell'Editor di Power Query. In Power BI Desktop viene reso disponibile un subset del set di dati.

> [!NOTE]
> Una volta pubblicati, i valori dei parametri vengono automaticamente sottoposti a override dal servizio Power BI. Non è necessario definirli nelle impostazioni del set di dati.

### <a name="define-the-refresh-policy"></a>Definire i criteri di aggiornamento

L'aggiornamento incrementale è disponibile nel menu di scelta rapida per le tabelle, salvo per i modelli di connessione dinamica.

![Criteri di aggiornamento](media/service-premium-incremental-refresh/refresh-policy.png)

#### <a name="incremental-refresh-dialog"></a>Finestra di dialogo Aggiornamento incrementale

Viene visualizzata la finestra di dialogo Aggiornamento incrementale. Usare l'interruttore per abilitare la finestra di dialogo.

![Dettagli aggiornamento dati](media/service-premium-incremental-refresh/refresh-details.png)

> [!NOTE]
> Se l'espressione di Power Query per la tabella non fa riferimento ai parametri con i nomi riservati, l'interruttore è disattivato.

Il testo dell'intestazione illustra quanto segue:

-   L'aggiornamento incrementale è supportato solo per le aree di lavoro con capacità Premium. I criteri di aggiornamento sono definiti in Power BI Desktop e vengono applicati dalle operazioni di aggiornamento nel servizio.

-   Se si è in grado di scaricare il file PBIX contenente un criterio di aggiornamento incrementale dal servizio Power BI, tale file non si aprirà in Power BI Desktop. A breve non sarà più possibile eseguirne il download. Il supporto di questa funzionalità potrebbe essere disponibile in futuro, ma ricordare che questi set di dati possono diventare così grandi che la loro gestione (download e apertura) in un PC desktop tipico può causare problemi.

#### <a name="refresh-ranges"></a>Intervalli di aggiornamento

L'esempio seguente definisce un criterio di aggiornamento per l'archiviazione di 5 anni di dati in totale e l'aggiornamento incrementale di 10 giorni di dati. Se il set di dati viene aggiornato quotidianamente, l'istruzione che segue viene eseguita per ogni operazione di aggiornamento.

-   Aggiungere un nuovo giorno di dati.

-   Aggiornare 10 giorni fino alla data corrente.

-   Rimuovere gli anni di calendario con più di 5 anni dalla data corrente. Se ad esempio la data corrente è 1 gennaio 2019, l'anno 2013 viene rimosso.

Il primo aggiornamento nel servizio Power BI può richiedere più tempo, perché importa i 5 anni di dati. È probabile che gli aggiornamenti successivi vengano completati in tempi molto più ridotti.

![Intervalli di aggiornamento](media/service-premium-incremental-refresh/refresh-ranges.png)

**La definizione di questi intervalli potrebbe essere sufficiente. In tal caso passare direttamente al passaggio pubblicazione riportato di seguito. Gli altri elenchi a discesa sono destinati a funzionalità avanzate.**

#### <a name="detect-data-changes"></a>Rileva modifiche ai dati

L'aggiornamento incrementale di 10 giorni è ovviamente molto più efficiente rispetto all'aggiornamento completo di 5 anni. Tuttavia è possibile migliorare ancora l'efficienza. Se si seleziona la casella di controllo **Rileva modifiche ai dati**, è possibile selezionare una colonna di data/ora e usarla per identificare e aggiornare solo i giorni in cui i dati vengono modificati. Questa opzione presuppone l'esistenza di una colonna di questo tipo (usata in genere per operazioni di controllo) nel sistema di origine. Il valore massimo di questa colonna viene valutato per ciascuno dei periodi dell'intervallo incrementale. Se tale valore non è cambiato dall'ultimo aggiornamento, non è necessario aggiornare il periodo. Nell'esempio questa opzione può ridurre ulteriormente i giorni sottoposti ad aggiornamento incrementale, ad esempio da 10 a 2.

![Rilevare le modifiche](media/service-premium-incremental-refresh/detect-changes.png)

> [!TIP]
> La struttura corrente richiede che la colonna per il rilevamento delle modifiche ai dati sia persistente e memorizzata nella cache. Può essere utile considerare una delle tecniche seguenti per ridurre la cardinalità e il consumo di memoria.
>
> Mantenere solo il valore massimo della colonna al momento dell'aggiornamento, ad esempio con una funzione di Power Query.
>
> Ridurre la precisione a un livello accettabile in base ai requisiti di frequenza di aggiornamento.
>
> L'abilitazione di query personalizzate per il rilevamento delle modifiche dei dati è prevista in una fase successiva. Questa funzionalità potrebbe consentire di evitare il salvataggio permanente del valore della colonna.

#### <a name="only-refresh-complete-periods"></a>Aggiorna solo periodi completi

Si supponga che l'aggiornamento sia stato pianificato per l'esecuzione ogni mattina alle 4.00. Se durante queste 4 ore appaiono dati nel sistema di origine, è possibile che non si desideri includere tali dati nel set complessivo. Alcune metriche di business, ad esempio i barili al giorno nel settore estrattivo, non hanno alcun significato se sono relativi a giorni parziali.

Un altro esempio è l'aggiornamento dei dati di un sistema finanziario in cui i dati per il mese precedente vengono approvati il giorno 12 del mese. È possibile impostare l'intervallo incrementale su 1 mese e pianificare l'esecuzione dell'aggiornamento il dodicesimo giorno del mese. Con questa opzione selezionata, ad esempio, i dati di gennaio verranno aggiornati il 12 febbraio.

![Periodi completi](media/service-premium-incremental-refresh/complete-periods.png)

> [!NOTE]
> Le operazioni di aggiornamento nel servizio vengono eseguite in base all'ora UTC. Questa impostazione può determinare la data di validità e influire sui periodi completi. È prevista l'aggiunta della possibilità di sostituire la data di validità per un'operazione di aggiornamento.

## <a name="publish-to-the-service"></a>Pubblicare nel servizio

Dato che l'aggiornamento incrementale è una funzionalità Premium, la finestra di dialogo di pubblicazione consente la selezione di un'area di lavoro solo se è disponibile la capacità Premium.

![Pubblicare nel servizio](media/service-premium-incremental-refresh/publish.png)

Ora è possibile aggiornare il modello. Il primo aggiornamento può richiedere più tempo per l'importazione dei dati cronologici. Gli aggiornamenti successivi sono in genere molto più rapidi perché usano l'aggiornamento incrementale.

## <a name="query-timeouts"></a>Timeout della query

L'articolo [Scenari per la risoluzione dei problemi di aggiornamento](https://docs.microsoft.com/power-bi/refresh-troubleshooting-refresh-scenarios) spiega che le operazioni di aggiornamento nel servizio Power BI sono soggette a timeout. Le query possono essere limitate anche dal timeout predefinito dell'origine dati. La maggior parte delle origini relazionali consente l'override dei timeout nell'espressione M. Ad esempio l'espressione seguente usa la [funzione di accesso ai dati di SQL Server](https://msdn.microsoft.com/query-bi/m/sql-database) per impostare il timeout su 2 ore. Ogni periodo definito dagli intervalli dei criteri invia una query osservando l'impostazione di timeout del comando.

```
let
    Source = Sql.Database("myserver.database.windows.net", "AdventureWorks", [CommandTimeout=#duration(0, 2, 0, 0)]),
    dbo_Fact = Source{[Schema="dbo",Item="FactInternetSales"]}[Data],
    #"Filtered Rows" = Table.SelectRows(dbo_Fact, each [OrderDate] >= RangeStart and [OrderDate] < RangeEnd)
in
    #"Filtered Rows"
```
