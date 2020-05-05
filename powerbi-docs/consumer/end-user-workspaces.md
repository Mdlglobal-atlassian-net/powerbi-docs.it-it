---
title: Come è organizzato il contenuto nelle aree di lavoro
description: Informazioni sulle aree di lavoro e sui relativi ruoli
author: mihart
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/22/2020
ms.author: mihart
LocalizationGroup: Consumers
ms.openlocfilehash: 801b5cf5400bbe1cc0487eef596ea3d1cdc5fb1e
ms.sourcegitcommit: 9ec2c608b90bf651df613f0714addd251a885039
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2020
ms.locfileid: "82120173"
---
# <a name="collaborate-in-workspaces"></a>Collaborare nelle aree di lavoro

 Le *aree di lavoro* sono posizioni in cui è possibile collaborare con i colleghi su contenuti specifici. Le aree di lavoro vengono create dai *progettisti* di Power BI e includono raccolte di dashboard e report. Il progettista può quindi riunire una raccolta in un'*app* e distribuirla all'intera organizzazione o a specifici utenti o gruppi. 

 Tutti gli utenti del servizio Power BI hanno a disposizione anche un'**area di lavoro personale**,  ossia una sandbox personale in cui creare contenuti a proprio uso.

 Le aree di lavoro in Power BI sono accessibili dalla pagina **Home** o selezionando **Area di lavoro** o **Area di lavoro personale** nel riquadro di spostamento a sinistra.

 ![Riquadro di spostamento che mostra due tipi di aree di lavoro](media/end-user-workspaces/power-bi-home.png)

## <a name="types-of-workspaces"></a>Tipi di aree di lavoro
In **Area di lavoro personale** viene archiviato tutto il contenuto di cui si è proprietari o autori. È possibile considerarla come un sandbox personale o un'area di lavoro per il proprio contenuto. Per molti *utenti finali* di Power BI, l'**Area di lavoro personale** rimane vuota perché il loro lavoro non implica la creazione di nuovi contenuti. Gli *utenti finali*, per definizione, usufruiscono di dati creati da altri e li usano per prendere decisioni aziendali. Se si è autori di contenuto, è consigliabile leggere invece gli [articoli di Power BI per progettisti](../create-reports/index.yml).

Le **aree di lavoro per le app** includono tutto il contenuto per un'app specifica. Quando un *progettista* crea un'app, aggrega tutto il contenuto necessario per utilizzare tale app. Il contenuto può includere dashboard, report e set di dati. Non tutte le app conterranno questi tre componenti. Un'app può contenere solo un dashboard oppure i tre tipi di contenuto o persino venti report. Tutto dipende da quello che il *progettista* decide di includere nell'app. In genere le aree di lavoro per le app destinate agli *utenti finali* non includono i set di dati.

L'area di lavoro per le app Fig sales nella figura seguente contiene tre report e un dashboard. 

![Riquadro di spostamento che mostra due tipi di aree di lavoro](media/end-user-workspaces/power-bi-app-workspace.png)

## <a name="roles-in-the-workspaces"></a>Ruoli nelle aree di lavoro

I ruoli determinano le operazioni possibili per un utente in un'area di lavoro, favorendo la collaborazione dei team.  Quando concede l'accesso a una nuova area di lavoro, il *progettista* aggiunge singoli utenti o gruppi a uno dei ruoli dell'area di lavoro: **Vsualizzatore**, **Membro**, **Collaboratore** o **Amministratore**. 


L'*utente finale* di Power BI in genere interagisce nelle aree di lavoro con il ruolo **Visualizzatore**. Un *progettista* può però assegnargli anche il ruolo **Membro** o **Collaboratore**. Il ruolo Visualizzatore consente di visualizzare e interagire con il contenuto (dashboard, report, app) creato e condiviso da altri utenti. Inoltre, poiché il ruolo Visualizzatore non può accedere al set di dati sottostante, è un modo sicuro per interagire con il contenuto senza preoccuparsi di alterare i dati sottostanti.


Per un elenco dettagliato delle operazioni che è possibile eseguire come *utente finale* con il ruolo Visualizzatore, vedere [Elenco di funzionalità di Power BI per gli utenti finali e gli altri utenti con licenze gratuite](end-user-features.md).


### <a name="workspace-roles"></a>Ruoli dell'area di lavoro
Ecco le funzionalità dei quattro ruoli: amministratori, membri, collaboratori e visualizzatori. Tutte queste funzionalità, a eccezione della visualizzazione e dell'interazione, richiedono una licenza di Power BI Pro.

|Funzionalità   | Amministratore  | Membro  | Collaboratore  | Visualizzatore |
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
| Copiare un report. | X | X | X |  |
| Visualizzare un elemento e interagire con esso.<sup>2</sup> |  X | X  | X  | X  |
| Leggere i dati archiviati nei flussi di dati dell'area di lavoro | X | X | X | X |

1. I collaboratori e i membri possono condividere elementi in un'area di lavoro se hanno autorizzazioni di ricondivisione.

2. Anche se non si ha una licenza di Power BI Pro, è possibile visualizzare e interagire con gli elementi nel servizio Power BI se gli elementi si trovano in un'area di lavoro nella capacità Premium.

## <a name="licensing-workspaces-and-capacity"></a>Licenze, aree di lavoro e capacità
Anche le licenze contribuiscono a determinare le operazioni consentite e non consentite all'utente in un'area di lavoro. Per poter usare molte funzionalità è necessaria una licenza di Power BI *Pro*. La maggior parte degli *utenti finali* ha una licenza *gratuita*. 

Se si ha una licenza gratuita e l'area di lavoro è archiviata nella *capacità Premium*, è possibile visualizzare e interagire con il contenuto di tale area di lavoro. Le aree di lavoro e le app archiviate nella capacità Premium sono identificate da un'icona a forma di rombo.

![Aree di lavoro selezionate](media/end-user-workspaces/power-bi-diamond.png) Per altre informazioni, vedere [Quali licenze sono disponibili?](end-user-license.md).



## <a name="next-steps"></a>Passaggi successivi
* [App in Power BI](end-user-apps.md)    

* Domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)

