---
title: Pacchetto di contenuto Servizio di controllo del database SQL
description: Pacchetto di contenuto Servizio di controllo del database SQL per Power BI
services: powerbi
documentationcenter: 
author: SarinaJoan
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 08/10/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: eec1af16156e4d4180dd130f4dd285bb78b19903
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/24/2018
---
# <a name="sql-database-auditing-content-pack-for-power-bi"></a>Pacchetto di contenuto Servizio di controllo del database SQL per Power BI
Il pacchetto di contenuto Power BI per il [servizio di controllo del database SQL](http://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/) di Azure consente di comprendere l'attività del database e di ottenere informazioni su discrepanze e anomalie che potrebbero indicare problemi aziendali o possibili violazioni della sicurezza. 

Connettersi al [pacchetto di contenuto Servizio di controllo del database SQL](https://app.powerbi.com/getdata/services/sql-db-auditing) per Power BI.

>[!NOTE]
>Il pacchetto di contenuto importa i dati da tutte le tabelle che contengono "AuditLogs" nel nome e li aggiunge a una singola tabella del modello di dati denominata "AuditLogs". Verranno inclusi gli ultimi 250.000 eventi e i dati verranno aggiornati quotidianamente.

## <a name="how-to-connect"></a>Come connettersi
1. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro.
   
   ![](media/service-connect-to-azure-sql-database-auditing/pbi_getdata.png) 
2. Nella casella Servizi selezionare Recupera.
   
   ![](media/service-connect-to-azure-sql-database-auditing/pbi_getservices.png) 
3. Selezionare **Servizio di controllo del database SQL** \>**Recupera**.
   
   ![](media/service-connect-to-azure-sql-database-auditing/sqldbaudit.png)
4. Nella finestra di connessione al servizio di controllo del database SQL:
   
   - Immettere l'URL o il nome dell'account di Archiviazione tabelle di Azure in cui sono archiviati i log.
   
   - Immettere il nome del server SQL a cui si è interessati. Immettere "\*" per caricare i log di controllo per tutti i server.
   
   - Immettere il nome del database SQL a cui si è interessati. Immettere "\*" per caricare i log di controllo per tutti i database.
   
   - Immettere il nome della tabella di Azure che contiene i log a cui si è interessati. Immettere "\*" per caricare i log di controllo da tutte le tabelle che contengono "AuditLogs" nel nome.
   
   >[!IMPORTANT]
   >Per motivi di prestazioni si consiglia di specificare sempre un nome di tabella esplicito, anche se tutti i log di controllo vengono archiviati in una singola tabella.
   
   - Immettere la data di inizio dei log di controllo a cui si è interessati. Immettere "\*" per caricare i log di controllo senza un limite di tempo inferiore o "1d" per caricare i log di controllo dell'ultimo giorno.
   
   - Immettere la data di fine dei log di controllo a cui si è interessati. Immettere "\*" per caricare i log di controllo senza un limite di tempo superiore.
   
   ![](media/service-connect-to-azure-sql-database-auditing/dbauditing_param.png)
5. In Metodo di autenticazione selezionare **Chiave**, immettere il valore di **Chiave account** \> **Accedi**.
   
   ![](media/service-connect-to-azure-sql-database-auditing/pbi_sqlauditing3.png)
6. Dopo l'importazione dei dati in Power BI, nel riquadro di spostamento sinistro vengono visualizzati il nuovo dashboard, il nuovo report e il nuovo set di dati. I nuovi elementi sono contrassegnati con un asterisco giallo \*.
   
   ![](media/service-connect-to-azure-sql-database-auditing/pbi_sqldbauditingnewdash.png)

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](power-bi-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](service-dashboard-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificare la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="next-steps"></a>Passaggi successivi
[Recuperare dati per Power BI](service-get-data.md)
[Introduzione a Power BI](service-get-started.md)
