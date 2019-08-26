---
title: Scaricare un report dal servizio Power BI in Power BI Desktop (anteprima)
description: Scaricare un report dal servizio Power BI in un file di Power BI Desktop
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/12/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 61fc821e63889951aefd0ef815f885ffa8a880cf
ms.sourcegitcommit: d12bc6df16be1f1993232898f52eb80d0c9fb04e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2019
ms.locfileid: "68994816"
---
# <a name="download-a-report-from-the-power-bi-service-to-power-bi-desktop-preview"></a>Scaricare un report dal servizio Power BI in Power BI Desktop (anteprima)
In Power BI Desktop è possibile pubblicare un report (un file con estensione *pbix*) dal computer locale al servizio Power BI. I report di Power BI possono essere scaricati anche nell'altra direzione, ovvero dal servizio Power BI a Power BI Desktop. L'estensione per un report Power BI, in entrambi i casi, è pbix.

Occorre tenere presenti alcune limitazioni e considerazioni, che verranno discusse più avanti in questo articolo.

![Elenco a discesa File](media/service-export-to-pbix/power-bi-file-export.png)

## <a name="download-the-report-as-a-pbix-file"></a>Scaricare il report come file con estensione pbix

È possibile scaricare e aggiornare solo i report [creati con Power BI Desktop](guided-learning/publishingandsharing.yml?tutorial-step=2) dopo il 23 novembre 2016. Se un report è stato creato prima di tale data, la voce di menu **Scarica report** nel servizio Power BI è inattiva.

Per scaricare il file con estensione pbix, seguire questi passaggi:

1. Nel servizio Power BI aprire il report che si vuole scaricare in [Visualizzazione di modifica](https://docs.microsoft.com/power-bi/service-interact-with-a-report-in-editing-view).

2. Nella barra di spostamento superiore selezionare **File > Scarica report**.
   
3. Durante il download del report, un banner indica lo stato di avanzamento. Quando il file è pronto, viene chiesto dove salvare il file con estensione pbix. Il nome predefinito del file corrisponde al titolo del report.
   
4. Se non è già stato fatto, [installare Power BI Desktop](desktop-get-the-desktop.md), quindi aprire il file con estensione pbix in Power BI Desktop.
   
    Quando si apre il report in Power BI Desktop, può essere visualizzato un messaggio di avviso che informa che alcune funzionalità disponibili nel report del servizio Power BI non sono disponibili in Power BI Desktop.
   
    ![Finestra di dialogo di avviso](media/service-export-to-pbix/power-bi-export-to-pbix_2.png)

5. L'editor di report in Power BI Desktop è simile all'editor di report nel servizio Power BI.  
   
    ![Editor di report di Power BI Desktop](media/service-export-to-pbix/power-bi-desktop.png)

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi
Al download di un file con estensione pbix dal servizio Power BI sono associate alcune importanti considerazioni e limitazioni.

* Per scaricare il file, è necessario avere l'accesso in modifica al report.
* Il report deve essere stato creato usando Power BI Desktop ed essere stato *pubblicato* nel servizio Power BI oppure il file con estensione pbix deve essere stato *caricato* nel servizio Power BI.
* I report devono essere stati pubblicati o aggiornati dopo il 23 novembre 2016. I report pubblicati in precedenza non sono scaricabili.
* Questa funzionalità non funzionerà con i report e i pacchetti di contenuto creati in origine nel servizio Power BI.
* Per aprire i file scaricati, usare sempre la versione più recente di Power BI Desktop. Potrebbe non essere possibile aprire i file PBIX scaricati nelle versioni non correnti di Power BI Desktop.
* Se l'amministratore ha disattivato la possibilità di scaricare i dati, questa funzionalità non sarà visibile nel servizio Power BI.
* I set di dati con aggiornamento incrementale non possono essere scaricati in un file con estensione pbix.

## <a name="next-steps"></a>Passaggi successivi
Visualizzare il video di **Guy in a Cube** (durata: 1 minuto) che illustra questa funzionalità:

<iframe width="560" height="315" src="https://www.youtube.com/embed/ymWqU5jiUl0" frameborder="0" allowfullscreen></iframe>

Ecco alcuni articoli supplementari che possono essere d'aiuto per imparare a usare il servizio Power BI:

* [Report in Power BI](consumer/end-user-reports.md)
* [Concetti di base del servizio Power BI](service-basic-concepts.md)

Dopo aver installato Power BI Desktop, vedere l'articolo seguente per imparare a svolgere rapidamente le attività iniziali:

* [Introduzione a Power BI Desktop](desktop-getting-started.md)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/).

