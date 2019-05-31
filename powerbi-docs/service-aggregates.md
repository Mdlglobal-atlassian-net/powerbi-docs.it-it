---
title: Usare funzioni di aggregazione (somma, Media e così via) nel servizio Power BI
description: Informazioni su come modificare l'aggregazione in un grafico (somma, Media, massimo e così via.) nel servizio Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/03/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Reports
ms.openlocfilehash: 7cee05df6a7d13e18bc31bc1a1f34a5f89711c0d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65710589"
---
# <a name="work-with-aggregates-sum-average-and-so-on-in-the-power-bi-service"></a>Usare funzioni di aggregazione (somma, Media e così via) nel servizio Power BI

## <a name="what-is-an-aggregate"></a>Che cos'è un’aggregazione?

In alcuni casi è utile combinare matematicamente i valori dei dati. L'operazione matematica potrebbe essere somma, Media, massimo, conteggio e così via. Quando si combinano i valori nei dati, bensì *aggregando*. Il risultato di tale operazione matematica è un'*aggregazione*.

Quando il servizio Power BI e Power BI Desktop creano visualizzazioni, è possibile che eseguano aggregazioni dei dati. L'aggregazione risponde spesso alle esigenze dell'utente, ma in altri casi è possibile che si vogliano aggregare i valori in un modo diverso,  ad esempio per ottenere una somma invece di una media. Esistono diversi modi per gestire e modificare l'aggregazione che usa Power BI in una visualizzazione.

In primo luogo, diamo un'occhiata ai dati *tipi* perché dipende dal tipo di dati, se e come Power BI poter aggregarli.

## <a name="types-of-data"></a>Tipi di dati

La maggior parte dei set di dati ha più di un tipo di dati. A livello di base, i dati sono numerici o non è presente. Power BI è possibile aggregare i dati numerici usando una somma, Media, conteggio, minimo, varianza e molto altro ancora. Il servizio può anche aggregare dati testuali, spesso chiamati *categoriche* dati. Se si tenta di aggregare un campo categorico inserendolo in un bucket solo numerico, ad esempio **i valori** oppure **descrizioni comando**, Power BI verrà contare le occorrenze di ogni categoria o le occorrenze distinte di ogni categoria. Tipi speciali di dati, ad esempio date, hanno alcune delle proprie opzioni di aggregazione: più vecchia, più recente, primo e ultimo.

Nell'esempio seguente:

- **Units Sold** e **Manufacturing Price** sono colonne che contengono i dati numerici

- **Segment**, **Country**, **Product**, **Month** e **Month Name** contengono dati categorici

   ![Screenshot di un set di dati di esempio.](media/service-aggregates/power-bi-aggregate-chart.png)

Quando si crea una visualizzazione in Power BI, il servizio aggregherà i campi numerici (il valore predefinito è *somma*) su un campo categorico.  Ad esempio, "unità vendute ***by Product***", "unità vendute ***by Month***" e "Manufacturing Price ***dal segmento***". Power BI fa riferimento ad alcuni campi numerici come **misure**. È facile identificare le misure nell'editor di report di Power BI - il **campi** sono elencate le misure che includono il simbolo ∑. Vedere [l'editor di report... guardare la presentazione](service-the-report-editor-take-a-tour.md) per altre informazioni.

