---
title: Supporto per set di dati di grandi dimensioni in Power BI Premium
description: Power BI Premium supporta set di dati di dimensioni fino a 10 GB.
author: jocaplan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 10/18/2018
ms.author: jocaplan
LocalizationGroup: Premium
ms.openlocfilehash: 416f022ee3c413c69650e6f1736cc94edcd58f13
ms.sourcegitcommit: a764e4b9d06b50d9b6173d0fbb7555e3babe6351
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2018
ms.locfileid: "49641253"
---
# <a name="power-bi-premium-support-for-large-datasets"></a>Supporto per set di dati di grandi dimensioni in Power BI Premium

Power BI Premium supporta il caricamento di file di Power BI Desktop (.pbix) con dimensioni massime fino a 10 GB. Una volta caricato, è possibile aggiornare un set di dati con dimensioni fino a 12 GB. Per usare un set di dati più grande, pubblicarlo in un'area di lavoro a cui è assegnata capacità Premium. Questo articolo illustra considerazioni e procedure consigliate per l'uso di set di dati di grandi dimensioni.

**I modelli di grandi dimensioni usano una quantità elevata di risorse** rispetto alla capacità. Per i modelli superiori a 1 GB è consigliabile almeno uno SKU P1. La tabella seguente descrive gli SKU consigliati in base alle dimensioni del file PBIX:

   |SKU  |Dimensioni PBIX   |
   |---------|---------|
   |P1    | < 3 GB        |
   |P2    | < 6 GB        |
   |P3, P4, P5    | fino a 10 GB |

**I file PBIX rappresentano i dati in stato di compressione molto elevata**. I dati si espanderanno più volte una volta caricati nella memoria e si espanderanno ulteriormente durante l'aggiornamento dei dati.

**L'aggiornamento pianificato dei set di dati di grandi dimensioni può richiedere molto tempo** e utilizzare una quantità elevata di risorse. Di conseguenza, non pianificare un numero eccessivo di aggiornamenti sovrapposti. Si noti anche che il timeout per i processi di aggiornamento pianificato è stato raddoppiato fino a quattro ore per tutti i set di dati in questo livello di capacità. È consigliabile l'[aggiornamento incrementale](service-premium-incremental-refresh.md) perché è più veloce, più affidabile e consuma una quantità minore di risorse.

**Il caricamento del report iniziale dei set di dati di grandi dimensioni può richiedere molto tempo** se il set di dati non è stato usato di recente, poiché il modello è caricato nella memoria della capacità Premium. La barra di caricamento per i report a caricamento prolungato visualizza lo stato di avanzamento dell'operazione.

**Se si rimuove l'area di lavoro per la capacità Premium**, il modello e tutti i dashboard e i report associati non funzioneranno.

**Anche se i vincoli di tempo e memoria per query sono molto più elevati nel livello di capacità Premium**, è fortemente consigliato l'uso di filtri e filtri dei dati per limitare la visualizzazione degli oggetti visivi solo a quelli necessari.

**Passaggi successivi**

[Che cos'è Power BI Premium?](service-premium.md)
[Note sulla versione di Power BI Premium](service-premium-release-notes.md)
[White paper di Microsoft Power BI Premium](https://aka.ms/pbipremiumwhitepaper)
[White paper sulla pianificazione della distribuzione aziendale di Power BI](https://aka.ms/pbienterprisedeploy)

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
