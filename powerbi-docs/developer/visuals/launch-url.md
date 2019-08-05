---
title: URL di avvio
description: Gli oggetti visivi di Power BI possono aprire un URL in una nuova scheda
author: Guy-Moses
ms.author: guymos
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 1a7002c3b45f341c0cbc0db683bc4f8a113e21f9
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424862"
---
# <a name="launch-url"></a>URL di avvio

L'URL di avvio permette di aprire una nuova scheda o finestra del browser, delegando l'effettiva operazione a Power BI.

## <a name="sample"></a>Esempio

```typescript
   this.host.launchUrl('https://powerbi.microsoft.com');
```

## <a name="usage"></a>Usage

Usare la chiamata API `host.launchUrl()`, passando l'URL di destinazione come argomento stringa:

```typescript
this.host.launchUrl('http://some.link.net');
```

## <a name="restrictions"></a>Restrizioni

* Usare solo i percorsi assoluti, non quelli relativi. `http://some.link.net/subfolder/page.html` è corretto, mentre `/page.html` non verrà aperto.
* Attualmente sono supportati solo i protocolli `http` e `https`. Evitare `ftp`, `mailto` e così via.

## <a name="best-practices"></a>Procedure consigliate

1. Per la maggior parte dei casi, è preferibile aprire un collegamento solo come risposta a un'azione esplicita dell'utente. Spiegare chiaramente all'utente che facendo clic sul collegamento o sul pulsante verrà aperta una nuova scheda. L'attivazione di una chiamata `launchUrl()` senza un'azione da parte dell'utente o come effetto collaterale di un'azione diversa può causare confusione o frustrazione nell'utente.
2. Se il collegamento non è essenziale per il corretto funzionamento dell'oggetto visivo, è consigliabile fornire all'autore del report un modo per disabilitare e nascondere il collegamento. Questo è particolarmente importante per i casi d'uso speciali di Power BI, ad esempio l'incorporamento di un report in un'applicazione di terze parti o la sua pubblicazione sul Web.
3. Evitare di attivare una chiamata `launchUrl()` all'interno di un ciclo, della funzione `update` dell'oggetto visivo o di qualsiasi altro codice che ricorre di frequente.

## <a name="step-by-step-example"></a>Esempio dettagliato

### <a name="adding-a-link-launching-element"></a>Aggiunta di un elemento di avvio di un collegamento

Sono state aggiunte le righe seguenti alla funzione `constructor`:

```typescript
    this.helpLinkElement = this.createHelpLinkElement();
    options.element.appendChild(this.helpLinkElement);
```

È stata inoltre aggiunta una funzione privata creando e collegando l'elemento di ancoraggio:

```typescript
private createHelpLinkElement(): Element {
    let linkElement = document.createElement("a");
    linkElement.textContent = "?";
    linkElement.setAttribute("title", "Open documentation");
    linkElement.setAttribute("class", "helpLink");
    linkElement.addEventListener("click", () => {
        this.host.launchUrl("https://docs.microsoft.com/power-bi/developer/custom-visual-develop-tutorial");
    });
    return linkElement;
};
```

Infine, una voce nel file visual.less definisce lo stile per l'elemento link:

```less
.helpLink {
    position: absolute;
    top: 0px;
    right: 12px;
    display: block;
    width: 20px;
    height: 20px;
    border: 2px solid #80B0E0;
    border-radius: 20px;
    color: #80B0E0;
    text-align: center;
    font-size: 16px;
    line-height: 20px;
    background-color: #FFFFFF;
    transition: all 900ms ease;

    &:hover {
        background-color: #DDEEFF;
        color: #5080B0;
        border-color: #5080B0;
        transition: all 250ms ease;
    }

    &.hidden {
        display: none;
    }
}
```

### <a name="adding-a-toggling-mechanism"></a>Aggiunta di un meccanismo di attivazione/disattivazione

Questa operazione richiede l'aggiunta di un oggetto statico (vedere l'[esercitazione sugli oggetti statici](https://microsoft.github.io/PowerBI-visuals/docs/concepts/objects-and-properties)), in modo che l'autore del report possa attivare o disattivare la visibilità dell'elemento link. L'impostazione predefinita consiste nel nascondere l'elemento.
Un oggetto statico booleano `showHelpLink` è stato aggiunto alla voce objects in `capabilities.json`:

```typescript
"objects": {
    "generalView": {
            "displayName": "General View",
            "properties":
                "showHelpLink": {
                    "displayName": "Show Help Button",
                    "type": {
                        "bool": true
                    }
                }
            }
        }
    }
```

![Attivazione/disattivazione dell'URL di avvio](./media/launchurl-toggle.png)

Nella funzione `update` sono state inoltre aggiunte le righe seguenti:

```typescript
if (settings.generalView.showHelpLink) {
    this.helpLinkElement.classList.remove("hidden");
} else {
    this.helpLinkElement.classList.add("hidden");
}
```

In visual.less è stata definita la classe `hidden` per controllare la visualizzazione dell'elemento.
