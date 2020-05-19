---
title: Usare DirectQuery in Power BI Desktop
description: Usare DirectQuery, noto anche come connessione dinamica, in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 1224b7eaa6a19cab4bf6fa8304eb5c5b1fb27581
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83285855"
---
# <a name="use-directquery-in-power-bi-desktop"></a>Usare DirectQuery in Power BI Desktop
Con *Power BI Desktop*, quando ci si connette all'origine dati è sempre possibile importare una copia dei dati in Power BI Desktop. Per alcune origini dati è disponibile un approccio alternativo: connettersi direttamente all'origine dati usando DirectQuery.

## <a name="supported-data-sources"></a>Origini dati supportate
Per un elenco completo delle origini dati che supportano DirectQuery, vedere [Origini dati supportate da DirectQuery](power-bi-data-sources.md).

## <a name="how-to-connect-using-directquery"></a>Come connettersi tramite DirectQuery
Quando si usa **Recupera dati** per connettersi a un'origine dati supportata da DirectQuery, la finestra di dialogo di connessione consente di selezionare la modalità di connessione. In Power BI Desktop, ad esempio, nella scheda **Home** della barra multifunzione selezionare **Recupera dati** > **SQL Server**. Nella finestra di dialogo **Database SQL Server**, nell'area **Modalità Connettività dati** vengono visualizzate le opzioni **Importa** e **DirectQuery**:

![Opzioni Importa e DirectQuery, finestra di dialogo Database SQL Server, Power BI Desktop](media/desktop-use-directquery/directquery_sqlserverdb.png)

Di seguito sono spiegate le differenze tra le modalità **Importa** e **DirectQuery**.

- **Importa**: le tabelle e le colonne selezionate vengono importate in Power BI Desktop. Quando si crea o si interagisce con una visualizzazione, Power BI Desktop usa i dati importati. Per visualizzare eventuali modifiche apportate ai dati sottostanti dopo l'importazione iniziale o l'aggiornamento più recente, è necessario aggiornare i dati, in modo da importare nuovamente il set di dati completo.

- **DirectQuery**: nessun dato viene importato o copiato in Power BI Desktop. Per le origini relazionali, le tabelle e le colonne selezionate vengono visualizzate nell'elenco **Campi**. Per origini multidimensionali, ad esempio SAP Business Warehouse, le dimensioni e misure del cubo selezionato vengono visualizzate nell'elenco **Campi**. Quando si crea o si interagisce con una visualizzazione, Power BI Desktop esegue una query sull'origine dati sottostante, in modo che i dati visualizzati siano sempre correnti.

Quando si usa DirectQuery, sono disponibili molte modellazioni e trasformazioni dei dati, seppur con alcune limitazioni. Quando si crea o si interagisce con una visualizzazione, è necessario eseguire una query sull'origine sottostante. Il tempo impiegato per aggiornare la visualizzazione dipende dalle prestazioni dell'origine dati sottostante. Se i dati necessari per soddisfare la richiesta sono stati richiesti di recente, Power BI Desktop usa dati recenti per ridurre il tempo necessario per mostrare la visualizzazione. Se si seleziona **Aggiorna** nella scheda **Home** della barra multifunzione, tutte le visualizzazioni vengono aggiornate con i dati correnti.

L'articolo [Power BI e DirectQuery](desktop-directquery-about.md) descrive DirectQuery nel dettaglio. Per altre informazioni su vantaggi, limitazioni e considerazioni importanti relative all'utilizzo di DirectQuery, vedere le sezioni seguenti.

## <a name="benefits-of-using-directquery"></a>Vantaggi dell'uso di DirectQuery
L'uso di DirectQuery offre alcuni vantaggi:

