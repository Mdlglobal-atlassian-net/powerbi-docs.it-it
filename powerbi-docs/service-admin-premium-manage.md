---
title: Gestire capacità all'interno di Power BI Premium e Power BI Embedded
description: Informazioni su come gestire Power BI Premium e abilitare l'accesso al contenuto per tutta l'organizzazione.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 10/10/2017
ms.author: mblythe
LocalizationGroup: Premium
ms.openlocfilehash: b38c69d74141b28215e0a14a32fc7b03fab4fdbf
ms.sourcegitcommit: 9c3a9ec14c111d766ef5703366c316e72f6e588f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45558471"
---
# <a name="manage-capacities-within-power-bi-premium-and-power-bi-embedded"></a>Gestire capacità all'interno di Power BI Premium e Power BI Embedded
Informazioni su come gestire le capacità di Power BI Premium e Power BI Embedded che forniscono risorse dedicate per il contenuto usato.

![Schermata di impostazioni della capacità di Power BI](media/service-admin-premium-manage/premium-capacity-management.png)

Il concetto di capacità è al cuore delle offerte di Power BI Premium e Power BI Embedded.

## <a name="what-is-capacity"></a>Che cos'è la capacità?
Per capacità si intende un set di risorse riservate per l'uso esclusivo da parte dell'utente. Con la capacità è possibile pubblicare dashboard, report e set di dati per gli utenti dell'organizzazione senza dover acquistare licenze individuali e garantire prestazioni affidabili e coerenti per il contenuto ospitato nella capacità.

La capacità è totalmente trasparente per gli utenti finali, che continueranno a usare Power BI o l'applicazione scelta come di consueto. Non dovranno nemmeno sapere che parte del contenuto (o la sua interezza) è ospitata nella capacità dedicata. Per gli utenti, tutto funziona esattamente come in precedenza.

[!INCLUDE [powerbi-premium-illustration](./includes/powerbi-premium-illustration.md)]

