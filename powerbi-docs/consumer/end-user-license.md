---
title: Tipi di licenze per gli utenti finali di Power BI
description: Informazioni sui diversi tipi di licenze e su come determinare quale licenza si sta usando.
author: mihart
ms.reviewer: lukasz
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 03/27/2020
ms.author: mihart
LocalizationGroup: consumers
ms.openlocfilehash: 4615bae84ddeb3d3e0b3c471a6b9d6bcf7eda406
ms.sourcegitcommit: 81407c9ccadfa84837e07861876dff65d21667c7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2020
ms.locfileid: "81267297"
---
# <a name="types-of-power-bi-licenses"></a>Tipi di licenze di Power BI

[!INCLUDE[consumer-appliesto-ynnn](../includes/consumer-appliesto-ynnn.md)]

In qualità di *utente finale*, è possibile usare il servizio Power BI per esplorare i report e i dashboard e prendere così decisioni consapevoli a livello aziendale. Se si usa Power BI da un po' di tempo o si è parlato con colleghi *progettisti*, si è probabilmente riscontrato che alcune funzionalità sono attive solo se si ha un determinato tipo di licenza o sottoscrizione. 

In questo articolo vengono illustrate le differenze tra le licenze utente e le sottoscrizioni dell'organizzazione e il modo in cui interagiscono: versione gratuita, Pro e Premium e capacità Premium. Si apprenderà anche come determinare quale combinazione di licenza e sottoscrizione si sta usando.  

![Diagramma che illustra la modalità di connessione delle licenze](media/end-user-license/power-bi-venn.png)

Si inizieranno a esaminare le due categorie di licenze, ovvero le sottoscrizioni per utente e dell'organizzazione. Il punto di partenza è costituito dalle funzionalità predefinite disponibili con ognuna. Si esaminerà quindi come l'amministratore di Power BI e i proprietari del contenuto possono usare ruoli e autorizzazioni per modificare le funzionalità predefinite della licenza e della sottoscrizione. 

Ad esempio, anche se la licenza lo consente, l'amministratore può limitare la possibilità di eseguire operazioni come l'esportazione dei dati, l'uso di query in linguaggio naturale per domande e risposte o la pubblicazione sul Web. Quando un *progettista* di report assegna contenuto a un'[area di lavoro](end-user-workspaces.md), può assegnare l'utente a un ruolo dell'area di lavoro. I ruoli determinano ciò che l'utente può e non può fare all'interno di tale area di lavoro. Il *progettista* può modificare ulteriormente i limiti della licenza usando le impostazioni di autorizzazione. Evidentemente lo scenario è abbastanza complesso. Questo articolo dovrebbe eliminare la maggior parte dei dubbi in merito.

## <a name="per-user-licenses"></a>Licenze per utente
Il primo tipo di licenza è la licenza **per utente**. Ogni utente del servizio Power BI dispone di una licenza gratuita o di una licenza Pro. Alcune funzionalità sono riservate agli utenti con licenze Pro.  

- Una **licenza Power BI Pro (senza sottoscrizione Premium)** consente a un utente di collaborare con altri utenti Pro creando e condividendo contenuto. Solo gli utenti con licenza Pro possono pubblicare report, sottoscrivere dashboard e report e collaborare con i colleghi nelle aree di lavoro. 

    ![Immagine degli utenti Pro](media/end-user-license/power-bi-pro.jpg)

    Power BI Pro è una licenza per singolo utente che consente agli utenti di leggere e interagire con i report e i dashboard pubblicati da altri utenti nel servizio Power BI. Gli utenti con questo tipo di licenza possono condividere il contenuto e collaborare con altri utenti di Power BI Pro. Solo gli utenti di Power BI Pro possono pubblicare o condividere contenuto con altri utenti o usare contenuto creato da altri utenti. L'eccezione è rappresentata dal contenuto ospitato nella [capacità Power BI Premium](#understanding-premium-and-premium-capacity). Per altre informazioni, vedere [Capacità Power BI Premium](#understanding-premium-and-premium-capacity) più avanti. Le licenze Pro vengono in genere usate da *progettisti* e sviluppatori di report. 


- Una **licenza di Power BI autonoma gratuita (senza sottoscrizione Premium)** , anche se dotata di molte funzionalità, è destinata agli utenti che iniziano a usare Power BI o che creano contenuti per scopi personali. Vedere [Iscriversi al servizio Power BI come utente singolo](../service-self-service-signup-for-power-bi.md).   

    Una licenza utente autonoma gratuita è la soluzione ideale per chi usa gli esempi Microsoft per apprendere Power BI. Gli utenti con licenze autonome gratuite non possono visualizzare contenuto condiviso da altri utenti o condividere il proprio contenuto con altri utenti di Power BI. 

    ![Immagine di utenti autonomi](media/end-user-license/power-bi-free-license.jpg)

    Tutti i clienti con una licenza autonoma gratuita possono eseguire l'aggiornamento a una [versione di valutazione della licenza di Power BI Pro gratuita](../service-self-service-signup-for-power-bi.md). La versione di valutazione offre tutta la potenza e le funzionalità di un utente Power BI Pro.

    ![invito alla versione di valutazione Pro](media/end-user-license/power-bi-pro-trial.png)