- DirectQuery consente di creare visualizzazioni su set di dati molto grandi, in cui in caso contrario non sarebbe fattibile importare prima tutti i dati con la pre-aggregazione.
- Per modificare i dati sottostanti può essere necessario un aggiornamento dei dati. Per alcuni report, l'esigenza di visualizzare i dati correnti può richiedere trasferimenti di grandi quantità di dati, rendendo la reimportazione dei dati impossibile. Al contrario, i report di DirectQuery usano sempre dati aggiornati.
- La limitazione del set di dati da 1 GB *non* si applica a DirectQuery.

## <a name="limitations-of-directquery"></a>Limitazioni di DirectQuery
Esistono attualmente alcune limitazioni all'uso di DirectQuery:

- Se la query dell'**editor di query** è eccessivamente complessa, si verifica un errore. Per risolvere l'errore è necessario eliminare il passaggio problematico nell'**editor di query** o *importare* i dati invece di usare DirectQuery. Per origini multidimensionali come SAP Business Warehouse, non è disponibile alcun **editor di query**.

- In DirectQuery non sono disponibili funzionalità di Business Intelligence per le gerarchie temporali. In modalità DirectQuery, ad esempio, non è supportata la gestione speciale delle colonne di date (anno, trimestre, mese o giorno).

- Per garantire prestazioni accettabili per le query inviate all'origine dati sottostante, le espressioni DAX consentite nelle misure prevedono limitazioni.

