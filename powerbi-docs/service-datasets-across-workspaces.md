---
title: Usare set di dati in aree di lavoro diverse (anteprima) - Power BI
description: Di seguito viene descritto come è possibile condividere un set di dati con utenti in tutta l'organizzazione, che possono poi compilare report basati sul set di dati nelle proprie aree di lavoro.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/07/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: d893088978d7a412d0e005ca7b3280824974c76c
ms.sourcegitcommit: 206806d8ddb6bdfc322c1a46fb34a1b0678acba2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816655"
---
# <a name="use-datasets-across-workspaces-preview"></a>Usare set di dati in aree di lavoro diverse (anteprima)

Business intelligence è un'attività di collaborazione. È importante definire set di dati standardizzati che possono essere l'unica "fonte sicura". L'individuazione e il riutilizzo di tali set di dati standardizzati è fondamentale. Quando gli esperti di modellazione dati dell'organizzazione creano e condividono set di dati ottimizzati, gli autori di report possono iniziare a compilare report accurati partendo da questi set di dati. L'organizzazione può quindi usare dati coerenti per prendere decisioni e disporre di una cultura di dati integra.

![Selezionare un set di dati condiviso](media/service-datasets-across-workspaces/power-bi-select-shared-dataset.png)

In Power BI è più semplice per gli autori di set di dati certificare o promuovere i set di dati in modo che possano essere individuati da altri utenti. Gli autori di report possono quindi trovare set di dati di qualità e ufficiali da usare ovunque in Power BI. I proprietari dei set di dati possono controllare chi può accedere ai dati usando l'[autorizzazione di compilazione](service-datasets-build-permissions.md#build-permissions-for-shared-datasets). Per gli amministratori tenant è disponibile una nuova impostazione tenant per [controllare l'uso dei set di dati in aree di lavoro diverse](service-datasets-admin-across-workspaces.md).

## <a name="dataset-sharing-and-the-new-workspace-experience"></a>Condivisione di set di dati e nuova esperienza delle aree di lavoro

La compilazione di report basati su set di dati in aree di lavoro diverse e la copia di report in aree di lavoro diverse sono operazioni strettamente correlate alla [nuova esperienza delle aree di lavoro](service-create-the-new-workspaces.md):

- Quando nel servizio si apre il catalogo di set di dati da una nuova esperienza delle aree di lavoro, il catalogo di set di dati elenca i set di dati disponibili nell'area di lavoro personale e nella nuova esperienza delle aree di lavoro. 
- Quando si apre il catalogo di set di dati da un'area di lavoro classica, vengono visualizzati solo i set di dati di quell'area di lavoro specifica, non quelli di altre aree di lavoro.
- In Desktop è possibile pubblicare report Live Connect in diverse aree di lavoro, purché i relativi set di dati si trovino nelle aree di lavoro della nuova esperienza.
- Quando si copiano i report in aree di lavoro diverse, l'area di lavoro di destinazione deve essere un'area della nuova esperienza.

## <a name="build-permission-for-datasets"></a>Compilare l'autorizzazione per i set di dati

Con il tipo di autorizzazione di compilazione, è possibile consentire ad altri utenti dell'organizzazione di compilare in un set di dati esistente nuovo contenuto, ad esempio report, dashboard, riquadri aggiunti da Domande e risposte e Insights Discovery. Possono anche compilare nuovo contenuto nel set di dati esterno a Power BI, ad esempio in fogli di Excel, usando Analizza in Excel, XMLA ed Esporta. Per altre informazioni, vedere l'[autorizzazione di compilazione](service-datasets-build-permissions.md#build-permissions-for-shared-datasets).

## <a name="discover-datasets-preview"></a>Individuare set di dati (anteprima)

Quando si compila un report basato su un set di dati esistente, è prima di tutto necessario connettere il set di dati al servizio Power o a Power BI Desktop. Per altre informazioni, leggere come [individuare set di dati da aree di lavoro diverse (anteprima)](service-datasets-discover-across-workspaces.md)

## <a name="copy-a-report"></a>Copiare un report

Quando si individua un report interessante, che si trovi in un'area di lavoro oppure in un'app, è possibile crearne una copia e modificarlo in base alle esigenze. Non è necessario creare il modello di dati, perché è già stato creato. È molto più semplice modificare un report esistente anziché crearlo da zero. Per altre informazioni, leggere come [copiare i report](service-datasets-copy-reports.md).

## <a name="promotion-and-certification"></a>Promozione e certificazione

Se si creano set di dati o si crea un set di dati che altri utenti possono sfruttare, è possibile semplificarne l'identificazione [promuovendo il set di dati](service-datasets-promote.md). È anche possibile richiedere che esperti dell'organizzazione [certifichino il set di dati](service-datasets-certify.md).

## <a name="licensing"></a>Gestione delle licenze

Le funzioni e le esperienze specifiche integrate nelle funzionalità di un set di dati condiviso sono concesse in licenza in base ai rispettivi scenari esistenti.  ad esempio:

- L'individuazione e la connessione a set di dati condivisi sono generalmente disponibili a tutti gli utenti. Gli utenti che però non hanno una licenza Pro possono connettersi solo a set di dati che si trovano nella propria area di lavoro personale o in aree di lavoro Premium.
- Per promuovere e certificare set di dati esterni alle aree di lavoro personali, è richiesta una licenza Pro. È infatti necessaria una licenza Pro per essere membro di un'area di lavoro di un'app.
- Per copiare report tra aree di lavoro, è richiesta una licenza Pro. Anche in questo caso è infatti necessaria una licenza Pro per essere membro di un'area di lavoro di un'app.
- Per copiare report da un'app, è richiesta una licenza Pro, come era necessario per i pacchetti di contenuto dell'organizzazione.

## <a name="considerations-and-limitations"></a>Considerazioni e limitazioni

- La compilazione di un report basato su un set di dati in un'area di lavoro diversa richiede la nuova esperienza delle aree di lavoro su due fronti: Il report deve risiedere in una nuova esperienza delle aree di lavoro e il set di dati deve trovarsi in una nuova esperienza delle aree di lavoro.
- In un'area di lavoro classica l'esperienza di individuazione di set di dati visualizza solo i set di dati in quell'area di lavoro.
- È possibile creare report in aree di lavoro per le app basati su set di dati in aree di lavoro diverse. Non è tuttavia possibile creare un'app per un'area di lavoro che contiene tali set di dati.
- Gli utenti del piano gratuito in Desktop visualizzano solo i set di dati dell'area di lavoro personale e delle aree di lavoro con capacità Premium.
- Se si vuole aggiungere a un'app un report basato su un set di dati condiviso, è necessario essere membro dell'area di lavoro del set di dati. Si tratta di un problema noto.
- La funzionalità "Pubblica sul Web" non funziona per un report basato su un set di dati condiviso. È un'impostazione predefinita.
- Se due utenti sono membri di un'area di lavoro che ha accesso a un set di dati condiviso, è possibile che solo uno dei due possa visualizzare il set di dati correlato nell'area di lavoro. Solo gli utenti con almeno accesso in lettura al set di dati possono visualizzare il set di dati condiviso. 

## <a name="next-steps"></a>Passaggi successivi

- [Alzare di livello i set di dati](service-datasets-promote.md)
- [Certificare i set di dati](service-datasets-certify.md)
- [Controllare l'uso dei set di dati in aree di lavoro diverse](service-datasets-admin-across-workspaces.md)
- Domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)
