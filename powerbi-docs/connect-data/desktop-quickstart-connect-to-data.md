---
title: 'Avvio rapido: Connettersi ai dati in Power BI Desktop'
description: Come connettersi alle origini dati disponibili in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: quickstart
ms.date: 01/10/2020
ms.author: davidi
LocalizationGroup: quickstart
ms.openlocfilehash: d689258b4e4da5349d57b41f72d4266eb759029b
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83348598"
---
# <a name="quickstart-connect-to-data-in-power-bi-desktop"></a>Guida introduttiva: Connettersi ai dati in Power BI Desktop

In questo argomento di avvio rapido viene stabilita una connessione ai dati usando Power BI Desktop, che costituisce il primo passaggio per la compilazione di modelli di dati e la creazione di report.

![Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_01.png)

Se non si è ancora registrati in Power BI, [registrarsi per ottenere una versione di prova gratuita ](https://app.powerbi.com/signupredirect?pbi_source=web) prima di iniziare.

## <a name="prerequisites"></a>Prerequisiti

Per seguire la procedura descritta in questo articolo, sono necessarie le risorse seguenti:

* Scaricare e installare Power BI Desktop, un'applicazione gratuita eseguita nel computer locale. È possibile [scaricare Power BI Desktop](https://powerbi.microsoft.com/desktop) direttamente oppure da [Microsoft Store](https://aka.ms/pbidesktopstore).
* [Scaricare questa cartella di lavoro di Excel di esempio](https://go.microsoft.com/fwlink/?LinkID=521962) e creare una cartella denominata *C:\PBID-qs* in cui archiviare il file di Excel. I passaggi successivi di questo argomento di avvio rapido presuppongono che questo sia il percorso della cartella di lavoro di Excel scaricata.
* Molti connettori dati di Power BI Desktop richiedono Internet Explorer 10 (o versione successiva) per l'autenticazione.

## <a name="launch-power-bi-desktop"></a>Avviare Power BI Desktop

Dopo aver installato Power BI Desktop, avviare l'applicazione in modo che venga eseguita nel computer locale. Viene visualizzata un'esercitazione di Power BI. Eseguire l'esercitazione o chiudere la finestra di dialogo per iniziare con un'area di disegno vuota, che consente di creare grafici e report a partire dai dati.

![Power BI Desktop con un'area di disegno vuota](media/desktop-quickstart-connect-to-data/qs-connect-data_01.png)

## <a name="connect-to-data"></a>Connettersi ai dati

Power BI Desktop consente di connettersi a molti tipi diversi di dati, tra cui origini dati di base come un file di Microsoft Excel o servizi online contenenti tutti i tipi di dati, ad esempio Salesforce, Microsoft Dynamics, archiviazione BLOB di Azure e molti altri.

Per connettersi ai dati, dalla barra multifunzione **Home** selezionare **Dati**.

![Opzione Recupera dati sulla scheda Home della barra multifunzione](media/desktop-quickstart-connect-to-data/qs-connect-data_02.png)

Viene visualizzata la finestra **Recupera dati**, in cui è possibile scegliere tra una serie di origini dati diverse a cui Power BI Desktop può connettersi. In questo argomento di avvio rapido viene usata la cartella di lavoro di Excel scaricata al passaggio [Prerequisiti](#prerequisites).

![Tutte le origini per Recupera dati](media/desktop-quickstart-connect-to-data/qs-connect-data_03.png)

Poiché l'origine dati è un file di Excel, selezionare **Excel** nella finestra **Recupera dati** e quindi scegliere il pulsante **Connetti**.

Power BI chiede di specificare il percorso del file di Excel a cui connettersi. Il file scaricato è chiamato *Financial Sample*. Selezionare il file e quindi **Apri**.

![Recupera dati in Financial Sample](media/desktop-quickstart-connect-to-data/qs-connect-data_04.png)

Power BI Desktop carica la cartella di lavoro e ne legge il contenuto, quindi mostra i dati disponibili nel file tramite la finestra **Strumento di navigazione**, in cui è possibile scegliere quali dati caricare in Power BI Desktop. Scegliere le tabelle selezionando la casella di controllo accanto a ogni tabella che si vuole importare. Importare entrambe le tabelle disponibili.

![Selezione dei dati nella finestra Strumento di navigazione](media/desktop-quickstart-connect-to-data/qs-connect-data_05.png)

Dopo avere effettuato le selezioni, scegliere **Carica** per importare i dati in Power BI Desktop.

## <a name="view-data-in-the-fields-pane"></a>Visualizzare i dati nel riquadro Campi

Dopo che le tabelle sono state caricate, il riquadro **Campi** mostra i dati disponibili. È possibile espandere ogni tabella facendo clic sulla freccia accanto al nome. Nella figura seguente viene espansa la tabella *financials*, in modo da visualizzare tutti i campi contenuti.

![Recuperare i dati](media/desktop-quickstart-connect-to-data/qs-connect-data_06.png)

Non sono necessarie altre operazioni. È stata stabilita la connessione ai dati in Power BI Desktop, sono stati caricati i dati e ora è possibile visualizzare tutti i campi disponibili all'interno delle tabelle.

## <a name="next-steps"></a>Passaggi successivi

Dopo essersi connessi ai dati, è possibile eseguire qualsiasi tipo di operazione con Power BI Desktop, tra cui creare grafici e report. Esaminare le risorse seguenti per iniziare:

* [Introduzione a Power BI Desktop](../fundamentals/desktop-getting-started.md)
