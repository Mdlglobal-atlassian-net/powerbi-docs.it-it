---
ms.openlocfilehash: 4c1a7bce8eb24534974fe6a06a8bada4ba9fb708
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61265117"
---
In questo argomento, approfondiremo lo svolgimento delle prime due fasi di Power BI:

* Creare un report in **Power BI Desktop**
* Pubblicare il report nel **servizio Power BI**

Inizieremo con Power BI Desktop selezionando **Recupera dati**. Verrà visualizzata la raccolta di origini dati che consentirà di scegliere un'origine dati. L'immagine seguente mostra la selezione di una pagina Web come origine. Nel video precedente, Will ha selezionato una cartella di lavoro di **Excel**.

![](media/0-2-get-started-power-bi-desktop/c0a2_1.png)

A prescindere dall'origine dati selezionata, Power BI si connette all'origine dati e mostra i dati disponibili. L'immagine seguente è un altro esempio da una pagina Web che analizza diversi paesi e alcune statistiche interessanti sul pensionamento.

![](media/0-2-get-started-power-bi-desktop/c0a2_2.png)

Nella vista **Report** di Power BI Desktop è possibile iniziare a creare report.

La vista **Report** include cinque aree principali:

1. La barra multifunzione, che mostra le attività comuni associate ai report e alle visualizzazioni.
2. La vista **Report** , o area di disegno, dove vengono create e disposte le visualizzazioni.
3. La scheda **Pagine** nella parte inferiore, che consente di selezionare o aggiungere una pagina del report.
4. Il riquadro **Visualizzazioni** , dove è possibile modificare le visualizzazioni, personalizzare i colori o gli assi, applicare filtri, trascinare i campi e altro ancora.
5. Il riquadro **Campi** in cui gli elementi della query e i filtri possono essere trascinati nella vista **Report** oppure nell'area **Filtri** del riquadro **Visualizzazioni** .

![](media/0-2-get-started-power-bi-desktop/c0a2_3.png)

I riquadri **Visualizzazioni** e **Campi** possono essere compressi selezionando la piccola freccia lungo il bordo, in modo da ottenere più spazio nella vista **Report** per la creazione di visualizzazioni accattivanti. Quando si modificano le visualizzazioni, vengono visualizzate anche queste frecce rivolte verso l'alto o verso il basso, che indicano che è possibile espandere o comprimere la sezione.

![](media/0-2-get-started-power-bi-desktop/c0a2_4.png)

Per creare una visualizzazione, trascinare un campo dall'elenco **Campi** alla vista **Report** . In questo caso, trascinare il campo State da *RetirementStats* e vedere che cosa succede.

![](media/0-2-get-started-power-bi-desktop/c0a2_5.png)

Osservare cosa accade... Power BI Desktop ha creato automaticamente una visualizzazione basata su mappa, dopo aver riconosciuto che il campo State includeva dati di georilevazione.

Andiamo rapidamente avanti e, dopo aver creato un report con alcune visualizzazioni, saremo pronti per pubblicarlo nel servizio Power BI. Nella barra multifunzione **Home** in Power BI Desktop selezionare **Pubblica**.

![](media/0-2-get-started-power-bi-desktop/c0a2_6.png)

Verrà richiesto di accedere a Power BI.

![](media/0-2-get-started-power-bi-desktop/c0a2_7.png)

Dopo che l'accesso è stato effettuato e il processo di pubblicazione è stato completato, viene visualizzata la finestra di dialogo seguente. Selezionare il collegamento riportato sotto **Operazione riuscita** per passare al servizio Power BI dove visualizzare il report appena pubblicato.

![](media/0-2-get-started-power-bi-desktop/c0a2_8.png)

Quando si accede a Power BI, è possibile visualizzare il file Power BI Desktop appena pubblicato nel servizio. Nell'immagine riportata sotto, il report creato in Power BI Desktop viene visualizzato nella sezione **Report**.

![](media/0-2-get-started-power-bi-desktop/c0a2_9.png)

Nel report è possibile scegliere l'icona a forma di **puntina** per aggiungere l'oggetto visivo a un dashboard. L'immagine seguente mostra l'icona a forma di puntina evidenziata da una casella colorata e una freccia.

![](media/0-2-get-started-power-bi-desktop/c0a2_10.png)

Selezionandola, verrà visualizzata la finestra di dialogo seguente, che consentirà di aggiungere l'oggetto visivo a un dashboard esistente o di creare un nuovo dashboard.

![](media/0-2-get-started-power-bi-desktop/c0a2_11.png)

Quando si aggiungono oggetti visivi ricavati dal report, è possibile visualizzarli nel dashboard.

![](media/0-2-get-started-power-bi-desktop/c0a2_12.png)

Si può fare molto di più con Power BI, naturalmente, ad esempio condividere i dashboard creati. Parleremo della condivisione più avanti in questo corso.

Successivamente, esamineremo una funzionalità che consente di creare automaticamente i dashboard semplicemente tramite la connessione a un servizio cloud come Facebook, Salesforce e molti altri.

