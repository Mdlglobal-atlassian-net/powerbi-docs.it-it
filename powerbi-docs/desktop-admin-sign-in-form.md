---
title: Procedura per la gestione del modulo di accesso da parte degli amministratori di Power BI Desktop
description: Informazioni su come gestire il modulo di accesso iniziale durante l'apertura di Power BI Desktop.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
ms.openlocfilehash: a61075993afaa75aea420f55babc773dec075f73
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54280890"
---
# <a name="how-administrators-can-manage-the-power-bi-desktop-sign-in-form"></a>Procedura per la gestione del modulo di accesso da parte degli amministratori di Power BI Desktop
Al primo avvio di Power BI Desktop viene visualizzato un modulo di accesso. È possibile inserire le informazioni oppure accedere a Power BI per continuare. Gli amministratori gestiscono questo modulo usando una chiave del Registro di sistema. 

![Modulo di accesso iniziale per Power BI Desktop](media/desktop-admin-sign-in-form/sign-in-form.png)

Gli amministratori usano la chiave del Registro di sistema seguente per disabilitare il modulo di accesso. Questa modifica può essere estesa a un'intera organizzazione tramite i criteri globali.

```
Key: HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Power BI Desktop
valueName: ShowLeadGenDialog
```

Un valore pari 0 disabiliterà la finestra di dialogo.

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

