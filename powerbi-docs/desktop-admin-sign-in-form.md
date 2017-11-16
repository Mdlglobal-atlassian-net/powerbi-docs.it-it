---
title: Procedura per la gestione del modulo di accesso da parte degli amministratori di Power BI Desktop
description: Informazioni su come gestire il modulo di accesso iniziale durante l'apertura di Power BI Desktop.
services: powerbi
documentationcenter: 
author: davidiseminger
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
ms.date: 10/17/2017
ms.author: davidi
ms.openlocfilehash: eabb59b32234fce1ba5669b95abb41c4f7e04aa2
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2017
---
# <a name="how-administrators-can-manage-the-power-bi-desktop-sign-in-form"></a>Procedura per la gestione del modulo di accesso da parte degli amministratori di Power BI Desktop
Al primo avvio di Power BI Desktop viene visualizzato un modulo di accesso. È possibile inserire le informazioni oppure accedere a Power BI per continuare. Gli amministratori possono gestire questo modulo usando una chiave del Registro di sistema. 

![Modulo di accesso iniziale per Power BI Desktop](media/desktop-admin-sign-in-form/sign-in-form.png)

Gli amministratori possono usare la chiave del Registro di sistema seguente per disabilitare il modulo di accesso. Questa modifica può essere estesa all'intera organizzazione tramite i criteri globali.

```
Key: HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Power BI Desktop
valueName: ShowLeadGenDialog
```

Un valore pari 0 disabiliterà la finestra di dialogo.

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

