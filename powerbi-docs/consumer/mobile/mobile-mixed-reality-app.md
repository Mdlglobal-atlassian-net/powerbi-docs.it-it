---
title: App Power BI per realtà mista (anteprima)
description: È possibile visualizzare dashboard e report nell'app Power BI per realtà mista (anteprima), sia immersi nel mondo virtuale sia nel contesto del proprio ambiente.
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 06/05/2018
ms.author: mshenhav
ms.openlocfilehash: 443615a64bee1f4723450c6c8cc3c49feb81989c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61374071"
---
# <a name="power-bi-for-mixed-reality-app-preview"></a>App Power BI per realtà mista (anteprima)
È possibile visualizzare dashboard e report nell'app Power BI per realtà mista (anteprima) mentre si è immersi nel mondo virtuale o inserire tali elementi in posizioni specifiche nel contesto del proprio ambiente. 

[Scaricare l'app Power BI per la Realtà mista](https://www.microsoft.com/p/power-bi-mobile/9nblgggzlxn1?activetab=pivot%3aoverviewtab) da Windows Store: In Windows Store è chiamata "Power BI per dispositivi mobili". Interagire con dashboard e report nell'ambiente virtuale e selezionare gli elementi da inserire. 

## <a name="two-views-windows-classic-and-holographic"></a>Due visualizzazioni: Windows classica e olografica

Power BI per realtà mista si basa sull'app per dispositivi mobili Windows di Power BI con funzionalità aggiuntive esclusive della realtà mista. Quando si avvia Power BI per realtà mista, ci si trova in questa visualizzazione di Windows "classica" di Power BI. In questa visualizzazione è possibile spostarsi tra i dashboard e report ai quali si ha accesso. Quando si trova l'elemento desiderato, è possibile passare dalla visualizzazione di Windows classica all'esperienza olografica. 


## <a name="windows-classic-view-basics"></a>Informazioni di base sulla visualizzazione classica di Windows

Questa sezione è dedicata agli utenti che non hanno familiarità con l'esperienza della realtà mista. L'interazione con un'app per realtà mista è diversa dall'interazione con un computer o con un tablet o telefono. Nella visualizzazione classica di Windows le app per realtà mista rispondono a un serie di movimenti e comandi vocali che sostituiscono i tradizionali mouse e tastiera o il tocco sul telefono. 

**Indice puntato**

L'indice puntato è il movimento più semplice che è necessario conoscere per interagire con quasi tutte le app per realtà mista. Toccare il pollice con l'indice tenendo la mano sollevata, con un movimento simile al clic del mouse o al tocco sul telefono.  

![Movimento dell'indice puntato nella realtà mista](./media/mobile-mixed-reality-app/power-bi-hololens-airtap.png)

In Power BI l'indice puntato viene usato all'interno dell'app classica Windows negli stessi casi in cui si farebbe clic con il mouse. Puntare l'indice per aprire un dashboard o report nell'area di lavoro, oppure puntare l'indice su una parte di oggetto visivo per applicare un filtro o eseguire l'evidenziazione incrociata di altri oggetti visivi, e così via.

![Indice puntato in Power BI](./media/mobile-mixed-reality-app/power-bi-hololens-airtap-hand.png) 

Altre informazioni sui [movimenti della mano in Microsoft per la realtà mista](https://developer.microsoft.com/windows/mixed-reality/gestures).

**Aggiungere un elemento** 

Puntare l'indice sull'icona **Aggiungi** ![icona Aggiungi](./media/mobile-mixed-reality-app/power-bi-hololens-pin.png) per aggiungere un dashboard o report dalla visualizzazione classica di Windows alla visualizzazione olografica. È possibile aggiungere diversi elementi alla visualizzazione olografica. 

**Passare alla visualizzazione olografica**

Dopo aver aggiunto gli elementi nella visualizzazione classica di Windows, puntare l'indice sull'icona **Schermo intero** ![icona Schermo intero](./media/mobile-mixed-reality-app/power-bi-hololens-fullscreen.png) per passare alla visualizzazione olografica. 


## <a name="holographic-view-basics"></a>Informazioni di base sulla visualizzazione olografica

Ora che si è nella visualizzazione olografica, tutti gli elementi che sono stati aggiunti si trovano nell'area di ancoraggio. Questi elementi aggiunti possono essere inseriti in specifiche posizioni nello spazio fisico, ad esempio accanto all'attrezzatura che descrive l'elemento. Nella visualizzazione olografica i comandi vocali integrano i movimenti della mano. Ecco alcuni comandi vocali comuni.

**"Follow me"** ("Seguimi") 

Prelevare un elemento di Power BI in modo che rimanga nel campo visivo principale e fissare lo sguardo finché non viene inserito in un punto.

**"Dock"** ("Ancora") 

Usare questo comando per inserire un elemento nell'area di ancoraggio di Power BI, in modo che segua l'utente al di fuori del campo visivo principale, per un accesso semplificato.

**"Place here"** ("Inserisci qui")

Questo comando posiziona un dashboard o report su una parete o un oggetto o lo sospende nello spazio.

![Inserimento di un dashboard nello spazio](./media/mobile-mixed-reality-app/power-bi-hololens-place-visuals.png)

**"Go home"** ("Vai a Home page")

Questo comando consente di tornare alla visualizzazione di Windows classica di Power BI. 

**"Remove"** ("Rimuovi")

Usare questo comando per rimuovere un elemento dalla visualizzazione olografica.

**"Remove all"** (Rimuovi tutto) 

Usare questo comando per rimuovere tutti gli elementi dalla visualizzazione olografica.


## <a name="scan-a-report-qr-code-in-holographic-view"></a>Eseguire la scansione del codice a matrice di un report nella visualizzazione olografica

È possibile eseguire la scansione del codice a matrice per un report nella visualizzazione olografica, esattamente come è possibile [eseguire la scansione dei codici a matrice con le app per dispositivi mobili di Power BI](mobile-apps-qr-code.md) per iPhone e Android.

- Fissare un codice a matrice nella visualizzazione olografica. Power BI apre il report associato a quel codice a matrice.

## <a name="limitations-and-considerations"></a>Limitazioni e considerazioni

Di seguito sono elencate alcune limitazioni e considerazioni da tenere presenti per la visualizzazione olografica.

- I filtri incrociati o le evidenziazioni eventualmente impostati nella visualizzazione classica di Windows potrebbero non essere visualizzati.
- La visualizzazione dei dashboard e report aggiunti è privata. Non sono attualmente supportate le esperienze condivise.
- I dashboard e report vengono aggiornati ogni 45 secondi, poiché i dati vengono modificati.


## <a name="next-steps"></a>Passaggi successivi

- [Ottenere dati concreti con le app Power BI per dispositivi mobili](mobile-apps-data-in-real-world-context.md)

 



