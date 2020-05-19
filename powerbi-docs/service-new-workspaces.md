---
title: Organizzare il lavoro nelle nuove aree di lavoro in Power BI
description: Informazioni sulle nuove aree di lavoro, ovvero raccolte di dashboard e report che hanno lo scopo di fornire all'organizzazione le metriche chiave.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/07/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: c74e9c3119c9c9a8057672d68e6499d93b46e3f8
ms.sourcegitcommit: 9dd6dc8c06091ea02dee5e9ddc45a2922877b1f2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/08/2020
ms.locfileid: "82991386"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>Organizzare il lavoro nelle nuove aree di lavoro in Power BI

Le *aree di lavoro* sono spazi in cui collaborare con i colleghi per creare raccolte di dashboard, report, set di dati e report impaginati. La nuova esperienza delle aree di lavoro consente di gestire meglio l'accesso al contenuto. Questo articolo descrive le nuove aree di lavoro e le differenze rispetto alle aree di lavoro classiche.  Le nuove aree di lavoro, come quelle classiche, possono essere usate per creare e distribuire le app. Se si è pronti a creare una nuova area di lavoro, leggere l'articolo sulla [creazione di una nuova esperienza di area di lavoro](service-create-the-new-workspaces.md).

Le aree di lavoro nuove e aggiornate possono coesistere affiancate alle aree di lavoro classiche già esistenti. La nuova esperienza delle aree di lavoro rappresenta il tipo predefinito di area di lavoro. Se necessario, è comunque possibile creare e usare le [aree di lavoro classiche](service-create-workspaces.md) basate su Gruppi di Office 365. Pronti per la migrazione dell'area di lavoro classica? Per informazioni dettagliate, vedere [Aggiornare le aree di lavoro classiche alle nuove aree di lavoro in Power BI](designer/service-upgrade-workspaces.md).

Con le nuove aree di lavoro è possibile:

- Assegnare ruoli dell'area di lavoro a gruppi di utenti: gruppi di sicurezza, liste di distribuzione, gruppi di Office 365 e singoli utenti.
- Creare un'area di lavoro in Power BI senza creare un gruppo di Office 365 sottostante associato. Tutta l'amministrazione dell'area di lavoro viene gestita da Power BI e non da Office 365.
- Continuare a gestire l'accesso utente al contenuto usando i gruppi di Office 365, se necessario. È sufficiente aggiungere un gruppo di Office 365 nell'elenco di accesso all'area di lavoro.
- Per aumentare la flessibilità di gestione delle autorizzazioni in un'area di lavoro, usare ruoli dell'area di lavoro con maggiore granularità.

Power BI continua a elencare tutti i gruppi di Office 365 di cui si è membri. In questo modo si evita di modificare i flussi di lavoro esistenti.

## <a name="new-and-classic-workspace-differences"></a>Differenze tra aree di lavoro nuove e classiche

Con le nuove aree di lavoro, alcune funzionalità sono state riprogettate. Queste sono le principali differenze.

* La creazione di queste aree di lavoro non comporta la creazione di gruppi di Office 365 come avviene con le aree di lavoro classiche. Tuttavia, ora è possibile usare un gruppo di Office 365 per concedere agli utenti l'accesso all'area di lavoro assegnando al gruppo un ruolo. 
* Nelle aree di lavoro classiche è possibile aggiungere solo singoli utenti agli elenchi di membri e amministratori. Nelle nuove aree di lavoro è possibile aggiungere più gruppi di sicurezza di Active Directory, liste di distribuzione o gruppi di Office 365 a questi elenchi per semplificare la gestione degli utenti. 
- È possibile creare un pacchetto di contenuto aziendale da un'area di lavoro classica. Non è possibile crearne uno dalle nuove aree di lavoro.
- È possibile utilizzare un pacchetto di contenuto aziendale da un'area di lavoro classica. Non è possibile utilizzarne uno dalle nuove aree di lavoro.

### <a name="workspace-features-that-work-differently"></a>Funzionalità delle aree di lavoro che si comportano in modo diverso

Alcune funzionalità delle nuove aree di lavoro si comportano diversamente da quelle delle aree di lavoro correnti. Queste differenze sono intenzionali, basate sul feedback ricevuto dai clienti. Consentono un approccio più flessibile alla collaborazione con le aree di lavoro.

