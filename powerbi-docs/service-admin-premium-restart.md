---
title: Riavviare una capacità Power BI Premium
description: Informazioni su come riavviare una capacità Power BI Premium per risolvere i problemi di prestazioni.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 02/05/2019
LocalizationGroup: Premium
ms.openlocfilehash: 214b9fe48d5254e1bd2d436dd873b3c2d1d35f98
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65564926"
---
# <a name="restart-a-power-bi-premium-capacity"></a>Riavviare una capacità Power BI Premium

L'amministratore di Power BI potrebbe avere l'esigenza di riavviare una capacità Premium. In questo articolo viene illustrato come riavviare una capacità e vengono affrontate alcune domande sul riavvio e le prestazioni.

## <a name="why-does-power-bi-provide-this-option"></a>Perché Power BI offre questa opzione?

Power BI offre agli utenti la possibilità di eseguire analisi complesse su grandi quantità di dati. Gli utenti possono però provocare problemi di prestazioni sovraccaricando il servizio Power BI con processi, scrittura di query troppo complesse, creazione di riferimenti circolari e così via.

La capacità condivisa di Power BI offre un certo livello di protezione da tali eventi imponendo limiti a dimensioni dei file, pianificazioni degli aggiornamenti e altri aspetti del servizio. In una capacità Power BI Premium, al contrario, la maggior parte di questi limiti vengono aumentati. Un singolo report con un'espressione DAX non valida o un modello molto complesso possono pertanto provocare significativi problemi delle prestazioni. Durante l'elaborazione, il report può consumare tutte le risorse disponibili nella capacità. 

Power BI è oggetto di costanti miglioramenti per proteggere gli utenti della capacità Premium da questo tipo di problemi. Microsoft sta anche offrendo agli amministratori gli strumenti necessari per rilevare quando e perché le capacità vengono sovraccaricate. Per altre informazioni, vedere la [sessione di training breve](https://www.youtube.com/watch?v=UgsjMbhi_Bk&feature=youtu.be) e la [sessione di training lunga](https://www.microsoft.com/businessapplicationssummit/video/BAS2018-2174). È allo stesso tempo necessario avere la possibilità di limitare i problemi significativi quando si verificano. Il modo più rapido per attenuare questi problemi è riavviare la capacità.

## <a name="is-the-restart-process-safe-will-i-lose-any-data"></a>Il processo di riavvio è sicuro? Si perderanno dati?

Tutti i dati, le definizioni, i report e i dashboard salvati nella capacità rimangono completamente invariati dopo il riavvio. Quando si riavvia una capacità, tutti gli aggiornamenti pianificati e ad hoc in corso vengono arrestati. Il servizio tenta di ripetere gli aggiornamenti quando la capacità è disponibile. Gli utenti che interagiscono con la capacità perderanno il lavoro non salvato. Dovranno aggiornare i browser dopo aver completato il riavvio.

## <a name="how-do-i-restart-a-capacity"></a>Come riavviare una capacità?

Seguire questi passaggi per riavviare una capacità.

1. Nella scheda **Impostazioni di capacità** del portale di amministrazione di Power BI andare alla capacità. 

1. Aggiungere il *flag della funzionalità* **CapacityRestart** all'URL della propria capacità: https://app.powerbi.com/admin-portal/capacities/<YourCapacityId>?capacityRestartButton=true.

1. In **Impostazioni avanzate** > **RIAVVIO DELLA CAPACITÀ** selezionare **Riavvia la capacità**.

    ![Riavvia la capacità](media/service-admin-premium-restart/restart-capacity.png)

1. Nella finestra di dialogo **Riavvio della capacità** selezionare **Sì, riavvia la capacità**.

    ![Conferma del riavvio](media/service-admin-premium-restart/confirm-restart.png)

## <a name="how-can-i-prevent-issues-from-happening-in-the-future"></a>Come si possono impedire problemi in futuro?

Il modo migliore per evitare problemi è informare gli utenti sulla modellazione efficace dei dati. Per altre informazioni, vedere la nostra [sessione di training](https://www.microsoft.com/businessapplicationssummit/video/BAS2018-2170).

È anche consigliabile [monitorare le capacità](service-admin-premium-monitor-capacity.md) regolarmente per individuare eventuali tendenze indicative di problemi sottostanti. Si prevedono rilasci regolari dell'app di monitoraggio e altri strumenti che consentono di monitorare e gestire con maggior efficacia le capacità.

## <a name="next-steps"></a>Passaggi successivi

[Che cos'è Power BI Premium?](service-premium-what-is.md)

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)
