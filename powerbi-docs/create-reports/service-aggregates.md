---
title: Usare le aggregazioni (somma, media e così via) nel servizio Power BI
description: Informazioni su come modificare l'aggregazione in un grafico (somma, media, valore massimo e così via) nel servizio Power BI.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/03/2019
ms.author: maggies
ms.custom: seodec18
LocalizationGroup: Reports
ms.openlocfilehash: 469f217426f4c66c6d1d0d72192efbda8391689c
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83315295"
---
# <a name="work-with-aggregates-sum-average-and-so-on-in-the-power-bi-service"></a>Usare le aggregazioni (somma, media e così via) nel servizio Power BI

## <a name="what-is-an-aggregate"></a>Che cos'è un’aggregazione?

In alcuni casi è utile combinare matematicamente i valori dei dati. L'operazione matematica potrebbe essere somma, media, massimo, conteggio e così via. La combinazione dei valori dei dati viene definita *aggregazione*. Il risultato di tale operazione matematica è un'*aggregazione*.

Quando il servizio Power BI e Power BI Desktop creano visualizzazioni, è possibile che eseguano aggregazioni dei dati. L'aggregazione risponde spesso alle esigenze dell'utente, ma in altri casi è possibile che si vogliano aggregare i valori in un modo diverso,  ad esempio per ottenere una somma invece di una media. È possibile gestire e modificare in molti modi diversi l'aggregazione usata da Power BI in una visualizzazione.

Verranno esaminati prima di tutto i *tipi* di dati perché il tipo di dati determina come e se i dati possono essere aggregati da Power BI.

## <a name="types-of-data"></a>Tipi di dati

La maggior parte dei set di dati ha più di un tipo di dati. Al livello più basilare i dati sono numerici o non numerici. Power BI supporta l'aggregazione di dati numerici usando una somma, una media, un conteggio, un valore minimo, una varianza e altro ancora. Il servizio può anche aggregare dati testuali, spesso noti come dati *categorici*. Se si prova a eseguire l'aggregazione di un campo categorico, inserendolo in un bucket solo numerico come **Valori** o **Descrizioni comando**, Power BI conterà le occorrenze di ogni categoria o le occorrenze distinte di ogni categoria. I tipi speciali di dati, come le date, hanno opzioni di aggregazione specifiche, ovvero più vecchio, più recente, primo e ultimo.

Nell'esempio seguente:

- **Units Sold** e **Manufacturing Price** sono colonne che contengono i dati numerici

- **Segment**, **Country**, **Product**, **Month** e **Month Name** contengono dati categorici

   ![Screenshot di un set di dati di esempio.](media/service-aggregates/power-bi-aggregate-chart.png)

Quando si crea una visualizzazione in Power BI, il servizio aggregherà i campi numerici (con l'operazione predefinita *somma*) su un campo categorico.  Ad esempio, "Units Sold ***by Product***", "Units Sold ***by Month***" e "Manufacturing Price ***by Segment***". Power BI fa riferimento ad alcuni campi numerici come **misure**. È possibile identificare con facilità le misure nell'editor di report di Power BI: le misure vengono visualizzate con il simbolo ∑ nell'elenco **Campi**. Per altre informazioni, vedere [Presentazione dell'editor di report](service-the-report-editor-take-a-tour.md).

