---
title: Impostazioni di configurazione dell'app Power BI
description: Come personalizzare il comportamento di Power BI usando lo strumento MDM
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 11/07/2019
ms.author: painbar
ms.openlocfilehash: a517ee4edce6e18eadcbe2b1b6765684f8121b21
ms.sourcegitcommit: 768e1e4b19fe8c7627010127c2420d63021cb542
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2019
ms.locfileid: "74199429"
---
# <a name="remotely-configure-power-bi-app-using-mobile-device-management-mdm-tool"></a>Configurare in modalità remota l'app Power BI usando lo strumento di gestione dei dispositivi mobili (MDM)

L'app Power BI per dispositivi mobili per iOS e Android supporta le impostazioni dell'app che consentono agli amministratori di Office 365 e ai servizi di gestione dei dispositivi mobili (MDM), ad esempio Intune, di personalizzare il comportamento dell'app.

L'app Power BI per dispositivi mobili supporta gli scenari di configurazione seguenti:

- Configurazione del server di report (iOS e Android)
- Impostazioni di protezione dei dati (iOS)

## <a name="report-server-configuration-ios-and-android"></a>Configurazione del server di report (iOS e Android)

L'app Power BI per iOS e Android consente agli amministratori di eseguire il push in modalità remota della configurazione del server di report nei dispositivi registrati.

| Key | Tipo | Descrizione |
|---|---|---|
| com.microsoft.powerbi.mobile.ServerURL | Stringa | URL del server di report.<br><br>Deve iniziare con http/https.|
| com.microsoft.powerbi.mobile.ServerUsername | Stringa | [facoltativo]<br><br>Nome utente da usare per connettere il server.<br><br>Se non esiste, l'app richiede all'utente di digitare il nome utente per la connessione.|
| com.microsoft.powerbi.mobile.ServerDisplayName | Stringa | [facoltativo]<br><br>Il valore predefinito è "Server di report"<br><br>Nome descrittivo usato nell'app per rappresentare il server. |
| com.microsoft.powerbi.mobile.OverrideServerDetails | Boolean | [facoltativo]<br><br>Il valore predefinito è True. Se impostato su True, esegue l'override di qualsiasi definizione di server di report già presente nel dispositivo mobile. I server esistenti già configurati vengono eliminati. Impostando l'override su True si impedisce anche all'utente di rimuovere tale configurazione.<br><br>Impostandolo su False vengono aggiunti i valori inviati lasciando le impostazioni esistenti. Se nell'app per dispositivi mobili è già configurato l'URL dello stesso server, l'app lascia invariata la configurazione. Non chiede all'utente di ripetere l'autenticazione per lo stesso server. |

## <a name="data-protection-settings-ios"></a>Impostazioni di protezione dei dati (iOS)

L'app Power BI per iOS offre agli amministratori la possibilità di personalizzare la configurazione predefinita per le impostazioni di sicurezza e privacy. È possibile imporre agli utenti di specificare il loro Face ID, Touch ID o passcode quando eseguono l'accesso all'app Power BI.

| Key | Tipo | Descrizione |
|---|---|---|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | Boolean | Il valore predefinito è False. <br><br>Per consentire agli utenti di accedere all'app sul loro dispositivo, possono essere necessari dati biometrici come TouchID o FaceID. Quando richiesto, oltre all'autenticazione vengono usati dati biometrici.<br><br>Se si usano criteri di protezione delle app, è consigliabile disabilitare questa impostazione per impedire le richieste di doppio accesso. |

## <a name="deploying-app-configuration-settings"></a>Distribuzione delle impostazioni di configurazione dell'app

La procedura seguente consentirà di creare un criterio di configurazione dell'app. Dopo aver creato il criterio di configurazione, è possibile assegnare le impostazioni a gruppi di utenti.

1. Connettere lo strumento MDM.
2. Creare e denominare i nuovi criteri di configurazione dell'app.
3. Scegliere gli utenti ai quali distribuire tali criteri di configurazione dell'app.
4. Creare coppie chiave-valore per l'impostazione di cui si vuole eseguire il push agli utenti.

Il portale di Intune consente agli amministratori di distribuire facilmente queste impostazioni all'app Power BI tramite criteri di configurazione delle app. È tuttavia supportato qualsiasi provider MDM. Se non si usa Intune, leggere la documentazione di MDM per informazioni su come distribuire queste impostazioni.

## <a name="next-steps"></a>Passaggi successivi

* Ottenere l'app Power BI per dispositivi mobili dall'[App store](https://apps.apple.com/app/microsoft-power-bi/id929738808) e [Google Play Store](https://play.google.com/store/apps/details?id=com.microsoft.powerbim&amp;amp;clcid=0x409)
* Seguire [@MSPowerBI su Twitter](https://twitter.com/MSPowerBI)
* Partecipare alla conversazione nella [community di Power BI](https://community.powerbi.com/)
