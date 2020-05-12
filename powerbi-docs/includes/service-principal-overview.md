---
title: Panoramica dell'entità servizio
description: Panoramica dell'entità servizio
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 04/05/2020
ms.custom: include file
ms.openlocfilehash: 7fc4412a66602fe3a6548c3e1afb06de788da90d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82615970"
---
L'entità servizio è un metodo di autenticazione che può essere usato per consentire a un'applicazione Azure AD di accedere a contenuto e API del servizio Power BI.

Quando si crea un'app Azure Active Directory (Azure AD), viene creato un [oggetto entità servizio](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object). L'oggetto entità servizio, noto anche come *entità servizio*, consente ad Azure AD di autenticare l'app. Eseguita l'autenticazione, l'app può accedere alle risorse del tenant di Azure AD.

Per l'autenticazione, l'entità servizio usa l'*ID applicazione* dell'app Azure AD e uno dei seguenti elementi:
* Segreto dell'applicazione
* Certificato