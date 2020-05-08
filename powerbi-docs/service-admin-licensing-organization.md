---
title: Licenze di Power BI nell'organizzazione
description: Panoramica dei diversi tipi di licenze disponibili in Power BI e di come gli amministratori acquistano e gestiscono le licenze per l'organizzazione.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/08/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: a41e9453158c38a208fe7f4ac937b4e86a515f4b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "81436323"
---
# <a name="power-bi-licensing-in-your-organization"></a>Licenze di Power BI nell'organizzazione

Le operazioni che un utente può eseguire nel servizio Power BI dipendono dal tipo di licenza per utente disponibile e dal fatto che il contenuto con cui interagiscono sia incluso in un'area di lavoro assegnata alla capacità di Power BI Premium. Tutti gli utenti del servizio Power BI devono avere una licenza.

Gli utenti possono ottenere una licenza in due modi. Usando le funzionalità di iscrizione in modalità self-service e l'account aziendale o dell'istituto di istruzione, gli utenti possono ottenere una licenza gratuita o Pro. In alternativa, gli amministratori possono ottenere una sottoscrizione di Power BI e assegnare le licenze agli utenti.

Questo articolo illustra l'acquisto dei servizi e le licenze per utente dal punto di vista dell'amministratore. Per altre informazioni su come gli utenti possono ottenere la licenza, vedere [Iscrizione a Power BI come utente singolo](service-self-service-signup-for-power-bi.md).

## <a name="who-can-purchase-and-assign-licenses"></a>Utenti autorizzati ad acquistare e assegnare le licenze

Per acquistare o assegnare licenze per l'organizzazione, è necessario avere un ruolo di amministratore. I ruoli di amministratore vengono assegnati usando l'interfaccia di amministrazione di Azure Active Directory o di Microsoft 365. La tabella seguente indica il ruolo necessario per eseguire attività di acquisto e gestione delle licenze. Per altre informazioni sui ruoli di amministratore in Azure Active Directory, vedere [Visualizzare e assegnare i ruoli di amministratore in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-manage-roles-portal). Per altre informazioni sui ruoli di amministratore in Microsoft 365, incluse le procedure consigliate, vedere [Informazioni sui ruoli di amministratore](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide).

| Utenti autorizzati ad acquistare servizi e licenze | Utenti autorizzati a gestire le licenze utente |
| --------------- | --------------- |
| Amministratore fatturazione | Amministratore licenze |
| Amministratore globale | Amministratore utenti |
|  | Amministratore globale |

Questi ruoli gestiscono l'organizzazione. Per informazioni sui ruoli di amministratore del servizio Power BI, vedere [Informazioni sui ruoli di amministratore del servizio Power BI](service-admin-role.md).

## <a name="get-power-bi-for-your-organization"></a>Ottenere Power BI per l'organizzazione

