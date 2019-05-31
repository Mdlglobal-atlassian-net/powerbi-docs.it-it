---
title: Installa automaticamente le app di Power BI durante l'incorporamento per l'organizzazione
description: Informazioni su come auto installare Power BI App durante l'incorporamento per l'organizzazione.
ms.subservice: powerbi-developer
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.topic: how-to
ms.service: powerbi
ms.custom: ''
ms.date: 04/16/2019
ms.openlocfilehash: bb9ba5531c2a23f15ccbf98261e246ab7080aecb
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61376230"
---
# <a name="auto-install-power-bi-apps-when-embedding-for-your-organization"></a>Installa automaticamente le app di Power BI durante l'incorporamento per l'organizzazione

Per incorporare il contenuto da un'app, l'utente che è di incorporamento deve disporre [l'accesso all'app](../service-create-distribute-apps.md). Se l'app viene installata per l'utente, quindi funziona l'incorporamento in modo uniforme. Per altre informazioni, vedere [incorporare report o dashboard dall'app](embed-from-apps.md). È possibile definire in PowerBI.com che possono essere tutte le app [installati automaticamente](https://powerbi.microsoft.com/blog/automatically-install-apps/). Tuttavia, questa azione viene eseguita a livello di tenant e si applica a tutte le app.

## <a name="auto-install-app-on-embedding"></a>Installazione automatica di app per l'incorporamento

Se un utente ha accesso a un'app, ma non è installata l'app, quindi l'incorporamento ha esito negativo. È possibile evitare questi errori durante l'incorporamento di un'app, è possibile consentire l'installazione automatica dell'app durante l'incorporamento. Questa azione indica che se l'app a cui che l'utente tenta di incorporamento non è installato, viene automaticamente installato automaticamente. Pertanto, il contenuto da ottiene incorporato immediatamente, un'esperienza uniforme per l'utente.

## <a name="embed-for-power-bi-users-user-owns-data"></a>Incorporamento per gli utenti di Power BI (i dati utente è proprietario)

Per consentire l'installazione automatica di App per gli utenti, è necessario concedere all'applicazione l'autorizzazione 'Crea contenuto' quando [registrando l'applicazione](register-app.md#register-with-the-power-bi-application-registration-tool), o aggiungerla, se l'app è già registrata.

![Registra app crea un contenuto](media/embed-auto-install-app/register-app-create-content.png)

Successivamente, è necessario fornire l'ID app nell'URL di incorporamento. Per garantire l'ID dell'app, all'autore dell'app prima di tutto è necessario installare l'app, quindi usare uno degli [API Rest di Power BI](https://docs.microsoft.com/rest/api/power-bi/) chiamate - [Get Reports](https://docs.microsoft.com/rest/api/power-bi/reports/getreports) oppure [Get Dashboards](https://docs.microsoft.com/rest/api/power-bi/dashboards/getdashboards). Quindi all'autore dell'app deve richiedere l'Url di incorporamento dalla risposta dell'API REST. L'ID dell'app viene visualizzata nell'URL se il contenuto provenga da un'app.  Dopo aver ottenuto l'URL di incorporamento, è possibile usarlo per incorporare regolarmente.

## <a name="secure-embed"></a>Protezione di incorporamento

Per usare l'installazione automatica delle applicazioni, all'autore dell'app deve prima di tutto installare l'app, quindi passare all'app in PowerBI.com, passare al report e ottiene il collegamento in modo normale. Tutti gli altri utenti con accesso all'app che è possibile usare il collegamento possono incorporare il report.

## <a name="considerations-and-limitations"></a>Considerazioni e limitazioni

* È solo possibile incorporare report e dashboard per questo scenario.

* Questa funzionalità non è attualmente supportata per i dati con proprietà app e scenari di incorporamento di SharePoint.