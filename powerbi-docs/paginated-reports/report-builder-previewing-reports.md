---
title: Anteprima dei report nel Generatore report di Power BI
description: Durante la creazione di un report impaginato del Generatore report, è utile visualizzare in anteprima il report frequentemente per verificare che il report visualizzi i dati desiderati.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: ba6b5bdd-d8c6-4aa8-ba32-3a10b11969d4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: afbc31e3ece8bc72ad52bb2fe7c3d871b2f68e1b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "78922943"
---
# <a name="previewing-reports-in-power-bi-report-builder"></a>Anteprima dei report nel Generatore report di Power BI
  Durante la creazione di un report impaginato del Generatore report, è utile visualizzare in anteprima il report frequentemente per verificare che il report visualizzi i dati desiderati. Per visualizzare in anteprima il report, fare clic su **Esegui**. Viene eseguito il rendering del report in modalità di anteprima.  
  
 Il Generatore report migliora l'esperienza di anteprima tramite sessioni di modifica quando si è connessi a un server di report. La sessione di modifica crea una cache dei dati e rende disponibili i set di dati nella cache per le anteprime ripetute del report. Una sessione di modifica non è una funzionalità con cui si interagisce direttamente, ma comprendere quando viene aggiornato il set di dati memorizzato nella cache consente di migliorare le prestazioni quando si visualizza in anteprima un report e di individuare il motivo per cui il rendering del report è più veloce o più lento.  

  
> [!NOTE]  
> Esistono alcune differenze tra la visualizzazione in anteprima nel Generatore report e la visualizzazione in un browser. Ad esempio, un controllo calendario, aggiunto a un report quando si specifica un parametro di tipo Date/Time, è diverso nel Generatore report e in un browser. 
  
## <a name="improving-preview-performance"></a>Miglioramento delle prestazioni di anteprima  
 Il modo in cui si creano e si aggiornano i report ha effetto sulla velocità del rendering del report in anteprima. La prima volta che si visualizza in anteprima un report che si basa su un riferimento al server, viene creata automaticamente una sessione di modifica e i dati usati durante l'esecuzione del report vengono aggiunti a una cache dei dati che viene archiviata. Quando si apportano modifiche al report che non influiscono sui dati, il report usa la copia dei dati memorizzata nella cache. Ciò significa che non verranno visualizzate modifiche ai dati ogni volta che si visualizza l'anteprima del report. Per visualizzare i nuovi dati, fare clic sul pulsante **Aggiorna** nella barra multifunzione.  
  
 Le azioni seguenti causano l'aggiornamento della cache e rallentano il rendering del report alla successiva anteprima:  
  
-   Aggiungere, modificare o eliminare un set di dati. Il set di dati memorizzato nella cache contiene tutti i set di dati usati da un report e la modifica di qualsiasi set di dati invalida il set di dati memorizzato nella cache. Le modifiche includono la modifica del nome, della query o dei campi del set di dati.  
  
    > [!NOTE]  
    >  Se il set di dati include un numero elevato di campi che non si prevede di usare, è consigliabile aggiornare il set di dati per omettere tali campi. Sebbene questa operazione crei una nuova sessione di modifica e la prima anteprima del report risulti più lenta, un set di dati di minori dimensioni memorizzato nella cache rappresenta un vantaggio generale per le prestazioni del server di report.  
  
-   Aggiungere, modificare o eliminare un'origine dati. Queste azioni includono la modifica del nome o delle proprietà dell'origine dati, dell'estensione dati dell'origine dati o delle proprietà della connessione all'origine dati.  
  
-   Modificare l'origine dati usata dal report in un'origine dati diversa.  
  
-   Modificare la lingua del report.  
  
-   Modificare gli assembly o il codice personalizzato usato dal report.  
  
-   Aggiungere, modificare o eliminare i parametri di query nel report o i valori dei parametri.  
  
 Le modifiche al layout del report e alla formattazione dei dati non hanno effetto sul set di dati memorizzato nella cache. È possibile eseguire le azioni seguenti senza aggiornare il set di dati memorizzato nella cache:  
  
-   Aggiungere o rimuovere aree dati, ad esempio tabelle, matrici o grafici.  
  
-   Aggiungere o eliminare colonne dal report. Tutti i campi del set di dati possono essere usati nel report. L'aggiunta o la rimozione di campi nel report non ha effetto sul set di dati.  
  
-   Modificare l'ordine dei campi in tabelle e matrici.  
  
-   Aggiungere, modificare o eliminare gruppi di righe e colonne.  
  
-   Aggiungere, modificare o eliminare la formattazione dei valori dei dati nei campi.  
  
-   Aggiungere, modificare o eliminare immagini, linee o caselle di testo.  
  
-   Modificare le interruzioni di pagina.  
  
La sessione di modifica viene creata alla prima visualizzazione in anteprima di un report. Per impostazione predefinita, una sessione di modifica ha una durata di 7200 secondi (2 ore). La sessione viene reimpostata su due ore ogni volta che si esegue il report. Quando la sessione di modifica scade, viene eliminata la cache dei dati. Se la sessione di modifica scade, viene automaticamente creata una nuova sessione alla successiva visualizzazione in anteprima del report.
  
Per impostazione predefinita, la cache dei dati può contenere fino a cinque set di dati. Se si usano molte combinazioni diverse di valori di parametro, è possibile che il report necessiti di più dati. In questo caso è necessario aggiornare la cache e il rendering del report risulterà più lento alla successiva anteprima. 
  
## <a name="concurrency-of-report-updates"></a>Concorrenza degli aggiornamenti del report  
L'anteprima di un report viene eseguita spesso durante l'aggiornamento e il salvataggio di un report nel servizio Power BI. Quando si aggiorna un report, è possibile che un altro utente stia aggiornando e salvando il report nello stesso momento. Il report salvato per ultimo corrisponderà alla versione del report disponibile per le visualizzazioni e gli aggiornamenti successivi. Per questa ragione, è possibile che la versione del report visualizzata in anteprima non corrisponda alla versione che viene riaperta. In questo caso è possibile salvare il report con un nuovo nome usando l'opzione **Salva con nome** del menu del Generatore report.  
  
## <a name="external-report-items"></a>Elementi del report esterni  
 Il report può includere elementi, ad esempio immagini esterne che vengono archiviate separatamente dal report. Poiché gli elementi vengono archiviati separatamente è possibile che vengano spostati in una posizione diversa o eliminati. In questo caso, è possibile che il report non venga visualizzato in anteprima. È possibile aggiornare il report per specificare la posizione aggiornata dell'elemento oppure se l'elemento è stato eliminato, sostituirlo con un elemento esistente o rimuovere il riferimento all'elemento dal report.  
  
## <a name="next-steps"></a>Passaggi successivi

- [Che cosa sono i report impaginati in Power BI Premium?](paginated-reports-report-builder-power-bi.md)
  
