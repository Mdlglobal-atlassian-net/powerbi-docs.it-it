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
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65100161"
---
# <a name="capture-additional-diagnostic-information-for-power-bi"></a>Acquisire informazioni diagnostiche aggiuntive per Power BI

Questo articolo fornisce istruzioni per raccogliere manualmente informazioni diagnostiche aggiuntive dal client web di Power BI.

1. Passare a [Power BI](https://app.powerbi.com) con Microsoft Edge o Internet Explorer.

1. Premere **F12** per aprire gli strumenti di sviluppo di Microsoft Edge.

   ![Scheda elementi strumenti screenshot di Microsoft Edge per gli sviluppatori.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-developer-tools.png)

1. Selezionare la scheda **Network** (Rete). in cui sarà elencato il traffico già acquisito.

   ![Scheda di rete di strumenti screenshot di Microsoft Edge per gli sviluppatori.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab.png)

    è possibile:

    * Passare all'interno della finestra e riprodurre qualsiasi problema che potrebbero riscontrare.

    * Nascondere e mostrare finestra degli strumenti lo sviluppatore in qualsiasi momento durante la sessione premendo F12.

1. Per arrestare la sessione di profilatura, è possibile selezionare il quadrato rosso nella **rete** scheda dello sviluppatore dell'area degli strumenti.

   ![Scheda di rete screenshot di Microsoft Edge Developer tools con una chiamata all'esterno di pulsante di arresto.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-stop.png)

1. Selezionare l'icona del dischetto per esportare i dati come file di archivio HTTP (HAR).

   ![Scheda rete di strumenti screenshot di Microsoft Edge per gli sviluppatori con un callout dell'icona del dischetto.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-save.png)

1. Specificare un nome file e salvare il file HAR.

    Il file HAR conterrà tutte le informazioni sulle richieste di rete tra la finestra del browser e Power BI tra cui:

    * L'ID attività per ogni richiesta.

    * Il timestamp preciso di ogni richiesta.

    * Informazioni su eventuali errori restituiti al client.

    Questa traccia includerà anche i dati usati per popolare gli oggetti visivi presenti nella schermata.

1. È possibile fornire il file HAR al supporto per la revisione.

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)
