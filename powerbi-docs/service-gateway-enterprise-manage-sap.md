---
title: Gestire l'origine dati - SAP HANA
description: Come gestire il gateway dati locale e le origini dati che vi appartengono. Questo articolo è specifico per SAP HANA.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: a09388e8b22131c9b82771385b69142b18e3cc84
ms.sourcegitcommit: 73228d0a9038b8369369c059ad06168d2c5ff062
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/02/2019
ms.locfileid: "68730014"
---
# <a name="manage-your-data-source---sap-hana"></a>Gestire l'origine dati - SAP HANA

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Dopo aver [installato il gateway dati locale](/data-integration/gateway/service-gateway-install), sarà necessario [aggiungere le origini dati](service-gateway-data-sources.md#add-a-data-source) che possono essere usate con il gateway. Questo articolo descrive l'uso di gateway e origini dati SAP HANA per l'aggiornamento pianificato o per DirectQuery.

## <a name="add-a-data-source"></a>Aggiungere un'origine dati

Per informazioni sull'aggiunta di un'origine dati, vedere [Aggiungere un'origine dati](service-gateway-data-sources.md#add-a-data-source). Selezionare SAP HANA per il **Tipo di origine dati**.

![Aggiungere l'origine dati SAP HANA](media/service-gateway-enterprise-manage-sap/datasourcesettings2-sap.png)

Dopo aver selezionato il tipo di origine dati SAP HANA, inserire le informazioni per l'origine dati, tra cui **Server**, **Nome utente** e **Password**.

> [!NOTE]
> Tutte le query all'origine dati verranno eseguite utilizzando queste credenziali. Per altre informazioni sulla modalità di archiviazione delle credenziali, vedere [Archiviazione di credenziali crittografate nel cloud](service-gateway-data-sources.md#store-encrypted-credentials-in-the-cloud).

![Compilazione delle impostazioni origine dati](media/service-gateway-enterprise-manage-sap/datasourcesettings3-sap.png)

Selezionare **Aggiungi** dopo aver compilato tutti i campi. È ora possibile usare questa origine dati per l'aggiornamento pianificato, o per DirectQuery, su un server SAP HANA locale. Verrà visualizzato *Connessione riuscita* se la connessione ha avuto esito positivo.

![Visualizzazione dello stato della connessione](media/service-gateway-enterprise-manage-sap/datasourcesettings4.png)

### <a name="advanced-settings"></a>Impostazioni avanzate

È possibile configurare il livello di privacy per l'origine dati, se necessario. Questa impostazione controlla il modo in cui vengono combinati i dati. L'impostazione viene usata solo per l'aggiornamento pianificato e non per DirectQuery. Per altre informazioni sui livelli di privacy per l'origine dati, vedere [Livelli di privacy (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540).

![Impostazione del livello di privacy](media/service-gateway-enterprise-manage-sap/datasourcesettings9.png)

## <a name="using-the-data-source"></a>Uso dell'origine dati

Dopo aver creato l'origine dati, sarà possibile usarla con le connessioni DirectQuery o l'aggiornamento pianificato.

> [!NOTE]
> I nomi del server e del database devono corrispondere tra Power BI Desktop e l'origine dati all'interno del gateway dati locale.

Il collegamento tra il set di dati e l'origine dati all'interno del gateway si basa sul nome del server e sul nome del database. Questi nomi devono corrispondere. Ad esempio, se si indica un indirizzo IP per il nome del server, all'interno di Power BI Desktop è necessario usare l'indirizzo IP per l'origine dati all'interno della configurazione del gateway. Se si usa *SERVER\ISTANZA*, in Power BI Desktop è necessario usarlo anche all'interno dell'origine dati configurata per il gateway.

Questo vale sia per DirectQuery che per l'aggiornamento pianificato.

### <a name="using-the-data-source-with-directquery-connections"></a>Uso dell'origine dati con le connessioni DirectQuery

È necessario assicurarsi che i nomi del server e del database corrispondano tra Power BI Desktop e l'origine dati configurata per il gateway. È inoltre necessario assicurarsi che l'utente sia elencato nella scheda **Utenti** dell'origine dati per pubblicare i set di dati DirectQuery. La selezione per DirectQuery avviene all'interno di Power BI Desktop alla prima importazione dei dati. Per altre informazioni su DirectQuery, vedere [Usare DirectQuery in Power BI](desktop-use-directquery.md).

Dopo la pubblicazione, da Power BI Desktop o **Recupera dati**, i report dovrebbero iniziare a funzionare. Dopo la creazione dell'origine dati all'interno del gateway potrebbero essere necessari alcuni minuti prima di poter usare la connessione.

### <a name="using-the-data-source-with-scheduled-refresh"></a>Uso dell’origine dati con l'aggiornamento pianificato

Se si è presenti nella scheda **Utenti** dell'origine dati configurata all'interno del gateway e i nomi del server e del database corrispondono, il gateway viene visualizzato come un'opzione per l'uso con l'aggiornamento pianificato.

![Visualizzazione degli utenti](media/service-gateway-enterprise-manage-sap/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="next-steps"></a>Passaggi successivi

* [Risoluzione dei problemi del gateway dati locale](/data-integration/gateway/service-gateway-tshoot)
* [Risolvere i problemi relativi ai gateway - Power BI](service-gateway-onprem-tshoot.md)  

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

