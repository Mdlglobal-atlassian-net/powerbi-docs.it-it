---
title: Creare le aree di lavoro classici in Power BI
description: Informazioni su come creare aree di lavoro, raccolte di dashboard, report e i report impaginati compilati per offrire metriche chiave per l'organizzazione.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/18/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: dcf9b8befabfec98fcae154e6276f8e698b3ddc2
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61150955"
---
# <a name="create-classic-workspaces-in-power-bi"></a>Creare le aree di lavoro classici in Power BI

In Power BI, è possibile creare *aree di lavoro*, posiziona per collaborare con i colleghi per creare e ridefinire le raccolte di dashboard, report e report impaginati. Quindi è possibile aggregare la raccolta tra loro in *app* che è possibile distribuire nell'intera organizzazione o a specifici utenti o gruppi. 

**Non tutti lo sanno, ma** Power BI offre una nuova esperienza dell'area di lavoro, che ora è il valore predefinito. Lettura [organizzare il lavoro in nuove aree di lavoro](service-new-workspaces.md) per informazioni dettagliate sulle nuove aree di lavoro. 

Quando si crea un'area di lavoro classico, si crea un gruppo di Office 365 sottostante, associato. Tutta l'amministrazione dell'area di lavoro viene gestita in Office 365. È possibile aggiungere altri colleghi a queste aree di lavoro come membri o amministratori. Nell'area di lavoro tutti gli utenti possono collaborare su dashboard, report e altri articoli che si intende pubblicare e rendere disponibili a un pubblico più ampio. Tutti gli utenti che vengono aggiunti a un'area di lavoro per le app devono possedere una licenza di Power BI Pro. 

## <a name="video-apps-and-app-workspaces"></a>Video: Video: app e aree di lavoro per le app
<iframe width="640" height="360" src="https://www.youtube.com/embed/Ey5pyrr7Lk8?showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="create-a-classic-app-workspace-based-on-an-office-365-group"></a>Creare un'area di lavoro di app classico basato su un gruppo di Office 365

L'area di lavoro per le app viene creata in base a un gruppo di Office 365.

[!INCLUDE [powerbi-service-create-app-workspace](./includes/powerbi-service-create-app-workspace.md)]

Quando la si crea per la prima volta potrebbe essere necessario attendere circa un'ora per la propagazione dell'area di lavoro in Office 365. 

### <a name="add-an-image-to-your-office-365-app-workspace-optional"></a>Aggiungere un'immagine all'area di lavoro per le app di Office 365 (facoltativo)
Per impostazione predefinita, Power BI crea un cerchietto colorato per l'app, con le iniziali dell'app, ma potrebbe essere opportuno personalizzarlo con un'immagine. Per aggiungere un'immagine occorre una licenza per Exchange Online.

