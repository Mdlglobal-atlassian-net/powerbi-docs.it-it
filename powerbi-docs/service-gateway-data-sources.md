---
title: Gestire le origini dati
description: Informazioni su come gestire le origini dati in Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Gateways
ms.openlocfilehash: 3a4b343894f23d6f5720d95eb6c92436259befaa
ms.sourcegitcommit: a58461fe7dfa65c751490b52de5fc73f8e69a17f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/19/2019
ms.locfileid: "68352208"
---
# <a name="manage-data-sources"></a>Gestire le origini dati

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Power BI supporta molte origini dati locali, ognuna delle quali ha requisiti specifici. Un gateway può essere usato per una singola origine dati o più origini dati. Questo esempio illustra l'aggiunta di un'origine dati SQL Server, ma i passaggi per altre origini dati sono simili.

>[!NOTE]
>La maggior parte delle operazioni di gestione delle origini dati può essere eseguita anche usando le API. Per altre informazioni, vedere [API REST (gateway).](/rest/api/power-bi/gateways)

## <a name="add-a-data-source"></a>Aggiungere un'origine dati

>[!NOTE]
>Non è possibile aggiungere gruppi senza un messaggio di posta elettronica.

1. Nell'angolo in alto a destra del servizio Power BI selezionare l'icona dell'ingranaggio ![Icona dell'ingranaggio Impostazioni](media/service-gateway-data-sources/icon-gear.png) > **Gestisci gateway**.

    ![Gestisci gateway](media/service-gateway-data-sources/manage-gateways.png)

2. Selezionare un gateway > **Aggiungi origine dati** oppure passare a Gateway > **Aggiungi origine dati**.

    ![Aggiungere l'origine dati](media/service-gateway-data-sources/add-data-source.png)

3. Selezionare il **Tipo di origine dati**.

    ![Selezionare SQL Server](media/service-gateway-data-sources/select-sql-server.png)

4. Immettere le informazioni per l'origine dati. In questo esempio si tratta di **Server**, **Database** e altri dettagli.  

    ![Impostazioni origine dati](media/service-gateway-data-sources/data-source-settings.png)

5. Per SQL Server, scegliere il **Metodo di autenticazione** **Windows** oppure **Di base** (autenticazione SQL). Se si sceglie **Di base**, immettere le credenziali per l'origine dati.

6. Facoltativamente, in **Impostazioni avanzate** configurare il [livello di privacy](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540) per l'origine dati (non si applica a [DirectQuery](desktop-directquery-about.md)).

    ![Impostazioni avanzate](media/service-gateway-data-sources/advanced-settings.png)

7. Selezionare **Aggiungi**. Se il processo ha esito positivo viene visualizzato il messaggio *Connessione riuscita*.

    ![Connessione riuscita](media/service-gateway-data-sources/connection-successful.png)

Ora è possibile usare questa origine dati per includere dati da SQL Server nei dashboard e nei report di Power BI.

## <a name="remove-a-data-source"></a>Rimuovere un'origine dati

Se non si usa più un'origine dati, è possibile rimuoverla. Tenere presente che rimuovendo un'origine dati si interrompono tutti i dashboard o i report che si basano sull'origine dati specificata.

Per rimuovere un'origine dati, passare all'origine dati e selezionare **Rimuovi**.

![Rimuovere un'origine dati](media/service-gateway-data-sources/remove-data-source.png)

## <a name="using-the-data-source-for-scheduled-refresh-or-directquery"></a>Uso dell'origine dati per l'aggiornamento pianificato o DirectQuery

Dopo aver creato l'origine dati, sarà possibile usarla con le connessioni DirectQuery o l'aggiornamento pianificato.

> [!NOTE]
>I nomi del server e del database devono corrispondere tra Power BI Desktop e l'origine dati all'interno del gateway dati locale.

Il collegamento tra il set di dati e l'origine dati nel gateway si basa sul nome del server e sul nome del database. Questi nomi devono corrispondere. Ad esempio, se si indica un indirizzo IP per il nome del server, in Power BI Desktop è necessario usare l'indirizzo IP per l'origine dati nella configurazione del gateway. Se si usa *SERVER\ISTANZA*, in Power BI Desktop è necessario usarlo lo stesso nell'origine dati configurata per il gateway.

Se si è presenti nella scheda **Utenti** dell'origine dati configurata nel gateway e i nomi del server e del database corrispondono, il gateway viene visualizzato come un'opzione per l'uso con l'aggiornamento pianificato.

![Connessione gateway](media/service-gateway-data-sources/gateway-connection.png)

> [!WARNING]
> Se il set di dati contiene più origini dati, è necessario aggiungere ogni origine dati nel gateway. Se al gateway non vengono aggiunte una o più origini dati, il gateway non verrà visualizzato come disponibile per l'aggiornamento pianificato.

### <a name="limitations"></a>Limitazioni

OAuth è uno schema di autenticazione supportato solo per connettori personalizzati con il gateway dati locale. Non è possibile aggiungere altre origini dati che richiedono OAuth. Se il set di dati ha un'origine dati che richiede OAuth e l'origine dati non è un connettore personalizzato, non sarà possibile usare il gateway per l'aggiornamento pianificato.

## <a name="manage-users"></a>Gestire gli utenti

Dopo avere aggiunto un'origine dati a un gateway, si concede l'accesso all'origine dati specifica (non all'intero gateway) a utenti e gruppi di sicurezza abilitati per la posta elettronica. L'elenco di utenti di un'origine dati controlla soltanto chi è autorizzato a pubblicare report che includono dati provenienti da tale origine. I proprietari di report possono creare dashboard, pacchetti di contenuto e app e condividerli con altri utenti.

È anche possibile concedere a utenti e gruppi di sicurezza l'accesso amministrativo al gateway.

### <a name="add-users-to-a-data-source"></a>Aggiungere utenti a un'origine dati

1. Nell'angolo in alto a destra del servizio Power BI selezionare l'icona dell'ingranaggio ![Icona dell'ingranaggio Impostazioni](media/service-gateway-data-sources/icon-gear.png) > **Gestisci gateway**.

