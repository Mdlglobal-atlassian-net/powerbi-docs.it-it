---
title: Linee guida per l'uso di immagini nei report impaginati
description: Linee guida per l'uso di immagini nei report impaginati di Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: d2f3f36911c72df1b95ceb5bd90043870559cc62
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/07/2020
ms.locfileid: "78920722"
---
# <a name="image-use-guidance-for-paginated-reports"></a>Linee guida per l'uso di immagini nei report impaginati

Questo articolo è rivolto agli autori di report che progettano [report impaginati](../paginated-reports/paginated-reports-report-builder-power-bi.md) di Power BI. Questo articolo offre suggerimenti relativi all'uso di immagini. Nei layout dei report le immagini mostrano in genere un oggetto grafico, ad esempio un logo aziendale o una foto.

Le immagini possono essere archiviate in tre posizioni diverse:

- All'interno del report (incorporate)
- Su un server Web
- In un database, che può essere recuperato da un set di dati

Possono quindi essere usate in diversi contesti nei layout di un report:

- Logo o immagine indipendente
- Immagini associate a righe di dati
- Sfondo per determinati elementi del report:
  - Corpo del report
  - Casella di testo
  - Rettangolo
  - Un'area dati Tablix (tabella, matrice o elenco)

## <a name="suggestions"></a>Suggerimenti

Per offrire layout di report professionali, facilità di gestione e prestazioni di report ottimizzate, prendere in considerazione i suggerimenti seguenti:

- **Usare le dimensioni più piccole possibili**: è consigliabile preparare immagini di dimensioni ridotte, benché chiare e nitide. È importante trovare un giusto equilibrio tra qualità e dimensioni. Per ridurre le dimensioni dei file di immagine, provare a usare un editor di grafica, ad esempio MS Paint.
- **Evitare le immagini incorporate**: in primo luogo, le immagini incorporate possono aumentare la dimensione del file di report e rallentare così l'esecuzione del rendering. In secondo luogo, le immagini incorporate possono richiedere un eccessivo impegno di gestione se è necessario aggiornare molte immagini del report, come in caso di modifica del logo della società.
- **Usare le risorse di archiviazione del server Web**: l'archiviazione di immagini in un server Web è una soluzione ottimale, soprattutto per il logo della società, che può provenire dal sito Web della società. Prestare tuttavia attenzione se gli utenti del report accederanno ai report all'esterno della rete. In questo caso, assicurarsi che le immagini siano disponibili su Internet.

    Quando le immagini sono correlate ai dati (ad esempio le foto dei venditori), assegnare un nome ai file di immagine in modo che un'espressione di report possa generare dinamicamente il percorso dell'URL dell'immagine. È ad esempio possibile assegnare alle foto dei venditori un nome in base al relativo numero di dipendente. Se il set di dati del report recupera il numero di dipendente, sarà possibile scrivere un'espressione per generare il percorso completo dell'URL dell'immagine.
- **Usare le risorse di archiviazione del database**: quando un database relazionale archivia i dati delle immagini, può essere opportuno definire le tabelle di database come origine dei dati delle immagini, soprattutto quando le immagini non sono troppo grandi.
- **Usare immagini di sfondo appropriate**: se si decide di usare immagini di sfondo, fare attenzione a non usare immagini che distraggono l'attenzione dell'utente dai dati del report. 

    Accertarsi inoltre di usare _immagini in stile filigrana_. Le immagini di questo tipo hanno in genere uno sfondo trasparente (o hanno lo stesso colore di sfondo usato dal report) e presentano colori tenui. Esempi comuni di immagini in stile filigrana includono il logo della società o le etichette di riservatezza come "Bozza" o "Riservato".

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni correlate a questo articolo, vedere le risorse seguenti:

- [Che cosa sono i report impaginati in Power BI Premium?](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- Domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
- Se si hanno suggerimenti, [Contribuire con idee per migliorare Power BI](https://ideas.powerbi.com/)
