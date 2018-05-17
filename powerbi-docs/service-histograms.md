---
title: Istogrammi
description: Istogrammi
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Visualizations
ms.openlocfilehash: 7e4419afd4264b96d8f7fc60b72c7e276c014da4
ms.sourcegitcommit: f679c05d029ad0765976d530effde744eac23af5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="histograms"></a>Istogrammi
Esistono diversi modi per creare istogrammi in Power BI. Inizieremo dal più semplice per poi analizzare i più complessi.

## <a name="simple-histograms"></a>Istogrammi semplici
Per cominciare è necessario individuare la query contenente il campo in base a cui si vuole creare un istogramma.  Usare l'opzione *Riferimento* per la query per creare una nuova query e denominarla *Istogramma FieldName*. Usare l'opzione **Raggruppa per** nella scheda **Trasforma** della barra multifunzione e selezionare la funzionalità di aggregazione **Conteggio righe** . Verificare che il tipo di dati sia un numero per la colonna aggregata risultante. È quindi possibile visualizzare questi dati nella pagina dei report. Questa procedura è rapida e semplice, ma non è appropriata in presenza di numerosi punti dati e non consente il collegamento di oggetti visivi.

## <a name="defining-buckets-to-build-a-histogram"></a>Definizione di bucket per la creazione di istogrammi
Individuare la query contenente il campo in base a cui si vuole creare un istogramma. Usare l'opzione *Riferimento* per la query per creare una nuova query e denominarla *FieldName*.  Definire ora i bucket con una regola. Usare l'opzione **Aggiungi colonna personalizzata** nella barra multifunzione **Aggiungi colonna** e creare una regola personalizzata.

![](media/service-histograms/powerbi-service-histograms_1.png)

Verificare che il tipo di dati sia un numero per la colonna aggregata risultante. A questo punto è possibile usare la tecnica di raggruppamento descritta in precedenza in **Istogrammi semplici** per completare l'istogramma. Questa opzione consente di gestire più punti dati ma non consente comunque il collegamento di oggetti visivi.

## <a name="defining-a-histogram-that-supports-brushing"></a>Definizione di un istogramma che supporta il collegamento di oggetti visivi
Il collegamento di oggetti visivi fa in modo che, quando un utente seleziona un punto dati in un oggetto visivo, vengono evidenziati altri oggetti visivi nella pagina del report oppure vengono filtrati i punti dati correlati al punto dati selezionato.  Poiché i dati vengono modificati in fase di query, è necessario creare una relazione tra tabelle e assicurarsi di sapere quale elemento dei dettagli è correlato al bucket nell'istogramma e viceversa.

Iniziare il processo usando l'opzione *Riferimento* nella query contenente il campo in base a cui si vuole creare un istogramma.  Assegnare alla nuova query il nome *Bucket*.  Per questo esempio la query originale verrà denominata *Dettagli*.  Rimuovere quindi tutte le colonne ad eccezione di quella da usare come bucket per l'istogramma.  Usare poi la funzionalità *Rimuovi duplicati* nella query. Questa opzione è disponibile nel menu di scelta rapida quando si seleziona una colonna e consente di lasciare solo valori univoci nella colonna. Se sono presenti numeri decimali, è prima possibile applicare il suggerimento per la definizione di bucket per la creazione di un istogramma, in modo da ottenere un set gestibile di bucket.  Controllare ora i dati visualizzati nell'anteprima della query. Se sono presenti valori vuoti o null, è necessario correggerli prima di creare una relazione. Vedere "Creazione di relazioni quando i dati contengono valori null o vuoti". Questo approccio può essere problematico a causa della necessità di eseguire l'ordinamento. Per ordinare i bucket in modo corretto, vedere l'argomento relativo a ordinamento e visualizzazione delle categorie nell'ordine desiderato. 

> [!NOTE]
> È utile pensare all'ordinamento prima di creare oggetti visivi.   
> 
> 

Il passaggio successivo del processo consiste nel definire una relazione tra le query *Bucket* e *Dettagli* nella colonna dei bucket.  In *Power BI Desktop*fare clic su *Gestisci relazioni* sulla barra multifunzione.  Creare una relazione con *Bucket* nella tabella di sinistra e *Dettagli* nella tabella di destra e selezionare il campo da usare per l'istogramma. 

L'ultimo passaggio consiste nel creare l'istogramma. Trascinare il campo Bucket dalla tabella *Bucket* . Rimuovere il campo predefinito dall'istogramma risultante.  Dalla tabella *Dettagli* trascinare quindi il campo dell'istogramma nello stesso oggetto visivo. Nel contenitore di campi modificare l'aggregazione predefinita in Conteggio. Il risultato è l'istogramma. Se si crea un altro oggetto visivo come una mappa ad albero dalla tabella Dettagli, selezionare un punto dati nella mappa ad albero per visualizzare l'istogramma con un'evidenziazione e il punto dati selezionato rispetto alla tendenza per l'intero set di dati.

