---
title: Creare un report di Power BI per Server di report di Power BI
description: Informazioni su come creare un report di Power BI per il server di report di Power BI in pochi semplici passi.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 05/18/2018
ms.author: maggies
ms.openlocfilehash: 0debedc6e768fb3158ebe5cb4bf820ed3dc14a58
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2018
ms.locfileid: "34481418"
---
# <a name="create-a-power-bi-report-for-power-bi-report-server"></a>Creare un report di Power BI per Server di report di Power BI
È possibile archiviare e gestire report di Power BI nel portale Web del Server di report di Power BI, proprio come nel cloud nel servizio Power BI (https://powerbi.com)). È possibile creare e modificare i report in Power BI Desktop e pubblicarli nel portale Web. Quindi, i lettori dei report nell'organizzazione possono visualizzarli in un browser oppure in un'app Power BI per dispositivi mobili su un dispositivo mobile.

![Report di Power BI nel portale Web](media/quickstart-create-powerbi-report/report-server-powerbi-report.png)

Ecco quattro passaggi rapidi per iniziare.

## <a name="step-1-install-power-bi-desktop-optimized-for-power-bi-report-server"></a>Passaggio 1: Installare Power BI Desktop ottimizzato per il server di report di Power BI

Se sono già stati creati report di Power BI in Power BI Desktop, si è quasi pronti per creare report di Power BI per il server di report di Power BI. Si consiglia di installare la versione di Power BI Desktop ottimizzata per il server di report di Power BI: in tal modo, ci si assicura che il server e l'app siano sempre sincronizzati. È possibile avere entrambe le versioni di Power BI Desktop nello stesso computer.

1. Nel portale Web del server di report selezionare la freccia **Scarica** > **Power BI Desktop**.

    ![Scaricare Power BI Desktop dal portale Web](media/quickstart-create-powerbi-report/report-server-download-web-portal.png)

    In alternativa, passare direttamente a [Microsoft Power BI Desktop](https://www.microsoft.com/download/details.aspx?id=56723) (ottimizzato per il server di report di Power BI - marzo 2018) nell'Area download Microsoft.

2. Nella pagina dell'Area download selezionare **Scarica**.

3. In base al computer specifico, selezionare:

    - **PBIDesktopRS.msi** (versione a 32 bit) oppure

    - **PBIDesktopRS_x64.msi** (versione a 64 bit).

4. Dopo il download del programma di installazione, eseguire l'installazione guidata di Power BI Desktop (marzo 2018).

2. Al termine dell'installazione, selezionare **Avvia Power BI Desktop**.
   
    Verrà avviato automaticamente e si è pronti per iniziare. Per determinare se la versione in uso è quella corretta, verificare che nella barra del titolo sia presente "Power BI Desktop (marzo 2018)".

    ![Power BI Desktop versione di marzo 2018](media/quickstart-create-powerbi-report/report-server-desktop-march-2018.png)

3. Se non si ha familiarità con Power BI Desktop, è consigliabile guardare i video nella schermata iniziale.
   
    ![Schermata iniziale di Power BI Desktop](media/quickstart-create-powerbi-report/report-server-powerbi-desktop-start.png)

## <a name="step-2-select-a-data-source"></a>Passaggio 2: Selezionare un'origine dati
È possibile connettersi a una vasta gamma di origini dati. Altre informazioni sulla [connessione alle origini dati](connect-data-sources.md).

1. Nella schermata iniziale selezionare **Recupera dati**.
   
    In alternativa, nella schermata **Home** selezionare **Recupera dati**.
2. Selezionare l'origine dati, in questo esempio **Analysis Services**.
   
    ![Selezionare l'origine dati](media/quickstart-create-powerbi-report/report-server-get-data-ssas.png)
3. Compilare i campi **Server** e, facoltativamente, **Database**. Assicurarsi che **Connessione dinamica** sia selezionato > **OK**.
   
    ![Nome del server](media/quickstart-create-powerbi-report/report-server-ssas-server-name.png)
4. Scegliere il server di report in cui si salveranno i report.
   
    ![Selezione del server di report](media/quickstart-create-powerbi-report/report-server-select-server.png)

## <a name="step-3-design-your-report"></a>Passaggio 3: Progettare il report
Qui la cosa si fa interessante, perché si è giunti al momento di creare oggetti visivi per illustrare i propri dati.

Ad esempio, è possibile creare un grafico a imbuto di clienti e valori del gruppo in base al reddito annuo.

![Progettare un report](media/quickstart-create-powerbi-report/report-server-create-funnel.png)

1. In **Visualizzazioni**selezionare **Grafico a imbuto**.
2. Trascinare il campo da conteggiare nell'area **Valori**. Se non è un campo numerico, Power BI Desktop lo rende automaticamente un *Conteggio di* valore.
3. Trascinare il campo sul gruppo nell'area **Gruppo**.

Sono disponibili altre informazioni sulla [progettazione di un report di Power BI](../desktop-report-view.md).

## <a name="step-4-save-your-report-to-the-report-server"></a>Passaggio 4: Salvare il report nel server di report
Quando il report è pronto, salvarlo nel server di report di Power BI scelto nel passaggio 2.

1. Nel menu **File** selezionare **Salva con nome** > **Server di report di Power BI**.
   
    ![Salvataggio nel server di report](media/quickstart-create-powerbi-report/report-server-save-as-powerbi-report-server.png)
2. A questo punto è possibile visualizzarlo nel portale Web.
   
    ![Visualizzare il report nel portale Web](media/quickstart-create-powerbi-report/report-server-powerbi-report.png)

## <a name="considerations-and-limitations"></a>Considerazioni e limitazioni
I report nel server di report di Power BI e nel servizio Power BI (http://powerbi.com)) funzionano in modo quasi identico, ma alcune funzionalità sono diverse.

### <a name="in-a-browser"></a>In un browser
I report del server di report di Power BI supportano tutte le visualizzazioni, tra cui:

* Oggetti visivi personalizzati

I report del server di report di Power BI non supportano:

* Oggetti visivi R
* Mappe di ArcGIS
* Percorsi di navigazione
* Funzionalità in anteprima di Power BI Desktop

### <a name="in-the-power-bi-mobile-apps"></a>Nelle app Power BI per dispositivi mobili
I report del server di report di Power BI supportano tutte le funzionalità di base nelle [app Power BI per dispositivi mobili](../mobile-apps-for-mobile-devices.md), tra cui:

* [Layout del report per il telefono](../desktop-create-phone-report.md): è possibile ottimizzare un report per le app Power BI per dispositivi mobili. Sul telefono cellulare i report ottimizzati hanno un layout e un'icona speciale, ![Icona del layout del report per il telefono](media/quickstart-create-powerbi-report/power-bi-rs-mobile-optimized-icon.png).
  
    ![Report ottimizzati per i telefoni](media/quickstart-create-powerbi-report/power-bi-rs-mobile-optimized-report.png)

I report del server di report di Power BI non supportano queste funzionalità nelle app Power BI per dispositivi mobili:

* Oggetti visivi R
* Mappe di ArcGIS
* Oggetti visivi personalizzati
* Percorsi di navigazione
* Filtro geografico o codici a barre

## <a name="next-steps"></a>Passaggi successivi
### <a name="power-bi-desktop"></a>Power BI Desktop
Esistono tantissime ottime risorse per creare report in Power BI Desktop. Questi collegamenti sono un buon punto di partenza.

* [Introduzione a Power BI Desktop](../desktop-getting-started.md)
* Apprendimento guidato: [Introduzione a Power BI Desktop](../guided-learning/gettingdata.yml?tutorial-step=2)

### <a name="power-bi-report-server"></a>Server di report Power BI
* [Installare Power BI Desktop ottimizzato per il server di report di Power BI](install-powerbi-desktop.md)  
* [Che cos'è Server di report di Power BI?](get-started.md)  

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
