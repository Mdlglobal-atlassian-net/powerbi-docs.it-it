---
title: Introduzione ai set di dati in aree di lavoro diverse (anteprima)
description: Di seguito viene descritto come è possibile condividere un set di dati con utenti in tutta l'organizzazione, che possono poi compilare report basati sul set di dati nelle proprie aree di lavoro.
author: maggiesMSFT
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/01/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: d30a8012161934ada4ff3cb2ce6852fe62f48892
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/06/2020
ms.locfileid: "73877191"
---
# <a name="intro-to-datasets-across-workspaces-preview"></a>Introduzione ai set di dati in aree di lavoro diverse (anteprima)

Business intelligence è un'attività di collaborazione. È importante definire set di dati standardizzati che possono essere l'unica "fonte sicura". L'individuazione e il riutilizzo di tali set di dati standardizzati è fondamentale. Quando gli esperti di modellazione dati dell'organizzazione creano e condividono set di dati ottimizzati, gli autori di report possono iniziare a compilare report accurati partendo da questi set di dati. L'organizzazione può quindi usare dati coerenti per prendere decisioni e disporre di una cultura di dati integra.

![Selezionare un set di dati condiviso](media/service-datasets-across-workspaces/power-bi-select-shared-dataset.png)

In Power BI gli autori di set di dati possono controllare chi può accedere ai dati usando l'[autorizzazione di compilazione](service-datasets-build-permissions.md). Gli autori di set di dati possono anche *certificare* o *promuovere* i set di dati in modo che possano essere individuati da altri utenti. In questo modo gli autori di report sanno quali sono i set di dati di qualità elevata e ufficiali e possono usarli ovunque creano report in Power BI. Per gli amministratori tenant è disponibile una nuova impostazione tenant per [controllare l'uso dei set di dati in aree di lavoro diverse](service-datasets-admin-across-workspaces.md).

## <a name="dataset-sharing-and-the-new-workspace-experience"></a>Condivisione di set di dati e nuova esperienza delle aree di lavoro

La compilazione di report basati su set di dati in aree di lavoro diverse e la copia di report in aree di lavoro diverse sono operazioni strettamente correlate alla [nuova esperienza delle aree di lavoro](service-create-the-new-workspaces.md):

- Quando nel servizio si apre il catalogo di set di dati da una nuova esperienza delle aree di lavoro, il catalogo di set di dati mostra i set di dati disponibili nell'area di lavoro personale e nella nuova esperienza delle aree di lavoro. 
- Quando si apre il catalogo di set di dati da un'area di lavoro classica, vengono visualizzati solo i set di dati di quell'area di lavoro specifica, non quelli di altre aree di lavoro.
- In Power BI Desktop è possibile pubblicare report Live Connect in diverse aree di lavoro, purché i relativi set di dati si trovino nelle aree di lavoro della nuova esperienza.
- Quando si copiano i report in aree di lavoro diverse, l'area di lavoro di destinazione deve essere un'area della nuova esperienza.

## <a name="discover-datasets-preview"></a>Individuare set di dati (anteprima)

Quando si compila un report basato su un set di dati esistente, è prima di tutto necessario connettere il set di dati al servizio Power BI o a Power BI Desktop. Per altre informazioni, leggere come [individuare set di dati da aree di lavoro diverse (anteprima)](service-datasets-discover-across-workspaces.md)

## <a name="copy-a-report"></a>Copiare un report

Quando si individua un report interessante, che si trovi in un'area di lavoro oppure in un'app, è possibile crearne una copia e modificarlo in base alle esigenze. Non è necessario creare il modello di dati, perché è già stato creato. È molto più semplice modificare un report esistente anziché crearlo da zero. Per altre informazioni, leggere come [copiare i report](service-datasets-copy-reports.md).

## <a name="build-permission-for-datasets"></a>Compilare l'autorizzazione per i set di dati

Con l'autorizzazione per creazione report gli autori di set di dati possono stabilire quali utenti dell'organizzazione possono creare nuovo contenuto nei propri set di dati. Gli utenti con l'autorizzazione per creazione report possono anche creare nuovo contenuto in set di dati esterni a Power BI, ad esempio in fogli di Excel, usando Analizza in Excel, XMLA ed Esporta. Per altre informazioni, vedere l'[autorizzazione di compilazione](service-datasets-build-permissions.md).

## <a name="promotion-and-certification"></a>Promozione e certificazione

Se si creano set di dati, quando si crea un set di dati che altri utenti possono sfruttare, è possibile semplificarne l'identificazione [promuovendo il set di dati](service-datasets-promote.md). È anche possibile richiedere che esperti dell'organizzazione [certifichino il set di dati](service-datasets-certify.md).

## <a name="licensing"></a>Gestione delle licenze

Le funzioni e le esperienze specifiche integrate nelle funzionalità di un set di dati condiviso sono concesse in licenza in base ai rispettivi scenari esistenti. ad esempio:

- L'individuazione e la connessione a set di dati condivisi sono generalmente disponibili a tutti gli utenti, non si tratta di una funzionalità limitata ai piani Premium.
- Gli utenti che non hanno una licenza Pro possono usare set di dati di tutte le aree di lavoro per la creazione di report solo se tali set di dati si trovano nell'area di lavoro personale dell'utente o in un'area di lavoro supportata da un piano Premium. La stessa restrizione di licenza si applica indipendentemente dal fatto che la creazione di report avvenga in Power BI Desktop o nel servizio Power BI.
- Per la copia di report tra aree di lavoro è necessaria una licenza Pro.
- Per copiare report da un'app, è richiesta una licenza Pro, come era necessario per i pacchetti di contenuto dell'organizzazione.
- Per la promozione e la certificazione dei set di dati è necessaria una licenza Pro.

## <a name="considerations-and-limitations"></a>Considerazioni e limitazioni

- L'editore di un'app deve assicurarsi che il gruppo di destinatari abbia accesso ai set di dati all'esterno dell'area di lavoro. In caso contrario, gli utenti avranno problemi durante l'interazione con l'app: senza l'accesso ai set di dati i report non si apriranno e i riquadri dei dashboard verranno visualizzati come bloccati. Gli utenti, poi, non saranno in grado di aprire l'app se il primo elemento di spostamento di questa è un report senza accesso al set di dati.
- La compilazione di un report basato su un set di dati in un'area di lavoro diversa richiede la nuova esperienza delle aree di lavoro su due fronti: Il report deve risiedere in una nuova esperienza delle aree di lavoro e il set di dati deve trovarsi in una nuova esperienza delle aree di lavoro.
- In un'area di lavoro classica l'esperienza di individuazione di set di dati visualizza solo i set di dati in quell'area di lavoro.
- Per impostazione predefinita la funzionalità "Pubblica sul Web" non funziona per un report basato su un set di dati condiviso.
- Se due utenti sono membri di un'area di lavoro che ha accesso a un set di dati condiviso, è possibile che solo uno dei due possa visualizzare il set di dati correlato nell'area di lavoro. Solo gli utenti con almeno accesso in lettura al set di dati possono visualizzare il set di dati condiviso. 

## <a name="next-steps"></a>Passaggi successivi

- [Alzare di livello i set di dati](service-datasets-promote.md)
- [Certificare i set di dati](service-datasets-certify.md)
- [Controllare l'uso dei set di dati in aree di lavoro diverse](service-datasets-admin-across-workspaces.md)
- Domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
