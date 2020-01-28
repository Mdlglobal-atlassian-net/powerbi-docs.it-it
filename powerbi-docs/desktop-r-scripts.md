---
title: Esecuzione di script R in Power BI Desktop
description: Esecuzione di script R in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/14/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 358a61c13418bd29a9e83ed7029e8b90f9a5988e
ms.sourcegitcommit: 3d6b27e3936e451339d8c11e9af1a72c725a5668
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2020
ms.locfileid: "76161537"
---
# <a name="run-r-scripts-in-power-bi-desktop"></a>Esecuzione di script R in Power BI Desktop

È possibile eseguire gli script R direttamente in Power BI Desktop e importare i set di dati risultanti in un modello di dati di Power BI Desktop.

## <a name="install-r"></a>Installare R

Per eseguire script R in Power BI Desktop è necessario installare R nel computer locale. È possibile scaricare e installare R gratuitamente da molte posizioni, tra cui [Microsoft R Application Network](https://mran.revolutionanalytics.com/download/) e il [repository CRAN](https://cran.r-project.org/bin/windows/base/). La versione corrente supporta la presenza di caratteri Unicode e di spazi (caratteri vuoti) all'interno del percorso di installazione.

## <a name="run-r-scripts"></a>Eseguire gli script R

Con pochi passaggi in Power BI Desktop è possibile eseguire script R e creare un modello di dati. Con il modello di dati è possibile creare report e condividerli nel servizio Power BI. Lo script R in Power BI Desktop ora supporta i formati di numero contenenti separatori decimali (.) e virgole (,).

### <a name="prepare-an-r-script"></a>Preparare uno script R

Per eseguire uno script R in Power BI Desktop, creare lo script nell'ambiente di sviluppo locale R e verificare che venga eseguito correttamente.

Per eseguire lo script in Power BI Desktop, assicurarsi che lo script venga eseguito correttamente in un'area di lavoro nuova e non modificata. Questo prerequisito significa che tutti i pacchetti e le dipendenze devono essere caricati ed eseguiti esplicitamente. È possibile usare `source()` per eseguire gli script dipendenti.

La preparazione e l'esecuzione di uno script R in Power BI Desktop sono soggette ad alcune limitazioni:

* Poiché vengono importati solo i frame di dati, assicurarsi di rappresentare i dati da importare in Power BI in un frame di dati.
* Le colonne di tipo complesso e vettore non vengono importate e vengono sostituite con valori di errore nella tabella creata.
* In Power BI Desktop i valori `N/A` vengono convertiti in valori `NULL`.
* Se uno script R viene eseguito per più di 30 minuti genera un timeout.
* Le chiamate interattive all'interno dello script R, ad esempio l'attesa dell'input dell'utente, interrompono l'esecuzione dello script.
* Quando si imposta la directory di lavoro all'interno dello script R *è necessario* definire un percorso completo a questa directory, anziché un percorso relativo.

### <a name="run-your-r-script-and-import-data"></a>Eseguire lo script R e importare i dati

Ora è possibile eseguire lo script R per importare i dati in Power BI Desktop:

1. In Power BI Desktop selezionare **Recupera dati**, quindi scegliere **Altro** > **Script R** e selezionare **Connetti**:

    ![Connetti a script R, categoria Altro, finestra di dialogo Recupera dati, Power BI Desktop](media/desktop-r-scripts/r-scripts-1.png)

2. Se R è installato nel computer locale, è sufficiente copiare lo script nella finestra dello script e selezionare **OK**. La versione installata più recente viene visualizzata come motore R.

    ![Finestra di dialogo Script R, Power BI Desktop](media/desktop-r-scripts/r-scripts-2.png)

3. Selezionare **OK** per eseguire lo script R. Quando lo script viene eseguito correttamente, è possibile scegliere i frame di dati risultante da aggiungere al modello di Power BI.

È possibile controllare quale installazione R usare per eseguire lo script. Per specificare le impostazioni di installazione R scegliere **File** > **Opzioni e impostazioni** > **Opzioni** e selezionare **Script R**. In **Opzioni per gli script R** l'elenco a discesa **Home directory di R rilevate** visualizza le scelte per l'installazione di R correnti. Se l'installazione di R desiderata non è presente nell'elenco, selezionare **Altro** e quindi passare alla cartella di installazione di R preferita o immetterne il nome in **Impostare una home directory per R**.

![Opzioni di script R, Finestra di dialogo Opzioni, Power BI Desktop](media/desktop-r-scripts/r-scripts-4.png)

### <a name="refresh"></a>Aggiorna

È possibile aggiornare uno script R in Power BI Desktop. Quando si aggiorna uno script R, Power BI Desktop esegue nuovamente lo script R nell'ambiente di Power BI Desktop.

## <a name="next-steps"></a>Passaggi successivi

Esaminare le informazioni aggiuntive seguenti su R in Power BI.

* [Creare oggetti visivi di Power BI usando R](desktop-r-visuals.md)
* [Usare un IDE R esterno con Power BI](desktop-r-ide.md)
