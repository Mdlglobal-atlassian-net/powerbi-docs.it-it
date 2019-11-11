---
title: Combinare file (binari) in Power BI Desktop
description: Combinare facilmente file (binari) in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/26/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 03a6e044a55613d40a1cf195d6a0ad3b44a9f012
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73876565"
---
# <a name="combine-files-binaries-in-power-bi-desktop"></a>Combinare file (binari) in Power BI Desktop
Un solido approccio all'importazione di dati in **Power BI Desktop** consiste nel combinare più file con lo stesso schema in un'unica tabella logica. Questo approccio comodo e popolare è stato reso più pratico ed esteso, come descritto in questo articolo.

Per avviare il processo di combinazione di file dalla stessa cartella, selezionare **Recupera dati > File > Cartella**.

![](media/desktop-combine-binaries/combine-binaries_1.png)


## <a name="combine-files-behavior"></a>Comportamento di combinazione dei file
Per **combinare file (binari)** , è possibile selezionare **Combina file** dalla scheda della barra multifunzione **Home** nell'**Editor di query** o dalla colonna stessa.

![](media/desktop-combine-binaries/combine-binaries_2a.png)

La trasformazione **Combina file** si comporta come segue:

* La trasformazione **Combina file** analizza ogni file di input e determina il formato di file corretto da usare, ad esempio un file di *testo*, una *cartella di lavoro di Excel* o un file *JSON*.
* La trasformazione consente di selezionare un oggetto specifico dal primo file, ad esempio una *cartella di lavoro di Excel*, da estrarre.
  
  ![](media/desktop-combine-binaries/combine-binaries_3.png)
* La trasformazione **combina file** esegue quindi automaticamente le query seguenti:
  
  * Crea una query di esempio che esegue tutti i passaggi di estrazione necessari in un singolo file.
  * Crea un *query della funzione* che parametrizza l'input file/binario della *query di esempio*. La query di esempio e la query della funzione sono collegate in modo che le modifiche apportate alla query di esempio vengano riflesse nella query della funzione.
  * Applica la *query della funzione* alla query originale con binari di input, ad esempio la query *Cartella*, in modo da applicare la query della funzione per gli input binari in ciascuna riga, quindi espande l'estrazione dei dati risultanti come colonne di livello superiore.
    
    ![](media/desktop-combine-binaries/combine-binaries_4.png)

> [!NOTE]
> L'ambito della selezione in una cartella di lavoro di Excel influirà sul comportamento dei file binari combinati. Ad esempio, è possibile selezionare un foglio di lavoro specifico per combinare tale foglio di lavoro oppure selezionare la radice per combinare il file completo. Selezionando una cartella vengono combinati i file presenti nella cartella. 


Con il comportamento di **Combina file** è possibile combinare facilmente tutti i file con lo stesso tipo e struttura di file (ad esempio, le stesse colonne) in una determinata cartella.

È anche possibile applicare facilmente altri passaggi di trasformazione o estrazione modificando la *query di esempio* creata automaticamente, senza doversi preoccupare di modificare o creare altri passaggi della *query della funzione*. Qualsiasi modifica apportata alla *query di esempio* viene automaticamente generata nella *query della funzione* collegata.

## <a name="next-steps"></a>Passaggi successivi
È possibile connettersi a molti tipi di dati usando Power BI Desktop. Per altre informazioni sulle origini dati, vedere le risorse seguenti:

* [Che cos'è Power BI Desktop?](desktop-what-is-desktop.md)
* [Origini dati in Power BI Desktop](desktop-data-sources.md)
* [Effettuare il data shaping e combinare i dati con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Connettersi a file CSV in Power BI Desktop](desktop-connect-csv.md)   
* [Immettere dati direttamente in Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

