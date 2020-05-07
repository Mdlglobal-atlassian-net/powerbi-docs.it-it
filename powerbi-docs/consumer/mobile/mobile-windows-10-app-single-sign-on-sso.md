---
title: Single Sign-On nell'app per dispositivi mobili Power BI per Windows
description: Informazioni sull'autenticazione Single Sign-On (SSO) nell'app per dispositivi mobili Power BI per Windows. SSO consente di accedere a tutte le applicazioni e a tutte le risorse necessarie per le proprie attività effettuando la procedura di accesso una sola volta, con un unico account utente.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: painbar
ms.openlocfilehash: e9156e539ee9f1a344b89f7814c148829498e5fc
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "79435928"
---
# <a name="single-sign-on-in-the-power-bi-mobile-windows-app"></a>Single Sign-On nell'app per dispositivi mobili Power BI per Windows

Informazioni sull'autenticazione Single Sign-On (SSO) nell'app per dispositivi mobili Power BI per Windows. SSO consente di accedere a tutte le applicazioni e a tutte le risorse necessarie per le proprie attività effettuando la procedura di accesso una sola volta, con un unico account utente. Dopo aver eseguito l'accesso, sarà possibile accedere a tutte le applicazioni necessarie senza dover ripetere l'autenticazione. 

Poiché l'app Power BI per Windows è integrata in Azure Active Directory, è possibile usare l'account principale dell'organizzazione per accedere non solo ai dispositivi aggiunti a un dominio, ma anche al servizio Power BI. Se si visualizza Power BI da un telefono Windows, assicurarsi che l'account usato per Power BI sia configurato come account aziendale o dell'istituto di istruzione nelle impostazioni del dispositivo.  

L'accesso SSO è abilitato solo per i dispositivi Windows gestiti da Microsoft Azure Active Directory.

>[!NOTE]
>Il supporto delle app Power BI per dispositivi mobili per i **telefoni con Windows 10 Mobile** non sarà più disponibile dal 16 marzo 2021. [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2121400)

## <a name="sign-in-with-sso"></a>Accedere con SSO

Per semplificare la procedura di accesso, quando si installa l'app per la prima volta, questa tenta automaticamente di autenticare l'utente con il servizio Power BI tramite SSO. L'app richiederà le credenziali per Power BI solo se questa procedura non riesce.  

Se si sta già usando l'app Power BI per dispositivi mobili per Windows, con l'aggiornamento alla nuova versione sarà possibile usare anche l'accesso SSO. Disconnettersi dall'app, chiuderla e riaprirla. Quando l'app verrà riaperta, proverà automaticamente ad autenticare l'utente con il servizio Power BI tramite le credenziali Windows correnti. 

Se non si vogliono usare le credenziali della sessione attiva di Windows per accedere a Power BI, passare a **Impostazioni**, disconnettersi e accedere con credenziali diverse. 
 
## <a name="next-steps"></a>Passaggi successivi

- [Introduzione all'app Power BI per dispositivi mobili per Windows 10](mobile-windows-10-phone-app-get-started.md)
- Domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)

