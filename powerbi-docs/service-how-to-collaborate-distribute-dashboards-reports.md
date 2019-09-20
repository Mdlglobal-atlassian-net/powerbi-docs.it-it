---
title: Modalità per la condivisione del lavoro in Power BI
description: In Power BI si possono condividere ed elaborare in collaborazione dashboard, report, riquadri e app in diversi modi, ognuno dei quali presenta vantaggi specifici.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/06/2019
LocalizationGroup: Share your work
ms.openlocfilehash: 31310900b91924e639ce10a13aef3da996598502
ms.sourcegitcommit: 226b47f64e6749061cd54bf8d4436f7deaed7691
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2019
ms.locfileid: "70841673"
---
# <a name="ways-to-share-your-work-in-power-bi"></a>Modalità per la condivisione del lavoro in Power BI

Vengono creati dashboard e report. È probabile che si sia anche collaborato al loro contenuto con i colleghi. Ora si vuole che altri possano accedervi. Ma qual è il modo migliore di distribuire report e dashboard? In questo articolo vengono confrontate le opzioni disponibili per la collaborazione e la condivisione in Power BI:

* Collaborare con i colleghi allo scopo di creare report e dashboard significativi nelle *aree di lavoro*.
* Creare *app* contenenti i dashboard e i report e distribuire le app a un gruppo più ampio o all'intera organizzazione.
* Creare *set di dati condivisi* che i colleghi possono usare come base per personalizzare i report nelle proprie aree di lavoro.
* Creare un'*app modello* che è possibile distribuire a utenti di Power BI esterni tramite Microsoft AppSource.
* Condividere dashboard o report con alcune persone dal servizio o dalle app Power BI per dispositivi mobili.
* Stampare i report.
* *Incorporare* i report in portali sicuri o siti Web pubblici.

Indipendentemente dall'opzione scelta, per condividere contenuto è necessaria una [licenza di Power BI Pro](service-features-license-type.md). In caso contrario, il contenuto deve avere una [capacità Premium](service-premium-what-is.md). I requisiti relativi alla licenza per i colleghi che visualizzano il contenuto dipendono dall'opzione scelta. Le sezioni seguenti illustrano i dettagli. 

![App nel servizio Power BI](media/service-how-to-collaborate-distribute-dashboards-reports/power-bi-apps-new-look.png)

*App nel servizio Power BI*

## <a name="collaborate-in-a-workspace"></a>Collaborare in un'area di lavoro

Quando i team lavorano insieme, devono accedere agli stessi documenti in modo da poter collaborare rapidamente. Nelle aree di lavoro di Power BI i team si riuniscono per condividere la proprietà e la gestione di dashboard, report, set di dati e cartelle di lavoro. A volte gli utenti di Power BI organizzano le aree di lavoro in base alle strutture dell'organizzazione, altre volte creano aree di lavoro per progetti specifici. Altre organizzazioni usano invece diverse aree di lavoro per archiviare versioni diverse dei report o dei dashboard desiderati. 

Le aree di lavoro offrono ruoli che determinano le autorizzazioni dei colleghi. È possibile usare tali ruoli per determinare chi può gestire l'intera area di lavoro o chi può modificarne o distribuirne il contenuto.

![Aree di lavoro](media/service-how-to-collaborate-distribute-dashboards-reports/power-bi-workspace.png)

È naturalmente possibile inserire contenuto nell'area di lavoro personale e condividerlo da questa posizione. Per la collaborazione, le aree di lavoro sono tuttavia preferibili rispetto all'area di lavoro personale in quanto offrono la comproprietà del contenuto. L'utente e l'intero team possono eseguire facilmente aggiornamenti o concedere l'accesso ad altri utenti. L'area di lavoro personale è più adatta per gli utenti singoli per contenuto occasionale o personale.

Supponiamo di avere un dashboard completato da condividere con i colleghi. Qual è il modo migliore di concedere l'accesso al dashboard? La risposta dipende da numerosi fattori. 

- Se i colleghi devono mantenere aggiornato il dashboard o devono accedere a tutto il contenuto nell'area di lavoro, è consigliabile aggiungerli all'area di lavoro. 
- Se invece devono semplicemente visualizzare il dashboard e non tutto il contenuto nell'area di lavoro, è possibile scegliere tra diverse alternative. Se per alcuni è necessario solo un dashboard, la soluzione migliore potrebbe essere condividere il dashboard in questione.
- Se il dashboard però fa parte di un set di contenuto più grande che deve essere distribuito a molti colleghi, la scelta migliore sarà probabilmente quella di pubblicare un'*app*.

