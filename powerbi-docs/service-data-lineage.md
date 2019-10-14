---
title: Derivazione dei dati (anteprima)
description: Nei moderni progetti di business intelligence (BI) una delle principali problematiche affrontate da molti clienti è la necessità di conoscere il flusso dei dati dall'origine dati alla destinazione.
author: paulinbar
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.date: 10/03/2019
ms.author: painbar
LocalizationGroup: ''
ms.openlocfilehash: e91f1d5084957ee7266161b9a34f916e2902d1f4
ms.sourcegitcommit: 5e277dae93832d10033defb2a9e85ecaa8ffb8ec
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/07/2019
ms.locfileid: "72019578"
---
# <a name="data-lineage-preview"></a>Derivazione dei dati (anteprima)
Nei moderni progetti di business intelligence (BI) una delle possibili problematiche da affrontare è la necessità di conoscere il flusso dei dati dall'origine dati alla destinazione. La sfida è ancora più complessa se sono stati compilati progetti di analisi avanzati che comprendono più origini dati, elementi e dipendenze.  Rispondere a domande come "Che cosa accade se si modificano questi dati?" o "Perché questo report non è aggiornato?" può essere difficile. Per trovare una risposta potrebbe essere necessario un team di esperti o un'analisi approfondita. La visualizzazione di derivazione dei dati è stata pensata per poter rispondere a queste domande.

[ ![Visualizzazione di derivazione di Power BI](media/service-data-lineage/power-bi-lineage-view-cropped.png) ](media/service-data-lineage/power-bi-lineage-view-full-size.png#lightbox)
 
Power BI ha diversi tipi di elementi, ad esempio dashboard, report, set di dati e flussi di dati. Molti set di dati e flussi di dati si connettono a origini dati esterne, ad esempio SQL Server, e a set di dati esterni in altre aree di lavoro. Un set di dati esterno a un'area di lavoro di cui si è proprietari potrebbe trovarsi in un'area di lavoro di proprietà di un utente IT o di un altro analista. In definitiva, le origini dati e i set di dati esterni rendono più difficile sapere da dove provengono i dati. Per i progetti complessi e per quelli più semplici, è stata introdotta la visualizzazione di derivazione. 

Nella visualizzazione di derivazione vengono indicate le relazioni di derivazione tra tutti gli elementi di un'area di lavoro e tutte le dipendenze esterne. La visualizzazione di derivazione espande la visualizzazione diagramma dei flussi di dati mostrando le connessioni tra tutti gli elementi dell'area di lavoro, incluse le connessioni ai flussi di dati, sia upstream che downstream. La visualizzazione diagramma separata dei flussi di dati non sarà più disponibile a partire da novembre.

## <a name="explore-lineage-view"></a>Esplorare la visualizzazione di derivazione

Per impostazione predefinita, ogni area di lavoro, nuova o classica, ha una visualizzazione di derivazione, tranne Area di lavoro personale. È necessario almeno un ruolo Collaboratore nell'area di lavoro per visualizzarla. Per informazioni dettagliate, vedere [Autorizzazioni](#permissions) in questo articolo. 

- Per accedere alla visualizzazione di derivazione, passare alla visualizzazione elenco dell'area di lavoro. Toccare la freccia accanto a **Visualizzazione Elenco** e selezionare **Visualizzazione derivazione**.

    [ ![Passare alla visualizzazione di derivazione](media/service-data-lineage/power-bi-lineage-list-view-cropped.png) ](media/service-data-lineage/power-bi-lineage-list-view.png#lightbox)

    In questa visualizzazione sono visibili tutti gli elementi dell'area di lavoro e il flusso dei dati da uno all'altro.

**Origini dati**

Vengono visualizzate le origini dati da cui i set di dati e i flussi di dati ottengono i dati. Nelle schede delle origini dati vengono visualizzate altre informazioni che consentono di identificare l'origine. Ad esempio, per il server di Azure SQL viene visualizzato anche il nome del database.

![Origine dati della visualizzazione di derivazione senza gateway](media/service-data-lineage/power-bi-lineage-data-source-no-gateway.png)
 
**Gateway**

Se un'origine dati è connessa tramite un gateway locale, le informazioni sul gateway vengono aggiunte alla scheda dell'origine dati. Se si hanno le autorizzazioni come amministratore del gateway o come utente dell'origine dati, vengono visualizzate altre informazioni, ad esempio il nome del gateway.

![Origine dati della visualizzazione di derivazione con gateway](media/service-data-lineage/power-bi-lineage-data-source-with-gateway.png)

**Set di dati e flussi di dati**
 
Nei set di dati viene visualizzata l'ora dell'ultimo aggiornamento e viene indicato se un set di dati è stato certificato o alzato di livello.

![Set di dati certificato nella visualizzazione di derivazione](media/service-data-lineage/power-bi-lineage-external-certified-dataset.png)
 
Se un report nell'area di lavoro si basa su un set di dati in un'altra area di lavoro, viene visualizzato il nome dell'area di lavoro di origine nella scheda del set di dati. Per passare all'area di lavoro di origine, selezionarne il nome.
 
- Per qualsiasi elemento, selezionare i puntini di sospensione (...) per visualizzare il menu delle opzioni, che include le stesse azioni disponibili nella visualizzazione elenco.
  
Per visualizzare altri metadati nei set di dati, selezionare la scheda di un set di dati. Informazioni aggiuntive sul set di dati vengono visualizzate in un riquadro laterale.

![Riquadro laterale con altre informazioni](media/service-data-lineage/power-bi-lineage-side-pane.png)
 
## <a name="show-lineage-for-any-artifact"></a>Visualizzare la derivazione per qualsiasi elemento 

Si supponga di voler visualizzare la derivazione per un elemento specifico.

- Selezionare le frecce doppie sotto un elemento.

    [ ![Evidenziare la derivazione per un elemento specifico](media/service-data-lineage/power-bi-lineage-highlight-cropped.png) ](media/service-data-lineage/power-bi-lineage-highlight-full-size.png#lightbox)

    Power BI evidenzia tutti gli elementi correlati a tale elemento e attenua gli altri. 

## <a name="navigation-and-full-screen"></a>Esplorazione e schermo intero 

La visualizzazione di derivazione è un canvas interattivo. È possibile usare il mouse e il touchpad per spostarsi nel canvas e per fare zoom avanti o indietro.  

- Per fare zoom avanti e indietro, usare il menu nell'angolo in basso a destra oppure il mouse o il touchpad. 

- Per avere più spazio per il grafo, usare l'opzione schermo intero nell'angolo in basso a destra. 

    ![Zoom avanti o indietro oppure schermo intero](media/service-data-lineage/power-bi-lineage-zoom-full-screen.png)

## <a name="permissions"></a>Autorizzazioni

- Per vedere la visualizzazione di derivazione, è necessaria una licenza Power BI Pro.
- La visualizzazione di derivazione è disponibile solo per gli utenti con accesso all'area di lavoro.
- Gli utenti devono avere un ruolo Amministratore, Membro o Collaboratore nell'area di lavoro. Gli utenti con un ruolo Visualizzatore non possono passare alla visualizzazione di derivazione.

## <a name="considerations-and-limitations"></a>Considerazioni e limitazioni

La visualizzazione di derivazione non è disponibile in Internet Explorer. Per informazioni dettagliate, vedere [Browser supportati per Power BI](power-bi-browsers.md).

## <a name="next-steps"></a>Passaggi successivi

- [Introduzione ai set di dati in aree di lavoro diverse (anteprima)](service-datasets-across-workspaces.md)
