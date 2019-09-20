---
title: Usare R nell'Editor di Power Query
description: Usare R nell'Editor di query di Power BI Desktop per l'analisi avanzata
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/06/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: b64b4b736291ce1c3bde02010b7e583a0c3dc406
ms.sourcegitcommit: 226b47f64e6749061cd54bf8d4436f7deaed7691
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2019
ms.locfileid: "70841520"
---
# <a name="use-r-in-query-editor"></a>Usare R nell'Editor di query

[**R**](https://mran.microsoft.com/documents/what-is-r) è un potente linguaggio di programmazione usato da numerosi esperti di statistica, data scientist e analisti di dati. È possibile usare **R** nell'**Editor di query** di Power BI Desktop per eseguire queste operazioni:

* Preparare i modelli di dati

* Creare report

* Eseguire attività di pulizia dei dati, modifica avanzata della forma dei dati e analisi dei set di dati, inclusi il completamento dei dati mancanti, le stime, il clustering e altro ancora.  

## <a name="install-r"></a>Installare R

È possibile scaricare e installare **R** gratuitamente dalla [pagina di download di Revolution Open](https://mran.revolutionanalytics.com/download/) e dal [repository CRAN](https://cran.r-project.org/bin/windows/base/).

### <a name="install-mice"></a>Installare mice

Nell'ambiente R deve essere installata la [libreria **mice**](https://www.rdocumentation.org/packages/mice/versions/3.5.0/topics/mice). Senza **mice**, il codice degli script di esempio non funziona correttamente. Il pacchetto **mice** implementa un metodo per gestire i dati mancanti.

Per installare **mice**:

1. Avviare il programma R.exe, ad esempio C:\Programmi\Microsoft\R Open\R-3.5.3\bin\R.exe  

2. Eseguire il comando di installazione:

   ``` 
   >  install.packages('mice') 
   ```

## <a name="use-r-in-query-editor"></a>Usare R nell'Editor di query

Per illustrare l'uso di **R** nell'**Editor di query** si userà un set di dati di esempio del mercato azionario contenuto in un file con estensione csv e si eseguirà la procedura seguente:

1. [Scaricare il file **EuStockMarkets_NA.csv**](http://download.microsoft.com/download/F/8/A/F8AA9DC9-8545-4AAE-9305-27AD1D01DC03/EuStockMarkets_NA.csv). Ricordare il percorso in cui viene salvato.

1. Caricare il file in **Power BI Desktop**: dalla scheda **Home** della barra multifunzione selezionare **Recupera dati > Testo/CSV**.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_1.png)

1. Selezionare il file e quindi fare clic su **Apri**. I dati CSV vengono visualizzati nella finestra di dialogo del **file di testo/CSV**.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_2.png)

1. Una volta caricati, i dati saranno visibili nel riquadro **Campi**.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_3.png)

1. Per aprire l'**Editor di query**, nella scheda **Home** della barra multifunzione selezionare **Modifica query**.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_4.png)

1. Nella scheda **Trasforma** della barra multifunzione selezionare **Esegui script R**. Verrà visualizzato l'editor **Esegui script R**.  

   Nelle righe 15 e 20 mancano dei dati, così come in altre righe che non sono visibili nell'immagine. La procedura seguente mostra come usare R per completare automaticamente le righe.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_5d.png)

1. In questo esempio immettere il codice di script seguente. Assicurarsi di sostituire il percorso &lt;Your File Path&gt; con il percorso di **EuStockMarkets_NA.csv** nel file system locale, ad esempio C:/Utenti/John Doe/Documenti/Microsoft/EuStockMarkets_NA.csv

    ```r
       dataset <- read.csv(file="<Your File Path>/EuStockMarkets_NA.csv", header=TRUE, sep=",")
       library(mice)
       tempData <- mice(dataset,m=1,maxit=50,meth='pmm',seed=100)
       completedData <- complete(tempData,1)
       output <- dataset
       output$completedValues <- completedData$"SMI missing values"
    ```

    > [!NOTE]
    > Potrebbe essere necessario sovrascrivere una variabile denominata *output* per creare correttamente il nuovo set di dati con i filtri applicati.

