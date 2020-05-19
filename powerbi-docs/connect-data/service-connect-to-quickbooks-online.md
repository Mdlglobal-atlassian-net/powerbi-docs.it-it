---
title: Connettersi a QuickBooks Online con Power BI
description: QuickBooks Online per Power BI
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 05/04/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 4c21c36694f36e4d6f95b8edc920648313dc8a7a
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83348506"
---
# <a name="connect-to-quickbooks-online-with-power-bi"></a>Connettersi a QuickBooks Online con Power BI
Quando ci si connette ai dati di QuickBooks Online da Power BI, vengono immediatamente visualizzati un dashboard e report di Power BI che forniscono informazioni dettagliate sul flusso di cassa aziendale, sulla redditività, sui clienti e molto altro ancora. È possibile usare il dashboard e i report senza alcuna modifica oppure personalizzarli per evidenziare le informazioni a cui si è maggiormente interessati. I dati vengono aggiornati automaticamente una volta al giorno.

Connettersi all'[app modello QuickBooks Online](https://dxt.powerbi.com/getdata/services/quickbooks-online) per Power BI.

>[!NOTE]
>Per importare i dati di QuickBooks Online in Power BI, è necessario usare un account amministratore di QuickBooks Online e accedere con le credenziali di tale account. Non è possibile usare questo connettore con il software QuickBooks Desktop. 

## <a name="how-to-connect"></a>Come connettersi

[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]

3. Selezionare **QuickBooks Online**e quindi **Recupera**.
   
   ![Recuperare QuickBooks](media/service-connect-to-quickbooks-online/qbo.png)

4. In **Installare questa app di Power BI?** selezionare **Installa**.

    ![Installare QuickBooks](media/service-connect-to-quickbooks-online/power-bi-install-quickbooks.png)

4. Nel riquadro **App** selezionare il riquadro **QuickBooks**.

   ![Selezionare il riquadro QuickBooks](media/service-connect-to-quickbooks-online/power-bi-quickbooks-tile.png)

6. In **Operazioni iniziali con la nuova app** selezionare **Connetti**.

    ![Operazioni iniziali con la nuova app](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

4. Selezionare **oAuth2** come Metodo di autenticazione e fare clic su **Accedi**. 
5. Quando richiesto, immettere le credenziali di QuickBooks Online e seguire il processo di autenticazione. Se è già stato effettuato l'accesso a QuickBooks Online nel browser, le credenziali potrebbero non essere  richieste.
   >[!NOTE]
   >Sono necessarie le credenziali dell'account amministratore di QuickBooks Online.
6. Selezionare la società da connettere a Power BI nella schermata successiva.
   
   ![Quasi pronti in QuickBooks](media/service-connect-to-quickbooks-online/pbi_qbo_almost.png)

7. Selezionare **Autorizza** nella schermata successiva per avviare il processo di importazione. Il processo può richiedere qualche minuto a seconda delle dimensioni dei dati aziendali. 
   
   ![Autorizzare QuickBooks](media/service-connect-to-quickbooks-online/pbi_qbo_authorizesm.png)
   
8. Dopo l'importazione dei dati in Power BI, viene visualizzato l'elenco contenuto dell'app QuickBooks: un nuovo dashboard, un nuovo report e un nuovo set di dati.
9. Selezionare il dashboard QuickBooks per avviare il processo di esplorazione. Il dashboard viene creato automaticamente in Power BI per visualizzare i dati importati.

    ![Dashboard QuickBooks](media/service-connect-to-quickbooks-online/power-bi-connect-quickbooks-sample.png)

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](../consumer/end-user-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](../create-reports/service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](../consumer/end-user-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificarne la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="troubleshooting"></a>Risoluzione dei problemi
**"Si è verificato un errore"**

Se dopo aver selezionato **Autorizza**, viene visualizzato un messaggio di errore simile al seguente:

" "Si è verificato un errore". Chiudere la finestra e riprovare.

Un altro utente di questa società ha già effettuato la sottoscrizione per questa applicazione. Contattare [indirizzo di posta elettronica dell'amministratore] per apportare modifiche alla sottoscrizione."

![Si è verificato un errore.](media/service-connect-to-quickbooks-online/pbi_qbo_oopssm.png)

... un altro amministratore della società ha già stabilito la connessione tra i dati aziendali e Power BI. Chiedere all'amministratore di condividere il dashboard. Attualmente, un solo utente amministratore può connettere un determinato set di dati di QuickBooks Online a Power BI. Dopo la creazione del dashboard in Power BI, l'amministratore può condividerlo con più colleghi negli stessi tenant di Power BI.

**"Questa app non è configurata per consentire connessioni dal paese dell'utente"**

Attualmente, Power BI supporta solo le versioni di QuickBooks Online per gli Stati Uniti. 

![This app is not set up to allow connections from your country](media/service-connect-to-quickbooks-online/pbi_qbo_countrynotsupported.png)

## <a name="next-steps"></a>Passaggi successivi
[Che cos'è Power BI?](../fundamentals/power-bi-overview.md)

[Concetti di base del servizio Power BI](../fundamentals/service-basic-concepts.md)
