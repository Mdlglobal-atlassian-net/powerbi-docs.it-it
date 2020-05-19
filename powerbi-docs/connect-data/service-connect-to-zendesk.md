---
title: Connettersi a Zendesk con Power BI
description: Zendesk per Power BI
author: paulinbar
ms.reviewer: sarinas
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 05/04/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 17d65296246100180f722dfccacb31ee9ebeade7
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83327163"
---
# <a name="connect-to-zendesk-with-power-bi"></a>Connettersi a Zendesk con Power BI

Questo articolo illustra come eseguire il pull dei dati dall'account Zendesk con un'app modello di Power BI. L'app Zendesk offre un dashboard di Power BI e un set di report di Power BI che rendono disponibili informazioni dettagliate sul numero di ticket e sulle prestazioni degli agenti. I dati vengono aggiornati automaticamente una volta al giorno. 

Dopo aver installato l'app modello, è possibile personalizzare il dashboard e il report per evidenziare le informazioni a cui si è maggiormente interessati. È quindi possibile eseguirne la distribuzione come app ai colleghi dell'organizzazione.

Connettersi all'[app modello Zendesk](https://app.powerbi.com/getdata/services/zendesk) oppure leggere altre informazioni sull'[integrazione di Zendesk](https://powerbi.microsoft.com/integrations/zendesk) con Power BI.

Dopo avere installato l'app modello, è possibile modificare il dashboard e il report. È quindi possibile eseguirne la distribuzione come app ai colleghi dell'organizzazione.

>[!NOTE]
>Per la connessione, è necessario un account amministratore di Zendesk. Altre informazioni sui [requisiti](#system-requirements) sono disponibili più avanti.

## <a name="how-to-connect"></a>Come connettersi

[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]

3. Selezionare **Zendesk** \> **Scarica adesso**.
4. In **Installare questa app di Power BI?** selezionare **Installa**.
4. Nel riquadro **App** selezionare il riquadro **Zendesk**.

    ![Riquadro dell'app Zendesk per Power BI](media/service-connect-to-zendesk/power-bi-zendesk-tile.png)

6. In **Operazioni iniziali con la nuova app** selezionare **Connetti**.

    ![Operazioni iniziali con la nuova app](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

4. Specificare l'URL associato all'account. Il formato dell'URL è **https://company.zendesk.com** . Per informazioni dettagliate su [come trovare questi parametri](#finding-parameters), vedere più avanti.
   
   ![Connetti a Zendesk](media/service-connect-to-zendesk/pbi_zendeskconnect.png)

5. Quando richiesto, immettere le credenziali di Zendesk.  Selezionare **oAuth 2** come meccanismo di autenticazione e fare clic su **Accedi**. Seguire il flusso di autenticazione di Zendesk. Se è già stato effettuato l'accesso a Zendesk nel browser, le credenziali potrebbero non essere richieste.
   
   > [!NOTE]
   > Questa app modello richiede la connessione a un account amministratore Zendesk. 
   > 
   
   ![Accedere con oAuth2](media/service-connect-to-zendesk/pbi_zendesksignin.png)
6. Fare clic su **Consenti** per consentire a Power BI di accedere ai dati Zendesk.
   
   ![Fare clic su Consenti](media/service-connect-to-zendesk/zendesk2.jpg)
7. Fare clic su **Connetti** per avviare il processo di importazione. 
8. Dopo l'importazione dei dati in Power BI, viene visualizzato l'elenco contenuto dell'app Zendesk: un nuovo dashboard, un nuovo report e un nuovo set di dati.
9. Selezionare il dashboard per avviare il processo di esplorazione.

    ![Dashboard di Zendesk](media/service-connect-to-zendesk/power-bi-zendesk-dashboard.png)
   
## <a name="modify-and-distribute-your-app"></a>Modificare e distribuire l'app

È stata installata l'app modello Zendesk. Ciò significa che è stata anche creata l'area di lavoro Zendesk. Nell'area di lavoro è possibile modificare il report e il dashboard e quindi eseguirne la distribuzione come *app* ai colleghi dell'organizzazione. 

1. Per visualizzare tutti i contenuti della nuova area di lavoro Zendesk, nel riquadro di spostamento selezionare **Aree di lavoro** > **Zendesk**. 

    ![Area di lavoro Zendesk nel riquadro di spostamento](media/service-connect-to-zendesk/power-bi-zendesk-workspace-left-nav.png)

    Questa visualizzazione rappresenta l'elenco di contenuti per l'area di lavoro. Nell'angolo in alto a destra è disponibile il comando **Aggiorna app**. Quando si è pronti per distribuire l'app ai colleghi, è possibile iniziare. 

    ![Elenco contenuto di Zendesk](media/service-connect-to-zendesk/power-bi-zendesk-content-list.png)

2. Selezionare **Report** e **Set di dati** per visualizzare gli altri elementi nell'area di lavoro.

    Leggere altre informazioni sulla [distribuzione di app](../collaborate-share/service-create-distribute-apps.md) ai colleghi.

## <a name="system-requirements"></a>Requisiti di sistema
Per accedere all'app modello Zendesk, è necessario un account amministratore di Zendesk. Gli agenti o gli utenti finali interessati a visualizzare i dati di Zendesk possono aggiungere un suggerimento ed esaminare il connettore di Zendesk in [Power BI Desktop](desktop-connect-to-data.md).

## <a name="finding-parameters"></a>Individuazione dei parametri
L'URL di Zendesk corrisponderà a quello usato per accedere all'account Zendesk. Se non si è certi di quale sia l'URL di Zendesk, è possibile vedere la [Guida di accesso](https://www.zendesk.com/login/) di Zendesk.

## <a name="troubleshooting"></a>Risoluzione dei problemi
In caso di problemi di connessione, verificare l'URL di Zendesk e assicurarsi che si stia usando un account amministratore di Zendesk.

## <a name="next-steps"></a>Passaggi successivi

* [Creare le nuove aree di lavoro in Power BI](../collaborate-share/service-create-the-new-workspaces.md)
* [Installare e usare app in Power BI](../consumer/end-user-apps.md)
* [Connettersi alle app Power BI per servizi esterni](service-connect-to-services.md)
* Domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
