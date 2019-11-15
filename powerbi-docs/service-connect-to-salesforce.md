---
title: Connettersi a Salesforce con Power BI
description: Salesforce per Power BI
author: SarinaJoan
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 05/30/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 6fedd3994a9e6a14ea89637a0c12aa8dd47928a9
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73854634"
---
# <a name="connect-to-salesforce-with-power-bi"></a>Connettersi a Salesforce con Power BI
Con Power BI è possibile connettersi facilmente all'account di Salesforce.com. Con questa connessione è possibile recuperare i dati di Salesforce e distribuire automaticamente un dashboard e i report.

Vedere altre informazioni sull'[integrazione di Salesforce](https://powerbi.microsoft.com/integrations/salesforce) con Power BI.

## <a name="how-to-connect"></a>Come connettersi
1. In Power BI selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento.
   
   ![](media/service-connect-to-salesforce/pbi_getdata.png) 
2. Nella casella **Servizi** selezionare **Recupera**.
   
   ![](media/service-connect-to-salesforce/pbi_getservices.png) 
3. Selezionare **Analisi per Salesforce** e **Recupera**.  
   
   ![](media/service-connect-to-salesforce/salesforce.png)
4. Selezionare **Accedi** per avviare il flusso di accesso.
   
    ![](media/service-connect-to-salesforce/dialog.png)
5. Quando richiesto, immettere le credenziali di Salesforce. Selezionare **Consenti** e lasciare che Power BI acceda alle informazioni e ai dati di base di Salesforce.
   
   ![](media/service-connect-to-salesforce/sf_authorize.png)
6. Per configurare gli elementi da importare in Power BI, usare l'opzione dell'elenco a discesa:
   
   * **Dashboard**
     
     Selezionare un dashboard predefinito in base a un utente tipo, ad esempio **Responsabile vendite**. Questi dashboard recuperano un set specifico di dati standard da Salesforce, che non include campi personalizzati.
     
     ![](media/service-connect-to-salesforce/pbi_salesforcechooserole.png)
   * **Report**
     
     Selezionare uno o più report personalizzati dell'account di Salesforce. Questi report corrispondono alle visualizzazioni in Salesforce e possono includere dati di oggetti o campi personalizzati.
     
     ![](media/service-connect-to-salesforce/pbi_salesforcereports.png)
     
     Se non viene visualizzato alcun report, aggiungerli o crearli nell'account di Salesforce e provare nuovamente a connettersi.

7. Selezionare **Connetti** per avviare il processo di importazione. Durante l'importazione viene visualizzata una notifica che indica che l'operazione è in corso. Al termine dell'importazione, vengono visualizzati un dashboard, un report e un set di dati per i dati di Salesforce elencati nel riquadro di spostamento.
   
   ![](media/service-connect-to-salesforce/pbi_getdatasalesforcedash.png)

È possibile modificare il dashboard per visualizzare i dati nel modo preferito. È possibile porre una domanda in Domande e risposte o [selezionare un riquadro](consumer/end-user-tiles.md) per aprire il report sottostante e [modificare o rimuovere i riquadri del dashboard](service-dashboard-edit-tile.md).

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](consumer/end-user-q-and-a.md) nella parte superiore del dashboard
* [Modificare o rimuovere un riquadro](service-dashboard-edit-tile.md) nel dashboard
* [Selezionare un riquadro](service-dashboard-tiles.md) per aprire il report sottostante
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificarne la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="system-requirements-and-considerations"></a>Requisiti di sistema e considerazioni

- Connessione effettuata con un account di Salesforce con accesso API abilitato

- Autorizzazione concessa all'app Power BI durante l'accesso

- Account con un numero di chiamate API disponibili sufficiente per eseguire il pull e aggiornare i dati

- Un token di autenticazione valido è necessario per l'aggiornamento. Salesforce prevede un limite di cinque token di autenticazione per applicazione, quindi assicurarsi di non importare più di cinque set di dati di Salesforce.

- L'API di Report di Salesforce ha una limitazione che consente di supportare al massimo 2000 righe di dati.


## <a name="troubleshooting"></a>Risoluzione dei problemi

Se si riscontrano errori, esaminare i requisiti riportati sopra. 

L'accesso a un dominio personalizzato o sandbox attualmente non è supportato.

### <a name="unable-to-connect-to-the-remote-server-message"></a>Messaggio "Non è possibile connettersi al server remoto"

Se quando si prova a connettersi all'account di Salesforce viene visualizzato il messaggio "Non è possibile connettersi al server remoto", vedere questa soluzione nel forum seguente: [Salesforce Connector sign in Error Message: Unable to connect to the remote server](https://www.outsystems.com/forums/Forum_TopicView.aspx?TopicId=17674&TopicName=log-in-error-message-unable-to-connect-to-the-remote-server&) (Messaggio di errore all'accesso a Salesforce Connector: Non è possibile connettersi al server remoto)


## <a name="next-steps"></a>Passaggi successivi
[Che cos'è Power BI?](fundamentals/power-bi-overview.md)

[Origini dati per il servizio Power BI](service-get-data.md)

