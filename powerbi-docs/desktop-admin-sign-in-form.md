---
title: Procedura per la gestione del modulo di accesso da parte degli amministratori di Power BI Desktop
description: Informazioni su come gestire il modulo di accesso iniziale durante l'apertura di Power BI Desktop.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/15/2019
ms.author: davidi
ms.openlocfilehash: 5c31277b640b16882bef5c5f2cd9c56b441ede82
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61329901"
---
# <a name="how-administrators-can-manage-the-power-bi-desktop-sign-in-form"></a>Procedura per la gestione del modulo di accesso da parte degli amministratori di Power BI Desktop
Al primo avvio di Power BI Desktop viene visualizzato un modulo di accesso. È possibile inserire le informazioni oppure accedere a Power BI per continuare. Gli amministratori gestiscono questo modulo usando una chiave del Registro di sistema. 

![Modulo di accesso iniziale per Power BI Desktop](media/desktop-admin-sign-in-form/sign-in-form.png)

Gli amministratori usano la chiave del Registro di sistema seguente per disabilitare il modulo di accesso. Questa modifica può essere estesa a un'intera organizzazione tramite i criteri globali.

```
Key: HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Microsoft Power BI Desktop
valueName: ShowLeadGenDialog
```
È anche possibile provare la chiave seguente che ha avuto esito positivo per alcuni clienti in base alle relative configurazioni:

```
Key: HKEY_CURRENT_USER\SOFTWARE\Microsoft\Microsoft Power BI Desktop
valueName: ShowLeadGenDialog
```

Un valore pari 0 disabiliterà la finestra di dialogo.




Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

