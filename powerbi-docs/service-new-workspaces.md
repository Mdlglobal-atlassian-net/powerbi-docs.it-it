---
title: Organizzare il lavoro nelle nuove aree di lavoro in Power BI
description: Informazioni sulle nuove aree di lavoro, ovvero raccolte di dashboard e report che hanno lo scopo di fornire all'organizzazione le metriche chiave.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/05/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 32d43ca4b9681495e22db023604afeac31d15e7e
ms.sourcegitcommit: d04b9e1426b8544ce16ef25864269cc43c2d9f7b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2019
ms.locfileid: "71715202"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>Organizzare il lavoro nelle nuove aree di lavoro in Power BI

 Le *aree di lavoro* sono spazi per collaborare con i colleghi per creare raccolte di dashboard, report e report impaginati. La nuova esperienza delle aree di lavoro consente di gestire meglio l'accesso al contenuto. Questo articolo descrive le nuove aree di lavoro e le differenze rispetto alle aree di lavoro classiche.  Le nuove aree di lavoro, come quelle classiche, possono essere usate per creare e distribuire le app. Vedere le informazioni su come [creare un'area di lavoro della nuova esperienza](service-create-the-new-workspaces.md).

La nuova esperienza delle aree di lavoro è disponibile a livello generale ed è ora l'area di lavoro predefinita. È comunque possibile continuare a creare e usare [aree di lavoro classiche](service-create-workspaces.md) basate su Gruppi di Office 365. 

> [!NOTE]
> Per applicare la sicurezza a livello di riga per gli utenti che esplorano il contenuto in un'area di lavoro, usare il ruolo Visualizzatore. Per applicare la sicurezza a livello di riga senza concedere l'accesso all'area di lavoro, pubblicare un'app Power BI per tali utenti o usare la condivisione per distribuire il contenuto.

Con le nuove aree di lavoro è possibile:

- Assegnare ruoli dell'area di lavoro a gruppi di utenti: gruppi di sicurezza, liste di distribuzione, gruppi di Office 365 e singoli utenti.
- Creare un'area di lavoro in Power BI senza creare un gruppo di Office 365.
- Usare ruoli dell'area di lavoro con maggiore granularità per aumentare la flessibilità di gestione delle autorizzazioni in un'area di lavoro.
- L'amministratore di Power BI può controllare quali utenti possono creare aree di lavoro in Power BI.

Quando si crea una delle nuove aree di lavoro, non si crea un gruppo di Office 365 sottostante associato. Tutta l'amministrazione dell'area di lavoro viene gestita da Power BI e non da Office 365. Con la nuova esperienza delle aree di lavoro, è ora possibile aggiungere un gruppo di Office 365 all'elenco di accesso dell'area di lavoro per continuare a gestire l'accesso degli utenti al contenuto tramite i gruppi di Office 365.

## <a name="administering-new-workspace-experience-workspaces"></a>Amministrazione delle aree di lavoro della nuova esperienza
L'amministrazione delle aree di lavoro della nuova esperienza avviene ora in Power BI e gli amministratori di Power BI decidono chi può creare aree di lavoro in un'organizzazione. Possono anche gestire e recuperare le aree di lavoro, usando il portale di amministrazione di Power BI o i cmdlet di PowerShell. Per le aree di lavoro classiche basate su Gruppi di Office 365, l'amministrazione continua ad avvenire nel portale di amministrazione di Office 365 e in Azure Active Directory.

In **Impostazioni area di lavoro** nel portale di amministrazione gli amministratori possono usare l'impostazione Crea aree di lavoro (nuova esperienza delle aree di lavoro) per consentire a tutti gli utenti o a nessun utente in un'organizzazione di creare aree di lavoro della nuova esperienza. Possono anche limitare la creazione ai membri di gruppi di sicurezza specifici.

> [!NOTE]
> Per impostazione predefinita, l'opzione Crea aree di lavoro (nuova esperienza delle aree di lavoro) consente la creazione di nuove aree di lavoro in Power BI solo agli utenti autorizzati a creare gruppi di Office 365. Assicurarsi di impostare un valore nel portale di amministrazione di Power BI per garantire che gli utenti appropriati possano creare aree di lavoro della nuova esperienza.

