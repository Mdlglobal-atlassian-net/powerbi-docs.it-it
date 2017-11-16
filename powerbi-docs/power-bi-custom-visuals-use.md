---
title: Aggiungere un oggetto visivo personalizzato a un report (Desktop)
description: Aggiungere un oggetto visivo personalizzato a un report in Desktop
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: complete
qualitydate: 03/15/2016
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/27/2017
ms.author: mihart
ms.openlocfilehash: b3a3e34fac546ee57cd66924e72a2c93aa647850
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2017
---
# <a name="add-a-custom-visual-to-a-report-desktop"></a>Aggiungere un oggetto visivo personalizzato a un report (Desktop)
È stato [scaricato un modello di oggetto visivo personalizzato](service-custom-visuals-office-store.md) ed è stato salvato nel computer o in un'altra posizione.  Il passaggio successivo consiste nell'importare il modello visivo personalizzato in un report in modo da aggiungerlo eventualmente al riquadro Visualizzazione.

![](media/power-bi-custom-visuals-use/pbi-custom-viz-icon.png)

un modello di oggetto visivo personalizzato viene aggiunto a un determinato report durante l'importazione. Se si vuole usare l'oggetto visivo in un altro report, è necessario importarlo anche in tale report. Quando un report con un oggetto visivo personalizzato viene salvato usando l'opzione **Salva con nome**, una copia del modello di oggetto visivo personalizzato viene salvata con il nuovo report.

1. Aprire Power BI Desktop e selezionare il report in cui si vuole aggiungere una visualizzazione personalizzata.   
2. Per importare un modello di oggetto visivo personalizzato è possibile procedere in due modi: dal menu **File** o dal riquadro **Visualizzazioni**.
   
    **Dal menu file del Desktop**
   
    Nel menu **File** del report, scegliere **Importa** &gt; **Oggetto visivo personalizzato di Power BI**. È necessario essere in Visualizzazione di modifica.    
   
      ![](media/power-bi-custom-visuals-use/power-bi-import.png)
   
    **Dal riquadro Visualizzazioni**
   
    Nel riquadro **Visualizzazioni** scegliere **Inserisci (...)**.    
   
      ![](media/power-bi-custom-visuals-use/insertpane.png)
   
    Selezionare **Importa un oggetto visivo personalizzato**.  
   
      ![](media/power-bi-custom-visuals-use/insertpane.png)
3. **Esaminare l'avviso**.
   
    Un oggetto visivo personalizzato ha accesso ai dati nel report e quando si condivide un report contenente oggetti visivi personalizzati, i colleghi potrebbero riuscire ad accedere agli stessi dati. Prestare attenzione nell'esaminare l'oggetto visivo personalizzato per garantire che provenga da una fonte attendibile. Microsoft consiglia di collaborare con il reparto IT se non si è certi se usare uno specifico oggetto visivo personalizzato ottenuto da Office Store online, attraverso la posta elettronica o da un'altra origine.
   
    ![](media/power-bi-custom-visuals-use/caution.png)
4. Passare al percorso in cui è stato salvato il file degli oggetti visivi personalizzati con estensione pbiviz e aprirlo.
5. Un'icona (chiamata anche *modello*) verrà aggiunta al riquadro **Visualizzazioni**.
   
    ![](media/power-bi-custom-visuals-use/visualuse.png)
6. Selezionare il modello visivo personalizzato da aggiungere al report come si fa per qualsiasi altro modello nel riquadro Visualizzazioni. Aggiungere campi e filtri e compilare l'oggetto visivo.
7. Formattare l'oggetto visivo personalizzato come qualsiasi altro oggetto visivo.  Nel riquadro **Visualizzazioni** selezionare l'icona del rullo. Le opzioni di formattazione disponibili variano in base al tipo di oggetto visivo.

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi
* Se si vuole che gli oggetti visivi personalizzati siano supportati durante l'[esportazione in PowerPoint](service-publish-to-powerpoint.md) o [visualizzati nei messaggi di posta elettronica ricevuti quando un cliente effettua la sottoscrizione alle pagine del report](service-report-subscribe.md), è necessario definirli come *oggetti visivi certificati* che hanno superato il processo di certificazione degli oggetti visivi personalizzati Microsoft.  Per visualizzare l'elenco degli *oggetti visivi personalizzati certificati* e per informazioni sul processo di certificazione, vedere [Oggetti visivi certificati](power-bi-custom-visuals-certified.md)

## <a name="next-steps"></a>Passaggi successivi
[Scaricare e usare oggetti visivi personalizzati da Office Store](service-custom-visuals-office-store.md)  
[Aggiungere un oggetto visivo personalizzato a un report nel servizio Power BI](power-bi-report-add-custom-visual.md)  
[Pubblicare oggetti visivi personalizzati in Office Store](developer/office-store.md)  
[Visualizzazioni personalizzate in Power BI](power-bi-custom-visuals.md)  
Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

