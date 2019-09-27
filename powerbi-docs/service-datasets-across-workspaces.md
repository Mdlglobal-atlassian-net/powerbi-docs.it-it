---
title: Introduzione ai set di dati in aree di lavoro diverse (anteprima)
description: Di seguito viene descritto come è possibile condividere un set di dati con utenti in tutta l'organizzazione, che possono poi compilare report basati sul set di dati nelle proprie aree di lavoro.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/16/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: ace40fed472dc516cce5a761544cc5365566f3cd
ms.sourcegitcommit: a97c0c34f888e44abf4c9aa657ec9463a32be06f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2019
ms.locfileid: "71074116"
---
# <a name="intro-to-datasets-across-workspaces-preview"></a>Introduzione ai set di dati in aree di lavoro diverse (anteprima)

Business intelligence è un'attività di collaborazione. È importante definire set di dati standardizzati che possono essere l'unica "fonte sicura". L'individuazione e il riutilizzo di tali set di dati standardizzati è fondamentale. Quando gli esperti di modellazione dati dell'organizzazione creano e condividono set di dati ottimizzati, gli autori di report possono iniziare a compilare report accurati partendo da questi set di dati. L'organizzazione può quindi usare dati coerenti per prendere decisioni e disporre di una cultura di dati integra.

![Selezionare un set di dati condiviso](media/service-datasets-across-workspaces/power-bi-select-shared-dataset.png)

In Power BI gli autori di set di dati possono controllare chi può accedere ai dati usando l'[autorizzazione di compilazione](service-datasets-build-permissions.md#build-permissions-for-shared-datasets). Gli autori di set di dati possono anche *certificare* o *promuovere* i set di dati in modo che possano essere individuati da altri utenti. In questo modo gli autori di report sanno quali sono i set di dati di qualità elevata e ufficiali e possono usarli ovunque creano report in Power BI. Per gli amministratori tenant è disponibile una nuova impostazione tenant per [controllare l'uso dei set di dati in aree di lavoro diverse](service-datasets-admin-across-workspaces.md).

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

Con l'autorizzazione di tipo compilazione, gli autori di set di dati possono stabilire chi nell'organizzazione può creare nuovo contenuto nei set di dati. Gli utenti con l'autorizzazione di compilazione possono anche creare nuovo contenuto nel set di dati esterno a Power BI, ad esempio in fogli di Excel, usando Analizza in Excel, XMLA ed Esporta. Per altre informazioni, vedere l'[autorizzazione di compilazione](service-datasets-build-permissions.md#build-permissions-for-shared-datasets).

## <a name="promotion-and-certification"></a>Promozione e certificazione

Se si creano set di dati, quando si crea un set di dati che altri utenti possono sfruttare, è possibile semplificarne l'identificazione [promuovendo il set di dati](service-datasets-promote.md). È anche possibile richiedere che esperti dell'organizzazione [certifichino il set di dati](service-datasets-certify.md).

## <a name="licensing"></a>Gestione delle licenze

Le funzioni e le esperienze specifiche integrate nelle funzionalità di un set di dati condiviso sono concesse in licenza in base ai rispettivi scenari esistenti. ad esempio:

- L'individuazione e la connessione a set di dati condivisi sono generalmente disponibili a tutti gli utenti. Gli utenti che però non hanno una licenza Pro possono connettersi solo a set di dati che si trovano nella propria area di lavoro personale.
- Gli utenti che non hanno una licenza Pro possono usare report e dashboard basati su un set di dati condiviso solo se entrambe le aree di lavoro (quella che include il contenuto e quella che contiene il set di dati) sono ospitate in un'area Premium.
- In Power BI Desktop gli utenti senza licenza Pro possono visualizzare solo i set di dati dell'area di lavoro personale.
- Per la copia di report tra aree di lavoro è necessaria una licenza Pro.
- Per copiare report da un'app, è richiesta una licenza Pro, come era necessario per i pacchetti di contenuto dell'organizzazione.
- Per la promozione e la certificazione dei set di dati è necessaria una licenza Pro.

## <a name="considerations-and-limitations"></a>Considerazioni e limitazioni

- La compilazione di un report basato su un set di dati in un'area di lavoro diversa richiede la nuova esperienza delle aree di lavoro su due fronti: Il report deve risiedere in una nuova esperienza delle aree di lavoro e il set di dati deve trovarsi in una nuova esperienza delle aree di lavoro.
- Supponiamo di creare un report nell'area di lavoro A basato su un set di dati dell'area di lavoro B. Quando si crea un'app per l'area di lavoro A, è possibile includere tale report nell'app dell'area di lavoro A solo se si è membro anche dell'area di lavoro B.
- In un'area di lavoro classica l'esperienza di individuazione di set di dati visualizza solo i set di dati in quell'area di lavoro.
- Se si vuole aggiungere a un'app un report basato su un set di dati condiviso, è necessario essere membro dell'area di lavoro del set di dati. Si tratta di un problema noto.
- Per impostazione predefinita la funzionalità "Pubblica sul Web" non funziona per un report basato su un set di dati condiviso.
- Se due utenti sono membri di un'area di lavoro che ha accesso a un set di dati condiviso, è possibile che solo uno dei due possa visualizzare il set di dati correlato nell'area di lavoro. Solo gli utenti con almeno accesso in lettura al set di dati possono visualizzare il set di dati condiviso. 

## <a name="next-steps"></a>Passaggi successivi

- [Alzare di livello i set di dati](service-datasets-promote.md)
- [Certificare i set di dati](service-datasets-certify.md)
- [Controllare l'uso dei set di dati in aree di lavoro diverse](service-datasets-admin-across-workspaces.md)
- Domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)
