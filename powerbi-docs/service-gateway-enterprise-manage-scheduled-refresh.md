---
title: Gestire l'origine dati - Importazione/aggiornamento pianificato
description: Come gestire il gateway dati locale e le origini dati che vi appartengono. Questo articolo è specifico per le origini dati che possono essere usate con operazioni di importazione/aggiornamento pianificato.
author: arthiriyer
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: arthii
LocalizationGroup: Gateways
ms.openlocfilehash: 13d8cd9838cdcb035e7dd30a1180ac77957441ea
ms.sourcegitcommit: 7e845812874b3347bcf87ca642c66bed298b244a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/13/2020
ms.locfileid: "79207414"
---
# <a name="manage-your-data-source---importscheduled-refresh"></a>Gestire l'origine dati - Importazione/aggiornamento pianificato

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Dopo aver [installato il gateway dati locale](/data-integration/gateway/service-gateway-install), è necessario [aggiungere le origini dati](service-gateway-data-sources.md#add-a-data-source) che possono essere usate con il gateway. Questo articolo descrive l'uso di gateway e origini dati per l'aggiornamento pianificato rispetto all'uso di DirectQuery o di connessioni in tempo reale.

## <a name="add-a-data-source"></a>Aggiungere un'origine dati

Per altre informazioni sull'aggiunta di un'origine dati, vedere [Aggiungere un'origine dati](service-gateway-data-sources.md#add-a-data-source). Selezionare un tipo di origine dati.

Tutti i tipi di origini dati elencati possono essere usati per l'aggiornamento pianificato con il gateway dati locale. È possibile usare Analysis Services, SQL Server e SAP HANA per l'aggiornamento pianificato o per le connessioni DirectQuery/in tempo reale.

![Selezionare l'origine dati](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings2.png)

Inserire quindi le informazioni per l'origine dati, che includono le informazioni sull'origine e le credenziali usate per accedere all'origine dati.

> [!NOTE]
> Tutte le query all'origine dati vengono eseguite usando queste credenziali. Per altre informazioni sulla modalità di archiviazione delle credenziali, vedere [Archiviazione di credenziali crittografate nel cloud](service-gateway-data-sources.md#store-encrypted-credentials-in-the-cloud).

![Compilazione delle impostazioni origine dati](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings3-oracle.png)

Per un elenco dei tipi di origine dati che possono essere usati con l'aggiornamento pianificato, vedere l'[elenco dei tipi di origine dati disponibili](service-gateway-data-sources.md#list-of-available-data-source-types).

Dopo aver compilato tutti gli elementi, selezionare **Aggiungi**. È ora possibile usare questa origine dati per l'aggiornamento pianificato con i dati locali. Se la connessione ha esito positivo, viene visualizzato il messaggio *Connessione riuscita*.

![Visualizzazione dello stato della connessione](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings4.png)

### <a name="advanced-settings"></a>Impostazioni avanzate

È possibile configurare il livello di privacy per l'origine dati, se necessario. Questa impostazione controlla il modo in cui possono essere combinati i dati L'impostazione viene usata solo per l'aggiornamento pianificato. Per altre informazioni sui livelli di privacy per l'origine dati, vedere [Livelli di privacy (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540).

![Impostazione del livello di privacy](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings9.png)

## <a name="use-the-data-source-for-scheduled-refresh"></a>Usare l'origine dati per l'aggiornamento pianificato

Dopo aver creato l'origine dati, è possibile usarla con le connessioni DirectQuery o l'aggiornamento pianificato.

> [!NOTE]
> I nomi del server e del database devono corrispondere tra Power BI Desktop e l'origine dati all'interno del gateway dati locale.

Il collegamento tra il set di dati e l'origine dati all'interno del gateway si basa sul nome del server e sul nome del database. Tali nomi devono corrispondere. Se ad esempio si specifica un indirizzo IP per il nome del server all'interno di Power BI Desktop, è necessario usare l'indirizzo IP per l'origine dati nella configurazione del gateway. Se si usa *SERVER\INSTANCE* (SERVER\ISTANZA) in Power BI Desktop, è necessario usarlo anche nell'origine dati configurata per il gateway.

Se si è presenti nella scheda **Utenti** dell'origine dati configurata all'interno del gateway e i nomi del server e del database corrispondono, il gateway viene visualizzato come opzione da usare con l'aggiornamento pianificato.

![Visualizzazione degli utenti](media/service-gateway-enterprise-manage-scheduled-refresh/powerbi-gateway-enterprise-schedule-refresh.png)

> [!WARNING]
> Se il set di dati contiene più origini dati, è necessario aggiungere ogni origine dati all'interno del gateway. Se al gateway non vengono aggiunte origini dati, il gateway non è disponibile per l'aggiornamento pianificato.

## <a name="limitations"></a>Limitazioni

OAuth non è uno schema di autenticazione supportato con il gateway dati locale. Non è possibile aggiungere origini dati che richiedono OAuth. Se il set di dati dispone di un'origine dati che richiede OAuth, non è possibile usare il gateway per l'aggiornamento pianificato.

## <a name="next-steps"></a>Passaggi successivi

* [Risoluzione dei problemi del gateway dati locale](/data-integration/gateway/service-gateway-tshoot)
* [Risolvere i problemi relativi ai gateway - Power BI](service-gateway-onprem-tshoot.md)

Altre domande? Provare la [Community di Power BI](https://community.powerbi.com/).
