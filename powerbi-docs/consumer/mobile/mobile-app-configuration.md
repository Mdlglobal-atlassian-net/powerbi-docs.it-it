---
title: Impostazioni di configurazione dell'app Power BI per iOS
description: Come personalizzare il comportamento di Power BI per iOS usando lo strumento MDM
author: paulinbar
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 06/07/2019
ms.author: mshenhav
ms.openlocfilehash: bc9c6dd8cd892ab0304cc5a99a3bb780486f32f0
ms.sourcegitcommit: c0f4d00d483121556a1646b413bab75b9f309ae9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/29/2019
ms.locfileid: "70160165"
---
# <a name="remotely-configure-power-bi-ios-app-using-mobile-device-management-mdm-tool"></a>Configurare in modalità remota l'app Power BI per iOS usando lo strumento di gestione dei dispositivi mobili (MDM)

L'app Power BI per dispositivi mobili per iOS supporta le impostazioni dell'app che consentono agli amministratori di Office 365 e alla gestione dei dispositivi mobili (MDM), ad esempio Intune, di personalizzare il comportamento dell'app.

L'app Power BI per dispositivi mobili iOS supporta gli scenari di configurazione seguenti:

- Configurazione del server di report
- Impostazioni di protezione dei dati

## <a name="report-server-configuration"></a>Configurazione del server di report

L'app Power BI per iOS consente agli amministratori di eseguire il push in modalità remota della configurazione del server di report con i dispositivi registrati.

| Key | Tipo | Descrizione |
|---|---|---|
| com.microsoft.powerbi.mobile.ServerURL | Stringa | URL del server di report.<br><br>Deve iniziare con http/https.|
| com.microsoft.powerbi.mobile.ServerUsername | Stringa | [facoltativo]<br><br>Nome utente da usare per connettere il server.<br><br>Se non esiste, l'app richiede all'utente di digitare il nome utente per la connessione.|
| com.microsoft.powerbi.mobile.ServerDisplayName | Stringa | [facoltativo]<br><br>Il valore predefinito è "Server di report"<br><br>Nome descrittivo usato nell'app per rappresentare il server. |
| com.microsoft.powerbi.mobile.OverrideServerDetails | Boolean | [facoltativo]<br><br>Il valore predefinito è True. Se impostato su True, esegue l'override di qualsiasi definizione di server di report già presente nel dispositivo mobile. I server esistenti già configurati vengono eliminati. Impostando l'override su True si impedisce anche all'utente di rimuovere tale configurazione.<br><br>Impostandolo su False vengono aggiunti i valori inviati lasciando le impostazioni esistenti. Se nell'app per dispositivi mobili è già configurato l'URL dello stesso server, l'app lascia invariata la configurazione. Non chiede all'utente di ripetere l'autenticazione per lo stesso server. |

## <a name="data-protection-setting"></a>Impostazione di protezione dei dati

L'app Power BI per iOS offre agli amministratori la possibilità di personalizzare la configurazione predefinita per le impostazioni di sicurezza e privacy. È possibile imporre agli utenti di specificare il loro Face ID, Touch ID o passcode quando eseguono l'accesso alle app di Power BI.

| Key | Tipo | Descrizione |
|---|---|---|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | Boolean | Il valore predefinito è False. <br><br>Per consentire agli utenti di accedere all'app sul loro dispositivo, possono essere necessari dati biometrici come TouchID o FaceID. Quando richiesto, oltre all'autenticazione vengono usati dati biometrici.<br><br>Se si usano criteri di protezione delle app, è consigliabile disabilitare questa impostazione per impedire le richieste di doppio accesso. |

## <a name="deploying-app-configuration-settings"></a>Distribuzione delle impostazioni di configurazione dell'app

La procedura seguente consentirà di creare un criterio di configurazione dell'app. Dopo aver creato i criteri di configurazione, è possibile assegnare le impostazioni a gruppi di utenti.

1. Connettere lo strumento MDM.

2. Creare e denominare i nuovi criteri di configurazione dell'app.

3. Scegliere gli utenti ai quali distribuire tali criteri di configurazione dell'app.

4. Creare coppie chiave-valore per l'impostazione di cui si vuole eseguire il push agli utenti.

Il portale di Intune consente agli amministratori di distribuire facilmente queste impostazioni all'app Power BI per iOS tramite criteri di configurazione delle app.
È tuttavia supportato qualsiasi provider MDM. Se non si usa Intune, leggere la documentazione di MDM per informazioni su come distribuire queste impostazioni.

## <a name="next-steps"></a>Passaggi successivi

* Scaricare l'[app Power BI per dispositivi mobili per iPhone](http://go.microsoft.com/fwlink/?LinkId=522062)
* Seguire [@MSPowerBI su Twitter](https://twitter.com/MSPowerBI)
* Partecipare alla conversazione nella [community di Power BI](http://community.powerbi.com/)