Per altre informazioni, vedere [What is Power BI Pro?](service-premium.md) (Che cos'è Power BI Pro?).

### <a name="capacity-admins"></a>Amministratori della capacità
> [!NOTE]
> Gli amministratori della capacità, per la capacità di Power BI Embedded, vengono definiti all'interno del portale di Microsoft Azure.

Quando l'utente viene assegnato come amministratore della capacità a una capacità, avrà il controllo completo sulla capacità e sulle relative funzionalità amministrative. Dal portale di amministrazione di Power BI è possibile aggiungere altri amministratori della capacità (solo per Power BI Premium) o concedere agli utenti le autorizzazioni di assegnazione della capacità. È possibile assegnare in blocco le aree di lavoro a una capacità e visualizzare le metriche di utilizzo di una capacità.

Ogni capacità ha i propri amministratori. La definizione di un amministratore della capacità a una capacità non garantisce l'accesso a tutte le capacità all'interno dell'organizzazione. Per impostazione predefinita gli amministratori della capacità non hanno accesso a tutte le aree degli amministratori di Power BI come ad esempio le metriche di utilizzo, i log di controllo o le impostazioni del tenant. Gli amministratori delle capacità non avranno neanche le autorizzazioni per configurare nuove capacità o modificare lo SKU delle capacità esistenti. Solo gli amministratori globali o gli amministratori del servizio Power BI hanno accesso a tali elementi.

Tutti gli amministratori globali di Office 365 e gli amministratori di Power BI sono automaticamente amministratori sia della capacità di Power BI Premium che della capacità di Power BI Embedded.

## <a name="purchase-capacity"></a>Acquistare capacità
Per sfruttare i vantaggi della capacità dedicata, è necessario acquistare una sottoscrizione per Power BI Premium all'interno dell'interfaccia di amministrazione di Office 365 o creare una risorsa di Power BI Embedded all'interno del portale di Microsoft Azure. Per altre informazioni, vedere gli argomenti seguenti:

* **Power BI Premium:** [Come acquistare Power BI Premium](service-admin-premium-purchase.md)
* **Power BI Embedded:** [Creare la capacità di Power BI Embedded nel portale di Azure](https://docs.microsoft.com/azure/power-bi-embedded/create-capacity)

Quando si acquistano gli SKU di Power BI Premium, il tenant riceverà il numero corrispondente di memorie centrali virtuali da usare nelle capacità in esecuzione. Ad esempio, l'acquisto di uno SKU P3 di Power BI Premium fornisce al tenant 32 memorie centrali virtuali.

> [!NOTE]
> Saranno disponibili 30 giorni di accesso completo dopo il termine della sottoscrizione, ma dopo tale periodo verrà ripristinata la capacità condivisa per il contenuto. I modelli > 1 GB non saranno supportati con una licenza condivisa normale.


## <a name="manage-capacity"></a>Gestire la capacità
Dopo aver acquistato i nodi della capacità all'interno di Office 365, sarà necessario configurare una nuova capacità. Questa operazione viene eseguita tramite il [portale di amministrazione di Power BI](service-admin-portal.md). All'interno del portale di amministrazione è presente una sezione denominata **Impostazioni di capacità** in cui gestire le capacità di Power BI Premium per l'organizzazione.

![Impostazioni di capacità all'interno del portale di amministrazione](media/service-admin-premium-manage/admin-portal-premium.png)

Selezionando **Impostazioni di capacità** verrà visualizzata la schermata di gestione della capacità, che per impostazione predefinita è la capacità di Power BI Premium.

### <a name="setting-up-a-new-capacity-power-bi-premium"></a>Configurazione di una nuova capacità (Power BI Premium)
Il numero di memorie centrali virtuali rifletterà la quantità usata e la quantità disponibile con cui creare le capacità. La quantità di memorie centrali virtuali disponibili per l'organizzazione è basata sugli SKU Premium che sono stati acquistati. Ad esempio, l'acquisto di uno SKU P3 e di uno P2 comporta 48 memorie centrali disponibili: 32 dallo SKU P3 e 16 da P2.

![Memorie centrali virtuali usate e disponibili per Power BI Premium](media/service-admin-premium-manage/admin-portal-v-cores.png)

Se si hanno memorie centrali virtuali disponibili, configurare la nuova capacità eseguendo le operazioni seguenti.

1. Selezionare **Configura nuova capacità**.
2. Assegnare un **nome** alla capacità.
3. Definire chi è l'amministratore per questa capacità.

    Gli amministratori della capacità non devono essere obbligatoriamente un amministratore di Power BI o un amministratore globale di Office 365. Per altre informazioni, vedere [Power BI Premium capacity admins](#capacity-admins) (Amministratori della capacità di Power BI Premium)
4. Selezionare le dimensioni della capacità. Le opzioni disponibili dipendono dal numero di memorie centrali virtuali disponibili. Non è possibile selezionare un'opzione che è maggiore del numero disponibile.

    ![Dimensioni della capacità Premium disponibili](media/service-admin-premium-manage/premium-capacity-size.png)
5. Selezionare **Configura**.

    ![Configurare una nuova capacità](media/service-admin-premium-manage/set-up-capacity.png)

Gli amministratori della capacità, nonché gli amministratori di Power BI e gli amministratori globali di Office 365, vedranno quindi la capacità elencata nel portale di amministrazione.

### <a name="capacity-settings"></a>Impostazioni di capacità
All'interno della schermata di gestione della capacità Premium, è possibile selezionare l'**icona dell'ingranaggio (impostazioni)** sotto le azioni. In questo modo sarà possibile rinominare o eliminare una capacità. Indicherà anche chi sono gli amministratori del servizio, la SKU/dimensione della capacità e in quale regione si trova la capacità.

![Azioni della capacità all'interno dell'area di gestione della capacità](media/service-admin-premium-manage/capacity-actions.png)

![Impostazioni di capacità](media/service-admin-premium-manage/capacity-settings.png)

![Pulsanti di eliminazione e applicazione per le impostazioni di capacità in Power BI Premium](media/service-admin-premium-manage/capacity-settings-delete.png)

> [!NOTE]
> Le impostazioni di capacità di Power BI Embedded vengono gestite all'interno del portale di Microsoft Azure.

### <a name="change-capacity-size-power-bi-premium"></a>Modificare le dimensioni della capacità (Power BI Premium)
Gli amministratori di Power BI e gli amministratori globali di Office 365 modificano le dimensioni della capacità di Power BI Premium selezionando **Modifica le dimensioni della capacità**. Gli amministratori della capacità che non sono amministratori di Power BI o amministratori globali di Office 365 non avranno questa opzione.

![Modificare le dimensioni della capacità di Power BI Premium](media/service-admin-premium-manage/change-capacity-size.png)

La schermata **Modifica le dimensioni della capacità** consente di aggiornare le dimensioni della capacità o di effettuarne il downgrade, se si hanno le risorse disponibili. Gli amministratori possono creare, ridimensionare ed eliminare i nodi purché abbiano il numero necessario di memorie centrali virtuali.

Non è possibile effettuare il downgrade degli SKU P agli SKU EM. È possibile passare il mouse sulle opzioni disabilitate per visualizzare una spiegazione.

![Elenco a discesa per modificare le dimensioni della capacità di Power BI Premium](media/service-admin-premium-manage/change-capacity-size2.png)

### <a name="capacity-assignment"></a>Assegnazione della capacità
È possibile gestire una capacità selezionandone il nome per passare alla schermata di gestione della capacità.

![Selezionare il nome della capacità per visualizzare la schermata di assegnazione della capacità](media/service-admin-premium-manage/capacity-assignment.png)

Se nessuna area di lavoro è stata assegnata alla capacità, verrà visualizzato un messaggio che consente di **assegnare le aree di lavoro**.

#### <a name="user-permissions"></a>Autorizzazioni utente
È possibile assegnare altri **amministratori della capacità** per le capacità di Power BI Premium nonché assegnare gli utenti che avranno le **autorizzazioni di assegnazione della capacità**, che potranno assegnare un'area di lavoro per le app alla capacità se sono anche amministratori di tale area di lavoro, oltre ad assegnare l'*Area di lavoro personale* alla capacità. Gli utenti con autorizzazioni di assegnazione non avranno accesso al portale di amministrazione.

> [!NOTE]
> Per la capacità di Power BI Embedded gli amministratori della capacità vengono assegnati all'interno del portale di Microsoft Azure.
>
>

![](media/service-admin-premium-manage/capacity-user-permissions.png)

![](media/service-admin-premium-manage/capacity-user-permissions2.png)

## <a name="assign-a-workspace-to-a-capacity"></a>Assegnare un'area di lavoro a una capacità
Esistono alcuni modi in cui un'area di lavoro può essere assegnata a una capacità.

### <a name="capacity-management-in-admin-portal"></a>Gestione della capacità nel portale di amministrazione
Gli amministratori della capacità, insieme agli amministratori di Power BI e agli amministratori globali di Office 365, possono assegnare in blocco le aree di lavoro all'interno della sezione di gestione capacità premium del portale di amministrazione. Quando si gestisce una capacità, si noterà una sezione **Aree di lavoro** che consente di assegnare le aree di lavoro.

![Area di assegnazione delle aree di lavoro della gestione della capacità](media/service-admin-premium-manage/capacity-manage-workspaces.png)

1. Selezionare **Assegna aree di lavoro**. Questa opzione è presente in più posizioni ed eseguirà sempre la stessa attività.
2. Selezionare **Aree di lavoro dell'intera organizzazione** oppure **Aree di lavoro specifiche in base agli utenti**.

   | Selezione | Descrizione |
   | --- | --- |
   | **Aree di lavoro dell'intera organizzazione** |L'assegnazione di aree di lavoro dell'intera organizzazione alla capacità Premium comporta l'assegnazione di tutte le aree di lavoro per le app e delle aree di lavoro personali, all'interno dell'organizzazione, a questa capacità Premium. In più, tutti gli utenti attuali e futuri saranno autorizzati a riassegnare singole aree di lavoro a questa capacità. |
   | **Aree di lavoro specifiche in base agli utenti** |Quando si assegnano le aree di lavoro per utente o gruppo, tutte le aree di lavoro appartenenti a tali utenti vengono assegnate alla capacità Premium, tra cui l'area di lavoro personale dell'utente. Tali utenti ottengono automaticamente le autorizzazioni di assegnazione dell'area di lavoro.<br>Ciò include le aree di lavoro già assegnata a una capacità diversa. |
3. Selezionare **Applica**.

Questa opzione non consente di assegnare specifiche aree di lavoro a una capacità.

### <a name="app-workspace-settings"></a>Impostazioni dell'area di lavoro per le app
È anche possibile assegnare capacità Premium a un'area di lavoro per le app dalle relative impostazioni. Per assegnare un'area di lavoro a una capacità premium, procedere come segue.

Per spostare un'area di lavoro nella capacità, è necessario avere le autorizzazioni di amministratore per tale area di lavoro, nonché delle autorizzazioni di assegnazione di capacità per tale capacità. Gli amministratori dell'area di lavoro possono sempre rimuovere un'area di lavoro dalla capacità Premium.

1. Modificare un'area di lavoro per le app selezionando il **puntini di sospensione (...)**  e selezionando **Modifica area di lavoro**.

    ![Menu di scelta rapida Modifica area di lavoro visualizzato selezionando i puntini di sospensione](media/service-admin-premium-manage/edit-app-workspace.png)
2. In **Modifica area di lavoro**, espandere **Avanzate**.
3. Se l'utente ha ricevuto le autorizzazioni di assegnazione della capacità per qualsiasi capacità, potrà scegliere di attivare **Premium** per quest'area di lavoro.
4. Selezionare la capacità che si vuole assegnare a questa area di lavoro per le app.

    ![Elenco a discesa di selezione della capacità](media/service-admin-premium-manage/app-workspace-advanced.png)
5. Selezionare **Salva**.

Dopo il salvataggio, l'area di lavoro e il relativo contenuto verranno spostati nella capacità Premium senza interruzione dell'esperienza per gli utenti finali.


## <a name="monitor-capacity-usage"></a>Monitorare l'utilizzo della capacità

Power BI offre un'app per il monitoraggio dell'utilizzo della capacità. Per altre informazioni, vedere [Monitorare le capacità di Power BI Premium nell'organizzazione](service-admin-premium-monitor-capacity.md).

## <a name="what-premium-looks-like-for-users"></a>Aspetto di Premium per gli utenti
Per la maggior parte, gli utenti non dovranno neanche sapere di essere in una capacità Premium, perché i dashboard e i report continueranno a funzionare normalmente. Come suggerimento visivo, verrà visualizzata un'icona di diamante accanto alle aree di lavoro che sono in una capacità Premium.

![L'area di lavoro con un'icona di diamante dispone della capacità Premium](media/service-admin-premium-manage/premium-workspace.png)

## <a name="power-bi-report-server-product-key"></a>Codice Product Key del Server di report Power BI
Nella scheda **Impostazioni di capacità** del portale di amministratore di Power BI si avrà accesso al codice Product Key del Server di Report di Power BI. Questo sarà disponibile solo per gli amministratori globali o per gli utenti a cui è stato assegnato il ruolo di amministratore del servizio Power BI e se è stato acquistato uno SKU di Power BI Premium.

![Codice Product Key del Server di report di Power BI all'interno di Impostazioni di capacità](media/service-admin-premium-manage/pbirs-product-key.png)

Se si seleziona **Chiave del server di report di Power BI** viene visualizzata una finestra di dialogo contenente il codice Product Key. È possibile copiarlo e usarlo durante l'installazione.

![Codice Product Key del Server di report Power BI](media/service-admin-premium-manage/pbirs-product-key-dialog.png)

Per altre informazioni, vedere [Install Power BI Report Server](report-server/install-report-server.md) (Installare il Server di report di Power BI).

## <a name="next-steps"></a>Passaggi successivi
Condividere app pubblicate con altri utenti. Per altre informazioni, vedere [Creare e distribuire un'app in Power BI](service-create-distribute-apps.md).

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)
