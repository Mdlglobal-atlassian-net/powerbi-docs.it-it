---
title: Registrare un'app in Azure AD
description: Procedura dettagliata - Eseguire il push dei dati in un set di dati - Registrare un'app in Azure AD
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 08/10/2017
ms.author: maghan
ms.openlocfilehash: 48ab2a51a479269b8846288b64089964a0544681
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/30/2018
---
# <a name="step-1-register-an-app-with-azure-ad"></a>Passaggio 1: Registrare un'app in Azure AD
Questo articolo fa parte di una procedura dettagliata per il [push dei dati in un set di dati](walkthrough-push-data.md).

Il primo passaggio per eseguire il push dei dati in un set di dati di Power BI consiste nel registrare l'app in Azure AD. Questo passaggio è necessario per ottenere un **ID client** che identifica l'app in Azure AD. Senza un **ID client**, Azure AD non è in grado di autenticare l'app.

> **NOTA**: prima di registrare un'app per Power BI, è necessario [iscriversi a Power BI](create-an-azure-active-directory-tenant.md).
> 
> 

Ecco come registrare un'app in Azure AD.

## <a name="register-an-app-in-azure-ad"></a>Registrare un'app in Azure AD
1. Passare a dev.powerbi.com/apps.
2. Fare clic su **Accedi con l'account esistente**e accedere al proprio account di Power BI.
3. In **Nome app** immettere un nome, ad esempio "Esempio di app per il push dei dati".
4. In **Tipo di app**scegliere **App nativa**.
5. Immettere un **URL di reindirizzamento**, ad esempio **https://login.live.com/oauth20_desktop.srf**. Per un' **app client nativa**, l'URI di reindirizzamento fornisce ad **Azure AD** altri dettagli sull'applicazione specifica che verrà autenticata. L'Uri standard per un'applicazione client è https://login.live.com/oauth20_desktop.srf.
6. In **Scegliere le API per accedere**selezionare **Lettura e scrittura in tutti i set di dati**. Per tutte le autorizzazioni delle app di Power BI, vedere [Autorizzazioni di Power BI](power-bi-permissions.md).
7. Fare clic su **Registra app**e salvare l' **ID client** che è stato generato. Un **ID client** identifica l'app in Azure AD.

Ecco come dovrebbe risultare la pagina **Registra un'applicazione per Power BI** :

![](media/walkthrough-push-data-register-app-with-azure-ad/powerbi-developer-sample-register-app.png)

Il passaggio successivo illustra come [ottenere un token di accesso per l'autenticazione](walkthrough-push-data-get-token.md).

[Passaggio successivo >](walkthrough-push-data-get-token.md)

## <a name="next-steps"></a>Passaggi successivi
[Iscriversi a Power BI](create-an-azure-active-directory-tenant.md)  
[Ottenere un token di accesso per l'autenticazione](walkthrough-push-data-get-token.md)  
[Procedura dettagliata: Eseguire il push dei dati in un set di dati](walkthrough-push-data.md)  
[Registrare un'applicazione](register-app.md)  
[Panoramica dell'API REST di Power BI](overview-of-power-bi-rest-api.md)  

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

