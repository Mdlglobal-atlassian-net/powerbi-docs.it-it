---
title: API per gli oggetti visivi
description: Questo articolo descrive come usare l'API IVisual per gli oggetti visivi di Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/19/2020
ms.openlocfilehash: 6ec30fdd4812427ae855ff9a167d946d2a415c28
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83302967"
---
# <a name="visual-api"></a>API per gli oggetti visivi
Tutti gli oggetti visivi iniziano con una classe che implementa l'interfaccia `IVisual`. È possibile assegnare alla classe qualsiasi nome purché la classe che implementa l'interfaccia `IVisual` sia esattamente una sola.

> [!NOTE]
> Il nome della classe per gli oggetti visivi deve corrispondere a quello definito nel file *pbiviz.json*.

Vedere la classe per gli oggetti visivi di esempio con i metodi da implementare seguenti:

* `constructor`, costruttore standard per l'inizializzazione dello stato dell'oggetto visivo
* `update`, per l'aggiornamento dei dati dell'oggetto visivo
* `enumerateObjectInstances`, per restituire gli oggetti necessari a popolare il riquadro delle proprietà (opzioni di formattazione) in cui è possibile modificarli in base alle esigenze
* `destroy`, distruttore standard per la pulizia

```typescript
class MyVisual implements IVisual {
    
    constructor(options: VisualConstructorOptions) {
        //one time setup code goes here (called once)
    }
    
    public update(options: VisualUpdateOptions): void {
        //code to update your visual goes here (called on all view or data changes)
    }

    public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
        //returns objects to populate the property pane (called for each object defined in capabilities)
    }
    
    public destroy(): void {
        //one time cleanup code goes here (called once)
    }
}
```

## <a name="constructor"></a>constructor

Il costruttore della classe per gli oggetti visivi viene chiamato quando viene creata un'istanza dell'oggetto visivo. Può essere usato per qualsiasi operazione di configurazione necessaria per l'oggetto visivo.

```typescript
constructor(options: VisualConstructorOptions)
```

**VisualConstructorOptions**

* `element: HTMLElement`, riferimento all'elemento DOM che conterrà l'oggetto visivo
* `host: IVisualHost`, raccolta di proprietà e servizi che possono essere usati per interagire con l'host degli oggetti visivi (Power BI)

   `IVisualHost` contiene i servizi seguenti:

   ```typescript
   export interface IVisualHost extends extensibility.IVisualHost {
       createSelectionIdBuilder: () => visuals.ISelectionIdBuilder;
       : () => ISelectionManager;
       colorPalette: ISandboxExtendedColorPalette;
       persistProperties: (changes: VisualObjectInstancesToPersist) => void;
       applyJsonFilter: (filter: IFilter[] | IFilter, objectName: string, propertyName: string, action: FilterAction) => void;
       tooltipService: ITooltipService;
       telemetry: ITelemetryService;
       authenticationService: IAuthenticationService;
       locale: string;
       allowInteractions: boolean;
       launchUrl: (url: string) => void;
       fetchMoreData: () => boolean;
       instanceId: string;
       refreshHostData: () => void;
       createLocalizationManager: () => ILocalizationManager;
       storageService: ILocalVisualStorageService;
       eventService: IVisualEventService;
       switchFocusModeState: (on: boolean) => void;
   }
   ```
   * `createSelectionIdBuilder`, che genera e archivia i metadati per gli elementi selezionabili nell'oggetto visivo
   * `createSelectionManager`, che crea il bridge di comunicazione usato per notificare all'host dell'oggetto visivo le modifiche apportate allo stato di selezione. Vedere [API di selezione](./selection-api.md).
   * `createLocalizationManager`, che genera uno strumento di gestione per facilitare la [localizzazione](./localization.md)
   * `allowInteractions: boolean`, flag booleano che indica se l'oggetto visivo deve essere interattivo o meno
   * `applyJsonFilter`, che applica tipi di filtro specifici. Vedere [API di filtro](./filter-api.md)
   * `persistProperties`, che consente agli utenti di rendere persistente le proprietà e salvarle insieme alla definizione dell'oggetto visivo, in modo che siano disponibili al caricamento successivo
   * `eventService`, che restituisce un [servizio eventi](./event-service.md) a supporto degli eventi di **rendering**
   * `storageService`, che restituisce un servizio che consente di usare una [risorsa di archiviazione locale](./local-storage.md) nell'oggetto visivo
   * `authenticationService`, che genera un servizio per semplificare l'autenticazione utente
   * `tooltipService`, che restituisce un [servizio descrizioni comandi](./add-tooltips.md) per consentire l'uso di descrizioni comandi nell'oggetto visivo
   * `launchUrl`, che consente di [avviare un URL](./launch-url.md) nella scheda successiva
   * `locale`, che restituisce una stringa di impostazioni locali. Vedere [Localizzazione](./localization.md)
   * `instanceId`, che restituisce una stringa per identificare l'istanza dell'oggetto visivo corrente
   * `colorPalette`, che restituisce la tavolozza dei colori necessaria per applicare colori ai dati
   * `fetchMoreData`, che supporta l'uso di una quantità di dati maggiore rispetto al limite standard (1000 righe)
   * `switchFocusModeState`, che consente di modificare lo stato della modalità messa a fuoco

