---
title: Limitazioni dell'API REST di Power BI
description: L'API REST di Power BI presenta le limitazioni seguenti
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 6699167cecebea5085eff4621c077096fd4c6c2e
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61385144"
---
# <a name="power-bi-rest-api-limitations"></a>Limitazioni dell'API REST di Power BI  
  
**Per eseguire il POST di righe**
  
* Massimo 75 colonne
* Massimo 75 tabelle
* Massimo 10.000 righe per ogni singola richiesta di POST di righe  
* 1\.000.000 di righe aggiunte all'ora per set di dati  
* Massimo 5 richieste di POST di righe in sospeso per set di dati  
* 120 richieste di POST di righe al minuto per set di dati
* Se la tabella include 250.000 o più righe, 120 richieste di POST di righe all'ora per set di dati
* Massimo 200.000 righe archiviate per tabella nel set di dati FIFO (First In, First Out)
* Massimo 5.000.000 di righe archiviate per tabella nel set di dati 'senza criteri di conservazione'  
* 4000 caratteri per valore per le colonne di tipo stringa nelle operazioni di POST di righe
  
## <a name="see-also"></a>Vedere anche

[Restrizioni e limiti del servizio Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-service-limits-restrictions)   
[Panoramica dell'API REST di Power BI](https://docs.microsoft.com/rest/api/power-bi/)