![Impostazioni dell'area di lavoro nel portale di amministrazione](media/service-new-workspaces/power-bi-workspace-admin-settings.png)

L'[elenco di aree di lavoro è disponibile](service-admin-portal.md#workspaces) nel portale di amministrazione di Power BI. 

![Elenco delle aree di lavoro](media/service-admin-portal/workspaces-list.png)

## <a name="new-workspaces-side-by-side-with-classic-workspaces"></a>Nuove aree di lavoro affiancate alle aree di lavoro classiche

Le aree di lavoro nuove e aggiornate e le aree di lavoro classiche coesistono ed è possibile scegliere il tipo di area di lavoro da creare. La nuova esperienza delle aree di lavoro rappresenta il tipo predefinito di area di lavoro. Power BI continua a elencare tutti i gruppi di Office 365 di cui l'utente è membro in Power BI per evitare di modificare i flussi di lavoro esistenti. Per informazioni su come creare una nuova area di lavoro, vedere [Creare le nuove aree di lavoro](service-create-the-new-workspaces.md). Per informazioni su come creare un'area di lavoro classica, vedere [Creare le aree di lavoro classiche](service-create-workspaces.md).

## <a name="roles-in-the-new-workspaces"></a>Ruoli nelle nuove aree di lavoro

Per concedere l'accesso a una nuova area di lavoro, aggiungere gruppi di utenti o singoli utenti a uno dei ruoli dell'area di lavoro: visualizzatori, membri, collaboratori o amministratori. A tutti i membri in un gruppo di utenti viene assegnato il ruolo definito. Se un utente appartiene a più gruppi di utenti, ottiene il livello di autorizzazione più elevato fornito dai ruoli a lui assegnati.

I ruoli consentono di gestire chi può fare cosa in un'area di lavoro per permettere ai team di collaborare. Le nuove aree di lavoro consentono di assegnare ruoli a singoli utenti e gruppi di utenti: gruppi di sicurezza, gruppi di Office 365 e liste di distribuzione. 

Quando si assegnano i ruoli a un gruppo di utenti, i singoli utenti del gruppo possono accedere al contenuto. Se si annidano gruppi di utenti, tutti gli utenti contenuti sono autorizzati.

Ecco le funzionalità dei quattro ruoli: amministratori, membri, collaboratori e visualizzatori. Tutte queste funzionalità, ad eccezione dell'ultima, richiedono una licenza di Power BI Pro.

|Capacità   | Amministratore  | Membro  | Collaboratore  | Visualizzatore |
|---|---|---|---|---|
| Aggiornare ed eliminare l'area di lavoro.  | X  |   |   |   | 
| Aggiungere/rimuovere utenti, inclusi altri amministratori.  | X  |   |   |   |
| Aggiungere membri o altri utenti con autorizzazioni inferiori.  |  X | X  |   |   |
| Pubblicare e aggiornare un'app. |  X | X  |   |   |
| Condividere un elemento o condividere un'app. |  X | X  |   |   |
| Consentire ad altri utenti di ricondividere a loro volta gli elementi. |  X | X  |   |   |
| Creare, modificare ed eliminare contenuto nell'area di lavoro.  |  X | X  | X  |   |
| Pubblicare report nell'area di lavoro, eliminare contenuto.  |  X | X  | X  |   |
| Creare un report in un'altra area di lavoro in base a un set di dati in questa area di lavoro. |  X | X  | X  |   |
| Copiare un report. | X | X | X |  |
| Visualizzare un elemento e interagire con esso. |  X | X  | X  | X  |

> [!NOTE]
>Per copiare un report e creare un report in un'altra area di lavoro in base a un set di dati in questa area di lavoro, gli utenti dovranno soddisfare criteri aggiuntivi:
>- È necessaria una licenza di Power BI Pro. 
>- È necessaria l'autorizzazione di creazione per il set di dati. Per i set di dati in questa area di lavoro, le persone con i ruoli Amministratore, Membro e Collaboratore hanno l'autorizzazione di creazione tramite il ruolo dell'area di lavoro.
 
## <a name="licensing"></a>Gestione delle licenze
Tutti gli utenti che vengono aggiunti a un'area di lavoro nella capacità condivisa devono avere una licenza di Power BI Pro. Nell'area di lavoro tutti gli utenti possono collaborare sui dashboard e i report che si intende pubblicare e rendere disponibili a un pubblico più ampio o all'intera organizzazione. 

Per distribuire contenuto ad altri utenti all'interno dell'organizzazione, è possibile assegnare loro licenze di Power BI Pro oppure assegnare l'area di lavoro a una capacità Power BI Premium.

Quando l'area di lavoro è in una capacità Power BI Premium, gli utenti con il ruolo Visualizzatore possono accedere all'area di lavoro anche se non hanno una licenza di Power BI Pro. Se tuttavia si assegna a questi utenti un ruolo più elevato, ad esempio di amministratore, membro o collaboratore, verrà loro richiesto di avviare una versione di valutazione Pro quando provano ad accedere all'area di lavoro. Per sfruttare le capacità del ruolo Visualizzatore per gli utenti senza licenze Pro, assicurarsi che gli utenti con ruolo Visualizzatore non siano inclusi in altri ruoli delle aree di lavoro, individualmente o tramite un gruppo di utenti. 

> [!NOTE]
> Per la pubblicazione di report nella nuova esperienza delle aree di lavoro, le regole relative alle licenze vengono applicate in modo più rigoroso. Se gli utenti provano a pubblicare da Power BI Desktop o altri strumenti client senza una licenza Pro, viene visualizzato l'errore "Solo gli utenti con licenze di Power BI Pro possono pubblicare in quest'area di lavoro".

## <a name="how-the-new-workspaces-are-different"></a>Differenze delle nuove aree di lavoro

Con le nuove aree di lavoro, alcune funzionalità sono state riprogettate. Ecco le modifiche che verranno mantenute definitivamente. 

* La creazione di queste aree di lavoro non comporta la creazione di gruppi di Office 365 come avviene con le aree di lavoro classiche. Tuttavia, ora è possibile usare un gruppo di Office 365 per concedere agli utenti l'accesso all'area di lavoro assegnando al gruppo un ruolo. 
* Nelle aree di lavoro classiche è possibile aggiungere solo singoli utenti agli elenchi di membri e amministratori. Nelle nuove aree di lavoro è possibile aggiungere più gruppi di sicurezza di Active Directory, liste di distribuzione o gruppi di Office 365 a questi elenchi per semplificare la gestione degli utenti. 
- È possibile creare un pacchetto di contenuto aziendale da un'area di lavoro classica. Non è possibile crearne uno dalle nuove aree di lavoro.
- È possibile utilizzare un pacchetto di contenuto aziendale da un'area di lavoro classica. Non è possibile usarne uno dalle nuove aree di lavoro.

## <a name="workspace-contact-list"></a>Elenco contatti dell'area di lavoro
La nuova funzionalità **Elenco contatti** consente di specificare quali utenti ricevono una notifica relativa ai problemi che si verificano nell'area di lavoro. Per impostazione predefinita, qualsiasi utente o gruppo specificato come amministratore dell'area di lavoro riceve una notifica, ma è possibile personalizzare l'elenco. Gli utenti o i gruppi elencati nell'elenco contatti verranno visualizzati nell'interfaccia utente per consentire agli utenti di ottenere informazioni correlate all'area di lavoro. 

Vedere altre informazioni sull'[impostazione dell'elenco contatti dell'area di lavoro](service-create-the-new-workspaces.md#workspace-contact-list).

## <a name="workspace-onedrive"></a>OneDrive area di lavoro
La funzionalità OneDrive area di lavoro consente di configurare un gruppo di Office 365 la cui archiviazione file nella raccolta documenti di SharePoint è disponibile per gli utenti dell'area di lavoro. Il gruppo deve essere creato al di fuori di Power BI. 

Power BI non sincronizza le autorizzazioni di utenti o gruppi che sono configurati per l'accesso all'area di lavoro con l'appartenenza a un gruppo di Office 365. È consigliabile gestire l'accesso dell'area di lavoro tramite la stesso gruppo di Office 365 la cui archiviazione file si configura in questa impostazione. 

Vedere le informazioni su come [impostare OneDrive area di lavoro e accedervi](service-create-the-new-workspaces.md#workspace-onedrive).  
   
## <a name="auditing"></a>Controllo
Le attività seguenti vengono controllate da Power BI per la nuova esperienza delle aree di lavoro.

| Nome descrittivo |   Nome operazione |
|---|---|
| Cartella di Power BI creata | CreateFolder |
| Cartella di Power BI eliminata | DeleteFolder |
| Cartella di Power BI aggiornata | UpdateFolder |
| Accesso alla cartella di Power BI aggiornato| UpdateFolderAccess |

Vedere altre informazioni sul [controllo in Power BI](service-admin-auditing.md#activities-audited-by-power-bi).

## <a name="limitations-and-considerations"></a>Limitazioni e considerazioni

Limitazioni da tenere presenti:

- le aree di lavoro possono contenere un massimo di 1.000 set di dati o 1.000 report per ogni set di dati. 
- Una persona con una licenza di Power BI Pro può essere membro di un massimo di 1.000 aree di lavoro.
- Power BI Publisher per Excel non è supportato.

## <a name="workspace-features-that-work-differently"></a>Funzionalità delle aree di lavoro che si comportano in modo diverso

Alcune funzionalità delle nuove aree di lavoro si comportano diversamente da quelle delle aree di lavoro correnti. Queste differenze sono intenzionali e sono state implementate in base ai commenti e suggerimenti ricevuti dai clienti al fine di consentire un approccio più flessibile alla collaborazione con le aree di lavoro:

- Applicazione delle licenze: per la pubblicazione di report nella nuova esperienza delle aree di lavoro vengono applicate le regole relative alle licenze esistenti che richiedono una licenza di Power BI Pro per gli utenti che collaborano alle aree di lavoro o condividono contenuti con altri utenti nel servizio Power BI. Per gli utenti senza una licenza Pro, viene visualizzato l'errore "Solo gli utenti con licenze di Power BI Pro possono pubblicare in quest'area di lavoro".
- Ricondivisione/Non è possibile ricondividere per i membri: funzionalità sostituita dal ruolo Collaboratore
- Aree di lavoro di sola lettura: invece di concedere agli utenti l'accesso di sola lettura a un'area di lavoro, è possibile assegnare agli utenti il ruolo Visualizzatore, che consente un simile accesso di sola lettura al contenuto in un'area di lavoro.
- Gli utenti senza una licenza Pro possono accedere all'area di lavoro se questa è in una capacità Power BI Premium, anche se hanno solo il ruolo Visualizzatore.
- Per consentire agli utenti con ruolo Visualizzatore di esportare i dati, assicurarsi che abbiano il ruolo di compilazione sui set di dati nell'area di lavoro. Per altre informazioni, vedere [Compilare l'autorizzazione per i set di dati](service-datasets-build-permissions.md#build-permissions-for-shared-datasets).
- Il pulsante **Lascia l'area di lavoro** non è disponibile.

## <a name="frequently-asked-questions"></a>Domande frequenti

**La nuova esperienza delle aree di lavoro disponibile a livello generale influisce sui collegamenti al contenuto esistente?**

No. La nuova esperienza delle aree di lavoro non influisce sui collegamenti agli elementi esistenti nelle aree di lavoro classiche. La disponibilità generale della nuova esperienza delle aree di lavoro comporta un cambiamento dell'area di lavoro predefinita creata, ma non delle aree di lavoro esistenti. 

**Le aree di lavoro esistenti vengono aggiornate alla nuova esperienza delle aree di lavoro disponibile a livello generale?**

No. La nuova esperienza delle aree di lavoro disponibile a livello generale comporta un cambiamento solo del tipo predefinito di area di lavoro. Le aree di lavoro classiche esistenti basate su Gruppi di Office 365 rimangono invariate.

**Le aree di lavoro vengono comunque create automaticamente per i gruppi di Office 365?**

Sì. Poiché sono supportati entrambi i tipi di aree di lavoro affiancati, continuano a venire elencati tutti i gruppi di Office 365 a cui l'utente può accedere nell'elenco di aree di lavoro.

## <a name="next-steps"></a>Passaggi successivi
* [Creare le nuove aree di lavoro in Power BI](service-create-the-new-workspaces.md)
* [Creare le aree di lavoro classiche](service-create-workspaces.md)
* [Installare e usare app in Power BI](service-create-distribute-apps.md)
* Domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)
