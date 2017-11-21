---
title: Connettersi a QuickBooks Online con Power BI
description: QuickBooks Online per Power BI
services: powerbi
documentationcenter: 
author: joeshoukry
manager: kfile
backup: maggiesMSFT
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: yshoukry
ms.openlocfilehash: def174cb86b701f628e4637d3a9933a42c5a5740
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-quickbooks-online-with-power-bi"></a>Connettersi a QuickBooks Online con Power BI
Quando ci si connette ai dati di QuickBooks Online da Power BI, vengono immediatamente visualizzati un dashboard e report di Power BI che forniscono informazioni dettagliate sul flusso di cassa aziendale, sulla redditività, sui clienti e molto altro ancora. È possibile usare il dashboard e i report senza alcuna modifica oppure personalizzarli per evidenziare le informazioni a cui si è maggiormente interessati. I dati vengono aggiornati automaticamente una volta al giorno.

Connettersi al [Pacchetto di contenuto QuickBooks Online](https://dxt.powerbi.com/getdata/services/quickbooks-online) per Power BI.

>[!NOTE]
>Per importare i dati di QuickBooks Online in Power BI, è necessario usare un account amministratore di QuickBooks Online e accedere con le credenziali di tale account.

## <a name="how-to-connect"></a>Come connettersi
1. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro.
   
   ![](media/service-connect-to-quickbooks-online/pbi_getdata.png) 
2. Nella casella **Servizi** selezionare **Recupera**.
   
   ![](media/service-connect-to-quickbooks-online/pbi_getservices.png) 
3. Selezionare **QuickBooks Online**e quindi **Recupera**.
   
   ![](media/service-connect-to-quickbooks-online/qbo.png)
4. Selezionare **oAuth2** come Metodo di autenticazione e fare clic su **Accedi**. 
5. Quando richiesto, immettere le credenziali di QuickBooks Online e seguire il processo di autenticazione. Se è già stato effettuato l'accesso a QuickBooks Online nel browser, le credenziali potrebbero non essere  richieste.
   >[!NOTE]
   >Sono necessarie le credenziali dell'account amministratore di QuickBooks Online.
6. Selezionare la società da connettere a Power BI nella schermata successiva.
   
   ![](media/service-connect-to-quickbooks-online/pbi_qbo_almost.png)
7. Selezionare **Autorizza** nella schermata successiva per avviare il processo di importazione. L'operazione può richiedere qualche minuto a seconda delle dimensioni dei dati aziendali. 
   
   ![](media/service-connect-to-quickbooks-online/pbi_qbo_authorizesm.png)
   
   Dopo l'importazione dei dati in Power BI, nel riquadro di spostamento sinistro vengono visualizzati il nuovo dashboard, il nuovo report e il nuovo set di dati. I nuovi elementi sono contrassegnati con un asterisco giallo \*.
   
   ![](media/service-connect-to-quickbooks-online/pbi_qbo_leftnavnew.png)
8. Selezionare il dashboard di QuickBooks Online. Si tratta del dashboard creato automaticamente da Power BI per visualizzare i dati importati. È possibile modificare il dashboard per visualizzare i dati nel modo desiderato. 
   
   ![](media/service-connect-to-quickbooks-online/pbi_qbo_dash.png)

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](service-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](service-dashboard-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificare la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="troubleshooting"></a>Risoluzione dei problemi
**"Si è verificato un errore"**

Se dopo aver selezionato **Autorizza**, viene visualizzato un messaggio di errore simile al seguente:

" "Si è verificato un errore". Chiudere la finestra e riprovare.

Un altro utente di questa società ha già effettuato la sottoscrizione per questa applicazione. Contattare [indirizzo di posta elettronica dell'amministratore] per apportare modifiche alla sottoscrizione."

![](media/service-connect-to-quickbooks-online/pbi_qbo_oopssm.png)

... un altro amministratore della società ha già stabilito la connessione tra i dati aziendali e Power BI. Chiedere all'amministratore di condividere il dashboard. Attualmente, un solo utente amministratore può connettere un determinato set di dati di QuickBooks Online a Power BI. Dopo la creazione del dashboard in Power BI, l'amministratore può condividerlo con più colleghi negli stessi tenant di Power BI.

**"Questa app non è configurata per consentire connessioni dal paese dell'utente"**

Attualmente, Power BI supporta solo le versioni di QuickBooks Online per gli Stati Uniti. 

![](media/service-connect-to-quickbooks-online/pbi_qbo_countrynotsupported.png)

## <a name="next-steps"></a>Passaggi successivi
[Introduzione a Power BI](service-get-started.md)

[Power BI - Concetti di base](service-basic-concepts.md)

