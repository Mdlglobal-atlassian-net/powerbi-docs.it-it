---
title: Uso delle entità calcolate in Power BI Premium
description: Informazioni su come usare le entità calcolate in Power BI Premium
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 11/06/2018
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 8131722d0e035f28fcb88827b1a68c2da97959cb
ms.sourcegitcommit: b23fdcc0ceff5acd2e4d52b15b310068236cf8c7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2018
ms.locfileid: "51268093"
---
# <a name="using-computed-entities-on-power-bi-premium-preview"></a>Uso delle entità calcolate in Power BI Premium (anteprima)

È possibile eseguire **calcoli in archivio** quando si usano i **flussi di dati** con una sottoscrizione di Power BI Premium. Ciò consente di eseguire i calcoli sui flussi di dati esistenti e ottenere risultati che consentono di concentrarsi sulla creazione di report e sull'analisi. 

![Entità calcolate in Power BI Premium](media/service-dataflows-computed-entities-premium/computed-entities-premium_00.png)

Per eseguire i **calcoli in archivio**, è prima di tutto necessario creare il flusso di dati e inserire i dati nell'archivio del flusso di dati di Power BI. Dopo aver creato un flusso di dati contenente dati, è possibile creare **entità calcolate**, ovvero le entità che eseguono calcoli in archivio. 

Ci sono due modi per connettere i dati del flusso di dati a Power BI:

* [Usando la creazione self-service di un flusso di dati](service-dataflows-create-use.md)
* Usando un flusso di dati esterno

Le sezioni seguenti descrivono come creare entità calcolate sui dati del flusso di dati.

> [!NOTE]
> La funzionalità dei flussi di dati è disponibile in anteprima ed è soggetta a modifiche e aggiornamenti prima della disponibilità generale.


## <a name="how-to-create-computed-entities"></a>Come creare entità calcolate 

Dopo aver creato un flusso di dati con un elenco di entità, è possibile eseguire calcoli su tali entità.

Nello strumento di creazione del flusso di dati nel servizio Power BI selezionare **Modifica entità**, quindi fare clic con il pulsante destro del mouse sull'entità da usare come base per l'entità calcolata e in cui eseguire i calcoli. Dal menu di scelta rapida scegliere **Riferimento**.

Affinché l'entità possa essere usata come entità calcolata, l'opzione **Abilita caricamento** deve essere selezionata, come illustrato nell'immagine seguente. Fare clic con il pulsante destro del mouse sull'entità per visualizzare il menu di scelta rapida.

![Selezionare Abilita caricamento nel menu di scelta rapida](media/service-dataflows-computed-entities-premium/computed-entities-premium_01.png)

Se si seleziona **Abilita caricamento**, si crea una nuova entità la cui origine è l'entità di riferimento. L'icona cambia per indicare l'entità **calcolata**, come illustrato nell'immagine seguente.

![Entità calcolate in Power BI Premium](media/service-dataflows-computed-entities-premium/computed-entities-premium_00.png)

Qualsiasi trasformazione eseguita su questa entità appena creata verrà eseguita sui dati già presenti nell'archivio del flusso di dati di Power BI. Ciò significa che la query non verrà eseguita sull'origine dati esterna da cui sono stati importati i dati (ad esempio, il database SQL da cui è stato eseguito il pull dei dati), bensì sui dati che si trovano nell'archivio del flusso di dati.

### <a name="example-use-cases"></a>Casi d'uso di esempio
Quale tipo di trasformazioni è possibile eseguire con le entità calcolate? Tutte le trasformazioni che in genere si specificano usando l'interfaccia utente di trasformazione in Power BI o l'editor M sono supportate quando si esegue il calcolo in archivio. 

Considerare l'esempio seguente: si ha un'entità *Account* che contiene i dati non elaborati per tutti i clienti dalla sottoscrizione di Dynamics 365. Si hanno inoltre i dati non elaborati di *ServiceCalls* forniti dal centro assistenza, con dati relativi alle chiamate al supporto tecnico che sono state effettuate dai diversi account in ogni giorno dell'anno.

Si supponga di voler arricchire l'entità *Account* con i dati di *ServiceCalls*. 

Prima di tutto, è necessario aggregare i dati di ServiceCalls per calcolare il numero di chiamate al supporto tecnico per ogni account nell'anno precedente. 

![Esempio di entità calcolata in Power BI Premium](media/service-dataflows-computed-entities-premium/computed-entities-premium_02.png)

È quindi necessario unire l'entità *Account* con l'entità *ServiceCallsAggregated* per calcolare la tabella **Account** arricchita.

![Esempio di entità calcolata in Power BI Premium](media/service-dataflows-computed-entities-premium/computed-entities-premium_03.png)

È quindi possibile visualizzare i risultati, illustrati in *EnrichedAccount* nell'immagine seguente.

![Risultati di un'entità calcolata in Power BI Premium](media/service-dataflows-computed-entities-premium/computed-entities-premium_04.png)

La procedura è completata: la trasformazione viene eseguita sui dati nel flusso di dati che si trova nella sottoscrizione di Power BI Premium e non sui dati di origine.

## <a name="considerations-and-limitations"></a>Considerazioni e limitazioni

È importante notare che se si rimuove l'area di lavoro dalla capacità di Power BI Premium, il flusso di dati associato non verrà più aggiornato. 


## <a name="next-steps"></a>Passaggi successivi

In questo articolo sono stati descritti le entità calcolate e i flussi di dati disponibili nel servizio Power BI. Ecco alcuni altri articoli che potrebbero essere utili.


* [Preparazione dei dati self-service con flussi di dati](service-dataflows-overview.md)
* [Creare e usare flussi di dati in Power BI](service-dataflows-create-use.md)
* [Uso di flussi di dati con origini dati locali (anteprima)](service-dataflows-on-premises-gateways.md)
* [Risorse per sviluppatori per i flussi di dati Power BI (anteprima)](service-dataflows-developer-resources.md)

Per altre informazioni su Power Query e sull'aggiornamento pianificato, è possibile leggere questi articoli:
* [Panoramica delle query in Power BI Desktop](desktop-query-overview.md)
* [Configurazione dell'aggiornamento pianificato](refresh-scheduled-refresh.md)

Per altre informazioni sul modello CDM (Common Data Model), è possibile leggere l'articolo di panoramica:
* [Panoramica del modello CDM (Common Data Model)](https://docs.microsoft.com/powerapps/common-data-model/overview)