![Screenshot di Power BI con l'elenco dei campi indicato.](media/service-aggregates/power-bi-aggregate-fields.png)

## <a name="why-dont-aggregates-work-the-way-i-want-them-to"></a>Perché le aggregazioni non funzionano nel modo desiderato?

L'uso delle aggregazioni in Power BI service può generare confusione. Forse si dispone di un campo numerico e Power BI non consenta di modificare l'aggregazione. oppure può essere necessario non aggregare un campo, come un anno, ma semplicemente contare il numero di occorrenze.

In genere, il problema sottostante è la definizione di campo nel set di dati. Forse il proprietario del set di dati definito il campo come testo e questo spiega perché non è possibile somma o la media, Power BI. Sfortunatamente, [solo il proprietario del set di dati può modificare il modo in cui un campo è stato categorizzato](desktop-measures.md). Pertanto, se si dispone delle autorizzazioni di proprietario per il set di dati, nel Desktop o il programma utilizzato per creare il set di dati (ad esempio Excel), è possibile risolvere il problema. In caso contrario, sarà necessario contattare il proprietario del set di dati per ottenere assistenza.  

C'è una speciale sezione alla fine di questo articolo [ **considerazioni e risoluzione dei problemi**](#considerations-and-troubleshooting). Fornisce materiale sussidiario e suggerimenti. Se non si trova la risposta, inviare una domanda al [forum di Community di Power BI](http://community.powerbi.com). Si otterrà una risposta rapida direttamente dal team di Power BI.

## <a name="change-how-a-numeric-field-is-aggregated"></a>Modificare la modalità di aggregazione di un campo numerico

Si supponga di avere un grafico che somma le unità vendute per prodotti diversi, ma che si preferisca ottenere la media.

1. Creare un **istogramma a colonne raggruppate** che utilizza una misura e una categoria. In questo esempio viene usato "Units Sold by Product".  Per impostazione predefinita, Power BI crea un grafico che somma le unità vendute (trascinare la misura nel **valore** bene) per ogni prodotto (trascinare categoria nel **asse** anche).

   ![Screenshot del grafico, riquadro visualizzazioni ed elenco campi con somma indicata.](media/service-aggregates/power-bi-aggregate-sum.png)

1. Nel **visualizzazioni** riquadro, la misura e scegliere il tipo di aggregato necessario. In questo caso, selezioniamo HyperV **medio**. Se non viene visualizzata l'aggregazione è necessario, vedere la [ **considerazioni e risoluzione dei problemi** ](#considerations-and-troubleshooting) sezione.

   ![Screenshot dell'elenco di aggregazione con Media selezionato e segnalate.](media/service-aggregates/power-bi-aggregate-average.png)

   > [!NOTE]
   > Le opzioni disponibili nell'elenco a discesa variano in base 1) il campo selezionato e 2) il modo il proprietario del set di dati classificati in quel campo.

1. La visualizzazione usa ora l'aggregazione in base alla media.

   ![Screenshot del grafico a questo punto visualizzare medio di unità vendute per prodotto.](media/service-aggregates/power-bi-aggregate-average-2.png)

## <a name="ways-to-aggregate-your-data"></a>Modi per aggregare i dati

Alcune opzioni possono essere disponibili per l'aggregazione di un campo:

- **Non riepilogare**. Con questa opzione è selezionata, Power BI considera ogni valore in quel campo separatamente e non genera un riepilogo. Usare questa opzione se si dispone di una colonna di ID numerici che non dovrà sommare il servizio.

- **Somma**. Somma tutti i valori di un campo.

- **Media**. Acquisisce una media aritmetica dei valori.

- **Minimo**. Mostra il valore più basso.

- **Massimo**. Mostra il valore più alto.

- **Conteggio (non vuoto)** . Conta il numero di valori in tale campo non vuoto.

- **Conteggio (Distinct)** . Conta il numero di valori diversi nel campo.

- **Deviazione Standard**.

- **Varianza**.

- **Mediana**.  Mostra il valore mediano (intermedio). Questo valore ha lo stesso numero di elementi prima e dopo di esso.  Se sono presenti due mediane, Power BI ne calcola la media.

Ad esempio, questi dati:

| Paese | Quantità |
|:--- |:--- |
| USA |100 |
| Regno Unito |150 |
| Canada |100 |
| Germania |125 |
| Francia | |
| Giappone |125 |
| Australia |150 |

produrrebbero i risultati seguenti:

- **Non riepilogare**: ogni valore viene visualizzato separatamente

- **Somma**: 750

- **Media**: 125

- **Massimo**:  150

- **Minimo**: 100

- **Conteggio (non vuoto):** 6

- **Conteggio (Distinct):** 4

- **Deviazione standard:** 20,4124145...

- **Varianza:** 416,666...

- **Mediana:** 125

## <a name="create-an-aggregate-using-a-category-text-field"></a>Creare un'aggregazione usando un campo categoria (testo)

È anche possibile aggregare un campo non numerico. Ad esempio, se si ha un campo relativo al nome del prodotto, è possibile aggiungerlo come valore e impostarlo su **Conteggio**, **Conteggio valori univoci**, **Primo** o **Ultimo**.

1. Trascinare il **prodotto** campo nel **valori** bene. Il **valori** anche viene generalmente utilizzato per i campi numerici. Power BI riconosce che questo campo è un campo di testo, imposta la funzione di aggregazione **non riepilogare**e viene visualizzata una tabella a colonna singola.

   ![Screenshot del campo Product nel bene i valori.](media/service-aggregates/power-bi-aggregate-value.png)

1. Se si modifica l'aggregazione dal valore predefinito **non riepilogare** al **conteggio (Distinct)** , Power BI conta il numero di prodotti diversi. In questo caso, sono disponibili quattro.
  
   ![Schermata in cui la misura distinct count di prodotti.](media/service-aggregates/power-bi-aggregate-count.png)

1. E se si imposta l'aggregazione su **Conteggio**, Power BI conta il numero totale. In questo caso, sono disponibili sette voci relative **prodotto**.

   ![Screenshot del conteggio dei prodotti.](media/service-aggregates/power-bi-aggregate-count-2.png)

1. Trascinando lo stesso campo (in questo caso **prodotto**) nel **valori** bene e lasciando l'aggregazione predefinita **non riepilogare**, Power BI suddivide il conteggio da prodotto.

   ![Screenshot del prodotto e il conteggio dei prodotti.](media/service-aggregates/power-bi-aggregate-final.png)

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi

D:  perché non è disponibile l'opzione **Non riepilogare**?

R:  il campo selezionato è probabilmente una misura calcolata o una misura avanzata creata in Excel o in [Power BI Desktop](desktop-measures.md). Ogni misura calcolata ha una propria formula hardcoded. Non è possibile modificare l'aggregazione che usa Power BI. Ad esempio, se si tratta di una somma, può essere solo una somma. Il **i campi** elencati mostrano *misure calcolate* con il simbolo di calcolatrice.

D:  perché con un campo sicuramente **numerico** le uniche scelte disponibili sono **Conteggio** e **Conteggio valori univoci**?

R1:  È probabile che il proprietario del set di dati abbia *non* classificato il campo sotto forma di numero. Ad esempio, se un set di dati ha un **anno** campo, il proprietario del set di dati può classificarlo il valore come testo. È più probabile che Power BI conterà le **anno** campo (ad esempio, numero di persone nate nel 1974). È meno probabile che Power BI verrà somma o la Media. Se si è proprietari, è possibile aprire il set di dati in Power BI Desktop e usare la **modellazione** pressione di tab per modificare il tipo di dati.

R2: Se il campo dispone di un'icona della calcolatrice, ciò significa che è un *misura calcolata*. Ogni misura calcolata ha una propria formula hardcoded che è possibile modificare solo il proprietario del set di dati. Il calcolo che usa Power BI potrebbe essere un'aggregazione semplice come una media o una somma. Potrebbe anche essere qualcosa di più complicato come la "percentuale del contributo alla categoria padre" o "totale parziale dall'inizio dell'anno". Power BI non dovrà somma o Media dei risultati. Al contrario, questa verrà semplicemente ricalcolata (utilizzando la formula hardcoded) per ogni punto dati.

R3:  un'altra possibilità è che il campo sia stato inserito in un *bucket* che consente solo valori categorici.  In questo caso, le uniche opzioni disponibili saranno Conteggio e Conteggio valori univoci.

R4:  E la quarta possibilità è che si usa il campo per un asse. Su un asse di un grafico a barre, ad esempio, Power BI mostra una sola barra per ogni valore univoco e non applica alcuna aggregazione ai valori dei campi.

>[!NOTE]
>L'eccezione a questa regola è rappresentata dai grafici a dispersione, che *richiedono* valori aggregati per gli assi X e Y.

D:  Perché non è possibile aggregare campi di testo per le origini dati SQL Server Analysis Services (SSAS)?

R:  Le connessioni dinamiche ai modelli multidimensionali SSAS non consentono aggregazioni sul lato client, incluse quelle di tipo first, last, avg, min, max e sum.

D:  è disponibile un grafico a dispersione e si vuole che il campo *non* venga aggregato.  Come si procede?

R:  aggiungere il campo al bucket **Dettagli** e non ai bucket degli assi X o Y.

D:  quando si aggiunge un campo numerico a una visualizzazione, per la maggior parte dei campi di questo tipo l'aggregazione predefinita è la somma, ma per alcuni vengono eseguiti il conteggio, la media o altre aggregazioni.  Perché l'aggregazione predefinita non è sempre la stessa?

R:  I proprietari del set di dati è possono impostare l'esecuzione del riepilogo predefinita per ogni campo. Se dispone di un set di dati, modificare il riepilogo predefinito nella **modellazione** scheda di Power BI Desktop.

D:  come può il proprietario di un set di dati assicurarsi che un campo non venga mai aggregato?

R:  in Power BI Desktop, nella scheda **Creazione di modelli**, impostare **Tipo di dati** su **Testo**.

D:  Non è possibile visualizzare **non riepilogare** come opzione nell'elenco a discesa elenco.

R:  provare a rimuovere il campo e ad aggiungerlo di nuovo.

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)