---
title: 'Guida introduttiva: Connettersi ai dati'
description: Connettersi a un'origine dati in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: quickstart
ms.date: 05/07/2018
ms.author: davidi
LocalizationGroup: quickstart
ms.openlocfilehash: 3f29bd899c62adbe2de1fdedd25b60cb104c71e0
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34287832"
---
# <a name="quickstart-connect-to-data-in-power-bi-desktop"></a>Guida introduttiva: Connettersi ai dati in Power BI Desktop

In questa guida introduttiva viene stabilita una connessione ai dati usando **Power BI Desktop**, ovvero il primo passaggio per la compilazione di modelli di dati e la creazione di report.

![Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_01.png)

Se non si è ancora iscritti a Power BI, [iscriversi per ottenere una versione di prova gratuita](https://app.powerbi.com/signupredirect?pbi_source=web) prima di iniziare.

## <a name="prerequisites"></a>Prerequisiti

Per completare i passaggi descritti in questo articolo, è necessario quanto segue:
* Scaricare e installare **Power BI Desktop**, ovvero un'applicazione gratuita che viene eseguita nel computer locale. È possibile [scaricare **Power BI Desktop**](https://powerbi.microsoft.com/desktop) direttamente oppure [da **Microsoft Store**](http://aka.ms/pbidesktopstore).
* [Scaricare questa cartella di lavoro di Excel di esempio](http://go.microsoft.com/fwlink/?LinkID=521962) e creare una cartella denominata *C:\PBID-qs* in cui archiviare il file di Excel. I passaggi successivi di questa guida introduttiva presuppongono che questo sia il percorso della cartella di lavoro di Excel scaricata.

## <a name="launch-power-bi-desktop"></a>Avviare Power BI Desktop

Dopo avere installato **Power BI Desktop**, avviare l'applicazione in modo che venga eseguita nel computer locale. Viene visualizzata un'area di disegno vuota, in cui è possibile creare oggetti visivi e report dai dati a cui ci si connette. 

![Power BI Desktop - Area di disegno vuota](media/desktop-quickstart-connect-to-data/qs-connect-data_01.png)

## <a name="connect-to-data"></a>Connettersi ai dati

**Power BI Desktop** permette di connettersi a molti tipi diversi di dati. È possibile connettersi a origini dati di base come un file di Microsoft Excel, oltre che a servizi online contenenti tutti i tipi di dati come Salesforce, Microsoft Dynamics, Archiviazione BLOB di Azure e molto altro ancora. 

Per connettersi ai dati, dalla barra multifunzione **Home** selezionare **Dati**.

![Recupera dati](media/desktop-quickstart-connect-to-data/qs-connect-data_02.png)

Viene visualizzata la finestra **Recupera dati**, in cui è possibile scegliere tra una serie di origini dati diverse a cui **Power BI Desktop** può connettersi. In questa guida introduttiva viene usata la cartella di lavoro di Excel scaricata in precedenza, descritta nella sezione *Prerequisiti* all'inizio di questo articolo. 

![Recupera dati](media/desktop-quickstart-connect-to-data/qs-connect-data_03.png)

Trattandosi di un file di Excel, selezionare **Excel** nella finestra **Recupera dati** e quindi scegliere il pulsante **Connetti**.

Viene richiesto di specificare il percorso del file di Excel a cui ci si vuole connettere. Il file scaricato è chiamato *Financial Sample*, pertanto selezionare questo file e quindi scegliere **Apri**.

![Recupera dati](media/desktop-quickstart-connect-to-data/qs-connect-data_04.png)

**Power BI Desktop** carica la cartella di lavoro e ne legge il contenuto, quindi mostra i dati disponibili nel file tramite la finestra **Strumento di navigazione**, in cui è possibile scegliere quali dati caricare in Power BI Desktop. Selezionare le tabelle selezionando la casella di controllo accanto a ogni tabella che si vuole importare. In questo caso si importeranno entrambe le tabelle disponibili.

![Recupera dati](media/desktop-quickstart-connect-to-data/qs-connect-data_05.png)

Dopo avere effettuato le selezioni, scegliere **Carica** per importare i dati in Power BI Desktop.

## <a name="view-data-in-the-fields-pane"></a>Visualizzare i dati nel riquadro Campi

Dopo che le tabelle sono state caricate, il riquadro **Campi** mostra i dati disponibili. È possibile espandere ogni tabella facendo clic sul triangolo accanto al nome. Nella figura seguente viene espansa la tabella *financials*, in modo da visualizzare tutti i campi contenuti. 

![Recupera dati](media/desktop-quickstart-connect-to-data/qs-connect-data_06.png)

Non sono necessarie altre operazioni. È stata stabilita la connessione ai dati in **Power BI Desktop**, sono stati caricati i dati e ora è possibile visualizzare tutti i campi disponibili all'interno delle tabelle.


## <a name="next-steps"></a>Passaggi successivi
Dopo essersi connessi ai dati, è possibile eseguire qualsiasi tipo di operazione con **Power BI Desktop**, ad esempio creare oggetti visivi e report. Esaminare le risorse seguenti per iniziare:

* [Guida introduttiva per Power BI Desktop](desktop-getting-started.md)


