---
title: Sviluppo per dispositivi mobili
description: Come creare oggetti visivi di Power BI per dispositivi mobili
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 03/12/2019
ms.openlocfilehash: 38e6ac3be143381304f1fdfc8e1427b91f398a9a
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82196630"
---
# <a name="how-to-create-mobile-friendly-power-bi-visuals"></a>Come creare oggetti visivi di Power BI per dispositivi mobili
L'utilizzo su dispositivi mobili ha un ruolo fondamentale in Power BI. Uno dei suoi punti di forza è la possibilità di rimanere connessi ai dati in qualsiasi momento e ovunque.

Gli sviluppatori di oggetti visivi di Power BI devono gestire i vincoli esclusivi di ogni dispositivo mobile per raggiungere il maggior numero possibile di utenti e offrire la migliore esperienza per dispositivi mobili.

Usare l'[app Power BI per Windows, iOS e Android](/power-bi/consumer/mobile/mobile-apps-for-mobile-devices) per consentire agli utenti aziendali di avere sempre i propri dati a portata di mano, anche quando non sono sul luogo di lavoro.

## <a name="requirements"></a>Requisiti

I requisiti seguenti sono essenziali per lo sviluppo di oggetti visivi per dispositivi mobili:

- Rendering

  Il rendering degli oggetti visivi di Power BI deve essere possibile su tutti i dispositivi mobili supportati, inclusi i browser e le applicazioni supportati, senza errori nei report e nei dashboard né quando è attiva la modalità **messa a fuoco**. 

- Interattività

  Le funzionalità interattive devono essere fornite nello stesso modo in cui vengono fornite per i dispositivi desktop. Tutti gli eventi gestiti nei browser desktop devono essere supportati o avere gestori di eventi analoghi per i dispositivi mobili.
  
  Ad esempio, la navigazione di base e la selezione dei punti dati devono avere le stesse funzionalità supportate dai browser desktop. Se un oggetto visivo supporta la selezione multipla tramite **CTRL**, lo sviluppatore deve prendere in considerazione l'aggiunta di un gestore eventi simile per i dispositivi mobili.

  La tabella seguente fornisce un elenco di eventi corrispondenti nei dispositivi mobili.

  | Nome evento del mouse | Nome evento di tocco |
  |:----------------:|:----------------:|
  | `click` | `click` |
  | `mousemove` | `touchmove` |
  | `mousedown` | `touchstart` |
  | `mouseup` | `touchend` |
  | `dblclick` | usare una libreria esterna |
  | `contextmenu` | usare una libreria esterna |
  | `mouseover` | `touchmove` |
  | `mouseout` | `touchmove` (o una libreria esterna) |
  | `wheel` | `NaN` |

  > [!NOTE]
  > Non tutti i dispositivi mobili o con touch screen supportano gli eventi del mouse (o con prefisso *mouse*). In questi casi, gestire gli eventi *mouse* e *touch* contemporaneamente.

## <a name="optional"></a>Facoltativo
Le impostazioni seguenti sono considerate facoltative e vengono usate per creare una migliore esperienza dell'utente finale.

- Rendering

  Per supportare oggetti visivi di dimensioni più piccole, provare ad aggiungere opzioni di formattazione che l'utente può modificare per regolare le dimensioni di ogni elemento. Ad esempio, aggiungere opzioni di formattazione alle etichette da usare nei report e nei dashboard. Questo consente agli utenti di personalizzare un oggetto visivo in modo specifico per il proprio dispositivo mobile.
  
  È possibile applicare le stesse impostazioni anche agli oggetti visivi nei browser desktop e, se necessario, eseguirne l'override per adattare l'oggetto visivo a schermi più piccoli.

  > [!NOTE]
  > Per ottimizzare un oggetto visivo in modalità **messa a fuoco**, occorre tenere in considerazione l'orientamento sia verticale che orizzontale dello schermo. Vedere [Visualizzare il contenuto in modo più dettagliato: modalità messa a fuoco e modalità schermo intero](/power-bi/consumer/end-user-focus).

- Interattività

  Prendere in considerazione l'aggiunta di gestori eventi specifici per i dispositivi mobili, come il trascinamento e lo scorrimento.

- Failover

  Se non è possibile eseguire il rendering di un oggetto visivo sul dispositivo mobile, dovrebbe essere visualizzato un messaggio di errore descrittivo.

## <a name="supported-browsers-and-devices"></a>Browser e dispositivi supportati
Deve essere possibile eseguire il rendering di un oggetto visivo di Power BI su tutti i dispositivi che supportano App di Power BI. Per altre informazioni, vedere [Browser supportati per Power BI](/power-bi/power-bi-browsers) e [Cosa sono le app Power BI per dispositivi mobili?](/power-bi/consumer/mobile/mobile-apps-for-mobile-devices).

Durante l'esecuzione di test sui modelli più recenti di dispositivi Windows, iOS e Android, lo sviluppatore deve tenere in considerazione la maggior parte di questi aspetti qualitativi.

## <a name="next-steps"></a>Passaggi successivi
Per iniziare, vedere [Esercitazione: Sviluppo di un oggetto visivo di Power BI](/power-bi/developer/visuals/custom-visual-develop-tutorial).
