---
title: Autorizzazioni di Power BI
description: Autorizzazioni di Power BI
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 09/05/2017
ms.author: maghan
ms.openlocfilehash: 4ba0e62dd8c9ba537f56c97489541591ec0bf2bc
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34289419"
---
# <a name="power-bi-permissions"></a>Autorizzazioni di Power BI
## <a name="permission-scopes"></a>Ambiti delle autorizzazioni
Le autorizzazioni di Power BI permettono a un'applicazione di eseguire determinate azioni per conto dell'utente. Per essere valide, tutte le autorizzazioni devono essere approvate da un utente.

| Nome visualizzato | Descrizione | Valore di ambito |
| --- | --- | --- |
| Visualizza tutti i set di dati |L'app può visualizzare tutti i set di dati per l'utente connesso e i set di dati a cui l'utente può accedere. |Dataset.Read.All |
| Lettura e scrittura in tutti i set di dati |L'app può visualizzare e scrivere in tutti i set di dati per l'utente connesso e i set di dati a cui l'utente può accedere. |Dataset.ReadWrite.All |
| Aggiungere dati al set di dati dell'utente (anteprima) |Offre a un'app l'accesso per aggiungere o eliminare righe dei set di dati di un utente. Questa autorizzazione non concede all'app l'accesso ai dati dell'utente. |Data.Alter_Any |
| Creare il contenuto (anteprima) |L'app può creare automaticamente contenuti e set di dati per un utente. |Content.Create |
| Visualizza gruppi di utenti |L'app può visualizzare tutti i gruppi a cui appartiene l'utente connesso. |Group.Read |
| Visualizzare tutti i gruppi |L'app può visualizzare tutti i gruppi a cui appartiene l'utente connesso. |Group.Read.All |
| Visualizzare tutti i dashboard (anteprima) |L'app può visualizzare tutti i dashboard per l'utente connesso e i dashboard a cui l'utente può accedere. |Dashboard.Read.All |
| Visualizza tutti i report (anteprima) |L'app può visualizzare tutti i report per l'utente connesso e i report a cui l'utente può accedere. L'applicazione può anche visualizzare i dati all'interno dei report, nonché la relativa struttura. |Report.Read.All |
| Lettura e scrittura in tutti i report |L'app può visualizzare e scrivere in tutti i report per l'utente connesso e in tutti i report a cui l'utente può accedere. Questo non autorizza la creazione di un nuovo report. |Report.ReadWrite.All |

Un'applicazione può richiedere le autorizzazioni al primo tentativo di accesso alla pagina di un utente passando le autorizzazioni necessarie nel parametro dell'ambito della chiamata. Se le autorizzazioni vengono concesse, un token di accesso verrà restituito all'app e potrà essere usato nelle future chiamate all'API. L'accesso può essere usato solo da un'applicazione specifica.

> [!NOTE]
> Le API di Power BI fanno ancora riferimento alle aree di lavoro per le app come gruppi. I riferimenti ai gruppi indicano che si stanno usando le aree di lavoro per le app.
> 
> 

## <a name="requesting-permissions"></a>Richiesta di autorizzazioni
Anche se è possibile chiamare l'API per effettuare l'autenticazione con un nome utente e una password, per eseguire azioni per conto di un altro utente sarà necessario richiedere autorizzazioni che verranno approvate dall'utente e quindi inviare il token di accesso risultante in tutte le chiamate future. Per questo processo viene seguito il protocollo standard [OAuth 2.0](http://oauth.net/2/). Anche se l'implementazione effettiva può presentare alcune differenze, il flusso di OAuth per Power BI include gli elementi seguenti:

* **Interfaccia utente di accesso** - Si tratta di un'interfaccia utente che può essere chiamata dallo sviluppatore per richiedere autorizzazioni. Se non è già stato fatto, l'utente dovrà effettuare l'accesso. L'utente dovrà anche approvare le autorizzazioni richieste dall'applicazione. La finestra di accesso eseguirà il postback di un codice di accesso o un messaggio di errore a un URL di reindirizzamento fornito.
  * Un URL di reindirizzamento standard dovrebbe essere fornito da Power BI per l'uso da parte delle applicazioni native.
* **Codice di autorizzazione** - I codici di autorizzazione vengono restituiti alle applicazioni Web dopo l'accesso tramite i parametri dell'URL nell'URL di reindirizzamento. Poiché si trovano nei parametri, esistono alcuni rischi a livello di sicurezza. Le applicazioni Web dovranno scambiare il codice di autorizzazione per un token di autorizzazione.
* **Token di autorizzazione** - Permette di autenticare le chiamate API per conto di un altro utente. Ha come ambito un'applicazione specifica. I token hanno una durata predefinita e sarà necessario aggiornarli dopo la scadenza.
* **Token di aggiornamento** - Quando i token scadono, verrà eseguito un processo di aggiornamento.

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

