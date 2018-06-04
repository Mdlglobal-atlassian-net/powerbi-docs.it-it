---
title: Acquisizione di informazioni diagnostiche aggiuntive
description: Acquisizione di informazioni diagnostiche aggiuntive
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 06/28/2017
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 76860e740d43a1907692a7cd4fed1a6df68c93d4
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34239223"
---
# <a name="capturing-additional-diagnostic-information"></a>Acquisizione di informazioni diagnostiche aggiuntive
## <a name="capturing-additional-diagnostic-information-for-power-bi"></a>Acquisizione di informazioni diagnostiche aggiuntive per Power BI
Queste istruzioni illustrano le opzioni possibili per raccogliere manualmente informazioni diagnostiche aggiuntive per il client Web di Power BI.  È necessario usare una sola di queste opzioni.

## <a name="network-capture---edge--internet-explorer"></a>Acquisizione di rete - Microsoft Edge e Internet Explorer
1. Passare a [Power BI](https://app.powerbi.com) con Microsoft Edge o Internet Explorer.
2. Aprire gli strumenti di sviluppo di Edge premendo F12.
3. Verrà visualizzata la finestra Strumenti di sviluppo: 
   
   ![](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-developer-tools.png)
4. Passare alla scheda Rete, in cui sarà elencato il traffico già acquisito. 
   
   ![](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab.png)
5. È possibile esplorare la finestra e riprodurre qualsiasi problema che si potrebbe incontrare. È possibile nascondere e mostrare finestra degli strumenti di sviluppo in qualsiasi momento durante la sessione premendo F12.
6. Per interrompere l'acquisizione, è possibile selezionare il quadrato rosso nella scheda Rete dell'area degli strumenti di sviluppo.
   
   ![](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-stop.png)
7. Selezionare l'icona del dischetto per scegliere **Esporta come HAR**.
   
   ![](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-save.png)
8. Specificare un nome file e salvare il file HAR.
   
    Il file HAR conterrà tutte le informazioni sulle richieste di rete tra la finestra del browser e Power BI,  tra cui gli ID attività per ogni richiesta, il timestamp preciso di ogni richiesta ed eventuali informazioni sugli errori restituite al client.  Questa traccia includerà anche i dati usati per popolare gli oggetti visivi presenti nella schermata.
9. È possibile fornire il file HAR al supporto per la revisione.

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

