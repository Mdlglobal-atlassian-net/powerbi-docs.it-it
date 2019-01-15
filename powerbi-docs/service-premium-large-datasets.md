---
title: Supporto per set di dati di grandi dimensioni in Power BI Premium
description: Power BI Premium supporta set di dati di dimensioni fino a 10 GB.
author: jocaplan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 10/18/2018
ms.author: jocaplan
LocalizationGroup: Premium
ms.openlocfilehash: 3aa8ef5ea7a51da226d48869bdf255900dee8d6d
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54284197"
---
# <a name="power-bi-premium-support-for-large-datasets"></a>Supporto per set di dati di grandi dimensioni in Power BI Premium

Power BI Premium supporta il caricamento di file di Power BI Desktop (.pbix) con dimensioni massime fino a 10 GB. Una volta caricato, è possibile aggiornare un set di dati con dimensioni fino a 12 GB. Per usare un set di dati più grande, pubblicarlo in un'area di lavoro a cui è assegnata capacità Premium.
 
## <a name="best-practices"></a>Procedure consigliate

Questa sezione descrive le procedure consigliate per l'uso dei set di dati di grandi dimensioni.

**I modelli di grandi dimensioni usano una quantità elevata di risorse** rispetto alla capacità. Per i modelli superiori a 1 GB è consigliabile almeno uno SKU P1. Anche se la pubblicazione di modelli di grandi dimensioni in aree di lavoro supportate da SKU A fino ad A3 può funzionare, il relativo aggiornamento non funzionerà.

La tabella seguente descrive gli SKU consigliati in base alle dimensioni del file PBIX:

   |SKU  |Dimensioni PBIX   |
   |---------|---------|
   |P1    | < 3 GB        |
   |P2    | < 6 GB        |
   |P3, P4, P5    | fino a 10 GB   |

Lo SKU A4 di Power BI Embedded equivale allo SKU P1, A5 = P2 e A6 = P3. Tenere presente che la pubblicazione di modelli di grandi dimensioni in SKU A ed EM può restituire errori non specifici dell'errore di limitazione delle dimensioni del modello nella capacità condivisa. È probabile che gli errori di aggiornamento per i modelli di grandi dimensioni in SKU A ed EM indichino il timeout. Il team sta lavorando per migliorare i messaggi di errore per questi scenari.

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
