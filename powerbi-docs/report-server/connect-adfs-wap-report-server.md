---
title: Usare il proxy applicazione Web e Active Directory Federation Services - Server di report di Power BI
description: Informazioni su come usare il proxy applicazione Web e Active Directory Federation Services (AD FS) per connettersi a Server di report di Power BI e a SQL Server Reporting Services (SSRS) 2016 e versioni successive.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/14/2020
ms.openlocfilehash: 2caa96aceef90ad1d25a521cbf4a3f699a2a64e0
ms.sourcegitcommit: 0ae9328e7b35799d5d9613a6d79d2f86f53d9ab0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2020
ms.locfileid: "76042441"
---
# <a name="use-web-application-proxy-and-active-directory-federated-services---power-bi-report-server"></a>Usare il proxy applicazione Web e Active Directory Federation Services - Server di report di Power BI

Questo articolo illustra come usare il proxy applicazione Web e Active Directory Federation Services (AD FS) per connettersi a Server di report di Power BI e a SQL Server Reporting Services (SSRS) 2016 e versioni successive. Grazie a questa integrazione, gli utenti che si trovano fuori dalla rete aziendale possono accedere ai report di Server di report di Power BI e Reporting Services personali dal browser client usufruendo della protezione della preautenticazione di AD FS. Per le app Power BI per dispositivi mobili è anche necessario [configurare OAuth per la connessione a Server di report di Power BI e a SSRS](../consumer/mobile/mobile-oauth-ssrs.md).

## <a name="prerequisites"></a>Prerequisiti

### <a name="domain-name-services-dns-configuration"></a>Configurazione Domain Name Services (DNS)

- Determinare l'URL pubblico a cui si connetterà l'utente. Può essere simile all'esempio seguente: `https://reports.contosolab.com`.
- Configurare il record DNS per il nome host, `reports.contosolab.com`, ad esempio, in modo che punti all'indirizzo IP pubblico del server proxy applicazione Web.
- Configurare un record DNS pubblico per il server AD FS. Il server AD FS, ad esempio, potrebbe essere stato configurato con l'URL `https://adfs.contosolab.com`.
- Configurare il record DNS in modo che punti all'indirizzo IP pubblico del server proxy applicazione Web, ad esempio `adfs.contosolab.com`. Viene pubblicato nell'ambito dell'applicazione proxy applicazione Web.

### <a name="certificates"></a>Certificati

È necessario configurare i certificati per l'applicazione proxy applicazione Web e per il server AD FS. Entrambi questi certificati devono essere parte di un'autorità di certificazione valida e riconosciuta dai computer in uso.

## <a name="1-configure-the-report-server"></a>1. Configurare il server di report

È necessario assicurarsi che sia disponibile un nome dell'entità servizio (SPN) valido. Il nome SPN valido consente di eseguire l'autenticazione Kerberos in modo corretto e di abilitare il server di report per l'autenticazione con negoziazione.

### <a name="service-principal-name-spn"></a>Nome dell'entità servizio (SPN)

Il nome dell'entità servizio (SPN) è un identificatore univoco per un servizio che usa l'autenticazione Kerberos. Assicurarsi di avere un nome SPN HTTP corretto per il server di report.

