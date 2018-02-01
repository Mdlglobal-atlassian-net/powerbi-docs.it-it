---
title: Area di lavoro contenuto archiviato di Power BI
description: Area di lavoro contenuto archiviato di Power BI dopo la gestione del tenant di Office 365
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 06/28/2017
ms.author: maghan
ms.openlocfilehash: 7698a1207f19382430fb8e225543b32b6aebcd49
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/30/2018
---
# <a name="power-bi-archived-workspace"></a>Area di lavoro contenuto archiviato di Power BI
Con Power BI, chiunque può iscriversi e iniziare a usare il servizio in pochissimi minuti.  In seguito, il reparto IT della propria organizzazione può scegliere di prendere il controllo della gestione di Power BI per conto degli utenti.  Se si verifica questo avvicendamento, si trarrà vantaggio dalla gestione centrale degli utenti e delle autorizzazioni all'interno dell'organizzazione e, possibilmente, dall'iscrizione semplificata usando lo stesso nome utente e password usati per altri servizi. 

Qualsiasi contenuto creato prima che il reparto IT iniziasse a gestire Power BI sarà inserito in un'Area di lavoro contenuto archiviato di Power BI, accessibile dal riquadro di spostamento a sinistra di [Power BI](https://app.powerbi.com).  È consigliabile iniziare a creare nell'Area di lavoro personale nuovo contenuto Power BI che è protetto e gestito dal reparto IT della propria organizzazione.  L'area di lavoro contenuto archiviato continuerà a esistere, ma le azioni che è possibile eseguire sul relativo contenuto saranno limitate.  Per rimuovere queste restrizioni, sarà necessario eseguire la migrazione del contenuto dall'area di lavoro del contenuto archiviato all'Area di lavoro personale, gestita dal proprio reparto IT.

## <a name="restrictions-in-your-archived-workspace"></a>Restrizioni nell'area di lavoro contenuto archiviato
Nessun contenuto verrà eliminato dall'area di lavoro del contenuto archiviato.  È possibile continuare a recuperare dati, creare report e dashboard e aggiornare i set di dati.  Gli utenti esistenti con cui è stato condiviso il contenuto potranno comunque visualizzarlo anche nella propria area di lavoro contenuto archiviato.

Il contenuto è tuttavia sottoposto ad alcune restrizioni nell'area di lavoro contenuto archiviato:

* **OneDrive for Business.**  Non sarà più possibile recuperare dati o aggiornarli da OneDrive for Business per i set di dati nell'Area di lavoro contenuto archiviato.  Se si prova a connettersi a questa origine, si riceverà un avviso.
* **Condivisione di dashboard.**  Non è possibile condividere i dashboard con altri utenti dall'Area di lavoro contenuto archiviato.  Qualsiasi utente che abbia già accesso continuerà a poter visualizzare i dashboard condivisi accedendo alla propria area di lavoro contenuto archiviato.
* **Creazione di gruppi.**  Non è possibile creare gruppi nell'Area di lavoro contenuto archiviato.
* **Accesso alle app Power BI per dispositivi mobili.**  Anche se è ancora possibile visualizzare contenuto sul Web nell'area di lavoro contenuto archiviato, questo contenuto non verrà più visualizzato nelle app per dispositivi mobili di Power BI.

## <a name="migrating-content-in-your-archived-workspace"></a>Migrazione di contenuto nell'area di lavoro contenuto archiviato
Per continuare a usare Power BI occorre creare nuovo contenuto nell'Area di lavoro personale, gestita dal proprio reparto IT.   È anche consigliabile pianificare la migrazione di eventuale contenuto dall'area di lavoro contenuto archiviato nell'Area di lavoro personale.  La modalità di esecuzione della migrazione del contenuto dipende dal tipo di contenuto:

* **Set di dati Excel o Power BI Desktop.**  Eseguire la migrazione di questi set di dati passando dall'Area di lavoro contenuto archiviato all'Area di lavoro personale e ricaricando il file Excel o Power BI Desktop facendo clic sul pulsante "Dati personali".  Se è stato impostato un aggiornamento pianificato, sarà necessario riconfigurare tali impostazioni per il nuovo set di dati nell'Area di lavoro personale.
* **Altri set di dati.**  Passare all'Area di lavoro personale, quindi fare clic sul pulsante Recupera dati per riconnettersi a qualsiasi altro set di dati creato nell'Area di lavoro contenuto archiviato.  Può essere necessario reimmettere le informazioni di sicurezza o di connessione.
* **Report.**  I report che erano contenuti nei file Excel o Power BI Desktop oppure i report installati come parte dei pacchetti di contenuto vengono ricreati automaticamente dopo aver ricaricato il file Excel o Power BI Desktop corrispondente oppure dopo aver rieseguito la connessione al pacchetto di contenuto.  Se sono stati creati report personalizzati usando il servizio Power BI sarà necessario creare nuovamente tali report nell'Area di lavoro personale.
* **Dashboard.**  I dashboard installati come parte dei pacchetti di contenuto vengono ricreati automaticamente quando si riesegue la connessione al pacchetto di contenuto nell'Area di lavoro personale.  Se sono stati creati dashboard personalizzati usando il servizio Power BI sarà necessario creare nuovamente tali dashboard nell'Area di lavoro personale.

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

