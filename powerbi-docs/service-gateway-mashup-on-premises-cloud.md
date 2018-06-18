---
title: Unire o aggiungere origini dati locali e cloud
description: Usare il gateway dati locale per unire o aggiungere origini dati locali e cloud nella stessa query.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-gateways
ms.topic: conceptual
ms.date: 06/06/2018
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 3550a3fc0cfc51b61e1d7e51a50c2a36325f2388
ms.sourcegitcommit: 49570ab8f5b5cd5bab4cd388f4281b1372bcb80b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/09/2018
ms.locfileid: "35250661"
---
# <a name="merge-or-append-on-premises-and-cloud-data-sources"></a>Unire o aggiungere origini dati locali e cloud

Il gateway dati locale consente di unire o aggiungere origini dati locali e cloud nella stessa query. Questa funzionalità risulta utile quando si vuole eseguire il mashup di dati da più origini senza usare query separate.

## <a name="prerequisites"></a>Prerequisiti

- Un [gateway installato](service-gateway-install.md) in un computer locale.
- Un file di Power BI Desktop con query in cui sono combinate origini dati locali e cloud.

1. Nell'angolo in alto a destra del servizio Power BI selezionare l'icona dell'ingranaggio ![Icona dell'ingranaggio Impostazioni](media/service-gateway-mashup-on-premises-cloud/icon-gear.png) > **Gestisci gateway**.

    ![Gestisci gateway](media/service-gateway-mashup-on-premises-cloud/manage-gateways.png)

2. Selezionare il gateway da configurare.

3. In **Impostazioni del cluster di gateway** selezionare **Consente l'aggiornamento delle origini dati cloud dell'utente tramite questo cluster di gateway** > **Applica**.

    ![Aggiornamento tramite il cluster di gateway](media/service-gateway-mashup-on-premises-cloud/refresh-gateway-cluster.png)

4. Nel cluster di gateway aggiungere le [origini dati locali](service-gateway-enterprise-manage-scheduled-refresh.md#add-a-data-source) usate nelle query. Non è necessario aggiungere qui le origini dati cloud.

4. Caricare nel servizio Power BI il file di Power BI Desktop con le query in cui sono combinate origini dati locali e cloud.

5. Nella pagina **Impostazioni set di dati** per il nuovo set di dati:

    - Per l'origine locale, selezionare il gateway associato a questa origine dati.

    - In **Credenziali dell'origine dati** modificare le credenziali dell'origine dati cloud come necessario.

    ![Impostazioni set di dati](media/service-gateway-mashup-on-premises-cloud/dataset-settings.png)

6. Dopo che le credenziali cloud sono state impostate sarà possibile aggiornare il set di dati tramite l'opzione **Aggiorna adesso** oppure pianificarne l'aggiornamento periodico.


## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sull'aggiornamento dei dati per i gateway, vedere [Uso dell'origine dati per l'aggiornamento pianificato](service-gateway-enterprise-manage-scheduled-refresh.md#using-the-data-source-for-scheduled-refresh).