- **Una licenza di Power BI gratuita con una sottoscrizione Premium** Quando un'organizzazione ha una sottoscrizione Premium, gli amministratori e gli utenti Pro possono assegnare le aree di lavoro alla *capacità Premium* e concedere agli utenti l'accesso gratuito a tali aree di lavoro. Un'area di lavoro in una capacità Premium è uno spazio in cui gli utenti Pro possono condividere contenuti e collaborare con gli utenti con licenza gratuita, senza che questi debbano avere account Pro. In queste aree di lavoro gli utenti della versione gratuita hanno autorizzazioni elevate: possono collaborare e condividere, esportare dati, sottoscrivere, interagire con i filtri e molto altro ancora. 

Finora tutto chiaro?  OK. Esaminiamo più in dettaglio la **capacità Premium**.

## <a name="understanding-premium-and-premium-capacity"></a>Informazioni sulla licenza Premium e sulla capacità Premium
La sottoscrizione Premium è destinata alle **organizzazioni**. È possibile considerarla come l'aggiunta di un livello di caratteristiche e funzionalità a tutte le licenze **per utente** di Power BI in un'organizzazione. 

Quando un'organizzazione acquista una licenza Premium, in genere l'amministratore assegna licenze Pro ai dipendenti che dovranno creare e condividere contenuto e licenze gratuite a tutti gli utenti che utilizzeranno tale contenuto. Gli utenti Pro creano [aree di lavoro per le app](end-user-workspaces.md) e aggiungono contenuto (dashboard, report, app) a tali aree di lavoro. Per consentire agli utenti della versione gratuita di collaborare in tali aree di lavoro, l'amministratore o l'utente Pro salva le aree di lavoro nella *capacità Premium*. 

Quando un'organizzazione acquista una licenza Premium, la capacità che riceve per il servizio Power BI è allocata in modo esclusivo all'organizzazione. Non è condivisa da altre organizzazioni. La capacità è supportata da hardware dedicato completamente gestito da Microsoft. Le organizzazioni possono scegliere di applicare la propria capacità dedicata in modo esteso, oppure di allocarla ad aree di lavoro specifiche. Un'organizzazione può avere tutte le aree di lavoro nella capacità o solo alcune. È possibile identificare un'area di lavoro nella capacità Premium grazie all'icona a forma di diamante ![icona a forma di diamante](media/end-user-license/power-bi-diamond.png).  Un'area di lavoro in una capacità Premium è uno spazio in cui gli utenti Pro possono condividere contenuti e collaborare con gli utenti con licenza gratuita, senza che questi debbano avere account Pro. 

Nella capacità Premium le licenze Pro sono comunque necessarie per i progettisti del contenuto. I progettisti creano aree di lavoro per le app, si connettono alle origini dati, modellano i dati e creano report e dashboard che vengono condivisi direttamente o inseriti in pacchetti e condivisi come app. Gli utenti che non hanno una licenza Pro possono comunque accedere a un'area di lavoro per le app in Power BI Premium, a condizione che l'area di lavoro sia inclusa nella *capacità* Premium e che il proprietario dell'area di lavoro conceda loro le autorizzazioni necessarie.

Nel diagramma seguente il lato sinistro rappresenta gli utenti Pro che creano e condividono contenuto nelle aree di lavoro per le app. 

- L'**Area di lavoro A** è stata creata in un'organizzazione che non ha una sottoscrizione Premium. 

- L'**Area di lavoro B** è stata creata in un'organizzazione che ha una sottoscrizione Premium, anche se questa particolare area di lavoro non è stata salvata nella capacità Premium. Accanto al nome dell'area di lavoro non è presente l'icona a forma di rombo.

- L'**Area di lavoro C** è stata creata in un'organizzazione che ha una sottoscrizione Premium ed è stata salvata nella capacità Premium. Accanto a quest'area di lavoro è visualizzata l'icona a forma di rombo.  

![Immagine degli utenti Pro](media/end-user-license/power-bi-sharing-scenarios.jpg)

Il *progettista* di Power BI Pro può condividere contenuti e collaborare con altri utenti Pro in una delle tre aree di lavoro. Questo a condizione che il progettista condivida l'area di lavoro con l'intera organizzazione o che assegni i ruoli dell'area di lavoro agli utenti Pro. 

L'utente di Power BI Pro può condividere contenuti e collaborare solo con utenti della versione gratuita usando l'Area di lavoro C. Per consentire agli utenti con licenza gratuita di accedere all'area di lavoro, è necessario che l'area sia assegnata alla capacità Premium. All'interno dell'area di lavoro il progettista assegna ruoli ai collaboratori: *Amministratore*, *Membro*, *Collaboratore* o *Visualizzatore*. Il ruolo determina le azioni che il collaboratore può eseguire nell'area di lavoro. In genere agli utenti *consumer* di Power BI viene assegnato il ruolo *Visualizzatore*. Per altre informazioni, vedere [Aree di lavoro per consumer di Power BI](end-user-workspaces.md).

