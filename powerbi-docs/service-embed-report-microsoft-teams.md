---
title: Incorporare report con la scheda Power BI per Microsoft Teams
description: Con la scheda Power BI per Microsoft Teams, è possibile incorporare facilmente report interattivi in canali e chat.
author: LukaszPawlowski-MS
ms.author: lukaszp
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 03/12/2020
ms.openlocfilehash: fe8b5ed0e3cdf0003986ffe6eab18e97e83f3dec
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79381215"
---
# <a name="embed-report-with-the-power-bi-tab-for-microsoft-teams"></a>Incorporare il report con la scheda Power BI per Microsoft Teams

Con la scheda Power BI per Microsoft Teams aggiornata, è possibile incorporare facilmente report interattivi in canali e chat di Microsoft Teams.

Usare la scheda Power BI per Microsoft Teams per aiutare i colleghi a trovare i dati usati dal team e discutere sui dati nei canali del team.

## <a name="requirements"></a>Requisiti

Per il funzionamento della **scheda Power BI per Microsoft Teams**, è necessario quanto segue:

- Una licenza di Power BI Pro o la presenza del report in una risorsa con [capacità Power BI Premium (SKU EM o P)](service-premium-what-is.md) con una licenza di Power BI.
- La scheda Power BI per Microsoft Teams.
- L'utente deve accedere al servizio Power BI per attivare la licenza di Power BI e poter utilizzare il report.
- L'utente deve disporre dell'autorizzazione per visualizzare i dati.

## <a name="embed-your-report"></a>Incorporare il report
Per incorporare il report in un canale o una chat di Microsoft Teams, aggiungerlo come descritto di seguito.

1. Aprire il canale o la chat desiderata in Microsoft Teams e selezionare l'icona **+** .

    ![Aggiungere una scheda a un canale o a una chat](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-add.png)

2. Selezionare la scheda Power BI.

    ![Elenco delle schede Microsoft Teams con la scheda Power BI in evidenza](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-tab.png)

3. Usare le opzioni disponibili per selezionare un report da un'area di lavoro, da Condivisi con l'utente corrente o da un'app Power BI

    ![Impostazioni della scheda Power BI per Microsoft Teams](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-tab-settings.png)

4. Il nome della scheda viene aggiornato automaticamente in base al nome del report, ma è possibile modificarlo. 

5. Premere **Salva**.

## <a name="supported-reports"></a>Report supportati

La scheda consente di incorporare i report seguenti:

- Report interattivi e impaginati
- Report in Area di lavoro personale, nella nuova esperienza delle aree di lavoro e in aree di lavoro classiche
- Report nelle app Power BI


## <a name="grant-access-to-reports"></a>Concedere l'accesso ai report

L'incorporamento di un report in Microsoft Teams non autorizza automaticamente gli utenti a visualizzare il report: è necessario [consentire agli utenti di visualizzare il report in Power BI](service-share-dashboards.md). Per semplificare, è possibile usare un gruppo di Office 365 per il proprio team. 

> [!IMPORTANT]
> Assicurarsi di controllare chi può visualizzare il report all'interno del servizio Power BI e concedere l'accesso a chi non è elencato.

Un modo per assicurarsi che tutti gli utenti del team possano accedere ai report incorporati è quello di inserirli in un'unica area di lavoro in Power BI e concedere al gruppo di Office 365 del team l'accesso all'area di lavoro.

## <a name="start-a-conversation"></a>Avvia una conversazione

Quando si aggiunge una scheda per un report di Power BI a Teams, Teams crea automaticamente una conversazione nella scheda di accompagnamento al report. 

- Selezionare **Mostra scheda conversazione** nell'angolo in alto a destra.

    ![Icona Mostra scheda conversazione](media/service-embed-report-microsoft-teams/power-bi-teams-conversation-icon.png)

    Il primo commento è un collegamento al report. Tutti gli utenti in tale canale di Teams possono visualizzare il report e discuterne nella conversazione.

    ![Conversazione nella scheda](media/service-embed-report-microsoft-teams/power-bi-teams-conversation-tab.png)

## <a name="known-issues-and-limitations"></a>Limitazioni e problemi noti

- Power BI non supporta le stesse lingue localizzate supportate da Microsoft Teams. Di conseguenza, la localizzazione all'interno del report incorporato potrebbe non essere corretta.
- Non è possibile incorporare i dashboard di Power BI nella scheda Power BI per Microsoft Teams.
- Un utente che non dispone di una licenza di Power BI o di un'autorizzazione di accesso al report visualizzerà un messaggio in cui è indicato che il contenuto non è disponibile.
- Se si usa Internet Explorer 10, potrebbero verificarsi problemi. <!--You can look at the [browsers support for Power BI](consumer/end-user-browsers.md) and for [Office 365](https://products.office.com/office-system-requirements#Browsers-section). -->
- I [filtri di URL](service-url-filters.md) non sono supportati con la scheda Power BI per Microsoft Teams.
- Nei cloud nazionali la nuova scheda Power BI non è disponibile. È tuttavia possibile che sia disponibile una versione precedente che non supporta i report o le aree di lavoro della nuova esperienza nelle app Power BI. 
- Dopo il salvataggio, il nome della scheda non può essere modificato tramite le impostazioni della scheda. Usare l'opzione Rinomina per modificarlo.

## <a name="next-steps"></a>Passaggi successivi
- [Condividere un dashboard con i colleghi e altri utenti](service-share-dashboards.md)  
- [Creare e distribuire un'app in Power BI](service-create-distribute-apps.md)  
- [Che cos'è Power BI Premium?](service-premium-what-is.md)

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