- Quando si usa DirectQuery, è previsto un limite di un milione di righe per la restituzione di dati a meno che si usi una capacità Premium. Il limite non influenza le aggregazioni o i calcoli usati per creare il set di dati restituito usando DirectQuery, ma solo le righe restituite. Le capacità Premium possono impostare limiti massimi per le righe, come descritto in [questo post](https://powerbi.microsoft.com/blog/five-new-power-bi-premium-capacity-settings-is-available-on-the-portal-preloaded-with-default-values-admin-can-review-and-override-the-defaults-with-their-preference-to-better-fence-their-capacity/). 

    È possibile, ad esempio, aggregare 10 milioni di righe con la query eseguita sull'origine dati. In questo modo, vengono restituiti in modo accurato i risultati dell'aggregazione a Power BI usando DirectQuery, purché i dati restituiti a Power BI siano inferiori a 1 milione di righe. Se DirectQuery restituisce più di 1 milione di righe, Power BI restituirà un errore, a meno che non si usi una capacità Premium e il conteggio delle righe sia sotto il limite impostato dall'amministratore.


## <a name="important-considerations-when-using-directquery"></a>Considerazioni importanti relative all'utilizzo di DirectQuery
Quando si usa DirectQuery, devono essere presi in considerazione i tre punti seguenti:

- **Prestazioni e carico**: tutte le richieste di DirectQuery vengono inviate al database di origine e, pertanto, il tempo necessario per aggiornare un oggetto visivo dipende dal tempo impiegato dell'origine back-end per fornire i risultati di una o più query. Il tempo di risposta consigliato (comprendente la restituzione dei dati richiesti) quando si usa DirectQuery per gli oggetti visivi è di cinque secondi o meno; il tempo di risposta massimo consigliato è di 30 secondi. Tempi più lunghi renderebbero l'esperienza dell'utente che usa il report del tutto insoddisfacente. Dopo aver pubblicato un report nel servizio Power BI, l'utente riceverà un errore di timeout per tutte le query che richiedono più di qualche minuto per l'esecuzione.
  
    È necessario prendere in considerazione anche il carico sul database di origine, in base al numero di utenti di Power BI che utilizzerà il report pubblicato. Anche l'utilizzo della **sicurezza a livello di riga** (RLS) può influire in modo significativo. Un riquadro del dashboard non RLS condiviso da più utenti produce una sola query al database, mentre se si usa RLS in un riquadro del dashboard, quando questo viene aggiornato in genere viene richiesta una singola query *per ogni utente*, il che aumenta in modo significativo il carico sul database di origine e, potenzialmente, può avere ripercussioni negative sulle prestazioni.
  
    Power BI crea query il più efficaci possibile. In determinate situazioni, tuttavia, la query generata potrebbe non essere abbastanza efficace da evitare un aggiornamento non riuscito. Quando ad esempio una query generata recupera un numero eccessivamente elevato di righe dall'origine dati back-end, si verifica l'errore seguente:

    ```output
    The resultset of a query to external data source has exceeded
    ```
  
    Questa situazione può verificarsi con un grafico semplice che include una colonna di cardinalità molto elevata, con l'opzione di aggregazione impostata su **Non riepilogare**. L'oggetto visivo deve contenere solo colonne con una cardinalità inferiore a un milione o deve applicare i filtri appropriati.

- **Sicurezza**: per impostazione predefinita, tutti gli utenti che usano un report pubblicato si connettono all'origine dati back-end con le credenziali immesse dopo la pubblicazione nel servizio Power BI. Si tratta dello stesso processo adottato quando si importano i dati: tutti gli utenti vedono gli stessi dati, indipendentemente dalle eventuali regole di sicurezza definite nell'origine back-end.

    I clienti che preferiscono l'implementazione della sicurezza per singolo utente con origini DirectQuery devono usare la sicurezza a livello di riga o configurare l'autenticazione vincolata Kerberos per l'origine. Kerberos non è disponibile per tutte le origini. [Altre informazioni sulla sicurezza a livello di riga](../admin/service-admin-rls.md). [Altre informazioni su Kerberos in DirectQuery](service-gateway-sso-kerberos.md).

- **Funzionalità supportate**: Alcune funzionalità di Power BI Desktop non sono supportate in modalità DirectQuery o presentano limitazioni. Nel servizio Power BI sono disponibili anche alcune funzionalità, ad esempio *Informazioni rapide*, che non sono disponibili nei set di dati con DirectQuery. Quando si stabilisce se usare o meno DirectQuery, è necessario prendere in considerazione queste limitazioni di funzionalità.

> [!NOTE]
> Quando si usa DirectQuery con un database SQL di Azure e un indirizzo IP privato, è necessario un gateway locale. 

## <a name="publish-to-the-power-bi-service"></a>Pubblicare nel servizio Power BI
I report creati con DirectQuery possono essere pubblicati nel servizio Power BI.

Se l'origine dati usata non richiede il **gateway dati locale** (**database SQL di Azure**, **Azure SQL Data Warehouse** o **Redshift**), è necessario specificare le credenziali prima che venga visualizzato il report pubblicato nel servizio Power BI. Seguire questa procedura per fornire le credenziali:

1. Accedere a [Power BI](https://www.powerbi.com/).
2. Nel servizio Power BI selezionare l'icona a forma di ingranaggio **Impostazioni**  e scegliere la voce di menu **Impostazioni**.

    ![Impostazioni, servizio Power BI](media/desktop-use-directquery/directquery_pbiservicesettings.png)

3. Nella pagina **Impostazioni** del servizio Power BI selezionare la scheda **Set di dati** , scegliere il set di dati che usa DirectQuery e selezionare **Modifica credenziali**.

4. Aggiungere le credenziali. In caso contrario, quando si apre un report pubblicato o si esplora un set di dati creato con una connessione DirectQuery, si verifica un errore.

Per creare una connessione dati per origini dati diverse da **database SQL di Azure**, **Azure SQL Data Warehouse**, **Redshift** o **Snowflake Data Warehouse** che usano DirectQuery, installare un **gateway dati locale** e registrare l'origine dati. Per altre informazioni, vedere [Informazioni sul gateway dati locale](service-gateway-onprem.md).

## <a name="next-steps"></a>Passaggi successivi
Per altre informazioni su DirectQuery, vedere le risorse seguenti:

- [Uso di DirectQuery in Power BI](desktop-directquery-about.md)
- [Data sources supported by DirectQuery](power-bi-data-sources.md) (Origini dati supportate da DirectQuery)
- [DirectQuery e SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md)
- [DirectQuery and SAP HANA](desktop-directquery-sap-hana.md) (DirectQuery e SAP HANA)
- [Informazioni sul gateway dati locale](service-gateway-onprem.md)