- **Applicazione delle licenze**: Per la pubblicazione di report nella nuova esperienza delle aree di lavoro vengono applicate le regole relative alle licenze esistenti. Gli utenti che collaborano nelle aree di lavoro o condividono contenuti con altri utenti nel servizio Power BI devono avere una licenza Power BI Pro. Per gli utenti senza una licenza Pro, viene visualizzato l'errore "Solo gli utenti con licenze di Power BI Pro possono pubblicare in quest'area di lavoro".
- **Ricondivisione/Non è possibile ricondividere per i membri**: funzionalità sostituita dal ruolo Collaboratore.
- **Aree di lavoro di sola lettura**: anziché concedere agli utenti l'accesso in sola lettura a un'area di lavoro, assegnarli al ruolo Visualizzatore, che consente un accesso di sola lettura simile per il contenuto di un'area di lavoro.
- **Gli utenti senza una licenza Pro** possono accedere all'area di lavoro se questa è in una capacità Power BI Premium, anche se hanno solo il ruolo Visualizzatore.
- **Consenti agli utenti di esportare i dati**: gli utenti con ruolo Visualizzatore possono esportare i dati se hanno l'autorizzazione per la compilazione per i set di dati dell'area di lavoro. Per altre informazioni, vedere [Compilare l'autorizzazione per i set di dati](service-datasets-build-permissions.md).
- Il pulsante **Lascia l'area di lavoro** non è disponibile.

### <a name="workspace-contact-list"></a>Elenco contatti dell'area di lavoro

La nuova funzionalità **Elenco contatti** consente di specificare quali utenti ricevono una notifica relativa ai problemi che si verificano nell'area di lavoro. Per impostazione predefinita, qualsiasi utente o gruppo specificato come amministratore dell'area di lavoro riceve una notifica, ma è possibile personalizzare l'elenco. Gli utenti o i gruppi elencati nell'elenco contatti verranno visualizzati nell'interfaccia utente per consentire agli utenti di ottenere informazioni correlate all'area di lavoro. 

Vedere altre informazioni sull'[impostazione dell'elenco contatti dell'area di lavoro](service-create-the-new-workspaces.md#workspace-contact-list).

### <a name="workspace-onedrive"></a>OneDrive area di lavoro

La funzionalità OneDrive area di lavoro consente di configurare un gruppo di Office 365 la cui archiviazione file nella raccolta documenti di SharePoint è disponibile per gli utenti dell'area di lavoro. Il gruppo viene creato all'esterno di Power BI.

Power BI non sincronizza le autorizzazioni di utenti o gruppi che sono configurati per l'accesso all'area di lavoro con l'appartenenza a un gruppo di Office 365. È consigliabile gestire l'accesso dell'area di lavoro tramite la stesso gruppo di Office 365 la cui archiviazione file si configura in questa impostazione. 

Vedere le informazioni su come [impostare OneDrive area di lavoro e accedervi](service-create-the-new-workspaces.md#workspace-onedrive).  

## <a name="roles-in-the-new-workspaces"></a>Ruoli nelle nuove aree di lavoro

Per concedere l'accesso a una nuova area di lavoro, aggiungere gruppi di utenti o singoli utenti a uno dei ruoli dell'area di lavoro: amministratori, membri, collaboratori o visualizzatori. A tutti i membri in un gruppo di utenti viene assegnato il ruolo definito. Se un utente appartiene a più gruppi di utenti, ottiene il livello di autorizzazione più elevato concesso dai ruoli a lui assegnati.

I ruoli consentono di gestire chi può fare cosa in un'area di lavoro per permettere ai team di collaborare. Le nuove aree di lavoro consentono di assegnare ruoli a singoli utenti e gruppi di utenti: gruppi di sicurezza, gruppi di Office 365 e liste di distribuzione. 

Quando si assegnano i ruoli a un gruppo di utenti, i singoli utenti del gruppo possono accedere al contenuto. Se si annidano gruppi di utenti, tutti gli utenti contenuti sono autorizzati.

[!INCLUDE [power-bi-workspace-roles-table](includes/power-bi-workspace-roles-table.md)]

> [!NOTE]
> Per applicare la sicurezza a livello di riga per gli utenti che esplorano il contenuto in un'area di lavoro, usare il ruolo Visualizzatore. Per applicare la sicurezza a livello di riga senza concedere l'accesso all'area di lavoro, pubblicare un'app Power BI per tali utenti o usare la condivisione per distribuire il contenuto.

## <a name="licensing"></a>Gestione delle licenze
Tutti gli utenti che vengono aggiunti a un'area di lavoro nella capacità condivisa devono avere una licenza di Power BI Pro. Nell'area di lavoro tutti gli utenti possono collaborare sui dashboard e i report che si intende pubblicare e rendere disponibili a un pubblico più ampio o all'intera organizzazione. 

Per distribuire contenuto ad altri utenti all'interno dell'organizzazione, è possibile assegnare loro licenze di Power BI Pro oppure assegnare l'area di lavoro a una capacità Power BI Premium.

Quando l'area di lavoro è in una capacità Power BI Premium, gli utenti con il ruolo Visualizzatore possono accedere all'area di lavoro anche se non hanno una licenza di Power BI Pro. Se tuttavia si assegna a questi utenti un ruolo più elevato, ad esempio di amministratore, membro o collaboratore, viene loro richiesto di avviare una versione di valutazione Pro quando provano ad accedere all'area di lavoro. Per usare il ruolo Visualizzatore per gli utenti senza licenze Pro, assicurarsi che non abbiano anche altri ruoli nell'area di lavoro, singolarmente o come gruppo di utenti.

> [!NOTE]
> Per la pubblicazione di report nella nuova esperienza delle aree di lavoro, le regole relative alle licenze vengono applicate in modo più rigoroso. Se si tenta di pubblicare da Power BI Desktop o altri strumenti client senza una licenza Pro, viene visualizzato l'errore "Solo gli utenti con licenze di Power BI Pro possono pubblicare in quest'area di lavoro".

## <a name="administering-new-workspace-experience-workspaces"></a>Amministrazione delle aree di lavoro della nuova esperienza

L'amministrazione per le aree di lavoro della nuova esperienza è ora disponibile nel portale di amministrazione di Power BI. Gli amministratori di Power BI decidono chi in un'organizzazione può creare le aree di lavoro e distribuire le app. Possono visualizzare lo stato di tutte le aree di lavoro dell'organizzazione. Gli amministratori possono anche gestire e ripristinare le aree di lavoro. Per altre informazioni sulla [creazione di nuove aree di lavoro](service-admin-portal.md#create-the-new-workspaces), vedere l'articolo nel portale di amministrazione.

## <a name="guest-users"></a>Utenti guest

Per impostazione predefinita, gli [utenti guest B2B di Azure AD](service-admin-azure-ad-b2b.md) non possono accedere alle aree di lavoro. Gli amministratori di Power BI possono [consentire agli utenti guest esterni di modificare e gestire il contenuto dell'organizzazione](service-admin-azure-ad-b2b.md#guest-users-who-can-edit-and-manage-content). Gli utenti guest abilitati possono accedere alle aree di lavoro per cui hanno l'autorizzazione.

## <a name="auditing"></a>Controllo

Le attività seguenti vengono controllate da Power BI per la nuova esperienza delle aree di lavoro.

| Nome descrittivo | Nome operazione |
|---|---|
| Cartella di Power BI creata | CreateFolder |
| Cartella di Power BI eliminata | DeleteFolder |
| Cartella di Power BI aggiornata | UpdateFolder |
| Accesso alla cartella di Power BI aggiornato| UpdateFolderAccess |

Vedere altre informazioni sul [controllo in Power BI](service-admin-auditing.md).

## <a name="limitations-and-considerations"></a>Limitazioni e considerazioni

Limitazioni da tenere presenti:

- le aree di lavoro possono contenere un massimo di 1.000 set di dati o 1.000 report per ogni set di dati. 
- Una persona con una licenza di Power BI Pro può essere membro di un massimo di 1.000 aree di lavoro.
- Power BI Publisher per Excel non è supportato.

## <a name="frequently-asked-questions"></a>Domande frequenti

**La nuova esperienza delle aree di lavoro influisce sui collegamenti al contenuto esistente?**

No. La nuova esperienza delle aree di lavoro non influisce sui collegamenti agli elementi esistenti nelle aree di lavoro classiche. La disponibilità generale della nuova esperienza delle aree di lavoro comporta un cambiamento dell'area di lavoro predefinita creata, ma non delle aree di lavoro esistenti. 

**Le aree di lavoro esistenti vengono aggiornate alla nuova esperienza delle aree di lavoro disponibile a livello generale?**

No. La nuova esperienza delle aree di lavoro disponibile a livello generale comporta un cambiamento solo del tipo predefinito di area di lavoro. Le aree di lavoro classiche esistenti basate su Gruppi di Office 365 rimangono invariate.

**Le aree di lavoro vengono comunque create automaticamente per i gruppi di Office 365?**

Sì. Poiché sono supportati entrambi i tipi di aree di lavoro affiancati, continuano a venire elencati tutti i gruppi di Office 365 a cui si può accedere nell'elenco di aree di lavoro.

## <a name="next-steps"></a>Passaggi successivi

* [Creare le nuove aree di lavoro in Power BI](service-create-the-new-workspaces.md)
* [Creare le aree di lavoro classiche](service-create-workspaces.md)
* [Installare e usare app in Power BI](service-create-distribute-apps.md)
* Domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