## <a name="update"></a>update

Tutti gli oggetti visivi devono implementare un metodo di aggiornamento pubblico che venga chiamato ogni volta che viene apportata una modifica all'ambiente dati o host.

```typescript
public update(options: VisualUpdateOptions): void
```

**VisualUpdateOptions**

* `viewport: IViewport`, dimensioni del riquadro di visualizzazione in cui deve essere eseguito il rendering dell'oggetto visivo
* `dataViews: DataView[]`, oggetto dataview che contiene tutti i dati necessari per il rendering dell'oggetto visivo (l'oggetto visivo usa in genere la proprietà della categoria in DataView)
* `type: VisualUpdateType`, flag per indicare il tipo o i tipi di questo aggiornamento (**Data** | **Resize** | **ViewMode** | **Style** | **ResizeEnd**)
* `viewMode: ViewMode`, flag per indicare la modalità di visualizzazione dell'oggetto visivo (**View** | **Edit** | **InFocusEdit**)
* `editMode: EditMode`, flag per indicare la modalità di modifica dell'oggetto visivo (**Default** | **Advanced**) (se l'oggetto visivo supporta **AdvancedEditMode**, deve eseguire il rendering dei controlli dell'interfaccia utente avanzati solo quando **editMode** è impostato su **Advanced**. Vedere [AdvancedEditMode](./advanced-edit-mode.md))
* `operationKind?: VisualDataChangeOperationKind`, flag per indicare il tipo di modifica dei dati (**Create** | **Append**)
* `jsonFilters?: IFilter[]`, raccolta di filtri json applicati
* `isInFocus?: boolean`, flag per indicare se l'oggetto visivo è in modalità messa a fuoco o meno
    
## <a name="enumerateobjectinstances-optional"></a>enumerateObjectInstances `optional`

Questo metodo viene chiamato per ogni oggetto elencato nelle funzionalità. Quando si usano le opzioni (attualmente solo il nome), viene restituito un `VisualObjectInstanceEnumeration` con informazioni su come visualizzare questa proprietà.

```typescript
enumerateObjectInstances(options:EnumerateVisualObjectInstancesOptions):VisualObjectInstanceEnumeration
```

**EnumerateVisualObjectInstancesOptions**

* `objectName: string`, nome dell'oggetto

## <a name="destroy-optional"></a>destroy `optional`

La funzione destroy viene chiamata quando l'oggetto visivo viene scaricato e può essere usata per attività di pulizia, ad esempio la rimozione di listener di eventi.

``` typescript
public destroy(): void
```

> [!Note]
> Power BI in genere non chiama `destroy` perché è più veloce rimuovere l'intero IFrame che contiene l'oggetto visivo.
