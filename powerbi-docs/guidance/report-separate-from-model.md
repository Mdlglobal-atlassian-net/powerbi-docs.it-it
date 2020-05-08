---
title: Separare i report dai modelli in Power BI Desktop
description: Linee guida per separare i report dai modelli in Power BI Desktop.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/11/2020
ms.author: v-pemyer
ms.openlocfilehash: dad451da460abed65a69990394522f268d7f21cd
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "81525262"
---
# <a name="separate-reports-from-models-in-power-bi-desktop"></a>Separare i report dai modelli in Power BI Desktop

Quando si crea una nuova soluzione Power BI Desktop, una delle prime attività che è necessario eseguire è il recupero dei dati. Il recupero dei dati può generare due risultati nettamente diversi. Potrebbe:

- Creare una [connessione dinamica](../desktop-report-lifecycle-datasets.md) a un modello già pubblicato, che può essere un set di dati di Power BI o un modello di Analysis Services ospitato in remoto.
- Dare il via allo sviluppo di un nuovo modello, che può essere un modello di importazione, DirectQuery o composito.

Questo articolo riguarda il secondo scenario. Vengono fornite indicazioni per l'eventuale combinazione di un report e di un modello in un unico file di Power BI Desktop.

## <a name="single-file-solution"></a>Soluzione con singolo file

Una _soluzione con singolo file_ è appropriata quando è presente un singolo report basato sul modello. In questo caso, è probabile che il modello e il report siano stati creati dalla stessa persona. Viene definita soluzione _BI personale_, anche se il report può essere condiviso con altri utenti. Tali soluzioni possono corrispondere a report con ambito limitato a ruoli specifici o valutazioni una tantum di un progetto aziendale, spesso noti anche come _report ad hoc_.

:::image type="content" source="media/report-separate-from-model/single-file-solution.png" alt-text="Un singolo file contiene un modello e un report, sviluppati dalla stessa persona." border="true":::

## <a name="separate-report-files"></a>Separare i file di report

È opportuno separare lo sviluppo di modelli e report in file di Power BI Desktop separati nei casi seguenti:

- Gli autori del modello di dati e del report sono persone diverse.
- È assodato che un modello sarà l'origine di più report, ora o in futuro.

:::image type="content" source="media/report-separate-from-model/separate-report-files.png" alt-text="Sono disponibili tre file PBIX. Il primo contiene solo un modello. Gli altri due contengono solo report e si connettono in modo dinamico al modello ospitato nel servizio Power BI. I report vengono sviluppati da persone diverse." border="true":::

Gli autori di modelli di dati possono comunque usare l'esperienza di creazione di report di Power BI Desktop per testare e convalidare le progettazioni dei modelli. Tuttavia, subito dopo la pubblicazione del file nel servizio Power BI dovranno rimuovere il report dall'area di lavoro. Dovranno anche ricordarsi di rimuovere il report ogni volta che ripubblicano e sovrascrivono il set di dati.

### <a name="preserve-the-model-interface"></a>Mantenere l'interfaccia del modello

In alcuni casi le modifiche al modello sono inevitabili. In questi casi, gli autori dei modelli devono assicurarsi di non interrompere il funzionamento dell'interfaccia del modello. Se ciò accade, è possibile che gli oggetti visivi del report o i riquadri del dashboard correlati non funzionino. Gli oggetti visivi non funzionanti vengono visualizzati come errori e possono causare frustrazione per gli autori e gli utenti dei report. E peggio ancora possono minare la fiducia nei dati.

È quindi importante gestire con attenzione le modifiche ai modelli. Se possibile, evitare le modifiche seguenti:

- Ridenominazione di tabelle, colonne, gerarchie, livelli di gerarchia o misure.
- Modifica dei tipi di dati delle colonne.
- Modifica delle espressioni di misura in modo che restituiscano un tipo di dati diverso.
- Spostamento delle misure in una diversa tabella home. Lo spostamento di una misura potrebbe generare errori per le misure con ambito report ed è per questo che è consigliabile usare nomi completi per le misure includendo il nome della tabella home. Non è consigliabile scrivere espressioni DAX usando nomi di misure completi. Per altre informazioni, vedere [DAX: Riferimenti a colonne e misure](dax-column-measure-references.md).

L'aggiunta di nuove tabelle, colonne, gerarchie, livelli di gerarchia o misure è sicura, con un'unica eccezione: È possibile che un nuovo nome di misura entri in conflitto con un nome di misura con ambito report. Per evitare conflitti, si consiglia agli autori di report di adottare una convenzione di denominazione durante la definizione delle misure nei report. Possono aggiungere ai nomi delle misure con ambito report un prefisso con un carattere di sottolineatura o altri caratteri.

Se è necessario apportare modifiche che causano un'interruzione ai modelli, è consigliabile:

- [Visualizzare il contenuto correlato per il set di dati](../consumer/end-user-related.md#view-related-content-for-a-dataset) nel servizio Power BI.
- Esplorare la visualizzazione [Derivazione dei dati](../collaborate-share/service-data-lineage.md) nel servizio Power BI.

Entrambe le opzioni consentono di identificare rapidamente eventuali report e dashboard correlati. La visualizzazione Derivazione dei dati è probabilmente la scelta migliore perché è facile vedere il contatto per ogni artefatto correlato. In realtà, si tratta di un collegamento ipertestuale che apre un messaggio di posta elettronica destinato al contatto.

Si consiglia di contattare il proprietario di ogni artefatto correlato per avvisarlo di eventuali modifiche pianificate che causano interruzioni. In questo modo, tali autori potranno prepararsi per correggere e ripubblicare i report, riducendo al minimo tempi di inattività e disservizi.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni correlate a questo articolo, vedere le risorse seguenti:

- [Connettersi ai set di dati nel servizio Power BI da Power BI Desktop](../desktop-report-lifecycle-datasets.md)
- [Visualizzare il contenuto correlato nel servizio Power BI](../consumer/end-user-related.md)
- [Derivazione dei dati](../collaborate-share/service-data-lineage.md)
- Domande? [Contattare la community di Power BI](https://community.powerbi.com/)
- Se si hanno suggerimenti, [Contribuire con idee per migliorare Power BI](https://ideas.powerbi.com/)
