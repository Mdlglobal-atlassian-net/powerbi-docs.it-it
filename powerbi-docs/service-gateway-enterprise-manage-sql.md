---
title: Gestire l'origine dati - SQL
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
ms.openlocfilehash: ca8cf2e9c20f2efb4fe4b9f80a936ba887cccc93
ms.sourcegitcommit: 9665bdabce3bfc31f68dd8256b135bfd56f60589
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/06/2019
ms.locfileid: "68832382"
---
# <a name="manage-your-data-source---sql-server"></a>Gestire l'origine dati - SQL Server

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Dopo aver [installato il gateway dati locale](/data-integration/gateway/service-gateway-install), è possibile [aggiungere le origini dati](service-gateway-data-sources.md#add-a-data-source) da usare con il gateway. Questo articolo descrive l'uso di gateway e origini dati SQL Server per l'aggiornamento pianificato o per DirectQuery.

## <a name="add-a-data-source"></a>Aggiungere un'origine dati

Per altre informazioni sull'aggiunta di un'origine dati, vedere [Aggiungere un'origine dati](service-gateway-data-sources.md#add-a-data-source). In **Tipo di origine dati** selezionare **SQL Server**.

![Selezionare l'origine dati SQL Server](media/service-gateway-enterprise-manage-sql/datasourcesettings2.png)

> [!NOTE]
> Quando si usa DirectQuery, il gateway supporta solo **SQL Server 2012 SP1** e versioni successive.

Immettere quindi le informazioni per l'origine dati, tra cui **Server** e **Database**. 

In **Metodo di autenticazione** scegliere **Windows** o **Di base**. Scegliere **Di base** se si intende usare l'autenticazione SQL invece dell'autenticazione di Windows. Immettere quindi le credenziali da usare per questa origine dati.

> [!NOTE]
> Tutte le query nell'origine dati verranno eseguite usando queste credenziali, a meno che l'accesso Single Sign-On (SSO) Kerberos non sia configurato e abilitato per l'origine dati. Con SSO, i set di dati di importazione usano le credenziali archiviate, ma i set di dati di DirectQuery usano l'utente di Power BI corrente per eseguire le query che usano SSO. Per altre informazioni sulla modalità di archiviazione delle credenziali, vedere [Archiviazione di credenziali crittografate nel cloud](service-gateway-data-sources.md#store-encrypted-credentials-in-the-cloud). In alternativa, vedere l'articolo [Usare Kerberos per l'accesso Single Sign-On (SSO) da Power BI alle origini dati locali](service-gateway-sso-kerberos.md).

![Compilazione delle impostazioni origine dati](media/service-gateway-enterprise-manage-sql/datasourcesettings3.png)

Dopo aver compilato tutti i campi, selezionare **Aggiungi**. È ora possibile usare questa origine dati per l'aggiornamento pianificato o per DirectQuery in un'istanza di SQL Server locale. Se la connessione ha esito positivo, viene visualizzato il messaggio *Connessione riuscita*.

![Visualizzazione dello stato della connessione](media/service-gateway-enterprise-manage-sql/datasourcesettings4.png)

### <a name="advanced-settings"></a>Impostazioni avanzate

È possibile configurare il livello di privacy per l'origine dati, se necessario. Questa impostazione controlla il modo in cui possono essere combinati i dati. e viene usata solo per l'aggiornamento pianificato, ma non si applica a DirectQuery. Per altre informazioni sui livelli di privacy per l'origine dati, vedere [Livelli di privacy (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540).

![Impostazione del livello di privacy](media/service-gateway-enterprise-manage-sql/datasourcesettings9.png)

## <a name="use-the-data-source"></a>Usare l'origine dati

Dopo aver creato l'origine dati, è possibile usarla con le connessioni DirectQuery o l'aggiornamento pianificato.

> [!NOTE]
> I nomi del server e del database devono corrispondere tra Power BI Desktop e l'origine dati all'interno del gateway dati locale.

Il collegamento tra il set di dati e l'origine dati all'interno del gateway si basa sul nome del server e sul nome del database. Questi nomi devono corrispondere. Se ad esempio si specifica un indirizzo IP per il nome del server all'interno di Power BI Desktop, è necessario usare l'indirizzo IP per l'origine dati all'interno della configurazione del gateway. Se si usa l'indicazione *SERVER\ISTANZA* in Power BI Desktop, è necessario usarla anche nell'origine dati configurata per il gateway.

Questo vale sia per DirectQuery che per l'aggiornamento pianificato.

### <a name="use-the-data-source-with-directquery-connections"></a>Usare l'origine dati con le connessioni DirectQuery

Verificare che i nomi del server e del database corrispondano tra Power BI Desktop e l'origine dati configurata per il gateway. È anche necessario assicurarsi che l'utente sia elencato nella scheda **Utenti** dell'origine dati per pubblicare i set di dati DirectQuery. La selezione per DirectQuery avviene all'interno di Power BI Desktop alla prima importazione dei dati. Per altre informazioni su come usare DirectQuery, vedere [Usare DirectQuery in Power BI Desktop](desktop-use-directquery.md).

Dopo la pubblicazione, da Power BI Desktop o **Recupera dati**, i report devono iniziare a funzionare. Dopo la creazione dell'origine dati nel gateway, potrebbero essere necessari alcuni minuti prima di usare la connessione.

### <a name="use-the-data-source-with-scheduled-refresh"></a>Uso dell’origine dati con l'aggiornamento pianificato

Se si è presenti nella scheda **Utenti** dell'origine dati configurata all'interno del gateway e i nomi del server e del database corrispondono, il gateway viene visualizzato come opzione da usare con l'aggiornamento pianificato.

![Visualizzazione degli utenti](media/service-gateway-enterprise-manage-sql/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="next-steps"></a>Passaggi successivi

* [Connettersi a dati locali in SQL Server](service-gateway-sql-tutorial.md)
* [Risoluzione dei problemi del gateway dati locale](/data-integration/gateway/service-gateway-tshoot)
* [Risolvere i problemi relativi ai gateway - Power BI](service-gateway-onprem-tshoot.md)
* [Usare Kerberos per l'accesso Single Sign-On (SSO) da Power BI alle origini dati locali](service-gateway-sso-kerberos.md)

Altre domande? Provare a chiedere alla [community di Power BI](http://community.powerbi.com/).