Un amministratore globale o un amministratore fatturazione può iscriversi al servizio Power BI e acquistare le licenze per gli utenti dell'organizzazione. Se non si è ancora pronti per effettuare l'acquisto, selezionare la versione di valutazione di Power BI Pro. Si otterranno 25 licenze da usare per un mese. Per istruzioni dettagliate su come iscriversi, vedere [Ottenere una sottoscrizione di Power BI per l'organizzazione](admin/service-admin-org-subscription.md).

## <a name="about-self-service-sign-up"></a>Informazioni sull'iscrizione in modalità self-service

I singoli utenti possono ottenere una licenza di Power BI iscrivendosi con l'account aziendale o dell'istituto di istruzione. Con una licenza gratuita, gli utenti possono usare Power BI per l'analisi e la visualizzazione dei dati personali in Area di lavoro personale, ma non possono avviare la collaborazione con altri utenti. Per condividere il contenuto, è necessaria una licenza di Power BI Pro. Gli utenti possono aggiornare il tipo di licenza a Pro oppure iscriversi direttamente a Pro, se l'organizzazione usa il cloud commerciale. L'acquisto diretto o l'aggiornamento a Pro non è disponibile per istituti d'istruzione o organizzazioni distribuite in istanze di enti pubblici o cloud sovrani.

Se si preferisce che l'iscrizione in modalità self-service non sia disponibile per gli utenti dell'organizzazione, vedere [Abilitare o disabilitare l'iscrizione in modalità self-service](admin/service-admin-disable-self-service.md) per informazioni su come disattivarla.

Per verificare quali utenti dell'organizzazione hanno già una licenza, vedere [Visualizzare e gestire le licenze utente](admin/service-admin-manage-licenses.md).

## <a name="license-types-and-capabilities"></a>Tipi di licenze e funzionalità

Esistono due tipi di licenze per utente di Power BI: gratuita e Pro. Il tipo di licenza necessario per un utente è determinato dalla posizione in cui viene archiviato il contenuto e dal modo in cui l'utente interagirà con tale contenuto. La posizione in cui il contenuto può essere archiviato è determinata dal [tipo di sottoscrizione](#subscription-types) dell'organizzazione.

Un tipo di sottoscrizione, [Power BI Premium](service-admin-premium-purchase.md), consente agli utenti con una licenza gratuita di eseguire operazioni sul contenuto nelle aree di lavoro assegnate alla capacità Premium. Senza la capacità Premium, un utente con una licenza gratuita può usare il servizio Power BI solo per connettersi ai dati e creare report e dashboard in un'area di lavoro personale. Non può condividere il contenuto con altri utenti né pubblicarlo nelle aree di lavoro per le app.

Una sottoscrizione di Power BI standard usa la capacità condivisa. Quando il contenuto viene archiviato nella capacità condivisa, gli utenti a cui è assegnata una licenza di Power BI Pro possono collaborare solo con altri utenti di Power BI Pro. Possono utilizzare il contenuto condiviso da altri utenti, pubblicare contenuti nelle aree di lavoro per le app, condividere i dashboard e sottoscrivere dashboard e report.  Quando le aree di lavoro sono in capacità Premium, gli utenti Pro possono distribuire il contenuto agli utenti che non hanno una licenza Power BI Pro.

La tabella seguente riepiloga le funzionalità di base di ogni tipo di licenza. Per una suddivisione dettagliata delle funzionalità disponibili per ogni tipo di licenza, vedere [Funzionalità in base al tipo di licenza](service-features-license-type.md).

| Tipo di licenza | Funzionalità quando l'area di lavoro è nella capacità condivisa | Funzionalità aggiuntive quando l'area di lavoro è nella capacità Premium |
| --------- | ----------- | ----------- |
| Power BI (gratuito) | Accedere al contenuto in Area di lavoro personale | Utilizzare il contenuto condiviso con gli utenti correnti |
| Power BI Pro | Pubblicare contenuti nelle aree di lavoro per le app, condividere i dashboard e sottoscrivere dashboard e report, condividere con gli utenti che hanno una licenza Pro | Distribuire il contenuto agli utenti che hanno licenze gratuite |

## <a name="subscription-types"></a>Tipi di sottoscrizioni

Tutte le sottoscrizioni di licenze commerciali basate sull'utente di Microsoft si basano sulle identità di Azure Active Directory. È quindi necessario accedere con un'identità supportata da Azure Active Directory per le licenze commerciali. È possibile aggiungere una sottoscrizione di Power BI a qualsiasi sottoscrizione di Microsoft che usa Azure Active Directory per i servizi di gestione delle identità. Alcune sottoscrizioni, ad esempio Office 365 E5, includono una licenza Power BI Pro, quindi non è necessaria alcuna iscrizione separata per Power BI.

Esistono due tipi di sottoscrizioni di Power BI per le organizzazioni: BI in modalità self-service con Power BI Pro e analisi avanzata con Power BI Premium.

Con una sottoscrizione di Power BI Pro standard in modalità self-service, gli amministratori assegnano licenze per utente. È prevista una tariffa mensile per ogni utente per le licenze Power BI Pro, che consente la collaborazione, la pubblicazione, la condivisione e l'analisi ad hoc. Il contenuto viene salvato nella capacità di archiviazione condivisa completamente gestita da Microsoft.

Una sottoscrizione di Power BI Premium alloca una capacità dedicata a un'organizzazione. La sottoscrizione Premium, adatta per BI per le aziende, analisi dei Big Data e creazione di report nel cloud e in locale, offre controlli avanzati di amministrazione e distribuzione. Le risorse di calcolo e archiviazione dedicate vengono gestite dagli amministratori della capacità dell'organizzazione. Per questo ambiente dedicato è previsto un costo mensile. Tra gli altri vantaggi, è possibile accedere al contenuto archiviato nella capacità Premium e distribuirlo agli utenti che non hanno licenze Power BI Pro. Ad almeno un utente deve essere assegnata una licenza Power BI Pro per usare Premium e gli autori di contenuti e gli sviluppatori devono comunque avere una licenza Power BI Pro.

I due tipi di sottoscrizioni non si escludono a vicenda. È possibile avere sia Power BI Premium che Power BI Pro. In questa configurazione il contenuto archiviato nella capacità Premium può essere condiviso con tutti gli utenti ed è disponibile anche la capacità condivisa. Per informazioni sui limiti della capacità, vedere [Gestire l'archiviazione dei dati nelle aree di lavoro di Power BI](service-admin-manage-your-data-storage-in-power-bi.md).

Per confrontare le funzionalità e i prezzi del prodotto, vedere [Prezzi di Power BI](https://powerbi.microsoft.com/pricing).

## <a name="guest-user-access"></a>Accesso utente guest

Potrebbe essere necessario distribuire il contenuto a utenti esterni all'organizzazione. È possibile condividere il contenuto con utenti esterni invitandoli a visualizzare il contenuto come guest. Azure Active Directory Business-to-Business (Azure AD B2B) consente la condivisione con utenti guest esterni. Per condividere il contenuto con gli utenti esterni, è necessario soddisfare i prerequisiti seguenti:

- La possibilità di condividere il contenuto con gli utenti esterni deve essere abilitata

- L'utente guest deve essere in possesso delle licenze appropriate per visualizzare il contenuto condiviso

Per altre informazioni sull'accesso utente guest, vedere [Distribuire il contenuto di Power BI agli utenti guest esterni usando Azure AD B2B](service-admin-azure-ad-b2b.md).

## <a name="purchase-power-bi-pro-licenses"></a>Acquistare licenze di Power BI Pro

Come amministratore, è possibile acquistare le licenze Power BI Pro tramite Microsoft 365 o rivolgendosi a un partner Microsoft. Dopo aver acquistato le licenze, assegnarle ai singoli utenti. Per altre informazioni, vedere [Acquistare e assegnare licenze Power BI Pro](service-admin-purchasing-power-bi-pro.md).

### <a name="power-bi-pro-license-expiration"></a>Scadenza della licenza di Power BI Pro

È previsto un periodo di tolleranza dopo la scadenza di una licenza di Power BI Pro. Per le licenze che fanno parte dell'acquisto di un contratto multilicenza, il periodo di tolleranza è 90 giorni. Se la licenza è stata acquistata direttamente, il periodo di tolleranza è di 30 giorni.

Power BI Pro ha lo stesso ciclo di vita della sottoscrizione di Office 365. Per altre informazioni, vedere [Che cosa succede ai dati e all'accesso al termine della sottoscrizione di Office 365 per le aziende](https://support.office.com/article/What-happens-to-my-data-and-access-when-my-Office-365-for-business-subscription-ends-4436582f-211a-45ec-b72e-33647f97d8a3).


## <a name="next-steps"></a>Passaggi successivi

- [Acquistare e assegnare licenze Power BI Pro](service-admin-purchasing-power-bi-pro.md)
- [Documentazione sulle sottoscrizioni aziendali e sulla fatturazione di Microsoft 365](https://docs.microsoft.com/microsoft-365/commerce/?view=o365-worldwide)
- [Individuare gli utenti di Power BI che hanno effettuato l'accesso](service-admin-access-usage.md)
- Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
