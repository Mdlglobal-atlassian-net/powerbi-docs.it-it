---
title: Single Sign-On nell'app per dispositivi mobili Power BI per Windows
description: Informazioni sull'autenticazione Single Sign-On (SSO) nell'app per dispositivi mobili Power BI per Windows. SSO consente di accedere a tutte le applicazioni e a tutte le risorse necessarie per le proprie attività effettuando la procedura di accesso una sola volta, con un unico account utente.
author: mshenhav
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 09/17/2018
ms.author: mshenhav
ms.openlocfilehash: 4ec2e43843d37f0966070d39e08ae0ab6160dbf8
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73876662"
---
# <a name="single-sign-on-in-the-power-bi-mobile-windows-app"></a>Single Sign-On nell'app per dispositivi mobili Power BI per Windows

Informazioni sull'autenticazione Single Sign-On (SSO) nell'app per dispositivi mobili Power BI per Windows. SSO consente di accedere a tutte le applicazioni e a tutte le risorse necessarie per le proprie attività effettuando la procedura di accesso una sola volta, con un unico account utente. Dopo aver eseguito l'accesso, sarà possibile accedere a tutte le applicazioni necessarie senza dover ripetere l'autenticazione. 

Poiché l'app Power BI per Windows è integrata in Azure Active Directory, è possibile usare l'account principale dell'organizzazione per accedere non solo ai dispositivi aggiunti a un dominio, ma anche al servizio Power BI. Se si visualizza Power BI da un telefono Windows, assicurarsi che l'account usato per Power BI sia configurato come account aziendale o dell'istituto di istruzione nelle impostazioni del dispositivo.  

L'accesso SSO è abilitato solo per i dispositivi Windows gestiti da Microsoft Azure Active Directory. 

## <a name="sign-in-with-sso"></a>Accedere con SSO

Per semplificare la procedura di accesso, quando si installa l'app per la prima volta, questa tenta automaticamente di autenticare l'utente con il servizio Power BI tramite SSO. L'app richiederà le credenziali per Power BI solo se questa procedura non riesce.  

Se si sta già usando l'app Power BI per dispositivi mobili per Windows, con l'aggiornamento alla nuova versione sarà possibile usare anche l'accesso SSO. Disconnettersi dall'app, chiuderla e riaprirla. Quando l'app verrà riaperta, proverà automaticamente ad autenticare l'utente con il servizio Power BI tramite le credenziali Windows correnti. 

Se non si vogliono usare le credenziali della sessione attiva di Windows per accedere a Power BI, è sufficiente passare a **Impostazioni**, disconnettersi e accedere con credenziali diverse. 
 
## <a name="next-steps"></a>Passaggi successivi

- [Introduzione all'app Power BI per dispositivi mobili per Windows 10](mobile-windows-10-phone-app-get-started.md)
- Domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)

