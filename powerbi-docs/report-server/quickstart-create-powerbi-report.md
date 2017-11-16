---
title: 'Avvio rapido: Creare un report di Power BI per il server di report di Power BI'
description: Informazioni su come creare un report di Power BI per il server di report di Power BI in pochi semplici passi.
services: powerbi
documentationcenter: 
author: maggiesMSFT
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/28/2017
ms.author: maggies
ms.openlocfilehash: e492d31a8e1ed57a769c9a36f515d99369f6d6dc
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2017
---
# <a name="quickstart-create-a-power-bi-report-for-power-bi-report-server"></a>Avvio rapido: Creare un report di Power BI per il server di report di Power BI
È possibile archiviare e gestire report di Power BI nel portale Web del Server di report di Power BI, proprio come nel cloud nel servizio Power BI (https://powerbi.com). È possibile creare e modificare i report in Power BI Desktop e pubblicarli nel portale Web. Quindi, i lettori dei report nell'organizzazione possono visualizzarli in un browser oppure in un'app Power BI per dispositivi mobili su un dispositivo mobile.

![Report di Power BI nel portale Web](media/quickstart-create-powerbi-report/report-server-powerbi-report.png)

Se sono già stati creati report di Power BI in Power BI Desktop, si è pronti a creare report di Power BI per il server di report di Power BI. In caso contrario, ecco quattro passaggi rapidi per iniziare.

## <a name="step-1-install-power-bi-desktop-report-server"></a>Passaggio 1: Installare Power BI Desktop (server di report)
Si potrebbe già avere installato Power BI Desktop per creare report per il servizio Power BI. Si consiglia di installare la versione di Power BI Desktop ottimizzata per il server di report di Power BI: in tal modo, ci si assicura che il server e l'app siano sempre sincronizzati. È possibile avere entrambe le versioni di Power BI Desktop nello stesso computer.

1. Nel portale Web del Server di report di Power BI selezionare **Nuovo** > **Report di Power BI**.
   
    ![Nuovo report di Power BI](media/quickstart-create-powerbi-report/report-server-web-portal-new-powerbi-report.png)
   
    Se non si ha accesso al portale Web del Server di report di Power BI, visitare l'Area download Microsoft e scaricare [Microsoft Power BI Desktop](https://go.microsoft.com/fwlink/?linkid=837581) (ottimizzato per il server di report di Power BI - GA giugno 2017).
2. Al termine del processo di installazione, selezionare **Start Power BI Desktop now**.
   
    Verrà avviato automaticamente e si è pronti per iniziare. Per determinare se la versione in uso è quella corretta, verificare che nella barra del titolo sia presente "Power BI Desktop (Report Server)" (Power BI Desktop - Server di report).
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
I report nel server di report di Power BI e nel servizio Power BI (http://powerbi.com) operano quasi esattamente allo stesso modo, ma alcune funzionalità sono diverse.

### <a name="in-a-browser"></a>In un browser
I report del server di report di Power BI supportano tutte le visualizzazioni, tra cui:

* Oggetti visivi personalizzati

I report del server di report di Power BI non supportano:

* Oggetti visivi R
* Mappe di ArcGIS
* Percorsi di navigazione

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
* Apprendimento guidato: [Introduzione a Power BI Desktop](../guided-learning/gettingdata.yml#step-2)

### <a name="power-bi-report-server"></a>Server di report Power BI
* [Installare Power BI Desktop ottimizzato per il server di report di Power BI](install-powerbi-desktop.md)  
* [Manuale per l'utente del server di report di Power BI](user-handbook-overview.md)  

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)