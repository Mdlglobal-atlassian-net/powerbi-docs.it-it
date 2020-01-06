---
title: Area di lavoro contenuto archiviato di Power BI
description: Area di lavoro contenuto archiviato di Power BI dopo la gestione del tenant di Office 365
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/18/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 403bf213cc2da7ad803780946e606433166e3484
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/06/2020
ms.locfileid: "74699959"
---
# <a name="power-bi-archived-workspace"></a>Area di lavoro contenuto archiviato di Power BI

> [!IMPORTANT]
> Power BI non supporta più la funzionalità Area di lavoro contenuto archiviato, che verrà rimossa alla fine del 2019. Se si usa un'Area di lavoro contenuto archiviato, è necessario ricreare immediatamente il contenuto che si vuole mantenere in una nuova area di lavoro nel tenant corrente. Non è possibile fare affidamento sull'accesso continuativo all'Area di lavoro contenuto archiviato. Power BI non supporta più la funzionalità correlata di [acquisizione esterna di un tenant di Azure AD](service-admin-faq.md#what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users).

Con Power BI, chiunque può iscriversi e iniziare a usare il servizio in pochissimi minuti.  In seguito, il reparto IT della propria organizzazione potrebbe scegliere di prendere il controllo della gestione di Power BI per conto degli utenti.  Se si verifica questa acquisizione della proprietà, si trae vantaggio dalla gestione centrale degli utenti e delle autorizzazioni all'interno dell'organizzazione. È anche possibile sfruttare l'accesso semplificato usando lo stesso nome utente e password usati per altri servizi all'interno dell'organizzazione.

Qualsiasi contenuto creato prima che il reparto IT iniziasse a gestire Power BI sarà inserito in un'Area di lavoro contenuto archiviato di Power BI, accessibile dal riquadro di spostamento di [Power BI](https://app.powerbi.com). È consigliabile iniziare a creare nell'Area di lavoro personale nuovo contenuto Power BI che è protetto e gestito dal reparto IT della propria organizzazione.  L'area di lavoro contenuto archiviato continuerà a esistere, ma le azioni che è possibile eseguire sul relativo contenuto saranno limitate.  Per rimuovere queste restrizioni, è necessario eseguire la migrazione del contenuto dall'area di lavoro contenuto archiviato all'area di lavoro personale, gestita dal proprio reparto IT.

## <a name="restrictions-in-your-archived-workspace"></a>Restrizioni nell'area di lavoro contenuto archiviato

Power BI non eliminerà il contenuto dall'area di lavoro contenuto archiviato. È possibile continuare a recuperare dati, creare report e dashboard e aggiornare i set di dati. Gli utenti esistenti con cui è stato condiviso il contenuto possono comunque visualizzarlo anche nella propria area di lavoro contenuto archiviato. Il contenuto è tuttavia sottoposto ad alcune restrizioni nell'area di lavoro contenuto archiviato:

* **OneDrive for Business**: per i set di dati nell'area di lavoro contenuto archiviato, non è più possibile recuperare dati o aggiornarli da OneDrive for Business.  Se si prova a connettersi a questa origine, si riceve un avviso.

* **Condivisione di dashboard**: Non è possibile condividere i dashboard con altri utenti dall'Area di lavoro contenuto archiviato.  Qualsiasi utente che abbia già accesso continua a poter visualizzare i dashboard condivisi accedendo alla propria area di lavoro contenuto archiviato.

* **Creazione di gruppi**: Non è possibile creare gruppi nell'Area di lavoro contenuto archiviato.

* **Accesso alle app Power BI per dispositivi mobili**: anche se è ancora possibile visualizzare contenuto sul Web nell'area di lavoro contenuto archiviato, questo contenuto non verrà più visualizzato nelle app per dispositivi mobili di Power BI.

## <a name="migrating-content-in-your-archived-workspace"></a>Migrazione di contenuto nell'area di lavoro contenuto archiviato

Per continuare a usare Power BI, è consigliabile creare nuovo contenuto nell'area di lavoro personale. È anche consigliabile pianificare la migrazione di eventuale contenuto dall'area di lavoro contenuto archiviato nell'area di lavoro personale.  La modalità di esecuzione della migrazione del contenuto dipende dal tipo di contenuto:

* **Set di dati Excel o Power BI Desktop**: eseguire la migrazione di questi set di dati passando dall'area di lavoro contenuto archiviato all'area di lavoro personale e ricaricando il file Excel o Power BI Desktop facendo clic sul pulsante **Dati personali**.  Se è stato impostato un aggiornamento pianificato, è necessario riconfigurare tali impostazioni per il nuovo set di dati nell'area di lavoro personale.

* **Altri set di dati**: passare all'area di lavoro personale, quindi fare clic sul pulsante **Recupera dati** per riconnettersi a qualsiasi altro set di dati creato nell'area di lavoro contenuto archiviato.  Può essere necessario reimmettere le informazioni di sicurezza o di connessione.

* **Report**: i report contenuti in file di Excel o Power BI Desktop vengono automaticamente ricreati dopo aver ricaricato il file di Excel o Power BI Desktop corrispondente. Anche i report installati come parte di un pacchetto di contenuto vengono ricreati quando ci si riconnette al pacchetto di contenuto. Se sono stati creati report personalizzati usando il servizio Power BI, creare nuovamente tali report nell'area di lavoro personale.

* **Dashboard**: i dashboard installati come parte dei pacchetti di contenuto vengono ricreati automaticamente quando si riesegue la connessione al pacchetto di contenuto nell'area di lavoro personale. Se sono stati creati dashboard personalizzati usando il servizio Power BI, creare nuovamente tali dashboard nell'area di lavoro personale.

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)

