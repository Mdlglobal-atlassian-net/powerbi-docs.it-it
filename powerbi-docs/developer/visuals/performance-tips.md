---
title: Suggerimenti per le prestazioni
description: Come creare un oggetto visivo di Power BI con prestazioni elevate
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 04/20/2020
ms.openlocfilehash: 7ebc02b2c459517957425e78438e12e89dc2e1bb
ms.sourcegitcommit: 1059c6222458f189fb5301dcb689dad2b2c00bc1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/28/2020
ms.locfileid: "82196561"
---
# <a name="how-to-build-a-high-performance-power-bi-visual"></a>Come creare un oggetto visivo di Power BI con prestazioni elevate
Questo articolo illustra alcune tecniche che consentono agli sviluppatori di ottenere prestazioni elevate durante il rendering degli oggetti visivi. 

Nessuno vuole oggetti visivi il cui rendering impiega troppo tempo e sviluppare codice che offra le massime prestazioni durante il rendering è fondamentale. 

> [!NOTE]
> Nell'ottica del continuo miglioramento della piattaforma, vengono costantemente rilasciate nuove versioni dell'API. Per sfruttare al meglio la piattaforma e il set di funzionalità degli oggetti visivi di Power BI, è consigliabile usare sempre la versione più recente.
>
> A partire dalla **versione 2.1**, l'ultima, il tempo di caricamento degli oggetti visivi di Power BI è migliorato in media del 20%.

## <a name="power-bi-visual-performance-tips"></a>Suggerimenti per le prestazioni degli oggetti visivi di Power BI
Ecco alcuni consigli su come ottenere prestazioni ottimali per gli oggetti visivi. 

### <a name="use-user-timing-api"></a>Usare l'API di temporizzazione utente
L'uso dell'**API di temporizzazione utente** per misurare le prestazioni JavaScript dell'app può essere utile per decidere quali parti dello script devono essere ottimizzate.

Per altre informazioni, vedere l'[API di temporizzazione utente](https://msdn.microsoft.com/library/hh772738(v=vs.85).aspx).

### <a name="review-animation-loops"></a>Verificare i cicli di animazione
Il ciclo di animazione ridisegna gli elementi non modificati? 

 - Problema: aggiornare gli elementi che non cambiano da frame a frame è una perdita di tempo.

 - Soluzione: aggiornare i frame in modo selettivo. 
 
Quando occorre animare le visualizzazioni statiche, ci si potrebbe rassegnare a creare il codice in un'unica funzione di aggiornamento e chiamarla ripetutamente con nuovi dati per ogni iterazione del ciclo di animazione.

Considerare invece un modello di aggiornamento che usa un metodo costruttore di oggetti visivi per aggiornare tutti gli oggetti statici, in modo che la funzione di aggiornamento debba aggiornare solo gli elementi di visualizzazione che cambiano. 

   > [!TIP]
   > Cicli di animazione inefficienti si trovano comunemente in assi e legende.

### <a name="cache-dom-nodes"></a>Memorizzare nella cache i nodi DOM 
Quando un nodo o un elenco di nodi viene recuperato dal DOM, occorre considerare se è possibile riutilizzarlo in calcoli successivi (talvolta anche nell'iterazione del ciclo successiva). Finché non è necessario aggiungere o eliminare nodi nell'area pertinente, memorizzarli nella cache può migliorare l'efficienza complessiva dell'applicazione.

Per assicurarsi che il codice sia veloce e non rallenti il browser, tenere al minimo l'accesso al DOM. 

- Prima di: 

   ```javascript
   public update(options: VisualUpdateOptions) { 
       let axis = $(".axis"); 
   }
   ```

- Dopo: 

   ```javascript
   public constructor(options: VisualConstructorOptions) { 
       this.$root = $(options.element); 
       this.xAxis = this.$root.find(".xAxis"); 
   } 
 
   public update(options: VisualUpdateOptions) { 
       let axis = this.axis; 
   }
   ```

### <a name="avoid-dom-manipulation"></a>Evitare la modifica del DOM 
Limitare il più possibile la modifica del DOM.  Le operazioni di inserimento come `prepend()`, `append()` e `after()` richiedono molto tempo e devono essere eseguite solo se necessario.

Ad esempio:

  ```javascript
  for (let i=0; i<1000; i++) { 
      $('#list').append('<li>'+i+'</li>');
  }
  ```

L'esempio riportato sopra può essere velocizzato usando `html()` e compilando l'elenco anticipatamente: 

  ```javascript
  let list = ''; 
  for (let i=0; i<1000; i++) { 
      list += '<li>'+i+'</li>'; 
  } 

  $('#list').html(list); 
  ```

### <a name="reconsider-jquery"></a>Riconsiderare JQuery

Limitare i framework JS e usare JS nativo laddove possibile può aumentare la larghezza di banda disponibile e ridurre i costi di elaborazione, oltre a limitare i problemi di compatibilità con i browser meno recenti. 

Per altre informazioni, vedere [youmightnotneedjquery.com](http://youmightnotneedjquery.com/) per esempi alternativi di funzioni come `show`, `hide`, `addClass` e altre di JQuery.  

### <a name="use-canvas-or-webgl"></a>Usare Canvas o WebGL 
Se occorre usare le animazioni ripetutamente, prendere in considerazione l'uso di **Canvas** o **WebGL** invece di SVG. A differenza di SVG, con queste opzioni le prestazioni sono determinate dalle dimensioni anziché dal contenuto. 

Per altre informazioni sulle differenze, vedere [SVG o Canvas: come scegliere](https://msdn.microsoft.com/library/gg193983(v=vs.85).aspx). 

### <a name="use-requestanimationframe-instead-of-settimeout"></a>Usare requestAnimationFrame invece di setTimeout 
Se si usa [requestAnimationFrame](https://www.w3.org/TR/animation-timing/) per aggiornare le animazioni su schermo, le funzioni di animazione vengono chiamate **prima** che il browser chiami un'altra funzione di aggiornamento.

Per altre informazioni, vedere questo [esempio](https://testdrive-archive.azurewebsites.net/Graphics/RequestAnimationFrame/Default.html) di animazione che usa `requestAnimationFrame`.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sulle tecniche di ottimizzazione, vedere [Guida all'ottimizzazione per Power BI](/power-bi/guidance/power-bi-optimization).
