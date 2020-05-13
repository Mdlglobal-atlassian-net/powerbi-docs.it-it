---
title: Configurare app per dispositivi mobili con Microsoft Intune
description: Come configurare le app Power BI per dispositivi mobili con Microsoft Intune. Sono incluse informazioni su come aggiungere e distribuire l'applicazione, nonché su come creare criteri delle applicazioni per dispositivi mobili per controllare la sicurezza.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: e621deb2cc2db74d8836900aa65105a075d4cd3c
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83139481"
---
# <a name="configure-mobile-apps-with-microsoft-intune"></a>Configurare app per dispositivi mobili con Microsoft Intune

Microsoft Intune consente alle organizzazioni di gestire dispositivi e applicazioni. Le applicazioni Power BI per dispositivi mobili per iOS e Android si integrano con Intune. Questa integrazione consente di gestire l'applicazione nei dispositivi e di controllare la sicurezza. Attraverso i criteri di configurazione, è possibile controllare aspetti come la richiesta di un PIN di accesso, la modalità di gestione dei dati nell'applicazione e anche la crittografia dei dati dell'applicazione quando l'app non è in uso.

## <a name="general-mobile-device-management-configuration"></a>Configurazione generale della gestione di dispositivi mobili

Questo articolo presuppone che Intune sia configurato correttamente e che ci siano dispositivi registrati con Intune. L'articolo non è inteso come guida completa alla configurazione di Microsoft Intune. Per altre informazioni su Intune, vedere [Informazioni su Intune](/intune/introduction-intune/).

Microsoft Intune può coesistere con MDM (Mobile Device Management, Gestione dei dispositivi mobili) in Office 365. In caso di uso di MDM, il dispositivo apparirà come registrato in MDM, ma è disponibile per la gestione in Intune.

> [!NOTE]
> Dopo aver configurato Intune, l'aggiornamento dei dati in background è disattivato per l'app Power BI per dispositivi mobili nel dispositivo iOS o Android. Power BI aggiorna i dati dal servizio Power BI sul Web quando si accede all'app.

## <a name="step-1-get-the-url-for-the-application"></a>Passaggio 1: Ottenere l'URL per l'applicazione

Prima di creare l'applicazione in Intune, è necessario ottenere gli URL per le app. Per iOS, è possibile ottenere l'URL da iTunes. Per Android, è possibile ottenere l'URL dalla pagina di Power BI per dispositivi mobili.

Salvare l'URL, che sarà necessario quando si crea l'applicazione.

### <a name="get-ios-url"></a>Ottenere l'URL di iOS

Per ottenere l'URL dell'app per iOS, è necessario usare iTunes.

1. Aprire iTunes.

1. Cercare *Power BI*.

1. Nelle sezioni **Applicazioni per iPhone** e **Applicazioni per iPad** dovrebbe essere visualizzata l'app **Microsoft Power BI**. È possibile usare una delle due app a scelta, perché l'URL ottenuto sarà lo stesso.

