---
title: Controllo delle versioni del modello di dati di Power BI
description: Modello di dati esposto da un servizio OData
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 76947b1e311bbd1a21e09ce39461a70bed61d926
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "79079601"
---
# <a name="data-model-versioning"></a>Controllo delle versioni del modello di dati

Il modello di dati esposto da un servizio OData, ad esempio il modello di dati di Power BI, definisce un contratto tra il servizio OData e i relativi client. I servizi possono estendere il relativo modello solo nella misura in cui non interrompe i client esistenti. Modifiche significative, ad esempio la rimozione di proprietà o la modifica del tipo delle proprietà esistenti, richiedono la distribuzione di una nuova versione del servizio tramite un URL radice del servizio diverso per il nuovo modello.  
  
Le aggiunte del modello di dati seguenti sono considerate sicure e non richiedono servizi per controllare la versione del relativo punto di ingresso.  
  
* Aggiunta di una proprietà che ammette i valori Null o ha valori predefiniti. Se ha lo stesso nome di una proprietà dinamica esistente, deve essere dello stesso tipo (o tipo di base) di questa proprietà.  
* Aggiunta di una proprietà di navigazione che ammette i valori Null o con valore di raccolta. Se ha lo stesso nome di una proprietà di navigazione dinamica esistente, deve essere dello stesso tipo (o tipo di base) di questa proprietà.  
* Aggiunta di un nuovo tipo di entità al modello.  
* Aggiunta di un nuovo tipo complesso al modello.  
* Aggiunta di un nuovo set di entità.  
* Aggiunta di un nuovo singleton.  
* Aggiunta di un'azione, una funzione, un'importazione dell'azione o un'importazione della funzione.
* Aggiunta di un parametro azione che ammette i valori Null.  
* Aggiunta di una definizione di tipo o enumerazione.  
* Aggiunta di un'annotazione a un elemento del modello che non deve essere riconosciuto dal client per interagire correttamente con il servizio.  
  
Per apportare queste modifiche incrementali al modello, i client ***DEVONO*** essere preparati per i servizi. In particolare, i client devono essere preparati per ricevere le proprietà e i tipi derivati non definiti in precedenza dal servizio.  
  
I servizi ***NON DEVONO*** modificare il proprio modello di dati in base all'utente autenticato. Se il modello di dati dipende dall'utente o dal gruppo di utenti, tutte le modifiche DEVONO essere sicure, secondo quanto definito in questa sezione riguardo al confronto tra il modello completo e il modello visibile agli utenti che hanno autorizzazioni limitate.  
  
Per altre informazioni sugli standard del modello di dati, vedere la pagina relativa allo standard [OData Version 4.0 Part 1: Protocol Plus Errata 02](https://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html).  
  
## <a name="see-also"></a>Vedere anche
[Panoramica dell'API REST di Power BI](https://docs.microsoft.com/rest/api/power-bi/)