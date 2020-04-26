---
title: Copiare e incollare una visualizzazione in Power BI
description: Copiare e incollare una visualizzazione in Power BI
author: mihart
ms.reviewer: maggie tsang
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/13/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 03ce7f2a8ccd2c453521d28d172ffb25c1bb28bf
ms.sourcegitcommit: b2cb0b02bdc451bf11a92a68f2c4d560a811f563
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2020
ms.locfileid: "81440308"
---
# <a name="copy-and-paste-a-report-visualization"></a>Copiare e incollare una visualizzazione di report

[!INCLUDE[consumer-appliesto-yyyn](../includes/consumer-appliesto-yyyn.md)]

Questo articolo illustra due modi diversi per copiare e incollare un oggetto visivo. 
* copiare un oggetto visivo in un report e incollarlo in un'altra pagina del report (sono necessarie le autorizzazioni di modifica per il report)

* copiare un'immagine di un oggetto visivo da Power BI negli Appunti e incollarla in altre applicazioni

## <a name="copy-and-paste-within-the-same-report"></a>Copiare e incollare nello stesso report
Gli oggetti visivi nei report di Power BI possono essere copiati da una pagina del report alla stessa pagina o a una pagina diversa nello stesso report. 

Per copiare e incollare una visualizzazione sono necessarie autorizzazioni di modifica per il report. Nel servizio Power BI è necessario aprire il report in [Visualizzazione di modifica](../consumer/end-user-reading-view.md). 

Le visualizzazioni nei *dashboard* non possono essere copiate e incollate nei report di Power BI o in altri dashboard.

1. Aprire un report che include almeno una visualizzazione.  

2. Selezionare la visualizzazione e usare **CTRL+C** per copiare e **CTRL+V** per incollare.      

   ![breve video che illustra come copiare e incollare](media/power-bi-visualization-copy-paste/copypasteviznew.gif)


## <a name="copy-a-visual-as-an-image-to-your-clipboard"></a>Copiare un oggetto visivo come immagine negli Appunti

Può essere utile condividere un'immagine da un report o un dashboard di Power BI. È ora possibile copiare l'oggetto visivo e incollarlo in un'altra applicazione che supporta il comando Incolla. 

Quando si copia un'immagine statica di un oggetto visivo, si ottiene una copia dell'oggetto visivo insieme ai metadati. Ciò include:
* collegamento al report o al dashboard di Power BI di origine
* titolo del report o del dashboard
* avviso per segnalare la presenza di informazioni riservate nell'immagine
* data/ora dell'ultimo aggiornamento
* filtri applicati all'oggetto visivo

### <a name="copy-from-a-dashboard-tile"></a>Eseguire la copia da un riquadro del dashboard

1. Passare al dashboard da cui si vuole eseguire la copia.

2. Nell'angolo superiore destro dell'oggetto visivo selezionare **Altre opzioni (...)** e scegliere **Copia oggetto visivo come immagine**. 

    ![Icona Copia oggetto visivo come immagine visualizzata](media/power-bi-visualization-copy-paste/power-bi-copy-dashboard.png)

