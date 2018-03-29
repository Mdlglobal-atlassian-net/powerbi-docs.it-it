---
title: Installare il server di report di Power BI
description: Informazioni su come installare il server di report di Power BI.
services: powerbi
documentationcenter: ''
author: maggiesMSFT
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 03/19/2018
ms.author: maggies
ms.openlocfilehash: 8b8bb3867ec1630dc5163148e4aa20e10c0504b7
ms.sourcegitcommit: 93e7362fc47319959b6992dfd037effdf831d010
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2018
---
# <a name="install-power-bi-report-server"></a>Installare il server di report di Power BI

Informazioni su come installare il server di report di Power BI.

 **Scarica** ![scarica](media/install-report-server/download.png "scarica")

Per scaricare il server di report di Power BI, vedere [Creazione di report in locale con il server di report di Power BI](https://powerbi.microsoft.com/report-server/) e selezionare **Scarica la versione di valutazione gratuita**. 

## <a name="video-install-power-bi-report-server"></a>Video: Installare il server di report di Power BI

<iframe width="640" height="360" src="https://www.youtube.com/embed/zacaEb9A4F0?showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="before-you-begin"></a>Prima di iniziare
Prima di installare il server di report di Power BI è consigliabile esaminare i [requisiti hardware e software per l'installazione del server di report di Power BI](system-requirements.md).

### <a name="power-bi-report-server-product-key"></a>Codice Product Key del Server di report Power BI

#### <a name="power-bi-premium"></a>Power BI Premium
Se è stato acquistato Power BI Premium, nella scheda **Impostazioni Premium** del portale di amministratore di Power BI, si avrà accesso al codice Product Key del Server di Report di Power BI. Questo sarà disponibile solo per gli amministratori globali o per gli utenti a cui è stato assegnato il ruolo di amministratore del servizio Power BI.

![](../media/service-admin-premium-manage/pbirs-product-key.png "Codice Product Key del Server di report di Power BI all'interno di Impostazioni Premium")

Se si seleziona **Chiave del server di report di Power BI** viene visualizzata una finestra di dialogo contenente il codice Product Key. È possibile copiarlo e usarlo durante l'installazione.

![](../media/service-admin-premium-manage/pbirs-product-key-dialog.png "Codice Product Key del Server di report di Power BI")

#### <a name="sql-server-enterprise-software-assurance-sa"></a>SQL Server Enterprise Software Assurance (SA)
Se si dispone di un contratto SQL Server Enterprise SA, è possibile ottenere il codice Product Key dal [Centro servizi per contratti multilicenza](https://www.microsoft.com/Licensing/servicecenter/).

## <a name="install-your-report-server"></a>Installare il server di report
L'installazione del server di report di Power BI è molto semplice e richiede solo pochi passaggi.

Al momento dell'installazione non è necessario un server del motore di database di SQL Server, ma ne servirà uno per configurare Reporting Services dopo l'installazione.

1. Cercare il percorso di PowerBIReportServer.exe e avviare il programma di installazione.
2. Selezionare **Install Power BI Report Server**.
   
    ![Installare il server di report di Power BI](media/install-report-server/pbireportserver-install.png)
3. Scegliere una versione da installare e quindi selezionare **Next**.
   
    ![Scegliere una versione](media/install-report-server/pbireportserver-choose-edition.png)
   
    È possibile scegliere la versione Evaluation o Developer nell'elenco a discesa.
   
    ![](media/install-report-server/pbireportserver-choose-edition2.png)
   
    Altrimenti, è possibile immettere un codice Product Key per il server acquistato dal servizio Power BI o dal Centro servizi per contratti multilicenza. Per altre informazioni su come ottenere il codice Product Key, vedere la sezione [Prima di iniziare](#before-you-begin).
4. Leggere e accettare i termini e le condizioni di licenza, quindi selezionare **Next**.
   
    ![Condizioni di licenza](media/install-report-server/pbireportserver-eula.png)
5. È necessario avere un motore di database per archiviare il database del server di report. Selezionare **Next** per installare solo il server di report.
   
    ![Installare solo i file](media/install-report-server/pbireportserver-install-files-only.png)
6. Specificare il percorso di installazione del server di report. Selezionare **Install** per continuare.
   
    ![Specificare il percorso di installazione](media/install-report-server/pbireportserver-install-file-path.png)
   
    Il percorso predefinito è C:\Programmi\Server di report di Power BI.

1. Dopo la corretta installazione, selezionare **Configure Report Server** per avviare Reporting Services Configuration Manager.
   
    ![Configurare il server di report](media/install-report-server/pbireportserver-configure.png)

## <a name="configuring-your-report-server"></a>Configurazione del server di report

Dopo aver selezionato **Configure Report Server** nella procedura di installazione, verrà visualizzato Reporting Services Configuration Manager. Per altre informazioni, vedere [Reporting Services Configuration Manager](https://docs.microsoft.com/sql/reporting-services/install-windows/reporting-services-configuration-manager-native-mode).

È necessario [creare un database del server di report](https://docs.microsoft.com/sql/reporting-services/install-windows/ssrs-report-server-create-a-report-server-database) per completare la configurazione iniziale di Reporting Services. Per completare questo passaggio è necessario un server di Database SQL Server.

### <a name="creating-a-database-on-a-different-server"></a>Creazione di un database in un server diverso
Se si sta creando il database del server di report in un server di database in un computer diverso, è necessario modificare l'account di servizio del server di report in credenziali riconosciute nel server di database. 

Per impostazione predefinita, il server di report usa l'account del servizio virtuale. Se si prova a creare un database in un server diverso, potrebbe verificarsi l'errore seguente durante il passaggio Applicazione dei diritti di connessione.

`System.Data.SqlClient.SqlException (0x80131904): Windows NT user or group '(null)' not found. Check the name again.`

Per risolvere l'errore, è possibile modificare l'account del servizio in un account del servizio di rete o di dominio. Modificare l'account del servizio nel servizio di rete applica i diritti nel contesto dell'account computer del server di report.

![Configurare l'account del servizio del server di report](media/install-report-server/pbireportserver-configure-account.png)

Per altre informazioni, vedere [Configurare l'account del servizio del server di report](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager).

## <a name="windows-service"></a>Servizio di Windows
Un servizio di Windows viene creato come parte dell'installazione. Viene visualizzato come **Server di report di Power BI**. Il nome del servizio è **PowerBIReportServer**.

![Servizio di Windows del server di report](media/install-report-server/pbireportserver-windows-service.png)

![Proprietà del servizio di Windows del server di report](media/install-report-server/pbireportserver-windows-service2.png)

## <a name="default-url-reservations"></a>Prenotazioni URL predefinite
Le prenotazioni URL sono composte da un prefisso, un nome host, una porta e una directory virtuale:

| Parte | Descrizione |
| --- | --- |
| Prefisso |Il prefisso predefinito è HTTP. Se è stato precedentemente installato un certificato SSL (Secure Sockets Layer), il programma di installazione prova a creare prenotazioni URL che usano il prefisso HTTPS. |
| Nome host |Il nome host predefinito è un carattere jolly complesso (+). Specifica che il server di report accetta qualsiasi richiesta HTTP sulla porta designata per qualsiasi nome host risolto nel computer, tra cui `http://<computername>/reportserver`, `http://localhost/reportserver`, o `http://<IPAddress>/reportserver.` |
| Porta |La porta predefinita è 80. Se si usa una porta diversa dalla porta 80, è necessario aggiungerla in modo esplicito all'URL quando si apre il portale Web in una finestra del browser. |
| Directory virtuale |Per impostazione predefinita, le directory virtuali vengono create nel formato di ReportServer per il servizio Web ReportServer e Report per il portale Web. Per il servizio Web ReportServer, la directory virtuale predefinita è **reportserver**. Per il portale web, la directory virtuale predefinita è **reports**. |

Un esempio di stringa dell'URL completa potrebbe essere come segue:

* `http://+:80/reportserver`, fornisce l'accesso al server di report.
* `http://+:80/reports`, fornisce l'accesso al portale Web.

## <a name="firewall"></a>Firewall
Se si accede al server di report da un computer remoto, è consigliabile assicurarsi di aver configurato le regole del firewall, se è presente.

È necessario aprire la porta TCP che è stata configurata per l'URL del servizio Web e l'URL del portale Web. Per impostazione predefinita, questi vengono configurati sulla porta TCP 80.

## <a name="additional-configuration"></a>Configurazione aggiuntiva
* Per configurare l'integrazione con il servizio Power BI in modo che sia possibile aggiungere elementi del report a un dashboard di Power BI, vedere [Integrazione con il servizio Power BI](https://docs.microsoft.com/sql/reporting-services/install-windows/power-bi-report-server-integration-configuration-manager).
* Per configurare la posta elettronica per l'elaborazione di sottoscrizioni, vedere [Impostazioni di posta elettronica](https://docs.microsoft.com/sql/reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager) e [Recapito di posta elettronica in un server di report](https://docs.microsoft.com/sql/reporting-services/subscriptions/e-mail-delivery-in-reporting-services).
* Per configurare il portale Web in modo che sia possibile accedervi in un computer di report per visualizzare e gestire report, vedere [Configurare un firewall per l'accesso ai server di report](https://docs.microsoft.com/sql/reporting-services/report-server/configure-a-firewall-for-report-server-access) e [Configurare un server di report per l'amministrazione remota](https://docs.microsoft.com/sql/reporting-services/report-server/configure-a-report-server-for-remote-administration).

## <a name="next-steps"></a>Passaggi successivi
[Manuale per l'amministratore](admin-handbook-overview.md)  
[Come trovare il codice Product Key del server di report](find-product-key.md)  
[Installare Power BI Desktop ottimizzato per il server di report di Power BI](install-powerbi-desktop.md)  
[Verificare l'installazione di Reporting Services](https://docs.microsoft.com/sql/reporting-services/install-windows/verify-a-reporting-services-installation)  
[Configurare l'account del servizio del server di report](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager)  
[Configurare gli URL del server di report](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager)  
[Configurare una connessione al database del server di report](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager)  
[Inizializzare un server di report](https://docs.microsoft.com/sql/reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server)  
[Configurare le connessioni SSL in un server di report](https://docs.microsoft.com/sql/reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server)  
[Configurare le autorizzazioni e gli account del servizio di Windows](https://docs.microsoft.com/sql/database-engine/configure-windows/configure-windows-service-accounts-and-permissions)  
[Supporto del browser per il server di report di Power BI](browser-support.md)

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)

