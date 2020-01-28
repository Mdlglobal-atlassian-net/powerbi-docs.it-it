---
title: Combinare file (binari) in Power BI Desktop
description: Combinare facilmente file (binari) in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/13/2020
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 07381461375ea7b9707b91c807e92cdb85c1d440
ms.sourcegitcommit: 3d6b27e3936e451339d8c11e9af1a72c725a5668
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2020
ms.locfileid: "76161109"
---
# <a name="combine-files-binaries-in-power-bi-desktop"></a>Combinare file (binari) in Power BI Desktop

Ecco un approccio efficace per importare dati in **Power BI Desktop**: Se sono presenti più file con lo stesso schema, combinarli in un'unica tabella logica. Questa tecnica molto diffusa è stata resa più comoda e più ampia.

Per avviare il processo di combinazione di file dalla stessa cartella, selezionare **Recupera dati**, scegliere **File** > **Cartella**, quindi selezionare **Connetti**.

![Connessione alla cartella di file, finestra di dialogo Recupera dati, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_1.png)

Immettere il percorso della cartella, selezionare **OK**, quindi selezionare **Trasforma dati** per visualizzare i file della cartella nell'editor di Power Query.

## <a name="combine-files-behavior"></a>Comportamento di combinazione dei file

Per combinare i file binari nell'editor di Power Query, selezionare **Contenuto** (la prima etichetta di colonna) e selezionare **Home** > **Combina file**. In alternativa, è possibile selezionare semplicemente l'icona **Combina file** accanto a **Contenuto**.

![Comando Combina file, editor di Power Query, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_2a.png)

La trasformazione *Combina file* si comporta come segue:

* La trasformazione Combina file analizza ogni file di input per determinare il formato di file corretto da usare, ad esempio un file di *testo*, una *cartella di lavoro di Excel* o un file *JSON*.
* La trasformazione consente di selezionare un oggetto specifico dal primo file, ad esempio una cartella di lavoro di Excel, da estrarre.
  
  ![Finestra di dialogo Combina file, editor di Power Query, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_3.png)
* La trasformazione Combina file esegue automaticamente le operazioni seguenti:
  
  * Crea una query di esempio che esegue tutti i passaggi di estrazione necessari in un singolo file.
  * Crea un *query della funzione* che parametrizza l'input file/binario della *query di esempio*. La query di esempio e la query della funzione sono collegate in modo che le modifiche apportate alla query di esempio vengano riflesse nella query della funzione.
  * Applica la *query della funzione* alla query originale con i file binari di input, ad esempio la query *Cartella*. Applica la query della funzione per gli input binari in ogni riga, quindi espande l'estrazione dei dati risultanti come colonne di primo livello.

    ![Risultati della trasformazione Combina file, editor di Power Query, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_4.png)

> [!NOTE]
> L'ambito della selezione in una cartella di lavoro di Excel influirà sul comportamento dei file binari combinati. Ad esempio, è possibile selezionare un foglio di lavoro specifico per combinare tale foglio di lavoro oppure selezionare la radice per combinare il file completo. Selezionando una cartella vengono combinati i file presenti nella cartella. 

Con il comportamento di Combina file è possibile combinare facilmente tutti i file con lo stesso tipo e la stessa struttura di file (ad esempio, le stesse colonne) in una determinata cartella.

È anche possibile applicare facilmente altri passaggi di trasformazione o estrazione modificando la query di esempio creata automaticamente, senza doversi preoccupare di modificare o creare altri passaggi della query della funzione. Qualsiasi modifica apportata alla query di esempio viene automaticamente generata nella query della funzione collegata.

## <a name="next-steps"></a>Passaggi successivi

È possibile connettersi a molti tipi di dati usando Power BI Desktop. Per altre informazioni sulle origini dati, vedere le risorse seguenti:

* [Che cos'è Power BI Desktop?](desktop-what-is-desktop.md)
* [Origini dati in Power BI Desktop](desktop-data-sources.md)
* [Effettuare il data shaping e combinare i dati con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Connettersi a file CSV in Power BI Desktop](desktop-connect-csv.md)
* [Immettere dati direttamente in Power BI Desktop](desktop-enter-data-directly-into-desktop.md)
