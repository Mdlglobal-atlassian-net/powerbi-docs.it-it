---
title: include file
description: include file
services: powerbi
author: mgblythe
ms.service: powerbi
ms.topic: include
ms.date: 05/31/2019
ms.author: mblythe
ms.openlocfilehash: 94b6959b6bcbf250e54a353e8b725b6c9e5a2e30
ms.sourcegitcommit: c539726c9c180e899a8a34443e3fda2b9848beb2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/31/2019
ms.locfileid: "66448387"
---
## <a name="single-sign-on"></a>Accesso Single Sign-On

Dopo aver pubblicato un set di dati DirectQuery di Azure nel servizio, è possibile abilitare l'accesso Single Sign-On tramite OAuth2 in Azure Active Directory (Azure AD) per gli utenti finali.

Per abilitare l'accesso Single Sign-On, passare alle impostazioni per il set di dati, aprire la scheda **Origini dati** e selezionare la casella SSO.

![Finestra di dialogo Configura Azure SQL DirectQuery](media/direct-query-sso/sso-dialog.png)

Quando l'opzione SSO è abilitata e gli utenti accedono ai report generati dall'origine dati, Power BI invia le relative credenziali di Azure AD autenticate nelle query al database SQL di Azure o al data warehouse. Questo consente a Power BI di rispettare le impostazioni di sicurezza configurate al livello dell'origine dati.

L'opzione SSO interessa tutti i set di dati che usano l'origine dati specifica. Non interessa il metodo di autenticazione usato per gli scenari di importazione.

> [!Note]
> L'autenticazione MFA (Azure Multi-Factor Authentication) non è supportata. Gli utenti che vogliono usare SSO con Azure SQL DirectQuery devono essere esentati dall'autenticazione MFA.