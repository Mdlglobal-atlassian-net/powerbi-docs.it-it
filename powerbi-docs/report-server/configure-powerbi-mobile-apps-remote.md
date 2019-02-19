---
title: Configurare l'accesso delle app per dispositivi mobili iOS in modalità remota
description: Informazioni su come configurare le app per dispositivi mobili iOS in modalità remota per il server di report.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 11/15/2018
ms.author: maghan
ms.openlocfilehash: c50f9c482ba689fe81ee22b2b52564dec3cbf1d6
ms.sourcegitcommit: 91ac6185f7026ddbaa925dc54057bb742b4fa411
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/16/2019
ms.locfileid: "56324370"
---
# <a name="configure-power-bi-ios-mobile-app-access-to-a-report-server-remotely"></a>Configurare l'accesso delle app per dispositivi mobili iOS di Power BI in modalità remota

In questo articolo viene spiegato come usare lo strumento MDM dell'organizzazione per configurare l'accesso delle app per dispositivi mobili iOS di Power BI a un server di report. Per procedere a questa configurazione, gli amministratori IT creano criteri di configurazione dell'app con le informazioni necessarie da inviare all'app. 

 Con la connessione al server di report già configurata, gli utenti delle app per dispositivi mobili iOS di Power BI possono connettersi al server di report dell'organizzazione più facilmente. 

## <a name="create-the-app-configuration-policy-in-mdm-tool"></a>Creare i criteri di configurazione dell'app nello strumento MDM 

L'amministratore deve seguire i passaggi riportati di seguito in Microsoft Intune per creare i criteri di configurazione dell'app. I passaggi e l'esperienza di creazione dei criteri di configurazione dell'app potrebbero essere diversi in altri strumenti MDM. 

1. Connettere lo strumento MDM. 
2. Creare e denominare i nuovi criteri di configurazione dell'app. 
3. Scegliere gli utenti ai quali distribuire tali criteri di configurazione dell'app. 
4. Creare le coppie chiave-valore. 

Nella tabella seguente vengono illustrate in dettaglio le coppie.

|Key  |Tipo  |Descrizione  |
|---------|---------|---------|
| com.microsoft.powerbi.mobile.ServerURL | Stringa | URL server di report <br> Deve iniziare con http/https |
| com.microsoft.powerbi.mobile.ServerUsername | Stringa | [facoltativo] <br> Nome utente da usare per connettere il server. <br> Se non esiste, l'app richiede all'utente di digitare il nome utente per la connessione.| 
| com.microsoft.powerbi.mobile.ServerDisplayName | Stringa | [facoltativo] <br> Il valore predefinito è "Server di report" <br> Nome descrittivo usato nell'app per rappresentare il server | 
| com.microsoft.powerbi.mobile.OverrideServerDetails | Boolean | Il valore predefinito è True <br>Se impostato su "True", esegue l'override di qualsiasi definizione di server di report già presente nel dispositivo mobile. I server esistenti già configurati vengono eliminati. <br> Impostando l'override su True si impedisce anche all'utente di rimuovere tale configurazione. <br> Impostandolo su "False" vengono aggiunti i valori inviati lasciando le impostazioni esistenti. <br> Se nell'app per dispositivi mobili è già configurato l'URL dello stesso server, l'app lascia invariata la configurazione. Non richiede all'utente di ripetere l'autenticazione per lo stesso server. |

Di seguito è riportato un esempio di configurazione dei criteri di configurazione con Intune.

![Impostazioni di configurazione di Intune](media/configure-powerbi-mobile-apps-remote/power-bi-ios-remote-configuration-settings.png)

## <a name="end-users-connecting-to-a-report-server"></a>Utenti finali che si connettono a un server di report

 Si supponga ad esempio di pubblicare i criteri di configurazione dell'app per una lista di distribuzione. Quando gli utenti e i dispositivi inclusi nella lista di distribuzione avviano l'app per dispositivi mobili per iOS si verifica quanto segue. 

1. Viene visualizzato un messaggio che informa che l'app per dispositivi mobili è configurata con un server di report. Toccare **Accedi**.

    ![Accedere al server di report](media/configure-powerbi-mobile-apps-remote/power-bi-config-server-sign-in.png)

2.  Nella pagina **Connetti al server** il server di report è già compilato. Toccare **Connetti**.

    ![Dettagli del server di report compilati](media/configure-powerbi-mobile-apps-remote/power-bi-ios-remote-configure-connect-server.png)

3. Digitare una password per l'autenticazione e quindi toccare **Accedi**. 

    ![Dettagli del server di report compilati](media/configure-powerbi-mobile-apps-remote/power-bi-config-server-address.png)

È ora possibile visualizzare e interagire con gli indicatori KPI e i report di Power BI archiviati nel server di report.

## <a name="next-steps"></a>Passaggi successivi
[Panoramica amministratore](admin-handbook-overview.md)  
[Installare il server di report di Power BI](install-report-server.md)  

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)

