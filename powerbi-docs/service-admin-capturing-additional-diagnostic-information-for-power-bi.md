---
title: Acquisire informazioni diagnostiche aggiuntive
description: Queste istruzioni illustrano le opzioni possibili per raccogliere manualmente informazioni diagnostiche aggiuntive per il client Web di Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/25/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 710fb4cdcf9efb051434966d47c2eaced17ac9ba
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65100161"
---
# <a name="capture-additional-diagnostic-information-for-power-bi"></a>Acquisire informazioni diagnostiche aggiuntive per Power BI

Questo articolo include istruzioni per raccogliere manualmente informazioni diagnostiche aggiuntive per il client Web di Power BI.

1. Passare a [Power BI](https://app.powerbi.com) con Microsoft Edge o Internet Explorer.

1. Premere **F12** per aprire gli strumenti di sviluppo di Microsoft Edge.

   ![Screenshot della scheda Elementi degli strumenti di sviluppo di Microsoft Edge.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-developer-tools.png)

1. Selezionare la scheda **Network** (Rete). in cui sarà elencato il traffico già acquisito.

   ![Screenshot della scheda Rete degli strumenti di sviluppo di Microsoft Edge.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab.png)

    è possibile:

    * Esplorare la finestra e riprodurre qualsiasi problema riscontrato.

    * Nascondere e visualizzare la finestra degli strumenti di sviluppo in qualsiasi momento durante la sessione premendo F12.

1. Per interrompere la profilatura della sessione, selezionare il quadrato rosso nella scheda **Rete** dell'area degli strumenti di sviluppo.

   ![Screenshot della scheda Rete degli strumenti di sviluppo di Microsoft Edge con il pulsante Arresta evidenziato.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-stop.png)

1. Selezionare l'icona del dischetto per esportare i dati come file di archivio HTTP (con estensione har).

   ![Screenshot della scheda Rete degli strumenti di sviluppo di Microsoft Edge con l'icona del dischetto evidenziata.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-save.png)

1. Specificare un nome file e salvare il file HAR.

    Il file con estensione har contiene tutte le informazioni sulle richieste di rete tra la finestra del browser e Power BI, tra cui:

    * ID attività per ogni richiesta.

    * Timestamp preciso per ogni richiesta.

    * Eventuali informazioni sugli errori restituite al client.

    Questa traccia includerà anche i dati usati per popolare gli oggetti visivi presenti nella schermata.

1. È possibile fornire il file HAR al supporto per la revisione.

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)
