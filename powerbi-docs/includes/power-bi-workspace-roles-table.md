---
title: Ruoli dell'area di lavoro di Power BI
description: Tabella dei ruoli dell'area di lavoro di Power BI
services: powerbi
author: maggiesMSFT
ms.service: powerbi
ms.topic: include
ms.date: 04/23/2020
ms.author: maggies
ms.custom: include file
ms.openlocfilehash: 5ed3a65f1ef65640c76ada765931a85714aad3af
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82781352"
---
Ecco le funzionalità dei quattro ruoli: amministratori, membri, collaboratori e visualizzatori. Tutte queste funzionalità, a eccezione della visualizzazione e dell'interazione, richiedono una licenza di Power BI Pro.

|Funzionalità   | Amministrativi  | Membro  | Collaboratore  | Visualizzatore |
|---|---|---|---|---|
| Aggiornare ed eliminare l'area di lavoro.  | X  |   |   |   | 
| Aggiungere/rimuovere utenti, inclusi altri amministratori.  | X  |   |   |   |
| Aggiungere membri o altri utenti con autorizzazioni inferiori.  |  X | X  |   |   |
| Pubblicare e aggiornare un'app. |  X | X  |   |   |
| Condividere un elemento o un'app.<sup>1</sup> |  X | X  |   |   |
| Consentire ad altri utenti di ricondividere a loro volta gli elementi.<sup>1</sup> |  X | X  |   |   |
| Includere app nella sezione In primo piano nella home page dei colleghi |  X | X  |   |   |
| Includere dashboard e report nella sezione In primo piano nella home page dei colleghi |  X | X  | X |   |
| Creare, modificare ed eliminare contenuto nell'area di lavoro.  |  X | X  | X  |   |
| Pubblicare report nell'area di lavoro, eliminare contenuto.  |  X | X  | X  |   |
| Creare un report in un'altra area di lavoro in base a un set di dati in questa area di lavoro.<sup>1</sup> |  X | X  | X  |   |
| Copiare un report.<sup>2</sup> | X | X | X |  |
| Pianificare gli aggiornamenti dei dati tramite il gateway locale.<sup>3</sup> | X | X | X |  |
| Modificare le impostazioni di connessione del gateway.<sup>3</sup> | X | X | X |  |
| Visualizzare un elemento e interagire con esso.<sup>4</sup> |  X | X  | X  | X  |
| Leggere i dati archiviati nei flussi di dati dell'area di lavoro | X | X | X | X |

1. I collaboratori e i visualizzatori possono condividere elementi in un'area di lavoro se hanno autorizzazioni di ricondivisione.
2. Per copiare un report e crearne uno in un'altra area di lavoro in base a un set di dati all'interno di questa, è necessaria l'autorizzazione di compilazione per il set di dati. Per i set di dati in questa area di lavoro, le persone con i ruoli Amministratore, Membro e Collaboratore hanno l'autorizzazione di compilazione tramite il ruolo dell'area di lavoro.
3. Tenere presente che sono necessarie anche le autorizzazioni per il gateway. Tali autorizzazioni sono gestite altrove, indipendentemente dalle autorizzazioni e dai ruoli dell'area di lavoro. Per informazioni dettagliate, vedere [Gestire un gateway locale](https://docs.microsoft.com/data-integration/gateway/service-gateway-manage).
4. Anche se non si ha una licenza di Power BI Pro, è possibile visualizzare e interagire con gli elementi nel servizio Power BI se gli elementi si trovano in un'area di lavoro in una capacità Premium.

