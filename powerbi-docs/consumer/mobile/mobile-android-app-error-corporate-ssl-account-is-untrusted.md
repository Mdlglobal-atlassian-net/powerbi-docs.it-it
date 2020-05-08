---
title: Risoluzione di "Il certificato SSL aziendale non è considerato attendibile"
description: Quando si accede all'app Android per Power BI può essere visualizzato il messaggio "Non è stato possibile eseguire l'autenticazione perché il certificato SSL aziendale non è considerato attendibile"
.": ''
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: painbar
ms.openlocfilehash: a68644c63d3d5eaeb54a71683629af01817d62a7
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "79114611"
---
# <a name="fixing-corporate-ssl-certificate-is-untrusted---power-bi"></a>Risoluzione di "Il certificato SSL aziendale non è considerato attendibile" - Power BI
Quando si accede all'app per dispositivi mobili Android per Microsoft Power BI può essere visualizzato il messaggio "Non è stato possibile eseguire l'autenticazione perché il certificato SSL aziendale non è considerato attendibile da questo dispositivo. Contattare l'amministratore IT della società". 

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
Se si usa un server di autenticazione personalizzata, il certificato SSL nel server di autenticazione aziendale potrebbe non essere valido. Collaborare con il reparto IT dell'organizzazione per testare la configurazione del server di autenticazione aziendale, seguendo le indicazioni in [questo articolo](https://support.microsoft.com/help/3203929/using-adal-to-authenticate-from-android-devices-fails-if-additional-ce).

## <a name="next-steps"></a>Passaggi successivi
* [Scaricare l'app Android](https://go.microsoft.com/fwlink/?LinkID=544867) dall'App Store Android.
* Domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/) 