2. Selezionare l'origine dati in cui si vogliono aggiungere utenti.

3. Selezionare **Utenti** e immettere un utente dell'organizzazione al quale si intende concedere accesso all'origine dati selezionata. Ad esempio, nella schermata seguente si aggiungono Maggie e Adam.

    ![Scheda Utenti](media/service-gateway-data-sources/users-tab.png)

4. Selezionare **Aggiungi**. Il membro aggiunto compare nella casella.

    ![Aggiungere un utente](media/service-gateway-data-sources/add-user.png)

Non sono richieste altre operazioni. Non dimenticare che è necessario aggiungere utenti a ogni origine dati a cui si vuole concedere l'accesso. L'elenco di utenti è diverso per ogni origine dati, di conseguenza è necessario aggiungere gli utenti a ogni origine dati separatamente.

### <a name="remove-users-from-a-data-source"></a>Rimuovere utenti da un'origine dati

Nella scheda **Utenti** dell'origine dati è possibile rimuovere gli utenti o i gruppi di sicurezza che possono usare l'origine dati.

![Rimuovi utente](media/service-gateway-data-sources/remove-user.png)

## <a name="storing-encrypted-credentials-in-the-cloud"></a>Archiviazione di credenziali crittografate nel cloud

Quando si aggiunge un'origine dati al gateway, è necessario fornire le credenziali per l'origine dati. Tutte le query all'origine dati verranno eseguite utilizzando queste credenziali. Le credenziali vengono crittografate usando la crittografia asimmetrica in modo che non possano essere decrittografate nel cloud prima di essere archiviate nel cloud. Le credenziali vengono inviate al computer che esegue il gateway, in locale dove vengono decrittografate durante l'accesso alle origini dati.

## <a name="list-of-available-data-source-types"></a>Elenco di tipi di origini dati disponibili

Il gateway dati locale supporta le seguenti origini dati per Power BI. Oltre alle origini dati locali, anche per le origini protette da un firewall, una VPN o una rete virtuale potrebbe essere necessario un gateway dati.

| **Origine dati** | **Dinamico/DirectQuery** | **Aggiornamento pianificato o manuale configurato dall'utente** |
| --- | --- | --- |
| Active Directory |No |Sì |
| Amazon Redshift |Sì |Sì |
| Analysis Services |Sì |Sì |
| Cubi AtScale |Sì |Sì |
| Archiviazione BLOB di Azure |No |Sì |
| Azure DevOps Server |No |Sì |
| Archiviazione tabelle di Azure |No |Sì |
| Connettore BI |Sì |Sì |
| Denodo |Sì |Sì |
| Dremio |Sì |Sì |
| EmigoDataSourceConnector |No |Sì |
| Essbase |Sì |Sì |
| Exasol |Sì |Sì |
| File |No |Sì |
| Cartella |No |Sì |
| Paxata |No |Sì |
| IBM DB2 |Sì |Sì |
| Database Informix IBM |No |Sì |
| IBM Netezza |Sì |Sì |
| Impala |Sì |Sì |
| ODBC Jethro |Sì |Sì |
| Kyligence Enterprise |Sì |Sì |
| ODBC MarkLogic |Sì |Sì |
| Microsoft Graph Security |No |Sì |
| MySQL |No |Sì |
| ODBC |No |Sì |
| OData |No |Sì |
| OleDb |No |Sì |
| Oracle |Sì |Sì |
| PostgreSQL |No |Sì |
| QubolePresto |Sì |Sì |
| Connettore di base rapido |No |Sì |
| Server messaggi SAP Business Warehouse |Sì |Sì |
| Server SAP Business Warehouse |Sì |Sì |
| SAP HANA |Sì |Sì |
| SQL Server |Sì |Sì |
| SharePoint |No |Sì |
| Snowflake |Sì |Sì |
| Spark |Sì |Sì |
| SurveyMonkey |No |Sì |
| Sybase |No |Sì |
| TeamDesk.Database |No |Sì |
| Teradata |Sì |Sì |
| Vertica |Sì |Sì |
| Web |No |Sì |
| Workforce Dimensions |No |Sì |

## <a name="next-steps"></a>Passaggi successivi

* [Gestire l'origine dati - Analysis Services](service-gateway-enterprise-manage-ssas.md)
* [Gestire l'origine dati - SAP HANA](service-gateway-enterprise-manage-sap.md)
* [Gestire l'origine dati - SQL Server](service-gateway-enterprise-manage-sql.md)
* [Gestire l'origine dati - Oracle](service-gateway-onprem-manage-oracle.md)
* [Gestire l'origine dati - Importazione/aggiornamento pianificato](service-gateway-enterprise-manage-scheduled-refresh.md)
* [Indicazioni per la distribuzione di un gateway dati](service-gateway-deployment-guidance.md)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)