3. Quando viene visualizzata la finestra di dialogo **L'oggetto visivo è pronto per la copia** selezionare **Copia negli Appunti**.

    ![finestra di dialogo con l'opzione Copia negli Appunti](media/power-bi-visualization-copy-paste/power-bi-copied.png)

4. Quando l'oggetto visivo è pronto, incollarlo in un'altra applicazione usando **CTRL+V** oppure fare clic con il pulsante destro del mouse e scegliere Incolla. Nello screenshot seguente l'oggetto visivo è stato incollato in Microsoft Word. 

    ![oggetto visivo incollato in Word](media/power-bi-visualization-copy-paste/power-bi-paste-word.png)

### <a name="copy-from-a-report-visual"></a>Eseguire la copia da un oggetto visivo in un report 

1. Passare al report da cui si vuole eseguire la copia.

2. Nell'angolo superiore destro dell'oggetto visivo selezionare l'icona **Copia oggetto visivo come immagine**. 

    ![Icona Copia oggetto visivo come immagine visualizzata](media/power-bi-visualization-copy-paste/power-bi-copy-icon.png)

3. Quando viene visualizzata la finestra di dialogo **L'oggetto visivo è pronto per la copia** selezionare **Copia negli Appunti**.

    ![finestra di dialogo con l'opzione Copia negli Appunti](media/power-bi-visualization-copy-paste/power-bi-copied.png)


4. Quando l'oggetto visivo è pronto, incollarlo in un'altra applicazione usando **CTRL+V** oppure fare clic con il pulsante destro del mouse e scegliere Incolla. Nello screenshot seguente l'oggetto visivo è stato incollato in un messaggio di posta elettronica.

    ![oggetto visivo incollato in Outlook](media/power-bi-visualization-copy-paste/power-bi-copy-email.png)

5. Se al report è stata applicata un'etichetta di riservatezza dei dati, si riceverà un avviso quando si seleziona l'icona di copia.  

    ![avviso per dati sensibili](media/power-bi-visualization-copy-paste/power-bi-sensitive.png)

    Verrà aggiunta un'etichetta di riservatezza ai metadati sotto l'oggetto visivo incollato. 

    ![oggetto visivo con etichetta per informazioni riservate](media/power-bi-visualization-copy-paste/power-bi-confidential.png)

### <a name="manage-use-of-copying-a-visual-as-an-image"></a>Gestire l'uso della copia di un oggetto visivo come immagine
Se si è proprietari del contenuto o si è un amministratore del tenant, è possibile controllare se un oggetto visivo può essere copiato come immagine da un report o da un dashboard.

#### <a name="disable-copy-as-an-image-for-a-specific-visual"></a>Disabilitare la copia come immagine per un oggetto visivo specifico
Se non si vuole che gli utenti possano copiare un oggetto visivo specifico, è possibile rimuovere l'icona di copia da tale oggetto visivo.
1. Selezionare l'icona del rullo per aprire il riquadro Formattazione. 

1. Aprire la scheda **Formattazione** per l'oggetto visivo.
1. Scorrere verso il basso fino a **Intestazione oggetto visivo**, espandere la scheda e disattivare **Icona Copia**.

    ![icona del rullo selezionata e icona di copia selezionata](media/power-bi-visualization-copy-paste/power-bi-visual-header.png)

1. Se non è possibile trovare l'impostazione **Intestazione oggetto visivo** attivare l'opzione per l'intestazione moderna dell'oggetto visivo in **Impostazioni report**. 

    ![opzione per abilitare l'intestazione moderna dell'oggetto visivo selezionata](media/power-bi-visualization-copy-paste/power-bi-use-modern.png)

1. Salvare le modifiche. Ricondividere e ripubblicare se necessario.

#### <a name="disable-copy-as-an-image-for-a-group-of-users"></a>Disabilitare la copia come immagine per un gruppo di utenti

Se si è proprietari del contenuto o si è un amministratore del tenant, è possibile controllare chi può copiare gli oggetti visivi. Questa impostazione disabilita la *copia di oggetti visivi come immagine* per tutto il contenuto accessibile per gli utenti nel tenant di Power BI.
  
1. Passare al portale di amministrazione.

1. In **Impostazioni tenant** selezionare **Impostazioni di esportazione e condivisione**. 

    ![abilitare Copy and paste visuals (Copiare e incollare oggetti visivi)](media/power-bi-visualization-copy-paste/power-bi-enable.png)

1. Disabilitare **Copy and paste visuals** (Copiare e incollare oggetti visivi) per gruppi di utenti selezionati. 

1. Salvare le modifiche. I gruppi specificati non potranno usare l'opzione **Copia oggetto visivo come immagine** in tutto Power BI. 
  

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi

   ![copia non disponibile](media/power-bi-visualization-copy-paste/power-bi-copy-grey.png)


D: Perché l'icona Copia è disabilitata per un oggetto visivo?    
R: Attualmente sono supportati gli oggetti visivi di Power BI nativi e gli oggetti visivi certificati. È disponibile un supporto limitato per oggetti visivi specifici, tra cui: 
- ESRI e altri oggetti visivi Mappa 
- Oggetti visivi Python 
- Oggetti visivi R 
- PowerApps 
- Oggetti visivi personalizzati non certificati Per ottenere il supporto di oggetti visivi personalizzati, vedere le informazioni su [come certificare gli oggetti visivi personalizzati](../developer/visuals/power-bi-custom-visuals-certified.md). 


D: Perché l'oggetto visivo non viene incollato correttamente?    
R: Esistono alcune limitazioni per la copia di un oggetto visivo come immagine, tra cui: 
- Per gli oggetti visivi personalizzati 
    - Oggetti visivi con temi e colori applicati 
    - Ridimensionamento del riquadro quando si incolla 
    - Oggetti visivi personalizzati con animazioni 
- Vincoli per la copia 
    - Non è possibile copiare un riquadro del dashboard appena bloccato in alto 
    - Non è possibile reindirizzare gli utenti a contenuto con filtri OData e stati permanenti, ad esempio segnalibri personali 
- Le applicazioni con supporto limitato per incollare contenuto in formato HTML dagli Appunti potrebbero non eseguire il rendering di tutti gli elementi copiati dall'oggetto visivo 



## <a name="next-steps"></a>Passaggi successivi
Altre informazioni sulle [visualizzazioni nei report di Power BI](power-bi-report-visualizations.md)

Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)

