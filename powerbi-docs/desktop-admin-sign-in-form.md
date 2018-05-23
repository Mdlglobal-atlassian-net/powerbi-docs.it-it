---
title: Procedura per la gestione del modulo di accesso da parte degli amministratori di Power BI Desktop
description: Informazioni su come gestire il modulo di accesso iniziale durante l'apertura di Power BI Desktop.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: davidi
ms.openlocfilehash: 98bf9579ae7ee551634eed765138c0e78156464c
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
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

