---
title: API Power BI che usano criteri di conservazione automatici per dati in tempo reale
description: Informazioni sui criteri di conservazione automatici nel servizio Power BI
author: rkarlin
ms.author: rkarlin
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: e2d81ac67ea5c070f31315a381b42e3a1379a49b
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73865083"
---
# <a name="automatic-retention-policy-for-real-time-data"></a>Criteri di conservazione automatici per dati in tempo reale

I criteri di conservazione automatici nel servizio Power BI sono un parametro di stringa di query che abilita i criteri di conservazione predefiniti per pulire automaticamente i dati precedenti, mantenendo al tempo stesso un flusso costante di nuovi dati verso il dashboard. I primi criteri di conservazione sono denominati *FIFO (First In First Out)* . Se abilitati, i dati vengono raccolti in una tabella fino al raggiungimento di 200.000 righe. Superato questo numero di righe, le righe precedenti vengono eliminate dal set di dati. Viene così mantenuto un numero di righe compreso tra 200.000 e 210.000 contenenti solo i dati più recenti.  
  
<center>

![criteri di conservazione](media/api-Automatic-retention-policy-for-real-time-data/retention-policy.png) 

</center>

I criteri di conservazione vengono abilitati quando si creano set di dati per la prima volta. È sufficiente aggiungere il parametro di query relativo ai criteri di conservazione predefiniti alla chiamata ai set di dati POST e impostarlo come equivalente a *basicFIFO*.  
  
    POST https://api.powerbi.com/v1.0/myorg/datasets?defaultRetentionPolicy={None | basicFIFO}