---
title: Configurare l'accesso delle app per dispositivi mobili iOS di Power BI in modalità remota
description: Informazioni su come configurare le app per dispositivi mobili iOS in modalità remota per il server di report.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 05/22/2018
ms.author: maggies
ms.openlocfilehash: bbade67c9510b8d316364d991c09444712309514
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34722179"
---
# <a name="configure-power-bi-ios-mobile-app-access-to-a-report-server-remotely"></a>Configurare l'accesso delle app per dispositivi mobili iOS di Power BI in modalità remota

In questo articolo viene spiegato come usare lo strumento MDM dell'organizzazione per configurare l'accesso delle app per dispositivi mobili iOS di Power BI a un server di report. Per procedere a questa impostazione, gli amministratori IT creano criteri di configurazione dell'app con le informazioni necessarie da inviare all'app. 

 Gli utenti delle app per dispositivi mobili iOS di Power BI possono quindi connettersi al server di report dell'organizzazione più facilmente perché la connessione al server di report è già configurata. 


## <a name="create-the-app-configuration-policy-in-mdm-tool"></a>Creare i criteri di configurazione dell'app nello strumento MDM 

L'amministratore deve seguire i passaggi riportati di seguito in Microsoft Intune per creare i criteri di configurazione dell'app. I passaggi e l'esperienza di creazione dei criteri di configurazione dell'app potrebbero essere diversi in altri strumenti MDM. 

1. Connettere lo strumento MDM. 
2. Creare e denominare i nuovi criteri di configurazione dell'app. 
3. Scegliere gli utenti ai quali distribuire tali criteri di configurazione dell'app. 
4. Creare le coppie chiave-valore. 

Nella tabella seguente vengono illustrate in dettaglio le coppie.

|Chiave  |Tipo  |Descrizione  |
|---------|---------|---------|
| com.microsoft.powerbi.mobile.ServerURL | String | URL server di report </br> Deve iniziare con http/https |
| com.microsoft.powerbi.mobile.ServerUsername | String | [facoltativo] </br> Nome utente da usare per connettere il server. </br> Se non esiste, l'app richiede all'utente di digitare il nome utente per la connessione.| 
| com.microsoft.powerbi.mobile.ServerDisplayName | String | [facoltativo] </br> Il valore predefinito è "Server di report" </br> Nome descrittivo usato nell'app per rappresentare il server | 
| com.microsoft.powerbi.mobile.OverrideServerDetails | Booleano | Il valore predefinito è True </br> Se impostato su "True", esegue l'override di qualsiasi definizione di Server di report già presente nel dispositivo mobile (i server esistenti già configurati verranno eliminati). </br> Impostando l'override su True si impedisce anche all'utente di rimuovere tale configurazione. </br> Impostandolo su "False" vengono aggiunti i valori inviati lasciando le impostazioni esistenti. </br> Se nell'app mobile è già impostato l'URL del server di report, l'app lascia la configurazione esistente e non chiede all'utente di ripetere l'autenticazione per lo stesso server. |

Di seguito è riportato un esempio di configurazione dei criteri di configurazione con Intune.

![Impostazioni di configurazione di Intune](media/configure-powerbi-mobile-apps-remote/power-bi-ios-remote-configuration-settings.png)

## <a name="end-users-connecting-to-a-report-server"></a>Utenti finali che si connettono a un server di report

Dopo aver pubblicato i criteri di configurazione dell'app, gli utenti e i dispositivi che appartengono alla lista di distribuzione definita per quei criteri hanno l'esperienza seguente quando avviano l'app per dispositivi mobili iOS di Power BI. 

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

