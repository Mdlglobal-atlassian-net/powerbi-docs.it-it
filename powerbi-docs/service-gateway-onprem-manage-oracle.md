---
title: Gestire l'origine dati - Oracle
description: Come gestire il gateway dati locale e le origini dati che vi appartengono.
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: cb7856b0b5ac84684e8d0648b91e45805218cead
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73872471"
---
# <a name="manage-your-data-source---oracle"></a>Gestire l'origine dati - Oracle

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Dopo aver [installato il gateway dati locale](/data-integration/gateway/service-gateway-install), è necessario [aggiungere le origini dati](service-gateway-data-sources.md#add-a-data-source) che possono essere usate con il gateway. Questo articolo illustra come usare i gateway e le origini dati Oracle per l'aggiornamento pianificato o per DirectQuery.

## <a name="install-the-oracle-client"></a>Installare il client Oracle

Per connettere il gateway al server Oracle, è necessario avere installato e configurato il Provider di dati Oracle per .NET (ODP.NET). ODP.NET fa parte di Oracle Data Access Components (ODAC).

Per le versioni a 32 bit di Power BI Desktop, usare il collegamento seguente per scaricare e installare il client Oracle a 32 bit:

* [Oracle Data Access Components (ODAC) a 32 bit con strumenti di sviluppo Oracle per Visual Studio (12.1.0.2.4)](https://www.oracle.com/technetwork/topics/dotnet/utilsoft-086879.html)

Per le versioni a 64 bit di Power BI Desktop o per il gateway dati locale, usare il collegamento seguente per scaricare e installare il client Oracle a 64 bit:

* [ODAC 12.2c versione 1 (12.2.0.1.0) a 64 bit per Windows x64](https://www.oracle.com/technetwork/database/windows/downloads/index-090165.html)

Dopo l'installazione del client, configurare il file tnsnames.ora con le informazioni corrette per il proprio database. Power BI Desktop e il gateway si basano sul nome del servizio di rete net_service_name definito nel file tnsnames.ora. Se il valore di net_service_name non è configurato, non è possibile connettersi. Il percorso predefinito per il file tnsnames.ora è `[Oracle Home Directory]\Network\Admin\tnsnames.ora`. Per altre informazioni su come configurare i file tnsnames.ora, vedere [Oracle: Parametri di denominazione locale (tnsnames.ora)](https://docs.oracle.com/cd/B28359_01/network.111/b28317/tnsnames.htm).

### <a name="example-tnsnamesora-file-entry"></a>Esempio di immissione nel file tnsnames.ora

Il formato di base di una voce del file tnsnames.ora è il seguente:

```
net_service_name=
 (DESCRIPTION=
   (ADDRESS=(protocol_address_information))
   (CONNECT_DATA=
     (SERVICE_NAME=service_name)))
```

Di seguito è riportato un esempio delle informazioni relative al server e alla porta:

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

Per altre informazioni sull'aggiunta di un'origine dati, vedere [Aggiungere un'origine dati](service-gateway-data-sources.md#add-a-data-source). In **Tipo di origine dati** selezionare **Oracle**.

![Aggiungere l'origine dati Oracle](media/service-gateway-onprem-manage-oracle/data-source-oracle.png)

Dopo aver selezionato il tipo di origine dati Oracle, inserire le informazioni per l'origine dati, tra cui **Server** e **Database**. 

In **Metodo di autenticazione** è possibile scegliere **Windows** o **Di base**. Scegliere **Di base** se si intende usare un account creato in Oracle invece dell'autenticazione di Windows. Immettere quindi le credenziali da usare per questa origine dati.

> [!NOTE]
> Tutte le query all'origine dati verranno eseguite utilizzando queste credenziali. Per altre informazioni sulla modalità di archiviazione delle credenziali, vedere [Archiviazione di credenziali crittografate nel cloud](service-gateway-data-sources.md#store-encrypted-credentials-in-the-cloud).

![Compilazione delle impostazioni origine dati](media/service-gateway-onprem-manage-oracle/data-source-oracle2.png)

Dopo aver compilato tutti i campi, selezionare **Aggiungi**. È ora possibile usare questa origine dati per l'aggiornamento pianificato o per DirectQuery in un server Oracle locale. Se la connessione ha esito positivo, viene visualizzato il messaggio *Connessione riuscita*.

![Visualizzazione dello stato della connessione](media/service-gateway-onprem-manage-oracle/datasourcesettings4.png)

### <a name="advanced-settings"></a>Impostazioni avanzate

È possibile configurare il livello di privacy per l'origine dati, se necessario. Questa impostazione controlla il modo in cui possono essere combinati i dati e viene usata solo per l'aggiornamento pianificato, ma non si applica a DirectQuery. Per altre informazioni sui livelli di privacy per l'origine dati, vedere [Livelli di privacy (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540).

![Impostazione del livello di privacy](media/service-gateway-onprem-manage-oracle/datasourcesettings9.png)

## <a name="use-the-data-source"></a>Usare l'origine dati

Dopo aver creato l'origine dati, è possibile usarla con le connessioni DirectQuery o l'aggiornamento pianificato.

> [!WARNING]
> I nomi del server e del database devono corrispondere tra Power BI Desktop e l'origine dati all'interno del gateway dati locale.

Il collegamento tra il set di dati e l'origine dati all'interno del gateway si basa sul nome del server e sul nome del database. Tali nomi devono corrispondere. Se ad esempio si specifica un indirizzo IP per il nome del server all'interno di Power BI Desktop, è necessario usare l'indirizzo IP per l'origine dati nella configurazione del gateway. Anche questo nome deve corrispondere con un alias definito nel file tnsnames.ora. Per altre informazioni sul file tnsnames.ora, vedere [Installazione del client Oracle](#install-the-oracle-client).

Questo vale sia per DirectQuery che per l'aggiornamento pianificato.

### <a name="use-the-data-source-with-directquery-connections"></a>Usare l'origine dati con le connessioni DirectQuery

Verificare che i nomi del server e del database corrispondano tra Power BI Desktop e l'origine dati configurata per il gateway. È anche necessario assicurarsi che l'utente sia elencato nella scheda **Utenti** dell'origine dati per pubblicare i set di dati DirectQuery. La selezione per DirectQuery avviene all'interno di Power BI Desktop alla prima importazione dei dati. Per altre informazioni su come usare DirectQuery, vedere [Usare DirectQuery in Power BI Desktop](desktop-use-directquery.md).

Dopo la pubblicazione, da Power BI Desktop o **Recupera dati**, i report devono iniziare a funzionare. Dopo la creazione dell'origine dati nel gateway, potrebbero essere necessari alcuni minuti prima di usare la connessione.

### <a name="use-the-data-source-with-scheduled-refresh"></a>Uso dell’origine dati con l'aggiornamento pianificato

Se si è presenti nella scheda **Utenti** dell'origine dati configurata all'interno del gateway e i nomi del server e del database corrispondono, il gateway viene visualizzato come opzione da usare con l'aggiornamento pianificato.

![Visualizzazione degli utenti](media/service-gateway-onprem-manage-oracle/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="troubleshooting"></a>Risoluzione dei problemi

Quando la sintassi di denominazione non è corretta o non è configurata correttamente, possono verificarsi vari errori di Oracle:

* ORA-12154: TNS: impossibile risolvere l'identificativo di connessione specificato.
* ORA-12514: TNS: il listener non è attualmente a conoscenza del servizio richiesto nel descrittore di connessione.
* ORA-12541: TNS: nessun listener.
* ORA-12170: TNS: si è verificato il timeout della connessione.
* ORA-12504: TNS: il listener non ha ricevuto SERVICE_NAME in CONNECT_DATA.

Questi errori possono verificarsi se il client Oracle non è installato o se non è configurato correttamente. Se è installato, verificare che il file tnsnames.ora sia configurato correttamente e che sia in uso il valore di net_service_name corretto. È anche necessario assicurarsi che il valore di net_service_name sia lo stesso tra il computer che usa Power BI Desktop e quello che esegue il gateway. Per altre informazioni, vedere [Installazione del client Oracle](#install-the-oracle-client).

> [!NOTE]
> Potrebbe anche verificarsi un problema di compatibilità tra la versione del server Oracle e la versione del client Oracle. In genere, queste versioni devono corrispondere.

Per altre informazioni sulla risoluzione dei problemi relativi al gateway, vedere [Risolvere i problemi del gateway dati locale](/data-integration/gateway/service-gateway-tshoot).

## <a name="next-steps"></a>Passaggi successivi

* [Risolvere i problemi relativi ai gateway - Power BI](service-gateway-onprem-tshoot.md)
* [Power BI Premium](service-premium.md)

Altre domande? Provare a chiedere alla [community di Power BI](https://community.powerbi.com/).

