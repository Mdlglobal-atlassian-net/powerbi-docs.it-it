---
title: Procedura per la gestione del modulo di accesso da parte degli amministratori di Power BI Desktop
description: Informazioni su come gestire il modulo di accesso iniziale durante l'apertura di Power BI Desktop.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/21/2019
ms.author: davidi
ms.openlocfilehash: 9e35bbffec40aa57d3097e122bd038659405dfed
ms.sourcegitcommit: 76772a361e6cd4dd88824b2e4b32af30656e69db
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/27/2019
ms.locfileid: "56892299"
---
# <a name="how-administrators-can-manage-the-power-bi-desktop-sign-in-form"></a>Procedura per la gestione del modulo di accesso da parte degli amministratori di Power BI Desktop
Al primo avvio di Power BI Desktop viene visualizzato un modulo di accesso. È possibile inserire le informazioni oppure accedere a Power BI per continuare. Gli amministratori gestiscono questo modulo usando una chiave del Registro di sistema. 

![Modulo di accesso iniziale per Power BI Desktop](media/desktop-admin-sign-in-form/sign-in-form.png)

Gli amministratori usano la chiave del Registro di sistema seguente per disabilitare il modulo di accesso. Questa modifica può essere estesa a un'intera organizzazione tramite i criteri globali.

```
Key: HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Microsoft Power BI Desktop
valueName: ShowLeadGenDialog
```

Un valore pari 0 disabiliterà la finestra di dialogo.

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

