---
title: Introduzione ai pacchetti di contenuto aziendali in Power BI
description: Scoprire di più sulla creazione di pacchetti di dashboard, report, cartelle di lavoro di Excel e set di dati per ottenere pacchetti di contenuto aziendali da poter condividere con i colleghi.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/02/2018
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: f7e8d58e5fd738e5da678723ef239f5303be5070
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61226123"
---
# <a name="intro-to-organizational-content-packs-in-power-bi"></a>Introduzione ai pacchetti di contenuto aziendali in Power BI
> [!NOTE]
> Non è possibile creare pacchetti di contenuto aziendali né installarli nell'anteprima delle nuove esperienze delle aree di lavoro. Questo è un buon momento per aggiornare i pacchetti di contenuto per le app, se non è ancora stato fatto. [Altre informazioni sulla nuova esperienza dell'area di lavoro](service-create-the-new-workspaces.md).
> 

I report vengono distribuiti regolarmente tramite posta elettronica al team? Provare invece a creare pacchetti di dashboard, report, cartelle di lavoro di Excel e set di dati e pubblicarli per il team come *pacchetto di contenuto aziendale*. I pacchetti di contenuto sono facili da trovare per il team, perché sono tutti in AppSource. Dal momento che fanno parte di Power BI, sfruttano tutte le sue funzionalità, tra cui l'esplorazione interattiva dei dati, i nuovi elementi visivi, le domande e risposte, l'integrazione con altre origini dati, l'aggiornamento dei dati e molto altro.

![](media/service-organizational-content-pack-introduction/power-bi-org-content-packs.png)

La creazione di pacchetti di contenuto è diversa dalla condivisione di dashboard o dalla collaborazione negli stessi in un'area di lavoro dell'app. Per scegliere la soluzione migliore in base alla situazione specifica, leggere [Come si condividono i dashboard e i report e in che modo ci si collabora?](service-how-to-collaborate-distribute-dashboards-reports.md). 

In AppSource è possibile sfogliare o cercare i pacchetti di contenuto pubblicati per l'intera organizzazione, per i gruppi di distribuzione o sicurezza e per i [gruppi di Office 365 a cui si appartiene](https://support.office.com/article/Create-a-group-in-Office-365-7124dc4c-1de9-40d4-b096-e8add19209e9). Se non si è membri di un gruppo specifico, non saranno visualizzati i pacchetti di contenuto condivisi con tale gruppo. Tutti i membri del gruppo avranno lo stesso accesso in sola lettura ai dati del pacchetto di contenuto, ai report, alle cartelle di lavoro e ai dashboard (a meno che l'origine dati non sia di tipo SQL Server Analysis Services (SSAS), nel qual caso i privilegi verranno ereditati con l'origine dati).

I dashboard, i report e le cartelle di lavoro di Excel sono di sola lettura, ma è possibile copiarli e usarli come punto di partenza per creare una versione personalizzata del pacchetto di contenuto.

> [!NOTE]
> I pacchetti di contenuto aziendali sono disponibili solo se tutti gli utenti sono in possesso di [licenze Power BI Pro](service-features-license-type.md).
> 
> 

## <a name="what-is-appsource"></a>Informazioni su *AppSource*
La pubblicazione di un pacchetto di contenuto aziendale lo aggiunge ad AppSource.  Questo archivio centralizzato semplifica l'esplorazione e la ricerca di dashboard, report e set di dati pubblicati per i membri.  

* Per visualizzare AppSource, selezionare **Recupera dati** > **Organizzazione** > **Recupera**.

## <a name="the-life-cycle-of-an-organizational-content-pack"></a>Ciclo di vita di un pacchetto di contenuto aziendale
Qualsiasi utente di Power BI Pro può creare, pubblicare e accedere ai pacchetti di contenuto aziendali. Solo il creatore del pacchetto di contenuto può modificare la cartella di lavoro e il set di dati, pianificare l'aggiornamento ed eliminarlo.

Il ciclo di vita è simile al seguente:

1. In Power BI Pro Mattia crea un pacchetto di contenuto e lo pubblica nel gruppo di distribuzione Marketing. Le impostazioni di aggiornamento vengono ereditate con il set di dati e possono essere modificate solo da Mattia.
   
   > [!NOTE]
   > Se Mattia crea il pacchetto di contenuto dall'interno di un'[area di lavoro dell'app Power BI](service-create-distribute-apps.md) di appartenenza, ma anche se lascia l'area di lavoro, altri utenti dell'area di lavoro di Power BI possono acquisirne la proprietà.
   > 
   > 
2. Mattia invia un messaggio di posta elettronica al gruppo di distribuzione, per informarlo del nuovo pacchetto di contenuto.
3. In Power BI Pro, Giorgia, membro del gruppo di distribuzione Marketing, cerca questo pacchetto di contenuto in AppSource e vi si connette. Ora Giorgia ha una copia di sola lettura  e lo sa perché nel riquadro di spostamento sinistro è presente un'icona di condivisione, a sinistra del nome del dashboard e del report. Quando Giorgia seleziona il dashboard, un'icona di lucchetto la informa che sta visualizzando il dashboard di un pacchetto di contenuto. 
4. Ad esempio Giorgia decide di personalizzarlo. Giorgia ha ora la propria copia del dashboard e del report. Il suo lavoro non incide sull'origine, sul pacchetto di contenuto originale o su altri membri del gruppo di distribuzione. Giorgia può ora lavorare alla propria copia del dashboard e del report.
5. Mattia aggiorna il dashboard e, quando questo è pronto, pubblica una nuova versione del pacchetto di contenuto.
   
   * Giulio, un altro membro del gruppo di distribuzione, non ha personalizzato il pacchetto di contenuto originale. Le nuove modifiche vengono applicate automaticamente alla sua versione del pacchetto di contenuto.  
   * Giorgia ha personalizzato il pacchetto di contenuto. Riceve una notifica che è disponibile una nuova versione.  Potrà quindi passare ad AppSource e scaricare il pacchetto aggiornato senza perdere la sua versione personalizzata. Giorgia ha ora due versioni: quella personalizzata e il pacchetto di contenuto aggiornato.
6. Ad esempio Mattia modifica le impostazioni di sicurezza. Giulio e Giorgia non hanno più accesso al contenuto. In alternativa, vengono rimossi dal gruppo di distribuzione Marketing.
   
   * Giulio non ha personalizzato il pacchetto di contenuto originale, quindi il contenuto viene rimosso automaticamente. 
   * Giorgia ha personalizzato il pacchetto di contenuto. Alla successiva apertura del dashboard tutti i riquadri del pacchetto di contenuto originale sono stati eliminati, ma sono ancora visualizzati i riquadri che ha aggiunto da altri report (per i quali dispone ancora di autorizzazioni per l'uso). I report e il set di dati associati non sono più disponibili (e non sono visualizzati nel suo riquadro di spostamento sinistro).
7. In alternativa, Mattia elimina il pacchetto di contenuto.
   
   * Giulio non ha personalizzato il pacchetto di contenuto originale, quindi il contenuto viene rimosso automaticamente. 
   * Giorgia ha personalizzato il pacchetto di contenuto. Alla successiva apertura del dashboard tutti i riquadri del pacchetto di contenuto originale sono stati eliminati, ma sono ancora visualizzati i riquadri che ha aggiunto da altri report. I report e il set di dati associati non sono più disponibili (e non sono visualizzati nel suo riquadro di spostamento sinistro).

## <a name="data-security"></a>Sicurezza dei dati
Tutti i membri del gruppo di distribuzione hanno le stesse autorizzazioni per i dati dell'autore del pacchetto di contenuto. L'unica eccezione sono i set di dati tabulari locali di SQL Server Analysis Services (SSAS). Dal momento che i report e i dashboard si connettono direttamente al modello SSAS locale, vengono usate le credenziali di ogni singolo membro del gruppo di distribuzione per determinare i dati ai quali può accedere.

## <a name="next-steps"></a>Passaggi successivi
* [Creare e pubblicare un pacchetto di contenuto aziendale](service-organizational-content-pack-create-and-publish.md)
* [Creare e distribuire un'app in Power BI](service-create-distribute-apps.md) 
* [Power BI - Concetti di base](consumer/end-user-basic-concepts.md)
* Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