![Screenshot di Power BI con l'elenco Campi evidenziato.](media/service-aggregates/power-bi-aggregate-fields.png)

## <a name="why-dont-aggregates-work-the-way-i-want-them-to"></a>Perché le aggregazioni non funzionano nel modo desiderato?

L'utilizzo delle aggregazioni nel servizio Power BI può creare confusione. È possibile che Power BI non consenta di modificare l'aggregazione per un campo numerico oppure può essere necessario non aggregare un campo, come un anno, ma semplicemente contare il numero di occorrenze.

In genere, il problema sottostante è la definizione del campo nel set di dati. Forse il proprietario del set di dati ha definito il campo come testo e questo spiega perché Power BI non è in grado di eseguire operazioni di somma o media. Sfortunatamente, [solo il proprietario del set di dati può modificare il modo in cui un campo è stato categorizzato](../transform-model/desktop-measures.md). Se si hanno le autorizzazioni di proprietario per il set di dati in Desktop o nel programma usato per creare il set di dati, ad esempio Excel, è possibile risolvere questo problema. In caso contrario, sarà necessario contattare il proprietario del set di dati per ottenere assistenza.  

Alla fine di questo articolo è disponibile una sezione speciale intitolata [**Considerazioni e risoluzione dei problemi**](#considerations-and-troubleshooting) che fornisce suggerimenti e indicazioni. Se non si trova la risposta, inviare la domanda al [forum della Community di Power BI](https://community.powerbi.com). Si otterrà una risposta rapida direttamente dal team di Power BI.

## <a name="change-how-a-numeric-field-is-aggregated"></a>Modificare la modalità di aggregazione di un campo numerico

Si supponga di avere un grafico che somma le unità vendute per prodotti diversi, ma che si preferisca ottenere la media.

1. Creare un **istogramma a colonne raggruppate** che usa una misura e una categoria. In questo esempio viene usato "Units Sold by Product".  Per impostazione predefinita, Power BI crea un grafico che somma le unità vendute (trascinare la misura nell'area **Valore**) per ogni prodotto (trascinare la categoria nell'area **Asse**).

   ![Screenshot del grafico, riquadro Visualizzazioni ed elenco Campi con l'aggregazione Somma evidenziata.](media/service-aggregates/power-bi-aggregate-sum.png)

1. Nel riquadro **Visualizzazioni** fare clic con il pulsante destro del mouse sulla misura e scegliere il tipo di aggregazione necessario. In questo caso viene selezionato **Media**. Se non viene visualizzata l'aggregazione necessaria, vedere la sezione [**Considerazioni e risoluzione dei problemi**](#considerations-and-troubleshooting).

   ![Screenshot dell'elenco delle aggregazioni con l'opzione Media selezionata ed evidenziata.](media/service-aggregates/power-bi-aggregate-average.png)

   > [!NOTE]
   > Le opzioni disponibili nell'elenco a discesa variano a seconda del campo selezionato e del modo in cui tale campo è stato classificato dal proprietario del set di dati.

1. La visualizzazione usa ora l'aggregazione in base alla media.

   ![Screenshot del grafico che ora visualizza la media di Units Sold by Product.](media/service-aggregates/power-bi-aggregate-average-2.png)

## <a name="ways-to-aggregate-your-data"></a>Modi per aggregare i dati

Alcune opzioni possono essere disponibili per l'aggregazione di un campo:

- **Non riepilogare**. Se si sceglie questa opzione, Power BI considera separatamente ogni valore nel campo e non li riepiloga. Usare questa opzione in presenza di una colonna di ID numerici che non devono essere sommati dal servizio.

- **Somma**. Somma tutti i valori di un campo.

- **Media**. Acquisisce una media aritmetica dei valori.

- **Minimo**. Mostra il valore più basso.

- **Massimo**. Mostra il valore più alto.

- **Conteggio (non vuoto)** . Conta il numero di valori non vuoti nel campo.

- **Conteggio (Distinct)** . Conta il numero di valori diversi nel campo.

- **Deviazione Standard**.

- **Varianza**.

- **Mediana**.  Mostra il valore mediano (intermedio). Questo valore ha lo stesso numero di elementi prima e dopo di esso.  Se sono presenti due mediane, Power BI ne calcola la media.

Ad esempio, questi dati:

| Country | Amount |
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

1. Trascinare il campo **Product** nell'area **Valori**. L'area **Valori** viene in genere usata per i campi numerici. Power BI riconosce che questo campo è un campo di testo, imposta l'aggregazione su **Non riepilogare** e presenta una tabella con una singola colonna.

   ![Screenshot del campo Product nell'area Valori.](media/service-aggregates/power-bi-aggregate-value.png)

1. Se si cambia l'aggregazione dal valore predefinito **Non riepilogare** a **Conteggio (Distinct)** , Power BI conta il numero di prodotti diversi. In questo caso ne sono presenti quattro.
  
   ![Screenshot del conteggio dei prodotti distinti.](media/service-aggregates/power-bi-aggregate-count.png)

1. E se si imposta l'aggregazione su **Conteggio**, Power BI conta il numero totale. In questo caso sono presenti sette voci per **Product**.

   ![Screenshot del conteggio dei prodotti.](media/service-aggregates/power-bi-aggregate-count-2.png)

1. Trascinando lo stesso campo, in questo caso **Product**, nell'area **Valori** e lasciando l'aggregazione predefinita **Non riepilogare**, Power BI suddivide il conteggio per prodotto.

   ![Screenshot del prodotto e del conteggio dei prodotti.](media/service-aggregates/power-bi-aggregate-final.png)

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi

D:  perché non è disponibile l'opzione **Non riepilogare**?

A:  il campo selezionato è probabilmente una misura calcolata o una misura avanzata creata in Excel o in [Power BI Desktop](../transform-model/desktop-measures.md). Ogni misura calcolata ha una propria formula hardcoded. Non è possibile modificare l'aggregazione usata da Power BI. Ad esempio, se si tratta di una somma, può essere solo una somma. Nell'elenco **Campi** le *misure calcolate* vengono visualizzate con il simbolo di calcolatrice.

D:  perché con un campo sicuramente **numerico** le uniche scelte disponibili sono **Conteggio** e **Conteggio valori univoci**?

R1:  è probabile che il proprietario del set di dati *non* abbia classificato il campo come numero. Ad esempio, se un set di dati include un campo **anno**, il proprietario del set di dati può categorizzare il valore come testo. In questo caso, è più probabile che Power BI applichi un conteggio al campo **anno** (ad esempio, il numero di persone nate nel 1974) ed meno probabile che Power BI esegua una somma o una media. Il proprietario del set di dati può aprire il set di dati in Power BI Desktop e usare la scheda **Creazione di modelli** per modificare il tipo di dati.

R2: se al campo è associata l'icona di calcolatrice, significa che si tratta di una *misura calcolata*. Ogni misura calcolata ha una propria formula hardcoded che può essere modificata solo dal proprietario del set di dati. Il calcolo usato da Power BI può essere un'aggregazione semplice come una media o una somma. Potrebbe anche trattarsi di un calcolo più complesso come la "percentuale del contributo alla categoria padre" o il "totale parziale dall'inizio dell'anno". Power BI non eseguirà la somma o la media dei risultati, ma ripeterà semplicemente il calcolo (usando la formula hardcoded) per ogni punto dati.

R3:  un'altra possibilità è che il campo sia stato inserito in un *bucket* che consente solo valori categorici.  In questo caso, le uniche opzioni disponibili saranno Conteggio e Conteggio valori univoci.

R4:  la quarta possibilità è che il campo venga usato per un asse. Su un asse di un grafico a barre, ad esempio, Power BI mostra una sola barra per ogni valore univoco e non applica alcuna aggregazione ai valori dei campi.

>[!NOTE]
>L'eccezione a questa regola è rappresentata dai grafici a dispersione, che *richiedono* valori aggregati per gli assi X e Y.

D:  Perché non è possibile aggregare campi di testo per le origini dati SQL Server Analysis Services (SSAS)?

A:  Le connessioni dinamiche ai modelli multidimensionali SSAS non consentono aggregazioni sul lato client, incluse quelle di tipo first, last, avg, min, max e sum.

D:  è disponibile un grafico a dispersione e si vuole che il campo *non* venga aggregato.  Come si procede?

A:  aggiungere il campo al bucket **Dettagli** e non ai bucket degli assi X o Y.

D:  quando si aggiunge un campo numerico a una visualizzazione, per la maggior parte dei campi di questo tipo l'aggregazione predefinita è la somma, ma per alcuni vengono eseguiti il conteggio, la media o altre aggregazioni.  Perché l'aggregazione predefinita non è sempre la stessa?

A:  i proprietari del set di dati possono impostare l'esecuzione del riepilogo predefinita per ogni campo. Se si è il proprietario di un set di dati, modificare il riepilogo predefinito nella scheda **Creazione di modelli** di Power BI Desktop.

D:  come può il proprietario di un set di dati assicurarsi che un campo non venga mai aggregato?

A:  in Power BI Desktop, nella scheda **Creazione di modelli**, impostare **Tipo di dati** su **Testo**.

D:  nell'elenco a discesa non è disponibile l'opzione **Non riepilogare**.

A:  provare a rimuovere il campo e ad aggiungerlo di nuovo.

Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)