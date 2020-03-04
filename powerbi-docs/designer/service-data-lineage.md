---
title: Derivazione dei dati (anteprima)
description: Nei moderni progetti di business intelligence (BI) una delle principali problematiche affrontate da molti clienti è la necessità di conoscere il flusso dei dati dall'origine dati alla destinazione.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.date: 02/27/2020
ms.author: painbar
LocalizationGroup: ''
ms.openlocfilehash: cb58b71d4fe15458516dc0b1d3f25d79e6ef1a62
ms.sourcegitcommit: ec4d2d0f52d737e8e0583f6a7b16e6fd87382510
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782488"
---
# <a name="data-lineage-preview"></a>Derivazione dei dati (anteprima)
Nei moderni progetti di business intelligence (BI) una delle possibili problematiche da affrontare è la necessità di conoscere il flusso dei dati dall'origine dati alla destinazione. La sfida è ancora più complessa se sono stati compilati progetti di analisi avanzati che comprendono più origini dati, elementi e dipendenze. Rispondere a domande come "Che cosa accade se si modificano questi dati?" o "Perché questo report non è aggiornato?" può essere difficile. Per trovare una risposta potrebbe essere necessario un team di esperti o un'analisi approfondita. Per poter rispondere a queste domande, è stata creata una visualizzazione di derivazione dei dati.

![Visualizzazione di derivazione dei dati di Power BI](media/service-data-lineage/service-data-lineage-view.png)
 
Power BI ha diversi tipi di elementi, ad esempio dashboard, report, set di dati e flussi di dati. Molti set di dati e flussi di dati si connettono a origini dati esterne, ad esempio SQL Server, e a set di dati esterni in altre aree di lavoro. Un set di dati esterno a un'area di lavoro di cui si è proprietari potrebbe trovarsi in un'area di lavoro di proprietà di un utente IT o di un altro analista. In definitiva, le origini dati e i set di dati esterni rendono più difficile sapere da dove provengono i dati. Per i progetti complessi e per quelli più semplici, è stata introdotta la visualizzazione di derivazione.

Nella visualizzazione di derivazione vengono indicate le relazioni di derivazione tra tutti gli elementi di un'area di lavoro e tutte le dipendenze esterne. mostrando le connessioni tra tutti gli elementi dell'area di lavoro, incluse le connessioni ai flussi di dati, sia upstream che downstream.

## <a name="explore-lineage-view"></a>Esplorare la visualizzazione di derivazione

Ogni area di lavoro, nuova o classica, include automaticamente una visualizzazione di derivazione dei dati. Per visualizzarla, è necessario almeno un ruolo Collaboratore nell'area di lavoro. Per informazioni dettagliate, vedere [Autorizzazioni](#permissions) in questo articolo.

* Per accedere alla visualizzazione di derivazione, passare alla visualizzazione elenco dell'area di lavoro. Toccare la freccia accanto a **Visualizzazione Elenco** e selezionare **Visualizzazione derivazione**.

   ![Passare alla visualizzazione di derivazione dei dati](media/service-data-lineage/service-data-lineage-view-select.png)

In questa visualizzazione sono visibili tutti gli elementi dell'area di lavoro e il flusso di dati da un elemento all'altro.

**Origini dati**

Vengono visualizzate le origini dati da cui i set di dati e i flussi di dati ottengono i dati. Nelle schede delle origini dati vengono visualizzate altre informazioni che consentono di identificare l'origine. Ad esempio, per il server di Azure SQL viene visualizzato anche il nome del database.

![Origine dati della visualizzazione di derivazione senza gateway](media/service-data-lineage/service-data-lineage-data-source-card.png)
 
**Gateway**

Se un'origine dati è connessa tramite un gateway locale, le informazioni sul gateway vengono aggiunte alla scheda dell'origine dati. Se si hanno le autorizzazioni come amministratore del gateway o come utente dell'origine dati, vengono visualizzate altre informazioni, ad esempio il nome del gateway.

![Origine dati della visualizzazione di derivazione con gateway](media/service-data-lineage/service-data-lineage-data-gateway-card.png)

**Set di dati e flussi di dati**
 
Nei set di dati e nei flussi di dati viene visualizzata l'ora dell'ultimo aggiornamento e viene indicato se il set di dati o il flusso di dati è certificato o alzato di livello.

![Set di dati alzati di livello e certificati nella visualizzazione di derivazione dei dati](media/service-data-lineage/service-data-lineage-promoted-certified.png)
 
Se un report nell'area di lavoro si basa su un set di dati o un flusso di dati che si trova in un'altra area di lavoro, viene visualizzato il nome dell'area di lavoro di origine nella scheda del set di dati o del flusso di dati. Per passare all'area di lavoro di origine, selezionarne il nome.

* Per qualsiasi elemento, selezionare **Altre opzioni (...)** per visualizzare il menu delle opzioni, che include le stesse azioni disponibili nella visualizzazione elenco.

Per visualizzare altri metadati in qualsiasi elemento, selezionare la scheda dell'elemento. Informazioni aggiuntive sull'elemento sono visualizzate in un riquadro laterale. Nell'immagine seguente il riquadro laterale visualizza i metadati di un set di dati selezionato.

![Riquadro laterale con altre informazioni](media/service-data-lineage/service-data-lineage-side-pane.png)
 
## <a name="show-lineage-for-any-artifact"></a>Visualizzare la derivazione per qualsiasi elemento 

Si supponga di voler visualizzare la derivazione per un elemento specifico.

* Selezionare le frecce doppie sotto l'elemento.

   ![Evidenziare la derivazione dei dati per un elemento specifico](media/service-data-lineage/service-data-lineage-specific-artifact.png)

   Power BI evidenzia tutti gli elementi correlati a tale elemento e attenua gli altri. 

## <a name="navigation-and-full-screen"></a>Esplorazione e schermo intero 

La visualizzazione di derivazione è un canvas interattivo. È possibile usare il mouse e il touchpad per spostarsi nel canvas e per fare zoom avanti o indietro.

* Per fare zoom avanti e indietro, usare il menu nell'angolo inferiore destro oppure il mouse o il touchpad.
* Per avere più spazio per il grafo, usare l'opzione schermo intero nell'angolo inferiore destro. 

    ![Zoom avanti o indietro oppure schermo intero](media/service-data-lineage/service-data-lineage-zoom.png)

## <a name="permissions"></a>Autorizzazioni

* Per vedere la visualizzazione di derivazione, è necessaria una licenza Power BI Pro.
* La visualizzazione di derivazione è disponibile solo per gli utenti con accesso all'area di lavoro.
* Gli utenti devono avere un ruolo Amministratore, Membro o Collaboratore nell'area di lavoro. Gli utenti con un ruolo Visualizzatore non possono passare alla visualizzazione di derivazione.


## <a name="considerations-and-limitations"></a>Considerazioni e limitazioni

- La visualizzazione di derivazione non è disponibile in Internet Explorer. Per informazioni dettagliate, vedere [Browser supportati per Power BI](../power-bi-browsers.md).

## <a name="next-steps"></a>Passaggi successivi

* [Introduzione ai set di dati in aree di lavoro diverse (anteprima)](../service-datasets-across-workspaces.md)