Power BI offre una nuova esperienza dell'area di lavoro. Leggere [Creare le nuove aree di lavoro](service-create-the-new-workspaces.md) per informazioni sulle modifiche apportate alle aree di lavoro. 

## <a name="distribute-insights-in-an-app"></a>Distribuire informazioni dettagliate in un'app

Si supponga di voler distribuire il dashboard a un pubblico vasto all'interno dell'organizzazione. Dopo aver collaborato con i colleghi alla creazione di un'*area di lavoro* e aver creato e definito in dettaglio dashboard, report e set di dati nell'area di lavoro, è ora possibile selezionare i dashboard e i report e pubblicarli come app in un gruppo o nell'intera organizzazione.

![Icona Pubblica app](media/service-how-to-collaborate-distribute-dashboards-reports/power-bi-publish-app.png)

Le app possono essere facilmente individuate e installate nel servizio Power BI ([https://app.powerbi.com](https://app.powerbi.com)). È possibile inviare agli utenti aziendali un collegamento diretto all'app o dire loro di cercarla in AppSource. Se l'amministratore di Power BI concede le autorizzazioni, è possibile installare un'app automaticamente nell'account Power BI dei colleghi. Altre informazioni sulla [pubblicazione delle app](service-create-distribute-apps.md).

Dopo l'installazione di un'app è possibile visualizzarla nel browser o su un dispositivo mobile.

Per visualizzare l'app gli utenti devono disporre di una licenza Power BI Pro; in alternativa, l'app deve essere archiviata in una capacità di Power BI Premium. Per informazioni dettagliate, leggere [What is Power BI Premium?](service-premium-what-is.md) (Che cos'è Power BI Premium?).

È anche possibile pubblicare le app per gli utenti esterni all'organizzazione, che possono visualizzare il contenuto delle app e interagire con esso, ma non condividerlo con altri utenti. È ora possibile creare *app modello* e distribuirle a tutti gli utenti di Power BI.

## <a name="share-a-dataset"></a>Condividere un set di dati

Ovviamente c'è anche chi è molto abile a creare modelli di dati di qualità elevata e ben progettati nei report. In questo caso, l'intera organizzazione può trarne vantaggio, usando gli stessi modelli di dati ben progettati. I *set di dati condivisi* soddisfano questo tipo di ruolo. Quando si crea un report con un modello di dati che tutti useranno, è possibile salvare il report nel servizio Power BI e concedere alle persone giuste l'autorizzazione a usarlo. Sulla base del set di dati si potranno poi creare propri report. In questo modo, tutti gli utenti baseranno i propri report sugli stessi dati e avranno un'unica versione effettiva.

![Trovare un set di dati condiviso](media/service-how-to-collaborate-distribute-dashboards-reports/power-bi-shared-datasets.png)

Altre informazioni sulla [creazione e sull'uso di set di dati condivisi](service-datasets-across-workspaces.md).

## <a name="share-dashboards-and-reports"></a>Condividere dashboard e report

Si supponga di aver completato un dashboard e un report nell'area di lavoro personale o in un'area di lavoro e che si voglia consentirne l'accesso ad altre persone. Uno dei modi per farlo consiste nel *condividerlo*. 

![Condividere un report](media/service-how-to-collaborate-distribute-dashboards-reports/power-bi-share-report.png)

Per condividere il contenuto è necessario che sia l'utente che le persone con cui viene condiviso abbiano una licenza Power BI Pro. In caso contrario, il contenuto deve trovarsi in un'area di lavoro in una [capacità Premium](service-premium-what-is.md). Quando si condivide un dashboard o un report, i destinatari possono visualizzarlo e interagire con esso, ma non possono modificarlo. Essi vedranno gli stessi dati che l'utente vede nei dashboard e nei report, a meno che non sia stata applicata la sicurezza a livello di riga al set di dati sottostante. I colleghi con cui si condivide il dashboard possono condividerlo con i loro colleghi, se vengono autorizzati a tale scopo. 

È possibile condividere anche con utenti esterni all'organizzazione, che possono anche visualizzare il dashboard o il report e interagire con esso, ma non condividerlo. 

Altre informazioni sulla [condivisione di dashboard e report](service-share-dashboards.md) dal servizio Power BI. È anche possibile aggiungere un filtro a un collegamento e [condividere una vista filtrata del report](service-share-reports.md).

## <a name="annotate-and-share-from-the-power-bi-mobile-apps"></a>Annotare e condividere dalle app Power BI per dispositivi mobili

Nelle app Power BI per dispositivi mobili per i dispositivi iOS e Android, è possibile aggiungere annotazioni a un riquadro, un report o un oggetto visivo e quindi condividerlo con chiunque via posta elettronica.

![Annotare e condividere nelle app per dispositivi mobili](media/service-how-to-collaborate-distribute-dashboards-reports/power-bi-iphone-annotate.png)

Si condivide uno snapshot del riquadro, del report o dell'oggetto visivo e i destinatari lo vedono esattamente com'era quando è stato inviato il messaggio di posta elettronica. Il messaggio di posta elettronica contiene anche un collegamento al dashboard o al report. Se i destinatari hanno una licenza Power BI Pro o il contenuto ha una [capacità Premium](service-premium-what-is.md) e si è già condiviso l'oggetto, allora potranno aprirlo. È possibile inviare snapshot dei riquadri a chiunque, non solo ai colleghi nello stesso dominio di posta elettronica.

Altre informazioni su come [aggiungere annotazioni e condividere riquadri, report e oggetti visivi](consumer/mobile/mobile-annotate-and-share-a-tile-from-the-mobile-apps.md) dalle app per dispositivi mobili iOS e Android.

È anche possibile [condividere uno snapshot di un riquadro](consumer/mobile/mobile-windows-10-phone-app-get-started.md) dall'app Power BI per i dispositivi Windows 10.

## <a name="print-or-save-as-pdf-or-other-static-file"></a>Stampare o salvare in formato PDF o altri file statici

È possibile stampare o salvare in formato PDF o un altro formato di file statici un dashboard intero, un riquadro del dashboard, una pagina del report o una visualizzazione dal servizio Power BI. I report possono essere stampati solo una pagina alla volta, ovvero non è possibile stampare l'intero report in una sola volta. Altre informazioni su [stampa o salvataggio come file statico](consumer/end-user-print.md).

## <a name="embed-reports-in-secure-portals-or-public-web-sites"></a>Incorporare i report in portali sicuri o siti Web pubblici

### <a name="embed-in-secure-portals"></a>Incorporare in portali sicuri

È possibile incorporare i report di Power BI in portali o siti Web in cui gli utenti si aspettano di poterli visualizzare.  
L'opzione **Incorpora in SharePoint Online** e l'opzione **Incorpora** nel servizio Power BI consentono di incorporare i report per gli utenti interni in modo sicuro. 

- **Incorpora in SharePoint Online** funziona con la web part di Power BI per SharePoint Online. Offre un'esperienza di Single Sign-On con controllo della modalità di incorporamento del report. 
- L'opzione **Incorpora** funziona con qualsiasi portale o sito Web che supporta l'incorporamento del contenuto usando un URL o un iFrame. 

Indipendentemente dall'opzione scelta, Power BI impone tutte le autorizzazioni e la sicurezza dei dati prima che il contenuto sia visibile agli utenti. L'utente che visualizza il report deve avere la licenza appropriata. Altre informazioni sulle opzioni [Incorpora in SharePoint Online](service-embed-report-spo.md) e [Incorpora](service-embed-secure.md) in Power BI.

### <a name="publish-to-public-web-sites"></a>Pubblicazione in siti Web pubblici

Con **Pubblica sul Web** è possibile pubblicare report di Power BI ovunque in Internet incorporando visualizzazioni interattive in post di blog, siti Web, social media e altre comunicazioni online, su qualsiasi dispositivo. Chiunque su Internet può visualizzare i report e non si ha alcun controllo su chi può visualizzare ciò che è stato pubblicato. Non è necessaria una licenza di Power BI. La funzionalità di pubblicazione sul Web è disponibile solo per i report che è possibile modificare. Non è possibile pubblicare report sul Web se sono stati condivisi da altri utenti o se sono inclusi in un'app. Altre informazioni sulla [pubblicazione sul Web](service-publish-to-web.md).

>[!Warning]
>Usare [Pubblica sul Web](service-publish-to-web.md) solo per condividere il contenuto pubblicamente, non per la condivisione interna.

## <a name="create-and-deploy-template-apps"></a>Creare e distribuire app modello

Le *app modello* sono progettate per essere distribuite pubblicamente, spesso in Microsoft AppSource. Si compila un'app e con un uso minimo o nullo di codice si distribuisce l'app a qualsiasi cliente di Power BI. I clienti si connettono ai dati e creano un'istanza con i propri account. Altre informazioni sulle [app modello di Power BI](service-template-apps-overview.md).


## <a name="next-steps"></a>Passaggi successivi

* [Condividere i dashboard con i colleghi e con altri utenti](service-share-dashboards.md)
* [Creare e pubblicare un'app in Power BI](service-create-distribute-apps.md)
* [Incorporare un report in un portale sicuro o un sito Web](service-embed-secure.md)

Per inviare suggerimenti, passare al [sito della community di Power BI](https://community.powerbi.com/).

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)
