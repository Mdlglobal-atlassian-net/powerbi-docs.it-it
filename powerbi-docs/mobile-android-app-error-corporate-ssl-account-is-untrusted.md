---
title: Risoluzione di "Il certificato SSL aziendale non è considerato attendibile"
description: Quando si accede all'app Android per Power Bi potrebbe essere visualizzato il messaggio "Non è stato possibile eseguire l'autenticazione perché il certificato SSL aziendale non è considerato attendibile
.": ''
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-mobile
ms.topic: conceptual
ms.date: 05/18/2018
ms.author: maggies
ms.openlocfilehash: 494e148a62675aab1a6e799c4e4b61f022483d9f
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34444958"
---
# <a name="fixing-corporate-ssl-certificate-is-untrusted---power-bi"></a>Risoluzione di "Il certificato SSL aziendale non è considerato attendibile" - Power BI
Quando si accede all'app per dispositivi mobili Android per Microsoft Power Bi potrebbe essere visualizzato il messaggio "Non è stato possibile eseguire l'autenticazione perché il certificato SSL aziendale non è considerato attendibile da questo dispositivo. Contattare l'amministratore IT della società". 

Le operazioni necessarie di solito dipendono dal sistema operativo nel dispositivo Android, ma ci sono un paio di altri problemi che potrebbero causare questo errore.

## <a name="on-android-7-or-later"></a>In Android 7 o versioni successive
Cercare un aggiornamento di un'app denominata **Chrome**e installarlo.

## <a name="on-android-6-and-earlier"></a>In Android 6 e versioni precedenti
Il dispositivo potrebbe richiedere una versione aggiornata di System Webview. Può essere installata sul dispositivo e potrebbe essere necessario solo fare clic su **Aggiorna**.

Se System Webview non è installato nel dispositivo:

1. Nel dispositivo Android chiudere Power BI.
2. Aprire Google Play Store e cercare **System Webview** di Google Inc.
3. Installare l'app.
4. Riavviare l'app Power BI ed eseguire l'accesso.

## <a name="time-zone-settings"></a>Impostazioni di fuso orario
Le impostazioni di fuso orario nel dispositivo potrebbero essere errate. 

Passare a **Impostazioni** > **Sistema** > **Data e ora** per controllarle.

## <a name="custom-authentication-server"></a>Server di autenticazione personalizzata
Se si usa un server di autenticazione personalizzata, il certificato SSL nel server di autenticazione aziendale potrebbe non essere valido. Chiedere l'assistenza dell'amministratore IT dell'organizzazione.

## <a name="next-steps"></a>Passaggi successivi
* [Scaricare l'app Android](http://go.microsoft.com/fwlink/?LinkID=544867) dall'App Store Android.
* Domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

