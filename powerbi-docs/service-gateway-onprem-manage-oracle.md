---
title: Gestire l'origine dati - Oracle
description: Come gestire il gateway dati locale e le origini dati che vi appartengono.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: af3ebd421a82448ce8a3f13661801ffc1d0051e0
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271465"
---
# <a name="manage-your-data-source---oracle"></a>Gestire l'origine dati - Oracle

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Dopo aver [installato il gateway dati locale](/data-integration/gateway/service-gateway-install), sarà necessario [aggiungere le origini dati](service-gateway-data-sources.md#add-a-data-source) che possono essere usate con il gateway. Questo articolo illustra come usare i gateway e le origini dati Oracle per l'aggiornamento pianificato o per DirectQuery.

## <a name="installing-the-oracle-client"></a>Installazione del client Oracle

Per far sì che il gateway possa connettersi al server Oracle, è necessario aver installato e configurato il Provider di dati Oracle per .NET (ODP.NET), che fa parte di Oracle Data Access Components (ODAC).

Per le versioni a **32 bit** di Power BI Desktop, usare il collegamento seguente per scaricare e installare il client Oracle a **32 bit**:

* [Oracle Data Access Components (ODAC) a 32 bit con strumenti di sviluppo Oracle per Visual Studio (12.1.0.2.4)](http://www.oracle.com/technetwork/topics/dotnet/utilsoft-086879.html)

Per le versioni a **64 bit** di Power BI Desktop o per il gateway dati locale, usare il collegamento seguente per scaricare e installare il client Oracle a **64 bit**:

* [ODAC 12.2c versione 1 (12.2.0.1.0) a 64 bit per Windows x64](http://www.oracle.com/technetwork/database/windows/downloads/index-090165.html)

Dopo averlo installato, sarà necessario configurare il file tnsnames.ora con le informazioni corrette per il proprio database. Power BI Desktop e il gateway si baseranno sul nome del servizio di rete net_service_name definito nel file tnsnames.ora. Se non è configurato, non sarà possibile connettersi. Il percorso predefinito per il file tnsnames.ora è `[Oracle Home Directory]\Network\Admin\tnsnames.ora`. Per altre informazioni su come configurare i file tnsnames.ora, vedere [Oracle: Local Naming Parameters (tnsnames.ora)](https://docs.oracle.com/cd/B28359_01/network.111/b28317/tnsnames.htm) (Oracle: parametri di denominazione locale - tnsnames.ora).

### <a name="example-tnsnamesora-file-entry"></a>Esempio di immissione nel file tnsnames.ora

Il formato di base di un'immissione nel file tnsnames.ora è il seguente:

```
net_service_name=
 (DESCRIPTION=
   (ADDRESS=(protocol_address_information))
   (CONNECT_DATA=
     (SERVICE_NAME=service_name)))
```

Di seguito è riportato un esempio delle informazioni relative al server e alla porta già compilate.

```
CONTOSO =
  (DESCRIPTION =
    (ADDRESS = (PROTOCOL = TCP)(HOST = oracleserver.contoso.com)(PORT = 1521))
    (CONNECT_DATA =
      (SERVER = DEDICATED)
      (SERVICE_NAME = CONTOSO)
    )
  )
```

## <a name="add-a-data-source"></a>Aggiungere un'origine dati

Per informazioni sull'aggiunta di un'origine dati, vedere [Aggiungere un'origine dati](service-gateway-data-sources.md#add-a-data-source). Selezionare Oracle per il **Tipo di origine dati**.

![Aggiungere l'origine dati Oracle](media/service-gateway-onprem-manage-oracle/data-source-oracle.png)

Dopo aver selezionato il tipo di origine dati Oracle, inserire le informazioni per l'origine dati, tra cui il **Server** e il **Database**.  

È inoltre necessario scegliere un **metodo di autenticazione**,  **Windows** o **Basic**.  È preferibile scegliere **Basic** se si intende usare un account creato all'interno di Oracle anziché l'autenticazione di Windows. Immettere le credenziali che verranno utilizzate per questa origine dati.

> [!NOTE]
> Tutte le query all'origine dati verranno eseguite utilizzando queste credenziali. Per altre informazioni su come vengono archiviate le credenziali, vedere [Archiviazione di credenziali crittografate nel cloud](service-gateway-data-sources.md#storing-encrypted-credentials-in-the-cloud).

![Compilazione delle impostazioni origine dati](media/service-gateway-onprem-manage-oracle/data-source-oracle2.png)

Selezionare **Aggiungi** dopo aver compilato tutti i campi. È ora possibile usare questa origine dati per l'aggiornamento pianificato o DirectQuery su un server Oracle locale. Verrà visualizzato *Connessione riuscita* se la connessione ha avuto esito positivo.

![Visualizzazione dello stato della connessione](media/service-gateway-onprem-manage-oracle/datasourcesettings4.png)

### <a name="advanced-settings"></a>Impostazioni avanzate

È possibile configurare il livello di privacy per l'origine dati, se necessario. Questa impostazione controlla il modo in cui vengono combinati i dati. L'impostazione viene usata solo per l'aggiornamento pianificato e non per DirectQuery. Per altre informazioni sui livelli di privacy per l'origine dati, vedere [Livelli di privacy (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540).

![Impostazione del livello di privacy](media/service-gateway-onprem-manage-oracle/datasourcesettings9.png)

## <a name="using-the-data-source"></a>Uso dell'origine dati

Dopo aver creato l'origine dati, sarà possibile usarla con le connessioni DirectQuery o tramite l'aggiornamento pianificato.

> [!WARNING]
> I nomi del server e del database devono corrispondere tra Power BI Desktop e l'origine dati all'interno del gateway dati locale.

Il collegamento tra il set di dati e l'origine dati all'interno del gateway si basa sul nome del server e sul nome del database. Questi nomi devono corrispondere. Ad esempio, se si indica un indirizzo IP per il nome del server, all'interno di Power BI Desktop è necessario usare l'indirizzo IP per l'origine dati all'interno della configurazione del gateway. Anche questo nome deve corrispondere con un alias definito nel file tnsnames.ora. Per altre informazioni sul file tnsnames.ora, vedere [Installazione del client Oracle](#installing-the-oracle-client).

Questo vale sia per DirectQuery che per l'aggiornamento pianificato.

### <a name="using-the-data-source-with-directquery-connections"></a>Uso dell'origine dati con le connessioni DirectQuery

È necessario assicurarsi che i nomi del server e del database corrispondano tra Power BI Desktop e l'origine dati configurata per il gateway. È inoltre necessario assicurarsi che l'utente sia elencato nella scheda **Utenti** dell'origine dati per pubblicare i set di dati DirectQuery. Per DirectQuery, la selezione avviene all'interno di Power BI Desktop alla prima importazione dei dati. Per altre informazioni su DirectQuery, vedere [Usare DirectQuery in Power BI](desktop-use-directquery.md).

Dopo la pubblicazione, da Power BI Desktop o **Recupera dati**, i report dovrebbero iniziare a funzionare. Dopo la creazione dell'origine dati all'interno del gateway potrebbero essere necessari alcuni minuti prima di poter usare la connessione.

### <a name="using-the-data-source-with-scheduled-refresh"></a>Uso dell’origine dati con l'aggiornamento pianificato

Se si è presenti nella scheda **Utenti** dell'origine dati configurata all'interno del gateway e i nomi del server e del database corrispondono, il gateway viene visualizzato come un'opzione per l'uso con l'aggiornamento pianificato.

![Visualizzazione degli utenti](media/service-gateway-onprem-manage-oracle/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="troubleshooting"></a>Risoluzione dei problemi

Quando la sintassi di denominazione non è corretta o non è configurata correttamente, possono verificarsi vari errori di Oracle.

* ORA-12154: TNS: impossibile risolvere l'identificativo di connessione specificato  
* ORA-12514: TNS: il listener non è attualmente a conoscenza del servizio richiesto nel descrittore di connessione  
* ORA-12541: TNS: nessun listener  
* ORA-12170: TNS: si è verificato il timeout della connessione  
* ORA-12504: TNS: il listener non ha ricevuto SERVICE_NAME in CONNECT_DATA  

Questi errori potrebbero verificarsi se il client Oracle non è installato o se non è configurato correttamente. Se è installato, è consigliabile verificare che il file tnsnames.ora sia configurato correttamente e che si usi il valore net_service_name corretto. È anche necessario assicurarsi che il valore net_service_name sia lo stesso tra il computer che usa Power BI Desktop e il computer che esegue il gateway. Per altre informazioni, vedere [Installazione del client Oracle](#installing-the-oracle-client).

> [!NOTE]
> Potrebbe anche verificarsi un problema a causa dell'incompatibilità tra la versione del server Oracle e la versione del client Oracle, che in genere devono corrispondere.

Per altre informazioni sulla risoluzione dei problemi relativi al gateway, vedere [Risoluzione dei problemi del gateway dati locale](/data-integration/gateway/service-gateway-tshoot).

## <a name="next-steps"></a>Passaggi successivi

* [Risolvere i problemi relativi ai gateway - Power BI](service-gateway-onprem-tshoot.md)
* [Power BI Premium](service-premium.md)

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