## <a name="find-out-which-license-and-subscription-you-have"></a>Informazioni sulla licenza e la sottoscrizione in uso
Esistono diversi modi per cercare le informazioni sulla licenza e la sottoscrizione di Power BI in uso. 

Prima di tutto, determinare la licenza per **utente** a propria disposizione.

- Alcune versioni di Microsoft Office includono una licenza di Power BI Pro.  Per verificare se la versione di Office include Power BI, visitare il [portale di Office](https://portal.office.com/account) e selezionare **Sottoscrizioni**.

    Il primo utente (Pradtanna) dispone di Office 365 E5, che include una licenza di Power BI Pro.

    ![Scheda Sottoscrizioni del portale di Office](media/end-user-license/power-bi-license-office.png)

    Il secondo utente (Zalan) dispone di una licenza di Power BI gratuita. 

    ![Scheda Sottoscrizioni del portale di Office](media/end-user-license/power-bi-license-free.png)

Verificare se il proprio account ha anche una sottoscrizione Premium. Entrambi gli utenti precedenti (con licenza Pro o gratuita) possono appartenere a un'organizzazione con licenza Premium.  Si prenda in considerazione il secondo utente.  

- Nel servizio Power BI selezionare **Area di lavoro personale** e quindi selezionare l'icona dell'ingranaggio nell'angolo superiore destro. Scegliere **Gestisci archivio personale**.

    ![Menu Impostazioni con ingranaggio](media/end-user-license/power-bi-license-personal.png)

    Le licenze **per utente**, Pro o gratuite, offrono 10 GB di spazio di archiviazione nel cloud, che possono essere usati per ospitare report di Power BI o cartelle di lavoro di Excel. Se sono disponibili più di 10 GB, l'utente è membro di un account aziendale che dispone di una licenza Premium.

    ![Gestisci archiviazione con una capacità di 100 GB](media/end-user-license/power-bi-free-capacity.png)

    Tenere presente che, nella pagina del portale di Office, l'utente Zalan aveva una licenza per Power BI (gratuito). Tuttavia, dato che la sua organizzazione ha acquistato una sottoscrizione Premium, nel servizio Power BI l'utente Zalan non è limitato a 10 GB di spazio di archiviazione, ma ha 100 GB. Come *consumer* in un'organizzazione con una licenza Premium, a condizione che il *progettista* includa l'area di lavoro nella capacità Premium, Zalan è in grado di visualizzare contenuti condivisi, collaborare con i colleghi, usare le app e altro ancora. L'estensione delle autorizzazioni disponibili viene impostata dall'amministratore di Power BI e dal progettista dei contenuti. Osservare che un utente Pro ha già condiviso un'area di lavoro con Zalan. L'icona a forma di rombo gli segnala che questa area di lavoro è archiviata nella capacità Premium. 

   
## <a name="understanding-workspace-roles"></a>Informazioni sui ruoli dell'area di lavoro
Fino a qui sono state esaminate le licenze per utente, le licenze Premium, le aree di lavoro per le app e la capacità Premium. Ora si esamineranno i *ruoli* dell'area di lavoro.

Dato che questo articolo è destinato ai *consumer* di Power BI, è presente lo scenario seguente:

-  L'utente ha una licenza *gratuita* e appartiene a un'organizzazione che ha una sottoscrizione di Power BI Premium. 
- Un utente di Power BI Pro ha creato una raccolta di dashboard e report e l'ha pubblicata come *app* per l'intera organizzazione.  
- Le app esistono all'interno di *aree di lavoro* e questa area di lavoro è inclusa nella capacità Premium.    
- Questa area di lavoro dell'app ha un dashboard e due report.
- L'utente Pro ha assegnato all'utente con licenza gratuita il ruolo **Visualizzatore**.

### <a name="the-viewer-role"></a>Ruolo Visualizzatore
I ruoli consentono ai *progettisti* di Power BI di gestire chi può fare cosa in un'area di lavoro, in modo da permettere la collaborazione tra i team. Uno di questi ruoli è il ruolo **Visualizzatore**. 

Quando l'area di lavoro è in una capacità Power BI Premium, gli utenti con il ruolo Visualizzatore possono accedere all'area di lavoro anche se non hanno una licenza di Power BI Pro. Dato che il ruolo Visualizzatore non può accedere o esportare i dati sottostanti, rappresenta un approccio sicuro per l'interazione con dashboard, report e app.

> [!TIP]
> Per informazioni sugli altri ruoli (Amministratore, Membro e Collaboratore), vedere [Creazione di una nuova area di lavoro](../service-new-workspaces.md).

## <a name="next-steps"></a>Passaggi successivi
[Caratteristiche degli *utenti finali* di Power BI](end-user-consumer.md)    
[Informazioni sulle aree di lavoro](end-user-workspaces.md)    
<!--[View Power BI features by license type](end-user-features.md) -->

