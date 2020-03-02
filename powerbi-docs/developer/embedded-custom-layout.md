---
title: Layout personalizzati con il contenuto incorporato di Power BI
description: Informazioni sui layout personalizzati durante l'incorporamento del contenuto di Power BI nell'applicazione.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 12/19/2017
ms.openlocfilehash: c9827970600b4a4b84e422a3761b5b9a349c9e51
ms.sourcegitcommit: 032a77f2367ca937f45e7e751997d7b7d0e89ee2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2020
ms.locfileid: "77609716"
---
# <a name="custom-layouts"></a>Layout personalizzati

Usare un layout personalizzato per incorporare un report con un layout diverso rispetto a quello del report originale. La definizione di un nuovo layout può essere costituita dalla definizione delle dimensioni della pagina, dal controllo delle dimensioni degli oggetti visivi o dalla definizione di posizione o visibilità.

Per definire un layout personalizzato, specificare un oggetto layout personalizzato e passarlo all'oggetto impostazioni nella configurazione di incorporamento. Inoltre, impostare LayoutType su Custom. Per altre informazioni, vedere [Embed Configuration Details](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details) (Dettagli sulla configurazione di incorporamento).

```javascript
var embedConfig = {
    ...
    settings: {
            layoutType: models.LayoutType.Custom,
            customLayout: {...}
    }
};
```

## <a name="object-definition"></a>Definizione dell'oggetto

```javascript
interface ICustomLayout {
  pageSize?: IPageSize;
  displayOption?: DisplayOption;
  pagesLayout?: PagesLayout;
}

enum PageSizeType {
  Widescreen,
  Standard,
  Letter,
  Custom
}
interface IPageSize {
  type: PageSizeType;
}
interface ICustomPageSize extends IPageSize {
  width?: number;
  height?: number;
}

enum DisplayOption {
  FitToPage,
  FitToWidth,
  ActualSize
}
```

- `pageSize`: usare le dimensioni pagina per controllare le dimensioni dell'area di disegno, ovvero l'area vuota del report.
- `displayOptions`: i valori possibili sono: FitToWidth, FitToPage o ActualSize. Controlla come ridimensionare l'area di disegno per adattarla all'oggetto IFrame.
- `pagesLayout`: controlla il layout per ogni oggetto visivo. Per altre informazioni, vedere PagesLayout.

## <a name="pages-layout"></a>Layout delle pagine

La definizione di un oggetto layout delle pagine consiste nel definire un layout per ogni pagina e, per ogni pagina, definire un layout per ogni oggetto visivo.
L'oggetto PageLayout è facoltativo. Se non si definisce il layout per una pagina, verrà applicato il layout predefinito (salvato nel report).

L'oggetto pagesLayout è un mapping da un nome di pagina a un oggetto PageLayout. Definizione:

```javascript
type PagesLayout = { [key: string]: IPageLayout; };
```

PageLayout contiene una mappa di layout visivo, che esegue il mapping di ogni nome di oggetto visivo a un oggetto di layout visivo:

```javascript
interface IPageLayout {
  visualsLayout: { [key: string]: IVisualLayout; };
}
```

## <a name="visual-layout"></a>Layout visivo

Per definire un layout visivo, passare una nuova posizione, nuove dimensioni e un nuovo stato di visibilità.

```javascript
interface IVisualLayout {
  x?: number;
  y?: number;
  z?: number;
  width?: number;
  height?: number;
  displayState?: IVisualContainerDisplayState;
}

interface IVisualContainerDisplayState {
  mode: VisualContainerDisplayMode;
}

enum VisualContainerDisplayMode {
  Visible,
  Hidden
}
```

- `x,y,z`: definisce la nuova posizione dell'oggetto visivo.
- `width`, height: definisce le nuove dimensioni dell'oggetto visivo.
- `displayState`: definisce la visibilità dell'oggetto visivo.

## <a name="update-layout"></a>Aggiornare il layout

Quando il report è caricato, è possibile aggiornare il layout del report in qualsiasi momento con il metodo updateSettings. Vedere [Impostazioni di aggiornamento](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Update-Settings).

## <a name="code-example"></a>Esempio di codice

```javascript
// Get models. models contains enums that can be used.
var models = window['powerbi-client'].models;

var embedConfiguration = {
    type: 'report',
    id: '5dac7a4a-4452-46b3-99f6-a25915e0fe55',
    embedUrl: 'https://app.powerbi.com/reportEmbed',
    tokenType: models.TokenType.Embed,
    accessToken: 'H4...rf',
    settings: {
            layoutType: models.LayoutType.Custom,
            customLayout: {
                pageSize: {
                    type: models.PageSizeType.Custom,
                    width: 1600,
                    height: 1200
                }
            },
            displayOption: models.DisplayOption.ActualSize,
            pagesLayout: {
                "ReportSection1" : {
                    visualsLayout: {
                        "VisualContainer1": {
                            x: 1,
                            y: 1,
                            z: 1,
                            width: 400,
                            height: 300,
                            displayState: {
                                mode: models.VisualContainerDisplayMode.Visible
                            }
                        },
                        "VisualContainer2": {
                            displayState: {
                                mode: models.VisualContainerDisplayMode.Hidden
                            }
                        },
                    }
                }
            }
        }
    }
};

// Get a reference to the embedded report HTML element
var embedContainer = document.getElementById('embedContainer');

// Embed the report and display it within the div container.
var report = powerbi.embed(embedContainer, embedConfiguration);
```

## <a name="see-also"></a>Vedere anche

[Incorporare i dashboard, i report e i riquadri di Power BI](embedding-content.md)   
[Inviare una domanda alla community di Power BI](https://community.powerbi.com/)
