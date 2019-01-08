---
title: Pacchetto di contenuto Servizio di controllo del database SQL
description: Pacchetto di contenuto Servizio di controllo del database SQL per Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 11/09/2018
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 0d212510fd2856fd509077f35e0f10bb7c5dd4c5
ms.sourcegitcommit: 750f0bfab02af24c8c72e6e9bbdd876e4a7399de
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54008741"
---
# <a name="sql-database-auditing-content-pack-for-power-bi"></a>Pacchetto di contenuto Servizio di controllo del database SQL per Power BI

> [!IMPORTANT]
> Il pacchetto di contenuto Servizio di controllo del database SQL è stato deprecato e non è più disponibile.
 
Il pacchetto di contenuto Power BI per il [servizio di controllo del database SQL](/azure/sql-database/sql-database-auditing/) di Azure consente di comprendere l'attività del database e di ottenere informazioni su discrepanze e anomalie che potrebbero indicare problemi aziendali o possibili violazioni della sicurezza. 

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

* Provare a [porre una domanda nella casella Domande e risposte](consumer/end-user-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](consumer/end-user-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificarne la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="next-steps"></a>Passaggi successivi
[Recuperare dati per Power BI](service-get-data.md)
[Che cos'è Power BI?](power-bi-overview.md)
