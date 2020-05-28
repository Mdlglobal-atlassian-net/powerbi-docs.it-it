---
title: Consentire agli utenti di personalizzare gli oggetti visivi in un report
description: Consentire ai lettori di report di creare una propria visualizzazione di un report senza modificarlo.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/09/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: ab232d4e5b6d17e7f20ed8a41875ca47693eb285
ms.sourcegitcommit: 21b06e49056c2f69a363d3a19337374baa84c83f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2020
ms.locfileid: "83407603"
---
# <a name="let-users-personalize-visuals-in-a-report"></a>Consentire agli utenti di personalizzare gli oggetti visivi in un report

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Quando si condivide un report con un ampio pubblico, è possibile che alcuni utenti vogliano usare visualizzazioni leggermente diverse di particolari oggetti visivi. È possibile che vogliano sostituire le informazioni sull'asse, modificare il tipo di oggetto visivo o aggiungere informazioni alla descrizione comando. È difficile creare un unico oggetto visivo in grado di soddisfare i requisiti di tutti. Grazie a questa nuova funzionalità, è possibile offrire agli utenti la possibilità di esplorare e personalizzare gli oggetti visivi, il tutto nella visualizzazione di lettura del report. Possono modificare l'oggetto visivo nel modo desiderato e salvarlo come segnalibro per tornarci in seguito. Non è necessario avere l'autorizzazione di modifica per il report o rivolgersi all'autore del report per richiedere una modifica.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-visual.png" alt-text="Personalizzare un oggetto visivo":::
 
## <a name="what-report-consumers-can-change"></a>Cosa possono modificare gli utenti finali del report

Questa funzionalità consente agli utenti finali di ottenere ulteriori informazioni tramite l'esplorazione ad hoc degli oggetti visivi in un report di Power BI. Per informazioni su come usare questa funzionalità come utente finale, vedere [Personalizzare oggetti visivi in un report](../consumer/end-user-personalize-visuals.md). Questa funzionalità è ideale per gli autori di report che vogliono abilitare scenari di esplorazione di base per i lettori del report. Di seguito sono riportate le modifiche che i lettori di report possono eseguire:

- Modificare il tipo di visualizzazione
- Sostituire una misura o una dimensione
- Aggiungere o rimuovere una legenda
- Confrontare due o più misure
- Modificare le aggregazioni e così via.

Questa funzionalità non solo offre nuove opportunità di esplorazione, ma consente anche agli utenti finali di acquisire e condividere le modifiche in vari modi:

- Acquisire le modifiche
- Condividere le modifiche
- Reimpostare tutte le modifiche per un report
- Reimpostare tutte le modifiche per un oggetto visivo
- Cancellare le modifiche recenti

## <a name="turn-on-the-preview-feature"></a>Attivare la funzionalità di anteprima

Poiché questa funzionalità è in anteprima, è prima di tutto necessario attivare l'opzione della funzionalità. Passare a **File** > **Opzioni e impostazioni** > **Opzioni**. Nelle impostazioni **Globali**, in **Funzionalità di anteprima** assicurarsi che sia selezionata l'opzione **Personalizza oggetti visivi**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-preview-personalize-visual.png" alt-text="Attivare Personalizza oggetti visivi":::

Potrebbe essere necessario riavviare Power BI Desktop per visualizzare questa opzione nelle impostazioni per il file corrente.

## <a name="enable-personalization-in-a-report"></a>Abilitare la personalizzazione in un report

Dopo aver attivato l'opzione della funzionalità di anteprima, è necessario abilitarla in modo specifico per i report per i quali si vuole che gli utenti possano personalizzare gli oggetti visivi.

È possibile abilitare la funzionalità in Power BI Desktop o nel servizio Power BI.

### <a name="in-power-bi-desktop"></a>In Power BI Desktop

Per abilitare la funzionalità in Power BI Desktop, passare a **File** > **Opzioni e impostazioni** > **Opzioni** > **File corrente** > **Impostazioni report**. Verificare che l'opzione **Personalizza oggetti visivi (anteprima)** sia attivata.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-settings-personalize-visual.png" alt-text="Abilitare la personalizzazione in un report":::

### <a name="in-the-power-bi-service"></a>Nel servizio Power BI

Per abilitare invece la funzionalità nel servizio Power BI, passare a **Impostazioni** per il report.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-service-settings-personalize-visual.png" alt-text="Impostazioni del report nel servizio Power BI":::

Attivare **Personalizza oggetti visivi (anteprima)**  > **Salva**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-service-personalize-visual.png" alt-text="Attivare Personalizza oggetti visivi nel servizio":::

## <a name="select-visuals-that-can-be-personalized"></a>Selezionare gli oggetti visivi che possono essere personalizzati

Quando si abilita questa impostazione per un determinato report, per impostazione predefinita tutti gli oggetti visivi in tale report possono essere personalizzati. Se non si vuole che tutti gli oggetti visivi siano personalizzati, è possibile attivare o disattivare l'impostazione per ogni oggetto visivo.

Selezionare l'oggetto visivo > selezionare **Formato** nel riquadro **Visualizzazioni** > espandere **Intestazione oggetto visivo**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-format-visual-header-personalize.png" alt-text="Seleziona Intestazione oggetto visivo":::
 
Scorrere per impostare **Personalizza oggetto visivo** >  **Attiva** o **Disattiva**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-format-visual-personalize-on-off.png" alt-text="Dispositivo di scorrimento per attivare o disattivare la personalizzazione dell'oggetto visivo":::


## <a name="limitations-and-known-issues"></a>Limitazioni e problemi noti

Attualmente la funzionalità presenta alcune limitazioni di cui tenere conto.

- Questa funzionalità non è supportata per gli scenari di incorporamento, inclusa la funzionalità di pubblicazione sul Web.
- Le esplorazioni dell'utente non vengono mantenute automaticamente. È necessario salvare la visualizzazione come segnalibro personale per acquisire le modifiche.
- Non è possibile modificare gli oggetti visivi nelle app Power BI per dispositivi mobili. Tuttavia, qualsiasi modifica di un oggetto visivo salvata in un segnalibro personale nel servizio Power BI viene rispettata nelle app per dispositivi mobili.

Sono presenti anche alcuni problemi in corso di risoluzione:

- L'aggiunta di una gerarchia non è supportata. È necessario aggiungere i singoli elementi figlio.
- Non è possibile modificare una gerarchia di date in una data o viceversa. 
- Con i segnalibri personali si potrebbero ottenere risultati leggermente diversi in base alla sequenza selezionata. Le discrepanze sono possibili perché l'acquisizione non include lo stato completo del report, ma solo le modifiche apportate. La soluzione alternativa consiste nel selezionare **Ripristina impostazioni predefinite** e quindi selezionare il segnalibro che si vuole visualizzare. 

## <a name="next-steps"></a>Passaggi successivi

[Personalizzare oggetti visivi nei report](../consumer/end-user-personalize-visuals.md).     

Si consiglia di provare l'esperienza di personalizzazione degli oggetti visivi. Inviare commenti e suggerimenti su questa funzionalità e su come continuare a migliorarla nel [sito Power BI Ideas](https://ideas.powerbi.com/forums/265200-power-bi). 

Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)
