---
title: Opzioni di ordinamento per gli oggetti visivi di Power BI
description: Questo articolo illustra il comportamento di ordinamento predefinito per gli oggetti visivi di Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 546480ae863c63d6517fde7c98e7c9787c022ab6
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73875540"
---
# <a name="sorting-options-for-power-bi-visuals"></a>Opzioni di ordinamento per gli oggetti visivi di Power BI

Questo articolo descrive in che modo le opzioni di *ordinamento* specificano il comportamento di ordinamento per gli oggetti visivi di Power BI. 

Per la funzionalità di ordinamento è necessario uno dei parametri seguenti.

## <a name="default-sorting"></a>Ordinamento predefinito

L'opzione `default` è la forma più semplice. Permette di ordinare i dati presentati nella sezione "DataMappings". Questa opzione permette l'ordinamento dei mapping di dati da parte dell'utente e l'impostazione della direzione di ordinamento.

```json
    "sorting": {
        "default": {   }
    }
```

![Opzioni di ordinamento nel menu di scelta rapida](./media/sorting.png)

## <a name="implicit-sorting"></a>Ordinamento implicito

L'ordinamento implicito esegue l'ordinamento con il parametro di matrice `clauses`, che descrive l'ordinamento per ogni ruolo di dati. `implicit` indica che l'utente dell'oggetto visivo non può modificare l'ordinamento. Power BI non visualizza le opzioni di ordinamento nel menu dell'oggetto visivo. Tuttavia, Power BI ordina i dati in base alle impostazioni specificate.

I parametri `clauses` possono contenere diversi oggetti con due parametri:

- `role`: determina `DataMapping` per l'ordinamento
- `direction`: determina la direzione di ordinamento (1 = crescente, 2 = decrescente)

```json
    "sorting": {
        "implicit": {
            "clauses": [
                {
                    "role": "category",
                    "direction": 1
                },
                {
                    "role": "measure",
                    "direction": 2
                }
            ]
        }
    }
```

## <a name="custom-sorting"></a>Ordinamento personalizzato

L'ordinamento personalizzato indica che l'ordinamento è gestito dallo sviluppatore nel codice dell'oggetto visivo.
