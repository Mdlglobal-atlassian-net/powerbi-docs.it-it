---
title: Usare i temi del dashboard nel servizio Power BI
description: Informazioni su come usare una tavolozza dei colori personalizzata e applicarla a un intero dashboard nel servizio Power BI
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/22/2018
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: e2793fe56df462fd5f1bd1c266b75ad14fd9b375
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "73877440"
---
# <a name="use-dashboard-themes-in-power-bi-service"></a>Usare i temi del dashboard nel servizio Power BI
I **temi del dashboard** consentono di applicare un colore del tema a un intero dashboard, ad esempio i colori aziendali, i colori della stagione o qualunque altro tema di colori. Quando si applica un **tema del dashboard**, tutti gli oggetti visivi del dashboard usano i colori del tema selezionato, salvo alcuni casi particolari descritti più avanti in questo articolo.

![esempio di dashboard con tema](media/service-dashboard-themes/power-bi-full-dashboard-theme.png)

La modifica dei colori degli oggetti visivi del report nel dashboard non condiziona gli oggetti visivi nel report. Quando si aggiungono i riquadri di un report in cui è già applicato un [tema del report](desktop-report-themes.md), è anche possibile scegliere di continuare a usare il tema corrente oppure scegliere il tema del dashboard.


## <a name="prerequisites"></a>Prerequisiti
* Per procedere, [aprire il dashboard Esempio di analisi di vendite e marketing](sample-datasets.md).


## <a name="how-dashboard-themes-work"></a>Funzionamento dei temi del dashboard
Per iniziare, aprire un dashboard creato, o un dashboard di cui si dispone dell'autorizzazione di modifico, che si vuole personalizzare. Selezionare **Altre opzioni** (...) e scegliere **Tema del dashboard**. 

![opzione Tema del dashboard](media/service-dashboard-themes/power-bi-dashboard-theme.png)

Nel riquadro del dashboard visualizzato selezionare uno dei temi predefiniti.  Nell'esempio seguente è stato selezionato il tema **Scuro**.

![Opzione Chiaro selezionata](media/service-dashboard-themes/power-bi-theme-menu.png)

![Opzione Scuro applicata](media/service-dashboard-themes/power-bi-theme-dark.png)

## <a name="create-a-custom-theme"></a>Creare un tema personalizzato

Il tema predefinito per i dashboard di Power BI è **Chiaro**. Per personalizzare i colori o crea un tema personalizzato, selezionare **Personalizzato** nell'elenco a discesa. 

![Selezionare Personalizzato dall'elenco a discesa](media/service-dashboard-themes/power-bi-theme-custom.png)

Usare le opzioni personalizzate per creare un tema del dashboard personalizzato. Se si aggiunge un'immagine di sfondo, è consigliabile che la risoluzione sia almeno 1920x1080. Per usare un'immagine come sfondo, caricare l'immagine da un sito Web pubblico, copiare l'URL e incollarlo nel campo **URL immagine**. 

### <a name="using-json-themes"></a>Uso di temi JSON
Un altro modo per creare un tema personalizzato consiste nel caricare un file JSON contenente le impostazioni per tutti i colori che si vogliono usare nel dashboard. In Power BI Desktop gli autori dei report usano file JSON per [creare temi per i report](desktop-report-themes.md). Questi stessi file JSON possono essere caricati per i dashboard oppure è possibile trovare e caricare i file JSON dalla [pagina della raccolta temi](https://community.powerbi.com/t5/Themes-Gallery/bd-p/ThemesGallery) nella community di Power BI 

![Sito della raccolta temi](media/service-dashboard-themes/power-bi-theme-gallery.png)

È anche possibile salvare il tema personalizzato come file JSON e condividerlo con altri autori di dashboard. 

### <a name="use-a-theme-from-the-theme-gallery"></a>Usa un tema dalla raccolta temi

Come accade con le opzioni predefinite e personalizzate, quando si carica il tema, i colori vengono automaticamente applicati a tutti i riquadri del dashboard. 

1. Passare il mouse su un tema e scegliere **Visualizzazione report**.

    ![Visualizzazione report](media/service-dashboard-themes/power-bi-choose-theme.png)

2. Scorrere verso il basso per trovare il collegamento al file JSON.  Selezionare l'icona di download e salvare il file.

    ![File JSON denominato Spring Day](media/service-dashboard-themes/power-bi-theme-json.png)

3. Tornare al servizio Power BI. Nella finestra Tema del dashboard Personalizzato selezionare **Carica il tema JSON**.

    ![Caricare il tema JSON](media/service-dashboard-themes/power-bi-upload-theme.png)

4. Scegliere il percorso in cui è stato salvato il file del tema JSON e selezionare **Apri**.

5. Nella pagina Tema del dashboard selezionare **Salva**. Il nuovo tema sarà applicato al dashboard.

    ![nuovo tema applicato](media/service-dashboard-themes/power-bi-json.png)

## <a name="considerations-and-limitations"></a>Considerazioni e limitazioni

* Se il report usa un tema diverso da quello del dashboard, è possibile controllare se l'oggetto visivo mantiene il tema corrente o usa quello del dashboard per rispettare la coerenza tra gli oggetti visivi di varie origini. Quando si aggiunge un riquadro a un dashboard, selezionare **Mantieni tema corrente** se si vuole mantenere il tema del report. L'oggetto visivo nel dashboard continuerà a usare il tema del report, incluse le impostazioni relative alla trasparenza. 

    Le opzioni di **Tema del riquadro** vengono visualizzate solo quando il report è stato creato in Power BI Desktop, [è stato aggiunto un tema del report](desktop-report-themes.md) e il report è stato pubblicato nel servizio Power BI. 

    ![Opzione Mantieni tema corrente selezionata](media/service-dashboard-themes/power-bi-keep-current.png)

    Riprovare aggiungendo il riquadro e selezionando **Usa tema di destinazione**.

    ![Usa tema di destinazione](media/service-dashboard-themes/power-bi-use-destination.png)

* I temi del dashboard non possono essere applicati a pagine dinamiche del report aggiunte, riquadri iFrame, riquadri SSRS, riquadri di cartelle di lavoro o immagini.
* I temi del dashboard possono essere visualizzati nei dispositivi mobili, ma un tema del dashboard può essere creato solo nel servizio Power BI. 
* I temi personalizzati del dashboard funzionano solo con i riquadri aggiunti dei report. 

