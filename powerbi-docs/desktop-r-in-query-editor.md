---
title: Uso di R nell'Editor di query di Power BI
description: Usare R nell'Editor di query di Power BI Desktop per l'analisi avanzata
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/12/2017
ms.author: davidi
ms.openlocfilehash: c48e7042f16ac43619a7a0a6708a54f0575d795f
ms.sourcegitcommit: f2b38777ca74c28f81b25e2f739e4835a0ffa75d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="using-r-in-query-editor"></a>Uso di R nell'Editor di query
È possibile usare **R**, un linguaggio di programmazione ampiamente utilizzato da analisti e data scientist, nell'**Editor di query** di Power BI Desktop. L'integrazione di R nell'**Editor di query** consente di pulire i dati con R ed eseguire operazioni di data shaping e analisi in set di dati, tra cui completamento di dati mancanti, stime e clustering. **R** è un linguaggio potente e può essere usato nell'**Editor di query** per preparare il modello di dati e creare report.

## <a name="installing-r"></a>Installazione di R
Per usare **R** nell'**Editor di query** di Power BI Desktop, è necessario installare **R** nel computer locale. È possibile scaricare e installare **R** gratuitamente da molte posizioni, tra cui la [pagina di download di Revolution Open](https://mran.revolutionanalytics.com/download/) e il [repository CRAN](https://cran.r-project.org/bin/windows/base/).

