---
ms.openlocfilehash: 26f4b82301915524b65d9d2d6b39d61b54ed0321
ms.sourcegitcommit: 8eeb784fd46321680367ac913ef976aeedaa7766
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/03/2020
ms.locfileid: "80621580"
---
L'entità servizio è un metodo di autenticazione che può essere usato per consentire a un'applicazione Azure AD di accedere a contenuto e API del servizio Power BI.

Quando si crea un'app Azure Active Directory (Azure AD), viene creato un [oggetto entità servizio](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object). L'oggetto entità servizio, noto anche come *entità servizio*, consente ad Azure AD di autenticare l'app. Eseguita l'autenticazione, l'app può accedere alle risorse del tenant di Azure AD.

Per l'autenticazione, l'entità servizio usa l'*ID applicazione* dell'app Azure AD e uno dei seguenti elementi:
* Segreto dell'applicazione
* Certificato