1. Nell'elenco a discesa **Ottieni** selezionare **Copia il link**.

    ![URL dell'app in iTunes](media/service-admin-mobile-intune/itunes-url.png)

L'URL dovrebbe essere simile a quello indicato di seguito: *https://itunes.apple.com/us/app/microsoft-power-bi/id929738808?mt=8* .

### <a name="get-android-url"></a>Ottenere l'URL di Android

È possibile ottenere l'URL per Google Play dalla [pagina di Power BI per dispositivi mobili](https://powerbi.microsoft.com/mobile/). Selezionare **Scarica da Google Play** per visualizzare la pagina dell'app. È possibile copiare l'URL dalla barra degli indirizzi del browser. L'URL dovrebbe essere simile a quello indicato di seguito: *https://play.google.com/store/apps/details?id=com.microsoft.powerbim* .

## <a name="step-2-create-a-mobile-application-management-policy"></a>Passaggio 2: Creare criteri di gestione delle applicazioni per dispositivi mobili

I criteri di gestione delle applicazioni per dispositivi mobili consentono di imporre elementi come un PIN di accesso. È possibile creare i criteri nel portale di Intune.

È possibile creare prima i criteri oppure l'applicazione. L'ordine di aggiunta non è importante. È sufficiente che sia i criteri sia l'applicazione siano disponibili per il passaggio di distribuzione.

1. Nel portale di Intune selezionare **Criteri** > **Criteri di configurazione**.

    ![Portale di Intune](media/service-admin-mobile-intune/intune-policy.png)

1. Selezionare **Aggiungi**.

1. In **Software** è possibile selezionare Gestione di applicazioni mobili per Android o iOS. Per iniziare rapidamente, è possibile selezionare **Crea criteri con le impostazioni consigliate**oppure è possibile creare criteri personalizzati.

1. Modificare i criteri per configurare le restrizioni da implementare nell'applicazione.

## <a name="step-3-create-the-application"></a>Passaggio 3: Creare l'applicazione

L'applicazione è un riferimento, o un pacchetto, salvato in Intune per la distribuzione. Sarà necessario creare un'applicazione e fare riferimento all'URL dell'app ottenuto da Google Play o da iTunes.

È possibile creare prima i criteri oppure l'applicazione. L'ordine di aggiunta non è importante. È sufficiente che sia i criteri sia l'applicazione siano disponibili per il passaggio di distribuzione.

1. Passare al portale di Intune e scegliere **App** dal menu a sinistra.

1. Selezionare **Aggiungi app**. Verrà avviata l'applicazione **Aggiungi software** .

### <a name="create-for-ios"></a>Creare per iOS

1. Selezionare **App iOS gestita dall'App Store** nell'elenco a discesa.

1. Immettere l'URL dell'app ottenuto nel [passaggio 1](#step-1-get-the-url-for-the-application) e fare clic su **Avanti**.

    ![Installazione software: iOS](media/service-admin-mobile-intune/intune-add-software-ios1.png)

1. Specificare **Autore**, **Nome** e **Descrizione**. Facoltativamente, è possibile specificare un valore per **Icona**. **Categoria** è per l'app del portale aziendale. Al termine, fare clic su **Avanti**.

1. Come piattaforma per la pubblicazione dell'app è possibile scegliere tra **Qualsiasi** (impostazione predefinita), **iPad** o **iPhone**. L'impostazione predefinita è **Qualsiasi** , adatta per entrambi i tipi di dispositivi. L'URL dell'app Power BI per iPhone e per iPad è lo stesso. Selezionare **Avanti**.

1. Selezionare **Carica**.

1. Se l'app non è visualizzata nell'elenco, aggiornare la pagina: passare a **Panoramica**, quindi tornare ad **App**.

    ![Scheda App](media/service-admin-mobile-intune/intune-add-software-ios2.png)

### <a name="create-for-android"></a>Creare per Android

1. Selezionare **Collegamento esterno** nell'elenco a discesa.

1. Immettere l'URL dell'app ottenuto nel [passaggio 1](#step-1-get-the-url-for-the-application) e fare clic su **Avanti**.

    ![Installazione software: Android](media/service-admin-mobile-intune/intune-add-software-android1.png)

1. Specificare **Autore**, **Nome** e **Descrizione**. Facoltativamente, è possibile specificare un valore per **Icona**. **Categoria** è per l'app del portale aziendale. Al termine, fare clic su **Avanti**.

1. Selezionare **Carica**.

1. Se l'app non è visualizzata nell'elenco, aggiornare la pagina: passare a **Panoramica**, quindi tornare ad **App**.

    ![Scheda App](media/service-admin-mobile-intune/intune-add-software-android2.png)

## <a name="step-4-deploy-the-application"></a>Passaggio 4: Distribuire l'applicazione

Dopo aver aggiunto l'applicazione, è necessario distribuirla in modo da renderla disponibile per gli utenti finali. In questo passaggio si assoceranno i criteri creati con l'app.

### <a name="deploy-for-ios"></a>Distribuire per iOS

1. Nella schermata delle app selezionare l'app creata. Selezionare quindi il collegamento **Gestisci distribuzione** .

    ![Gestisci distribuzione](media/service-admin-mobile-intune/intune-deploy-ios1.png)

1. Nella schermata **Seleziona gruppi** è possibile scegliere i gruppi a cui distribuire l'app. Selezionare **Avanti**.

1. Nella schermata **Azione di distribuzione** è possibile scegliere come distribuire l'app. Selezionando **Installazione disponibile**o **Installazione richiesta**è possibile rendere disponibile l'app nel portale aziendale, per consentire agli utenti di installarla su richiesta. Dopo aver scelto l'opzione desiderata, fare clic su **Avanti**.

    ![Azione di distribuzione](media/service-admin-mobile-intune/intune-deploy-ios2.png)

1. Nella schermata **Gestione delle app mobili** è possibile selezionare i criteri di gestione delle app per dispositivi mobili creati nel [passaggio 2](#step-2-create-a-mobile-application-management-policy). I criteri creati verranno visualizzati per impostazione predefinita, se sono gli unici disponibili per iOS. Selezionare **Avanti**.

    ![Gestione delle app mobili](media/service-admin-mobile-intune/intune-deploy-ios3.png)

1. Nella schermata **Profilo VPN** è possibile selezionare i criteri per l'organizzazione, se disponibili. L'opzione predefinita è **Nessuno**. Selezionare **Avanti**.

1. Nella schermata **Configurazione delle app per dispositivi mobili** è possibile selezionare **Criteri di configurazione dell'app** , se sono stati creati criteri. L'opzione predefinita è **Nessuno**. Questa operazione non è obbligatoria. Fare clic su **Fine**.

Dopo che l'app è stata distribuita, nella pagina delle app dovrebbe venire visualizzata l'indicazione **Sì** per confermarne la distribuzione.

### <a name="deploy-for-android"></a>Distribuire per Android

1. Nella schermata delle app selezionare l'app creata. Selezionare quindi il collegamento **Gestisci distribuzione** .

    ![Gestisci distribuzione](media/service-admin-mobile-intune/intune-deploy-android1.png)
1. Nella schermata **Seleziona gruppi** è possibile scegliere i gruppi a cui distribuire l'app. Selezionare **Avanti**.

1. Nella schermata **Azione di distribuzione** è possibile scegliere come distribuire l'app. Selezionando **Installazione disponibile**o **Installazione richiesta**è possibile rendere disponibile l'app nel portale aziendale, per consentire agli utenti di installarla su richiesta. Dopo aver scelto l'opzione desiderata, fare clic su **Avanti**.

    ![Azione di distribuzione](media/service-admin-mobile-intune/intune-deploy-android2.png)

1. Nella schermata **Gestione delle app mobili** è possibile selezionare i criteri di gestione delle app per dispositivi mobili creati nel [passaggio 2](#step-2-create-a-mobile-application-management-policy). I criteri creati verranno visualizzati per impostazione predefinita, se sono gli unici disponibili per Android. Fare clic su **Fine**.

    ![Gestione delle app mobili](media/service-admin-mobile-intune/intune-deploy-android3.png)

Dopo che l'app è stata distribuita, nella pagina delle app dovrebbe venire visualizzata l'indicazione **Sì** per confermarne la distribuzione.

## <a name="step-5-install-the-application-on-a-device"></a>Passaggio 5: Installare l'applicazione in un dispositivo

L'applicazione viene installata usando l'app *Portale aziendale*. Se il portale aziendale non è stato installato, è possibile ottenere l'app dallo store per la piattaforma iOS o Android. Accedere al portale aziendale con l'account di accesso aziendale.

1. Aprire l'app del portale aziendale.

1. Se l'app Power BI non è elencata nella sezione App in evidenza, selezionare **App aziendali**.

    ![App aziendali](media/service-admin-mobile-intune/intune-companyportal1.png)

1. Selezionare l'app Power BI distribuita.

    ![App Power BI](media/service-admin-mobile-intune/intune-companyportal2.png)

1. Selezionare **Installa**.

    ![Installare l'app](media/service-admin-mobile-intune/intune-companyportal3.png)

1. Se si usa iOS, verrà effettuato il push dell'app. Selezionare **Installa** nella finestra di dialogo relativa al push.

    ![Installazione dell'app](media/service-admin-mobile-intune/intune-companyportal5.png)

1. Dopo l'installazione dell'app, verrà visualizzata l'indicazione **Gestito dall'azienda**. Se nei criteri è stato abilitato l'accesso con un PIN, verrà visualizzata una schermata come quella illustrata di seguito.

    ![Immettere il PIN](media/service-admin-mobile-intune/intune-powerbi-pin.png)

## <a name="next-steps"></a>Passaggi successivi

[Configurare e distribuire criteri di gestione delle applicazioni per dispositivi mobili nella console di Microsoft Intune](/intune/app-protection-policies/)  

[App Power BI per dispositivi mobili](../consumer/mobile/mobile-apps-for-mobile-devices.md)  

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)  