## <a name="using-r-in-query-editor"></a>Uso di R nell'Editor di query
Per illustrare l'uso di **R** nell'**Editor di query** si userà un esempio tratto da un set di dati del mercato azionario, basato su un file CSV che è possibile [scaricare qui](http://download.microsoft.com/download/F/8/A/F8AA9DC9-8545-4AAE-9305-27AD1D01DC03/EuStockMarkets_NA.csv) per seguire la spiegazione. Ecco la procedura per questo esempio:

1. Prima di tutto, caricare i dati in **Power BI Desktop**. In questo esempio si caricherà il file *EuStockMarkets_NA.csv*. Selezionare **Recupera dati > CSV** nella scheda **Home** della barra multifunzione in **Power BI Desktop**.
   
   ![](media/desktop-r-in-query-editor/r-in-query-editor_1.png)
2. Selezionare il file e scegliere **Apri**. Il file CSV verrà visualizzato nella finestra di dialogo **File CSV**.
   
   ![](media/desktop-r-in-query-editor/r-in-query-editor_2.png)
3. Una volta caricati, i dati saranno visibili nel riquadro **ampi** in Power BI Desktop.
   
   ![](media/desktop-r-in-query-editor/r-in-query-editor_3.png)
4. Aprire l'**Editor di query** selezionando **Modifica query** nella scheda **Home** in **Power BI Desktop**.
   
   ![](media/desktop-r-in-query-editor/r-in-query-editor_4.png)
5. Nella scheda **Trasforma** selezionare **Esegui script R**. Verrà visualizzato l'editor **Esegui script R** (illustrato nel passaggio successivo). Si noti che nelle righe 15 e 20 c'è un problema di dati mancanti, così come in altre righe non visibili nell'immagine seguente. La procedura seguente mostra come usare R per completare automaticamente le righe.
   
   ![](media/desktop-r-in-query-editor/r-in-query-editor_5d.png)
6. In questo esempio si immetterà il codice script seguente:
   
       library(mice)
       tempData <- mice(dataset,m=1,maxit=50,meth='pmm',seed=100)
       completedData <- complete(tempData,1)
       output <- dataset
       output$completedValues <- completedData$"SMI missing values"
   
   > [!NOTE]
   > Per il corretto funzionamento del codice script precedente, è necessario che nell'ambiente R sia installata la libreria *mice*. Per installare mice, eseguire quanto segue nell'installazione di R: |      > install.packages('mice')
   > 
   > 
   
   Quando viene inserito nella finestra di dialogo **Esegui script R**, il codice sarà analogo al seguente:
   
   ![](media/desktop-r-in-query-editor/r-in-query-editor_5b.png)
7. Quando si seleziona **OK**, l'**Editor di query** mostra un avviso relativo alla privacy dei dati.
   
   ![](media/desktop-r-in-query-editor/r-in-query-editor_6.png)
8. Per il corretto funzionamento degli script R nel servizio Power BI, è necessario impostare tutte le origini dati su *pubblico*. Per altre informazioni sulle impostazioni di privacy e sulle relative implicazioni, vedere [Livelli di privacy](desktop-privacy-levels.md).
   
   ![](media/desktop-r-in-query-editor/r-in-query-editor_7.png)
   
   A questo punto viene visualizzata una nuova colonna nell'area **Campi** denominata *completedValues*. Si noti che alcuni elementi dati risultano mancanti, ad esempio nelle righe 15 e 18. Nella prossima sezione si vedrà come questo problema viene gestito in R.
   

Con appena cinque righe di script R, l'**Editor di query** ha inserito i valori mancanti con un modello predittivo.

## <a name="creating-visuals-from-r-script-data"></a>Creazione di oggetti visivi da dati di script R
A questo punto è possibile creare un oggetto visivo per osservare come il codice script R con la libreria *mice* ha completato i valori mancanti, come mostrato nella figura seguente.

![](media/desktop-r-in-query-editor/r-in-query-editor_8a.png)

Una volta completato l'oggetto visivo e qualsiasi altro oggetto visivo si voglia creare con **Power BI Desktop**, è possibile salvare il file di **Power BI Desktop** (che viene salvato con estensione pbix) e quindi usare il modello di dati, compresi gli script R che ne fanno parte, nel servizio Power BI.

> [!NOTE]
> Se si vuole visualizzare un file con estensione pbix completato con questa procedura, il file di **Power BI Desktop** completato usato in questo esempio è disponibile per il download [qui](http://download.microsoft.com/download/F/8/A/F8AA9DC9-8545-4AAE-9305-27AD1D01DC03/Complete Values with R in PQ.pbix).
> 
> 

Dopo avere caricato il file con estensione pbix nel servizio Power BI, è necessario eseguire alcuni altri passaggi per abilitare l'aggiornamento dei dati (nel servizio) e per abilitare l'aggiornamento degli oggetti visivi nel servizio (i dati devono accedere a R perché gli oggetti visivi vengano aggiornati). I passaggi aggiuntivi sono i seguenti:

* **Abilitare l'aggiornamento pianificato per il set di dati**: per abilitare l'aggiornamento pianificato per la cartella di lavoro che contiene il set di dati con gli script R, vedere [Configurazione dell'aggiornamento pianificato](refresh-scheduled-refresh.md), che include anche informazioni su **Personal Gateway**.
* **Installare Personal Gateway**: è necessario che sia installato **Personal Gateway** nel computer in cui si trova il file e in cui è installato R. Il servizio Power BI deve accedere alla cartella di lavoro ed eseguire nuovamente il rendering degli oggetti visivi aggiornati. Sono disponibili altre informazioni su come [installare e configurare Personal Gateway](personal-gateway.md).

## <a name="limitations"></a>Limitazioni
Esistono alcune limitazioni per le query che includono script R creati nell'**Editor di query**:

* Tutte le impostazioni dell'origine dati R devono essere impostate su *Pubblico* e anche tutti gli altri passaggi di una query creata nell'**Editor di query** devono essere pubblici. Per ottenere le impostazioni dell'origine dati, in **Power BI Desktop** selezionare **File > Opzioni e impostazioni > Impostazioni origine dati**.
  
  ![](media/desktop-r-in-query-editor/r-in-query-editor_9.png)
  
  Nella finestra di dialogo **Impostazioni origine dati** selezionare le origini dati e quindi scegliere **Modifica autorizzazioni** per assicurarsi che il **Livello di privacy** sia impostato su *Pubblico*.
  
  ![](media/desktop-r-in-query-editor/r-in-query-editor_10.png)    
* Per abilitare l'aggiornamento pianificato degli oggetti visivi o del set di dati R, è necessario abilitare l'opzione **Aggiornamento pianificato** e che nel computer che ospita la cartella di lavoro e l'installazione di R sia installato **Personal Gateway**. Per altre informazioni su entrambi, vedere la sezione precedente di questo articolo, in cui sono riportati collegamenti a informazioni più specifiche.

Con R e le query personalizzate si possono eseguire moltissime operazioni, esplorando e modellando i dati per visualizzarli nel modo desiderato.

