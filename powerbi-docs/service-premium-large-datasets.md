---
title: Supporto per set di dati di grandi dimensioni in Power BI Premium
description: Power BI Premium supporta set di dati di dimensioni fino a 10 GB.
services: powerbi
documentationcenter: 
author: MarkMcGeeAtAquent
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
ms.date: 12/11/2017
ms.author: v-mamcge
ms.openlocfilehash: 82ac4382fe80d83b60705f135b50738718f28876
ms.sourcegitcommit: 7eb15c813a0d14322cb1316bb7aab23cbc13aae6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/11/2017
---
# <a name="power-bi-premium-support-for-large-datasets"></a>Supporto per set di dati di grandi dimensioni in Power BI Premium

Power BI Premium supporta il caricamento di file di Power BI Desktop (.pbix) con dimensioni massime fino a 10 GB. Per usare un set di dati più grande, pubblicarlo in un'area di lavoro a cui è assegnata capacità Premium.
 
## <a name="best-practices"></a>Procedure consigliate

Questa sezione descrive le procedure consigliate per l'uso dei set di dati di grandi dimensioni.

**I modelli di grandi dimensioni utilizzano una quantità elevata di risorse** rispetto alla capacità. È quindi consigliabile usare almeno uno SKU P1 per i modelli con dimensioni maggiori di 1 GB. La tabella seguente descrive gli SKU consigliati in base alle dimensioni del file PBIX:


   |SKU  |Dimensioni PBIX   |
   |---------|---------|
   |P1    | < 3 GB        |
   |P2    | < 6 GB        |
   |P3    | fino a 10 GB   |



**I file PBIX rappresentano i dati in stato di compressione molto elevata**. I dati si espanderanno più volte una volta caricati nella memoria e si espanderanno ulteriormente durante l'aggiornamento dei dati.

**L'aggiornamento pianificato dei set di dati di grandi dimensioni può richiedere molto tempo** e utilizzare una quantità elevata di risorse. Di conseguenza, non pianificare un numero eccessivo di aggiornamenti sovrapposti. Si noti anche che il timeout per i processi di aggiornamento pianificato è stato raddoppiato fino a quattro ore per tutti i set di dati in questo livello di capacità.

**Il caricamento del report iniziale dei set di dati di grandi dimensioni può richiedere molto tempo** se il set di dati non è stato usato di recente, poiché il modello è caricato nella memoria della capacità Premium. La barra di caricamento per i report a caricamento prolungato visualizza lo stato di avanzamento dell'operazione.

**Se si rimuove l'area di lavoro per la capacità Premium**, il modello e tutti i dashboard e i report associati non funzioneranno.

**Sebbene i vincoli di tempo e memoria per query siano molto più elevati nel livello di capacità Premium**, è consigliabile usare filtri e filtri dei dati per limitare la visualizzazione degli oggetti visivi solo a quelli necessari.

## <a name="next-steps"></a>Passaggi successivi
[Power BI Premium: di cosa si tratta?](service-premium.md)  
[Power BI Premium release notes](service-premium-release-notes.md) (Note sulla versione di Power BI Premium)  
[Microsoft Power BI Premium whitepaper](https://aka.ms/pbipremiumwhitepaper) (White paper su Microsoft Power BI Premium)  
[Planning a Power BI Enterprise Deployment whitepaper](https://aka.ms/pbienterprisedeploy) (White paper sulla pianificazione della distribuzione aziendale di Power BI)  
[Extended Pro Trial activation](service-extended-pro-trial.md) (Attivazione della versione di valutazione Pro estesa)  

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