Per informazioni su come configurare il corretto nome dell'entità servizio (SPN) per il server di report, vedere [Registrare un nome dell'entità servizio (SPN) per un server di report](https://docs.microsoft.com/sql/reporting-services/report-server/register-a-service-principal-name-spn-for-a-report-server).

### <a name="enabling-negotiate-authentication"></a>Abilitare la negoziazione dell'autenticazione

Per abilitare l'uso dell'autenticazione Kerberos in un server di report è necessario configurare il tipo di autenticazione del server di report come RSWindowsNegotiate. Questa configurazione viene eseguita all'interno del file rsreportserver.config.

```
<AuthenticationTypes>

    <RSWindowsNegotiate />

    <RSWindowsNTLM />

</AuthenticationTypes>
```

Per altre informazioni, vedere [Modificare un file di configurazione di Reporting Services](https://docs.microsoft.com/sql/reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config) e [Configurare l'autenticazione di Windows nel server di report](https://docs.microsoft.com/sql/reporting-services/security/configure-windows-authentication-on-the-report-server).

## <a name="2-configure-active-directory-federation-services-ad-fs"></a>2. Configurare Active Directory Federation Services (AD FS)

È necessario configurare AD FS in un server Windows 2016 all'interno dell'ambiente. La configurazione può essere eseguita usando Server Manager e selezionando Aggiungi ruoli e funzionalità in Gestisci. Per altre informazioni, vedere [Active Directory Federation Services](https://docs.microsoft.com/windows-server/identity/active-directory-federation-services).

Nel server AD FS completare questa procedura usando l'app di gestione di AD FS.

1. Fare clic con il pulsante destro del mouse su **Attendibilità componente** > **Aggiungi attendibilità componente**.

    ![Aggiungi attendibilità componente](media/connect-adfs-wap-report-server/report-server-adfs-add-relying-party-trust.png)

2. Seguire i passaggi nell'**Aggiunta guidata attendibilità componente**.

    Scegliere l'opzione **Non in grado di riconoscere attestazioni** per usare la sicurezza integrata di Windows come meccanismo di autenticazione.

    ![Aggiunta guidata attendibilità componente](media/connect-adfs-wap-report-server/report-server-adfs-add-relying-party-trust-welcome.png)

    Immettere il nome preferito in **Specifica nome visualizzato** e selezionare **Avanti**.
    Aggiungere l'identificatore dell'attendibilità componente: `<ADFS\_URL>/adfs/services/trust`

    Ad esempio: `https://adfs.contosolab.com/adfs/services/trust`

    ![di report di Power BI](media/connect-adfs-wap-report-server/report-server-adfs-configure-identifiers.png)

    Scegliere i **Criteri di controllo di accesso** adatti alle esigenze dell'organizzazione e selezionare **Avanti**.

    ![Scegli criteri di controllo di accesso](media/connect-adfs-wap-report-server/report-server-adfs-choose-access-control.png)
    
    Selezionare **Avanti** e quindi **Fine** per completare l'**Aggiunta guidata attendibilità componente**.

    Al termine, le proprietà delle attendibilità componente dovrebbero avere l'aspetto seguente.

    ![Attendibilità componente](media/connect-adfs-wap-report-server/report-server-adfs-relying-party-trusts.png)

## <a name="3-configure-web-application-proxy-wap"></a>3. Configurare il proxy applicazione Web

È consigliabile abilitare il ruolo di Proxy applicazione Web Windows in un server nell'ambiente in uso. Deve essere in un server Windows 2016. Per altre informazioni, vedere [Proxy di applicazione Web in Windows Server 2016](https://docs.microsoft.com/windows-server/remote/remote-access/web-application-proxy/web-application-proxy-windows-server) e [Pubblicazione di applicazioni con la preautenticazione di ADFS](https://docs.microsoft.com/windows-server/remote/remote-access/web-application-proxy/Publishing-Applications-using-AD-FS-Preauthentication).

### <a name="configure-constrained-delegation"></a>Configurare la delega vincolata

Per passare dall'autenticazione basata su form all'autenticazione di Windows, è necessario usare la delega vincolata con transizione del protocollo. Questo passaggio fa parte della configurazione di Kerberos. Il nome SPN del server di report è già stato definito nella configurazione del server di report.

È necessario configurare la delega vincolata nell'account del computer Server WAP all'interno di Active Directory. Se non si hanno diritti per Active Directory, può essere necessario collaborare con un amministratore di dominio.

Per configurare la delega vincolata, eseguire questa procedura.

1. Sul computer in cui sono installati gli strumenti di Active Directory, avviare **Utenti e computer di Active Directory**.
2. Trovare l'account del computer per il server WAP. Per impostazione predefinita, si trova nel contenitore **Computer**.
3. Fare clic con il pulsante destro sul server WAP e passare a **Proprietà**.
4. Nella scheda **Delega** selezionare **Computer attendibile per la delega solo ai servizi specificati** e quindi **Usa un qualsiasi protocollo di autenticazione**.

    ![Computer attendibile](media/connect-adfs-wap-report-server/report-server-adfs-delegation-use-any.png)

1. Questa opzione consente di impostare una delega vincolata per l'account computer del server proxy applicazione Web. È quindi necessario specificare i servizi che questo computer è autorizzato a delegare.
2. Selezionare **Aggiungi** nella casella Servizi.

    ![Aggiungi attendibilità AD FS](media/connect-adfs-wap-report-server/report-server-adfs-trust-add.png)

1. Selezionare **Utenti o computer**.
2. Immettere l'account del servizio che si sta usando per il server di report. Questo account è lo stesso usato per aggiungere il nome SPN HTTP nella sezione [Configurare il server di report](#1-configure-the-report-server) precedente. 

3. Selezionare il nome SPN HTTP per il server di report e quindi selezionare **OK**.

    > [!NOTE]
    > Potrebbe essere visualizzato solo il nome SPN di NetBIOS. Se esistono entrambi, verranno invece selezionati i nomi SPN di NetBIOS e FQDN.

1. Se si seleziona la casella di controllo **Espansa**, il risultato dovrebbe essere simile al seguente.

    ![Proprietà proxy applicazione Web](media/connect-adfs-wap-report-server/report-server-wap-properties.png)

### <a name="add-wap-application"></a>Aggiungere applicazione WAP

1. Nel server proxy applicazione Web aprire la console **Gestione accesso remoto** e selezionare **Proxy applicazione Web** nel riquadro di spostamento. 

2. Nel riquadro **Attività** selezionare **Pubblica**.

2. Nella pagina di benvenuto selezionare **Avanti**.

    ![Pagina di benvenuto della pubblicazione](media/connect-adfs-wap-report-server/report-server-welcome-publish-new-app-wizard.png)

3. Nella pagina **Preautenticazione** selezionare **Active Directory Federation Services (AD FS)** e quindi selezionare **Avanti**.

    ![Preautenticazione](media/connect-adfs-wap-report-server/report-server-preauthentication-new-app-wizard.png)

4. Selezionare la preautenticazione **Web e MSOFBA**, dato che si configurerà solo l'accesso al server di report tramite browser, non tramite app per dispositivi mobili.

    ![Client supportati](media/connect-adfs-wap-report-server/report-server-supported-clients-publish-new-app-wizard.png)

5. Aggiungere il **Componente** creato nel server AD FS, come illustrato di seguito, e quindi selezionare **Avanti**.

    ![Pubblicazione componente](media/connect-adfs-wap-report-server/report-server-relying-party-publish-new-app-wizard.png)

6. Nella sezione **URL esterno** inserire l'URL accessibile pubblicamente configurato nel server proxy applicazione Web. Aggiungere l'URL configurato con il server di report (Gestione configurazione del server di report) come illustrato di seguito nella sezione **URL server back-end**. Aggiungere il nome SPN del server di report nella sezione **SPN server back-end**.

    ![Impostazioni di pubblicazione](media/connect-adfs-wap-report-server/report-server-publishing-settings-new-app-wizard.png)

7. Selezionare **Avanti** e **Pubblica**.
8. Per convalidare la configurazione proxy applicazione Web, eseguire il comando di PowerShell seguente.

    ```
    Get-WebApplicationProxyApplication "PBIRSBrowser" | FL
    ```

    ![Comando di PowerShell](media/connect-adfs-wap-report-server/report-server-powershell-get-webapplication.png)

## <a name="connect-to-the-report-server-through-the-browser"></a>Connettersi al server di report tramite il browser

È quindi possibile accedere all'URL proxy applicazione Web pubblico, ad esempio `https://reports.contosolab.com/ReportServer` per il servizio Web e `https://reports.contosolab.com/Reports` per il portale Web dal browser. Dopo l'autenticazione, è possibile visualizzare i report.

![Accesso ad AD FS](media/connect-adfs-wap-report-server/report-server-adfs-sign-in.png)

## <a name="next-steps"></a>Passaggi successivi

* [Configurare OAuth per connettersi a Server di report di Power BI e a SSRS](../consumer/mobile/mobile-oauth-ssrs.md)
*[Che cos'è Server di report di Power BI?](get-started.md)  

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)

