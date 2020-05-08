---
title: Modalità di modifica avanzata negli oggetti visivi di Power BI
description: Questo articolo illustra come impostare controlli dell'interfaccia utente avanzati negli oggetti visivi di Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 97242883fe90c8f5e115818a24e4bb1c49f69b77
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "79380560"
---
# <a name="advanced-edit-mode-in-power-bi-visuals"></a>Modalità di modifica avanzata negli oggetti visivi di Power BI

Se sono necessari controlli dell'interfaccia utente avanzati nell'oggetto visivo di Power BI, è possibile sfruttare la modalità di modifica avanzata. In modalità di modifica report si seleziona un pulsante **Modifica** per impostare la modalità di modifica su **Avanzata**. L'oggetto visivo può usare il flag `EditMode` per determinare se visualizzare questo controllo dell'interfaccia utente.

Per impostazione predefinita, l'oggetto visivo non supporta la modalità di modifica avanzata. Se è necessario un comportamento diverso, è possibile dichiararlo in modo esplicito nel file *capabilities.json* dell'oggetto visivo, impostando la proprietà `advancedEditModeSupport`.

I valori possibili sono:

- `0`: NotSupported

- `1`: SupportedNoAction

- `2`: SupportedInFocus

## <a name="enter-advanced-edit-mode"></a>Attivare la modalità di modifica avanzata

Un pulsante **Modifica** viene visualizzato se:

* La proprietà `advancedEditModeSupport` è impostata nel file *capabilities.json* su `SupportedNoAction` o `SupportedInFocus`.

* L'oggetto visivo viene visualizzato in modalità di modifica report.

Se la proprietà `advancedEditModeSupport` non è presente nel file *capabilities.json* o è impostata su `NotSupported`, il pulsante **Modifica** non viene visualizzato.

![Attivare la modalità di modifica](media/advanced-edit-mode/edit-mode.png)

Quando si seleziona **Modifica**, l'oggetto visivo ottiene una chiamata a update() con EditMode impostato su `Advanced`. A seconda del valore impostato nel file *capabilities.json*, vengono eseguite le azioni seguenti:

* `SupportedNoAction`: nessun'altra azione richiesta da parte dell'host.
* `SupportedInFocus`: l'host espande l'oggetto visivo in modalità messa a fuoco.

## <a name="exit-advanced-edit-mode"></a>Disattivare la modalità di modifica avanzata

Il pulsante **Torna al report** viene visualizzato se:

* La proprietà `advancedEditModeSupport` è impostata nel file *capabilities.json* su `SupportedInFocus`.
