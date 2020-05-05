---
title: Introduzione all'uso delle utilità per i test negli oggetti visivi di Power BI
description: Questo articolo descrive come usare le utilità per i test per semplificare le simulazioni e l'utilizzo di metodi specifici nel testing unità per oggetti visivi di Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/14/2020
ms.openlocfilehash: c50ad894b2e1f5eb838abdd4442f473f8bcbbb10
ms.sourcegitcommit: 1059c6222458f189fb5301dcb689dad2b2c00bc1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/28/2020
ms.locfileid: "82196607"
---
# <a name="power-bi-visuals-test-utils"></a>Utilità per i test degli oggetti visivi di Power BI

Questo articolo illustra come installare, importare e usare le utilità per i test degli oggetti visivi di Power BI. Queste utilità possono essere usate per il testing unità e includono simulazioni e metodi per elementi come visualizzazioni dati, selezioni e schemi di colori.

## <a name="requirements"></a>Requisiti

Per usare questo pacchetto è necessario installare:

* [node.js](https://nodejs.org), versione LTS consigliata
* [npm](https://www.npmjs.com/), versione 3.0.0 o successiva
* Pacchetto [PowerBI-visuals-tools](https://github.com/Microsoft/PowerBI-visuals-tools)

## <a name="installation"></a>Installazione

Per installare le utilità per i test e aggiungere la relativa dipendenza a *package.json*, eseguire il comando seguente dalla directory degli oggetti visivi di Power BI:

```bash
npm install powerbi-visuals-utils-testutils --save
```

Di seguito vengono forniti descrizioni ed esempi sull'API pubblica per le utilità per i test.

## <a name="visualbuilderbase"></a>VisualBuilderBase

Usato da **VisualBuilder** negli unit test con i metodi usati più di frequente `build`, `update` e `updateRenderTimeout`. 

Il metodo `build` restituisce un'istanza creata dell'oggetto visivo.

I metodi `enumerateObjectInstances` e `updateEnumerateObjectInstancesRenderTimeout` sono necessari per controllare le modifiche alle opzioni bucket e di formattazione.

```typescript
abstract class VisualBuilderBase<T extends IVisual> {
    element: JQuery;
    viewport: IViewport;
    visualHost: IVisualHost;
    protected visual: T;
    constructor(width?: number, height?: number, guid?: string, element?: JQuery);
    protected abstract build(options: VisualConstructorOptions): T;
     nit(): void;
    destroy(): void;
    update(dataView: DataView[] | DataView): void;
    updateRenderTimeout(dataViews: DataView[] | DataView, fn: Function, timeout?: number): number;
    updateEnumerateObjectInstancesRenderTimeout(dataViews: DataView[] | DataView, options: EnumerateVisualObjectInstancesOptions, fn: (enumeration: VisualObjectInstance[]) => void, timeout?: number): number;
    updateFlushAllD3Transitions(dataViews: DataView[] | DataView): void;
    updateflushAllD3TransitionsRenderTimeout(dataViews: DataView[] | DataView, fn: Function, timeout?: number): number;
    enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstance[];
}
```

> [!NOTE]
> Per altri esempi, vedere [Creare un generatore dell'istanza dell'oggetto visivo](./unit-tests-introduction.md#create-a-visual-instance-builder) e uno [scenario di utilizzo reale di VisualBuilderBase](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/test/visualBuilder.ts).

## <a name="dataviewbuilder"></a>DataViewBuilder

Usato da **TestDataViewBuilder**, questo modulo fornisce una classe **CategoricalDataViewBuilder** usata nel metodo `createCategoricalDataViewBuilder`. Specifica anche le interfacce e i metodi necessari per usare **DataView** fittizi negli unit test.

* `withValues` aggiunge colonne di serie statiche e `withGroupedValues` aggiunge colonne di serie dinamiche

  Non applicare serie sia statiche che dinamiche a un oggetto visivo **DataViewCategorical**. È possibile usarle entrambe solo nella query **DataViewCategorical**, dove **DataViewTransform** dovrebbe suddividerle in oggetti visivi **DataViewCategorical** distinti.

* `build` restituisce l'oggetto DataView con i metadati e DataViewCategorical

  `build` restituisce **Undefined** se la combinazione di parametri non è valida, ad esempio se include serie sia dinamiche che statiche durante la compilazione dell'oggetto visivo **DataView**.

```typescript
class CategoricalDataViewBuilder implements IDataViewBuilderCategorical {
    withCategory(options: DataViewBuilderCategoryColumnOptions): IDataViewBuilderCategorical;
    withCategories(categories: DataViewCategoryColumn[]): IDataViewBuilderCategorical;
    withValues(options: DataViewBuilderValuesOptions): IDataViewBuilderCategorical;
    withGroupedValues(options: DataViewBuilderGroupedValuesOptions): IDataViewBuilderCategorical;
    build(): DataView;
}

function createCategoricalDataViewBuilder(): IDataViewBuilderCategorical;
```

## <a name="testdataviewbuilder"></a>TestDataViewBuilder

Usato per la creazione di **VisualData** negli unit test. Quando si inseriscono dati in bucket di campi dati, Power BI produce un oggetto **DataView** categorico basato su tali dati. **TestDataViewBuilder** consente di simulare la creazione dell'oggetto **DataView** categorico.

```typescript
abstract class TestDataViewBuilder {
    static DataViewName: string;
    private aggregateFunction;
    static setDefaultQueryName(source: DataViewMetadataColumn): DataViewMetadataColumn;
    static getDataViewBuilderColumnIdentitySources(options: TestDataViewBuilderColumnOptions[] | TestDataViewBuilderColumnOptions): DataViewBuilderColumnIdentitySource[];
    static getValuesTable(categories?: DataViewCategoryColumn[], values?: DataViewValueColumn[]): any[][];
    static createDataViewBuilderColumnOptions(categoriesColumns: (TestDataViewBuilderCategoryColumnOptions | TestDataViewBuilderCategoryColumnOptions[])[], valuesColumns: (DataViewBuilderValuesColumnOptions | DataViewBuilderValuesColumnOptions[])[], filter?: (options: TestDataViewBuilderColumnOptions) => boolean, customizeColumns?: CustomizeColumnFn): DataViewBuilderAllColumnOptions;
    static setUpDataViewBuilderColumnOptions(options: DataViewBuilderAllColumnOptions, aggregateFunction: (array: number[]) => number): DataViewBuilderAllColumnOptions;
    static setUpDataView(dataView: DataView, options: DataViewBuilderAllColumnOptions): DataView;
    protected createCategoricalDataViewBuilder(categoriesColumns: (TestDataViewBuilderCategoryColumnOptions | TestDataViewBuilderCategoryColumnOptions[])[], valuesColumns: (DataViewBuilderValuesColumnOptions | DataViewBuilderValuesColumnOptions[])[], columnNames: string[], customizeColumns?: CustomizeColumnFn): IDataViewBuilderCategorical;
    abstract getDataView(columnNames?: string[]): DataView;
}
```

  Di seguito sono elencate le interfacce usate più di frequente per creare un `testDataView`:

  ```typescript
  interface TestDataViewBuilderColumnOptions extends DataViewBuilderColumnOptions {
      values: any[];
  }

  interface TestDataViewBuilderCategoryColumnOptions extends TestDataViewBuilderColumnOptions {
      objects?: DataViewObjects[];
      isGroup?: boolean;
  }

  interface DataViewBuilderColumnOptions {
      source: DataViewMetadataColumn;
  }

  interface DataViewBuilderSeriesData {
      values: PrimitiveValue[];
      highlights?: PrimitiveValue[];
      /** Client-computed maximum value for a column. */
      maxLocal?: any;
      /** Client-computed maximum value for a column. */
      minLocal?: any;
  }

  interface DataViewBuilderColumnIdentitySource {
      fields: any[];
      identities?: CustomVisualOpaqueIdentity[];
  }
  ```
   
> [!NOTE]
> Per altri esempi, vedere [Come aggiungere dati statici per gli unit test](./unit-tests-introduction.md#how-to-add-static-data-for-unit-tests) e uno [scenario di utilizzo reale di TestDataViewBuilder](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/test/visualData.ts).

## <a name="mocks"></a>Simulazioni

### <a name="mockivisualhost"></a>MockIVisualHost

Implementa **IVisualHost** per testare gli oggetti visivi di Power BI senza dipendenze esterne, come il framework di Power BI.

Alcuni metodi utili sono `createSelectionIdBuilder`, `createSelectionManager`, `createLocalizationManager` e le proprietà Get.

```typescript
import powerbi from "powerbi-visuals-api";

import VisualObjectInstancesToPersist = powerbi.VisualObjectInstancesToPersist;
import ISelectionIdBuilder = powerbi.visuals.ISelectionIdBuilder;
import ISelectionManager = powerbi.extensibility.ISelectionManager;
import IColorPalette = powerbi.extensibility.IColorPalette;
import IVisualEventService = powerbi.extensibility.IVisualEventService;
import ITooltipService = powerbi.extensibility.ITooltipService;
import IVisualHost = powerbi.extensibility.visual.IVisualHost;

class MockIVisualHost implements IVisualHost {
      constructor(
          colorPalette?: IColorPalette,
          selectionManager?: ISelectionManager,
          tooltipServiceInstance?: ITooltipService,
          localeInstance?: MockILocale,
          allowInteractionsInstance?: MockIAllowInteractions,
          localizationManager?: powerbi.extensibility.ILocalizationManager,
          telemetryService?: powerbi.extensibility.ITelemetryService,
          authService?: powerbi.extensibility.IAuthenticationService,
          storageService?: ILocalVisualStorageService,
          eventService?: IVisualEventService);
      createSelectionIdBuilder(): ISelectionIdBuilder;
      createSelectionManager(): ISelectionManager;
      createLocalizationManager(): ILocalizationManager;
      colorPalette: IColorPalette;
      locale: string;
      telemetry: ITelemetryService;
      tooltipService: ITooltipService;
      allowInteractios: boolean;
      storageService: ILocalVisualStorageService;
      eventService: IVisualEventService;
      persistProperties(changes: VisualObjectInstancesToPersist): void;
}
```
   
- `createVisualHost` crea e restituisce un'istanza di **IVisualHost**, ossia **MockIVisualHost**
  ```typescript
  function createVisualHost(locale?: Object, allowInteractions?: boolean, colors?: IColorInfo[], isEnabled?: boolean, displayNames?: any, token?: string): IVisualHost;
  ```

    Esempio
    ```typescript
    import { createVisualHost } from "powerbi-visuals-utils-testutils"

    let host: IVisualHost = createVisualHost();
    ```

> [!IMPORTANT]
> **MockIVisualHost** è un'implementazione fittizia di **IVisualHost** e deve essere usata solo con gli unit test.

### <a name="mockicolorpalette"></a>MockIColorPalette

Implementa **IColorPalette** per testare gli oggetti visivi di Power BI senza dipendenze esterne, come il framework di Power BI.

**MockIColorPalette** fornisce proprietà utili per controllare lo schema di colori o la modalità a contrasto elevato negli unit test.

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import IColorPalette = powerbi.extensibility.ISandboxExtendedColorPalette;
  import IColorInfo = powerbi.IColorInfo;

  class MockIColorPalette implements IColorPalette {
      constructor(colors?: IColorInfo[]);
      getColor(key: string): IColorInfo;
      reset(): IColorPalette;
      isHighContrastMode: boolean;
      foreground: {value: string};
      foregroundLight: {value: string};
      ...
      background: {value: string};
      backgroundLight: {value: string};
      ...
      shapeStroke: {value: string};
  }
  ```
  - `createColorPalette` crea e restituisce un'istanza di **IColorPalette**, ossia **MockIColorPalette**
    ```typescript
    function createColorPalette(colors?: IColorInfo[]): IColorPalette;
    ```

    Esempio
    ```typescript
    import { createColorPalette } from "powerbi-visuals-utils-testutils"

    let colorPalette: IColorPalette = createColorPalette();
    ```
    
> [!IMPORTANT]
> **MockIColorPalette** è un'implementazione fittizia di **IColorPalette** e deve essere usata solo con gli unit test.

### <a name="mockiselectionid"></a>MockISelectionId

Implementa **ISelectionId** per testare gli oggetti visivi di Power BI senza dipendenze esterne, come il framework di Power BI.

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import Selector = powerbi.data.Selector;
  import ISelectionId = powerbi.visuals.ISelectionId;

  class MockISelectionId implements ISelectionId {
      constructor(key: string);
      equals(other: ISelectionId): boolean;
      includes(other: ISelectionId, ignoreHighlight?: boolean): boolean;
      getKey(): string;
      getSelector(): Selector;
      getSelectorsByColumn(): Selector;
      hasIdentity(): boolean;
  }
  ```

  - `createSelectionId` crea e restituisce un'istanza di **ISelectionId**, ossia **MockISelectionId**
    ```typescript
    function createSelectionId(key?: string): ISelectionId;
    ```

    Esempio
    ```typescript
    import { createColorPalette } from "powerbi-visuals-utils-testutils"

    let selectionId: ISelectionId = createSelectionId();
    ```
    
> [!NOTE]
> **MockISelectionId** è un'implementazione fittizia di **ISelectionId** e deve essere usata solo con gli unit test.

### <a name="mockiselectionidbuilder"></a>MockISelectionIdBuilder

Implementa **ISelectionIdBuilder** per testare gli oggetti visivi di Power BI senza dipendenze esterne, come il framework di Power BI. 

  ```typescript
  import DataViewCategoryColumn = powerbi.DataViewCategoryColumn;
  import DataViewValueColumn = powerbi.DataViewValueColumn;
  import DataViewValueColumnGroup = powerbi.DataViewValueColumnGroup;
  import DataViewValueColumns = powerbi.DataViewValueColumns;
  import ISelectionIdBuilder = powerbi.visuals.ISelectionIdBuilder;
  import ISelectionId = powerbi.visuals.ISelectionId;

  class MockISelectionIdBuilder implements ISelectionIdBuilder {
      withCategory(categoryColumn: DataViewCategoryColumn, index: number): this;
      withSeries(seriesColumn: DataViewValueColumns, valueColumn: DataViewValueColumn | DataViewValueColumnGroup): this;
      withMeasure(measureId: string): this;
      createSelectionId(): ISelectionId;
      withMatrixNode(matrixNode: DataViewMatrixNode, levels: DataViewHierarchyLevel[]): this;
      withTable(table: DataViewTable, rowIndex: number): this;
  }
  ```

  - `createSelectionIdBuilder` crea e restituisce un'istanza di **ISelectionIdBuilder**, ossia **MockISelectionIdBuilder**
    ```typescript
    function createSelectionIdBuilder(): ISelectionIdBuilder;
    ```

    Esempio
    ```typescript
    import { selectionIdBuilder } from "powerbi-visuals-utils-testutils";

    let selectionIdBuilder = createSelectionIdBuilder();
    ```

> [!NOTE]
> **MockISelectionIdBuilder** è un'implementazione fittizia di **ISelectionIdBuilder** e deve essere usata solo con gli unit test.

### <a name="mockiselectionmanager"></a>MockISelectionManager

Implementa **ISelectionManager** per testare gli oggetti visivi di Power BI senza dipendenze esterne, come il framework di Power BI. 

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import IPromise = powerbi.IPromise;
  import ISelectionId = powerbi.visuals.ISelectionId;
  import ISelectionManager = powerbi.extensibility.ISelectionManager;

  class MockISelectionManager implements ISelectionManager {
      select(selectionId: ISelectionId | ISelectionId[], multiSelect?: boolean): IPromise<ISelectionId[]>;
      hasSelection(): boolean;
      clear(): IPromise<{}>;
      getSelectionIds(): ISelectionId[];
      containsSelection(id: ISelectionId): boolean;
      showContextMenu(selectionId: ISelectionId, position: IPoint): IPromise<{}>;
      registerOnSelectCallback(callback: (ids: ISelectionId[]) => void): void;
      simutateSelection(selections: ISelectionId[]): void;
  }
  ```

  - `createSelectionManager` crea e restituisce un'istanza di **ISelectionManager**, ossia **MockISelectionManager**
    ```typescript
    function createSelectionManager(): ISelectionManager
    ```

    Esempio
    ```typescript
    import { createSelectionManager } from "powerbi-visuals-utils-testutils";

    let selectionManager: ISelectionManager = createSelectionManager();
    ```

> [!NOTE]
> **MockISelectionManager** è un'implementazione fittizia di **ISelectionManager** e deve essere usata solo con gli unit test.

### <a name="mockilocale"></a>MockILocale

  Seleziona le impostazioni locali e le modifica in base alle esigenze durante il processo di testing unità.
  ```typescript
  class MockILocale {
      constructor(locales?: Object): void; // Default locales are en-US and ru-RU 
      locale(key: string): void;// setter property
      locale(): string; // getter property
  }
  ```
  - `createLocale` crea e restituisce un'istanza di **MockILocale**
    ```typescript
    funciton createLocale(locales?: Object): MockILocale;
    ```

### <a name="mockitooltipservice"></a><a id="mockitooltipservice"></a> MockITooltipService
Simula `TooltipService` e lo chiama in base alle esigenze durante il processo di testing unità.
  ```typescript
  class MockITooltipService implements ITooltipService {
      constructor(isEnabled: boolean = true);
      enabled(): boolean;
      show(options: TooltipShowOptions): void;
      move(options: TooltipMoveOptions): void;
      hide(options: TooltipHideOptions): void;
  }
  ```
  - `createTooltipService` crea e restituisce un'istanza di **MockITooltipService**
    ```typescript
    function createTooltipService(isEnabled?: boolean): ITooltipService;
    ```

### <a name="mockiallowinteractions"></a>MockIAllowInteractions

```typescript
export class MockIAllowInteractions {
    constructor(public isEnabled?: boolean); // false by default
}
```
  - `createAllowInteractions` crea e restituisce un'istanza di **MockIAllowInteractions**
    ```typescript
    function createAllowInteractions(isEnabled?: boolean): MockIAllowInteractions;
    ```

### <a name="mockilocalizationmanager"></a><a id="mockilocalizationmanager"></a> MockILocalizationManager
Fornisce le funzionalità di base di **LocalizationManager** che sono necessarie per il testing unità.
```typescript
class MockILocalizationManager implements ILocalizationManager {
    constructor(displayNames: {[key: string]: string});
    getDisplayName(key: string): string; // returns default or setted displayNames for localized elements
}
```
  - `createLocalizationManager` crea e restituisce un'istanza di **ILocalizationManager**, ossia **MockILocalizationManager**
    ```typescript
    function createLocalizationManager(displayNames?: any): ILocalizationManager;
    ```

    Esempio
    ```typescript
    import { createLocalizationManager } from "powerbi-visuals-utils-testutils";
    let localizationManagerMock: ILocalizationManager = createLocalizationManager();
    ```

### <a name="mockitelemetryservice"></a>MockITelemetryService
Simula l'utilizzo di **TelemetryService**.
```typescript
class MockITelemetryService implements ITelemetryService {
    instanceId: string;
    trace(veType: powerbi.VisualEventType, payload?: string) {
    }
}
```
  Creazione di `MockITelemetryService`
    ```typescript
    function createTelemetryService(): ITelemetryService;
    ```
### <a name="mockiauthenticationservice"></a>MockIAuthenticationService
Simula il funzionamento di **AuthenticationService** fornendo un token AAD fittizio.
```typescript
class MockIAuthenticationService implements IAuthenticationService  {
    constructor(token: string);
    getAADToken(visualId?: string): powerbi.IPromise<string>
}
```
  - `createAuthenticationService` crea e restituisce un'istanza di **IAuthenticationService**, ossia **MockIAuthenticationService**
    ```typescript
    function createAuthenticationService(token?: string): IAuthenticationService;
    ```

### <a name="mockistorageservice"></a>MockIStorageService
Consente di usare **ILocalVisualStorageService** con lo stesso comportamento di **LocalStorage**.
```typescript
class MockIStorageService implements ILocalVisualStorageService {
  get(key: string): IPromise<string>;
  set(key: string, data: string): IPromise<number>;
  remove(key: string): void;
}
```
  - `createStorageService` crea e restituisce un'istanza di **ILocalVisualStorageService**, ossia **MockIStorageService**
    ```typescript
    function createStorageService(): ILocalVisualStorageService;
    ```

### <a name="mockieventservice"></a>MockIEventService
```typescript
import powerbi from "powerbi-visuals-api";
import IVisualEventService = powerbi.extensibility.IVisualEventService;
import VisualUpdateOptions = powerbi.extensibility.VisualUpdateOptions;

class MockIEventService implements IVisualEventService {
      renderingStarted(options: VisualUpdateOptions): void;
      renderingFinished(options: VisualUpdateOptions): void;
      renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```
  - `createEventService` crea e restituisce un'istanza di **IVisualEventService**, ossia **MockIEventService**
    ```typescript
    function createEventService(): IVisualEventService;
    ```

## <a name="utils"></a>Utilità

Le utilità includono metodi helper per il testing unità degli oggetti visivi di Power BI, tra cui gli helper relativi a colori, numeri ed eventi.

- `renderTimeout` restituisce il timeout
  ```typescript
  function renderTimeout(fn: Function, timeout: number = DefaultWaitForRender): number
  ```

- `testDom` consente di impostare la fixture negli unit test
  ```typescript
  function testDom(height: number | string, width: number | string): JQuery
  ```
  Esempio
  ```typescript
  import { testDom }  from "powerbi-visuals-utils-testutils";
  describe("testDom", () => {
      it("should return an element", () => {
          let element: JQuery = testDom(500, 500);
          expect(element.get(0)).toBeDefined();
      });
  });
  ```

### <a name="color-related-helper-methods"></a>Metodi helper relativi ai colori

- `getSolidColorStructuralObject`
  ```typescript
  function getSolidColorStructuralObject(color: string): any
  ```
  Restituisce la struttura seguente:

  ```json
  { solid: { color: color } }
  ```

- `assertColorsMatch` confronta gli oggetti **RgbColor** analizzati dalle stringhe di input
  ```typescript
  function assertColorsMatch(actual: string, expected: string, invert: boolean = false): boolean
  ```

- `parseColorString` analizza il colore dalla stringa di input e lo restituisce nell'interfaccia **RgbColor** specificata
  ```typescript
  function parseColorString(color: string): RgbColor
  ```

### <a name="number-related-helper-methods"></a>Metodi helper relativi ai numeri

- `getRandomNumbers` genera un numero casuale usando i valori minimo e massimo. È possibile specificare `exceptionList` e fornire una funzione per cambiare il risultato.
  ```typescript
  function getRandomNumber(
      min: number,
      max: number,
      exceptionList?: number[],
      changeResult: (value: any) => number = x => x): number
  ```

- `getRandomNumbers` fornisce una matrice di numeri casuali generati dal metodo `getRandomNumber` con i valori minimo e massimo specificati
  ```typescript
  function getRandomNumbers(count: number, min: number = 0, max: number = 1): number[]
  ```

### <a name="event-related-helper-methods"></a>Metodi helper relativi agli eventi
I metodi seguenti sono scritti per la simulazione di eventi di pagine Web negli unit test.

- `clickElement` simula un clic sull'elemento specificato
  ```typescript
  function clickElement(element: JQuery, ctrlKey: boolean = false): void
  ```

- `createTouch` restituisce un oggetto **Touch** per simulare un evento di tocco
  ```typescript
  function createTouch(x: number, y: number, element: JQuery, id: number = 0): Touch
  ```

- `createTouchesList` restituisce un elenco di eventi **Touch** simulati
  ```typescript
  function createTouchesList(touches: Touch[]): TouchList
  ```

- `createContextMenuEvent` restituisce **MouseEvent**
  ```typescript
  function createContextMenuEvent(x: number, y: number): MouseEvent
  ```

- `createMouseEvent` crea e restituisce **MouseEvent**
  ```typescript
  function createMouseEvent(
      mouseEventType: MouseEventType,
      eventType: ClickEventType,
      x: number,
      y: number,
      button: number = 0): MouseEvent
  ```

- `createTouchEndEvent`
  ```typescript
  function createTouchEndEvent(touchList?: TouchList): UIEvent
  ```

- `createTouchMoveEvent`
  ```typescript
  function createTouchMoveEvent(touchList?: TouchList): UIEvent
  ```

- `createTouchStartEvent`
  ```typescript
  function createTouchStartEvent(touchList?: TouchList): UIEvent
  ```

### <a name="d3-event-related-helper-methods"></a>Metodi helper relativi agli eventi D3

I metodi seguenti vengono usati per simulare gli eventi D3 negli unit test.

- `flushAllD3Transitions` impone il completamento di tutte le transizioni D3

  ```typescript
  function flushAllD3Transitions()
  ```
  
  > [!NOTE]
  > Normalmente le transizioni senza ritardo vengono eseguite dopo un ritardo istantaneo (meno di 10 ms), ma ciò può causare un breve sfarfallio se il browser esegue il rendering della pagina due volte, una volta alla fine del primo ciclo di eventi, quindi di nuovo subito dopo il primo callback del timer.
  >
  > Questi sfarfallii sono più evidenti in Internet Explorer e con un numero elevato di webview e non sono consigliati per iOS.
  > 
  > Scaricando la coda del timer alla fine del primo ciclo di eventi è possibile eseguire immediatamente eventuali transizioni senza ritardo ed evitare lo sfarfallio.

Sono inclusi anche i metodi seguenti:
```typescript
function d3Click(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseUp(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseDown(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseOver(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseMove(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseOut(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3KeyEvent(element: JQuery, typeArg: string, keyArg: string, keyCode: number): void
function d3TouchStart(element: JQuery, touchList?: TouchList): void
function d3TouchMove(element: JQuery, touchList?: TouchList): void
function d3TouchEnd(element: JQuery, touchList?: TouchList): void
function d3ContextMenu(element: JQuery, x: number, y: number): void
```

### <a name="helper-interfaces"></a>Interfacce helper
L'interfaccia e le enumerazioni seguenti sono usate nella funzione helper.

```typescript
interface RgbColor {
    R: number;
    G: number;
    B: number;
    A?: number; 
}

enum ClickEventType {
    Default = 0,
    CtrlKey = 1,
    AltKey = 2,
    ShiftKey = 4,
    MetaKey = 8,
}

enum MouseEventType {
    click,
    mousedown,
    mouseup,
    mouseover,
    mousemove,
    mouseout,
}
```

## <a name="next-steps"></a>Passaggi successivi

Per scrivere unit test per oggetti visivi di Power BI basati su webpack e unit test con `karma` e `jasmine`, vedere ad esempio [Esercitazione: Aggiungere unit test per progetti con oggetti visivi di Power BI](./unit-tests-introduction.md).