7. Dopo aver selezionato **OK**, l'**Editor di query** visualizza un avviso relativo alla privacy dei dati.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_6.png)
8. Per il corretto funzionamento degli script R nel servizio Power BI, è necessario impostare tutte le origini dati su **Pubblico**. Per altre informazioni sulle impostazioni di privacy e sulle relative implicazioni, vedere [Livelli di privacy](desktop-privacy-levels.md).

   ![](media/desktop-r-in-query-editor/r-in-query-editor_7.png)

   Dopo la selezione di **Salva**, viene eseguito lo script. Si noti una nuova colonna nel riquadro **Campi** denominata **completedValues**. Si noti che alcuni elementi dati risultano mancanti, ad esempio nelle righe 15 e 18. Scoprire come questo problema viene gestito in R nella prossima sezione.

   Con appena cinque righe di script R, l'**Editor di query** ha inserito i valori mancanti con un modello predittivo.

## <a name="create-visuals-from-r-script-data"></a>Creare oggetti visivi da dati di script R

A questo punto è possibile creare un oggetto visivo per osservare come il codice script R che usa la libreria **mice** ha completato i valori mancanti, come illustrato nella figura seguente:

![](media/desktop-r-in-query-editor/r-in-query-editor_8a.png)

È possibile salvare tutti gli oggetti visivi completati in un file con estensione pbix di **Power BI Desktop** e usare il modello di dati e i relativi script R nel servizio Power BI.

> [!NOTE]
> È possibile scaricare un [file con estensione pbix](http://download.microsoft.com/download/F/8/A/F8AA9DC9-8545-4AAE-9305-27AD1D01DC03/Complete%20Values%20with%20R%20in%20PQ.pbix) con tutti questi passaggi completati.

Dopo aver caricato il file con estensione pbix nel servizio Power BI, è necessario eseguire altri passaggi per abilitare l'aggiornamento dei dati del servizio e gli oggetti visivi aggiornati:  

* **Abilitare l'aggiornamento pianificato per il set di dati**: per abilitare l'aggiornamento pianificato per la cartella di lavoro che contiene il set di dati con gli script R, vedere [Configurare l'aggiornamento pianificato](refresh-scheduled-refresh.md), che include anche informazioni su **Personal Gateway**.

* **Installare Personal Gateway**: è necessario che sia installata un'istanza di **Personal Gateway** nel computer in cui si trovano il file e l'installazione di **R**. Il servizio Power BI accede a tale cartella di lavoro ed esegue nuovamente il rendering degli oggetti visivi aggiornati. Per altre informazioni, vedere le istruzioni per [installare e configurare Personal Gateway](service-gateway-personal-mode.md).

## <a name="limitations"></a>Limitazioni

Esistono alcune limitazioni per le query che includono script R creati nell'**Editor di query**:

* Tutte le impostazioni dell'origine dati R devono essere impostate su **Pubblico**. Anche tutti gli altri passaggi in una query dell'**Editor di query** devono essere pubblici. Per ottenere le impostazioni dell'origine dati, in **Power BI Desktop** selezionare **File > Opzioni e impostazioni > Impostazioni origine dati**.

  ![](media/desktop-r-in-query-editor/r-in-query-editor_9.png)

  Nella finestra di dialogo **Impostazioni origine dati** selezionare una o più origini dati e quindi **Modifica autorizzazioni**.  Impostare **Livello di privacy** su **Pubblico**.

  ![](media/desktop-r-in-query-editor/r-in-query-editor_10.png)    
* Per abilitare l'aggiornamento pianificato degli oggetti visivi o del set di dati R, è necessario che sia abilitata l'opzione **Aggiornamento pianificato** e che **Personal Gateway** sia installato nel computer in cui si trovano la cartella di lavoro e l'installazione di **R**. Per altre informazioni su entrambi, vedere la sezione precedente di questo articolo, in cui sono riportati collegamenti a informazioni più specifiche.

Con R e le query personalizzate si possono eseguire moltissime operazioni, esplorando e modellando i dati per visualizzarli nel modo desiderato.

## <a name="next-steps"></a>Passaggi successivi

* [Introduzione a R](https://mran.microsoft.com/documents/what-is-r) 

* [Eseguire script R in Power BI Desktop](desktop-r-scripts.md) 

* [Usare un IDE R esterno con Power BI](desktop-r-ide.md) 

* [Pacchetti R nel servizio Power BI](service-r-packages-support.md)