1. Selezionare **Aree di lavoro**, selezionare i puntini di sospensione (...) accanto al nome dell'area di lavoro, quindi **Membri**. 
   
     ![Selezionare i membri dell'area di lavoro](media/service-create-distribute-apps/power-bi-apps-workspace-members.png)
   
    L'account Outlook di Office 365 per l'area di lavoro verrà aperto in una nuova finestra del browser.
2. Quando si passa con il mouse sul cerchio colorato in alto a sinistra, il puntatore si trasforma in un'icona a forma di matita. Selezionarla.
   
     ![Icona della matita di Office 365](media/service-create-distribute-apps/power-bi-apps-workspace-edit-image.png)
3. Selezionare nuovamente l'icona a forma di matita e trovare l'immagine che si vuole usare.
   
     ![Selezionare nuovamente la matita](media/service-create-distribute-apps/power-bi-apps-workspace-edit-group.png)

     Le immagini possono essere file con estensione png, jpg o BMP. Le dimensioni del file possono essere elevata, backup su 3 MB. 

4. Selezionare **Salva**.
   
     ![Selezionare Salva](media/service-create-distribute-apps/power-bi-apps-workspace-save-image.png)
   
    L'immagine sostituisce il cerchio colorato nella finestra di Outlook di Office 365. 
   
     ![Immagine personalizzata](media/service-create-distribute-apps/power-bi-apps-workspace-image-in-office-365.png)
   
    In pochi minuti, verrà visualizzata anche nell'app Power BI.
   
     ![Immagine personalizzata](media/service-create-distribute-apps/power-bi-apps-image.png)

## <a name="add-content-to-your-app-workspace"></a>Aggiungere contenuto all'area di lavoro per le app

Dopo aver creato un'area di lavoro per le app, è possibile aggiungere il contenuto. Questa operazione è analoga all'aggiunta di contenuto all'Area di lavoro personale, tranne per il fatto che anche gli altri utenti dell'area di lavoro potranno vederlo ed elaborarlo. Un'enorme differenza consiste nel fatto che, al termine dell'elaborazione, sarà possibile pubblicare il contenuto come app. Quando si visualizza il contenuto in un'area di lavoro per le app, il nome dell'area di lavoro per le app è indicato come il proprietario.

### <a name="connect-to-third-party-services-in-app-workspaces"></a>Connettersi ai servizi di terze parti nelle aree di lavoro per le app

Le app vengono fornite per tutti i servizi di terze parti supportati da Power BI, rendendo più semplice il recupero dei dati dai servizi usati come ad esempio Microsoft Dynamics CRM, Salesforce o Google Analytics. È possibile pubblicare app aziendali per fornire agli utenti i dati di cui hanno bisogno.

Nelle aree di lavoro correnti è possibile connettersi anche con i pacchetti di contenuto aziendali e i pacchetti di contenuto di terze parti, ad esempio Microsoft Dynamics CRM, Salesforce o Google Analytics. Prendere in considerazione la migrazione dei pacchetti di contenuto aziendali nelle app.

## <a name="distribute-an-app"></a>Distribuire un'app

Se si desidera distribuire il contenuto ufficiale a un ampio all'interno dell'organizzazione, è possibile pubblicare un'app dall'area di lavoro.  Quando il contenuto è pronto, si scegliere quali dashboard e report da pubblicare e quindi pubblicarlo come un *app*. È possibile creare un'app da ogni area di lavoro.

L'elenco di App nel riquadro di spostamento a sinistra mostra tutte le app installate. I colleghi possono ottenere l'app in diversi modi. 
- È possibile trovare e installare l'app da Microsoft AppSource
- È possibile inviare loro un collegamento diretto. 
- Se l'amministratore di Power BI concede l'autorizzazione, è possibile installarla automaticamente nell'account Power BI dei colleghi. 

Gli utenti visualizzano contenuto di app aggiornate automaticamente dopo aver pubblicato un aggiornamento dall'area di lavoro. È possibile controllare con quale frequenza vengono aggiornati i dati impostando la pianificazione dell'aggiornamento nel set di dati usati per il contenuto dell'app nell'area di lavoro. Visualizzare [pubblicare un'app da nuove aree di lavoro in Power BI](service-create-distribute-apps.md) per informazioni dettagliate.

## <a name="power-bi-classic-apps-faq"></a>Classiche domande frequenti sull'App Power BI

### <a name="how-are-apps-different-from-organizational-content-packs"></a>Quali sono le differenze tra le app e i pacchetti di contenuto aziendali?
Le app rappresentano l'evoluzione dei pacchetti di contenuto aziendali. Se si hanno già pacchetti di contenuto aziendali, questi continueranno a funzionare contemporaneamente alle app. Le app e i pacchetti di contenuto hanno alcune differenze importanti. 

* Dopo che gli utenti aziendali avranno installato un pacchetto di contenuto, questo perde la propria identità raggruppata: è solo un elenco di dashboard e report intervallati da altri dashboard e report. Le app, d'altra parte, mantengono l'identità e il raggruppamento anche dopo l'installazione. Questo raggruppamento rende semplice per gli utenti aziendali continuare a passare alle app nel tempo.
* È possibile creare più pacchetti di contenuto da qualsiasi area di lavoro, ma un'app ha una relazione 1:1 con la relativa area di lavoro. 
* Nel corso del tempo i pacchetti di contenuto aziendali verranno deprecati, quindi si consiglia di creare app da oggi in poi.  
* Con l'anteprima della nuova esperienza dell'area di lavoro, stiamo compiendo i primi passi verso la deprecazione dei pacchetti di contenuto dell'organizzazione. Non sarà possibile utilizzarli o crearli nelle aree di lavoro dell'anteprima.

Per fare un confronto, vedere [Quali sono le differenze tra le nuove aree di lavoro per le app e quelle correnti?](service-new-workspaces.md#how-are-the-new-workspaces-different-from-current-workspaces). 

## <a name="next-steps"></a>Passaggi successivi
* [Installare e usare app in Power BI](service-create-distribute-apps.md)
- [Creare le nuove aree di lavoro (anteprima)](service-create-the-new-workspaces.md)
* Domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)
