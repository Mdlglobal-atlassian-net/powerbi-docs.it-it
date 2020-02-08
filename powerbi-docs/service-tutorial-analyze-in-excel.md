---
title: 'Esercitazione: Usare Analizza in Excel'
description: In questa esercitazione si usa la pagina Set di dati di Power BI per importare i set di dati in Excel.
author: tejaskulkarni
ms.reviewer: davidiseminger
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 01/27/2020
ms.author: tekulkar
LocalizationGroup: Connect to services
ms.openlocfilehash: a68adccec019e64e554d199d23d7dddd782f56a2
ms.sourcegitcommit: 53c2b5ea4ee1fe2659804d5ccc8e4bb445a8bcad
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921486"
---
# <a name="tutorial-use-analyze-in-excel"></a>Esercitazione: Usare Analizza in Excel

L'organizzazione usa Power BI per condividere l'accesso ai dati. Con la funzionalità Analizza in Excel è possibile creare una tabella pivot e grafici pivot per aggiungere contesto all'analisi o ridurre il tempo necessario per individuare e importare i set di dati rilevanti.

Per iniziare, selezionare un set di dati, selezionare "Analizza in Excel". Verrà illustrata la creazione guidata di una tabella pivot in cui vengono usati i dati.  

È possibile trovare set di dati aggiuntivi condivisi dall'organizzazione tornando alla pagina Set di dati.

Se si verificano problemi in qualsiasi momento, selezionare No nel passaggio appropriato del flusso seguente e aggiungere commenti nel modulo collegato.  

In questa esercitazione viene illustrato come:

> [!div class="checklist"]
> * Scaricare un file ODC dalla pagina Set di dati di Power BI.
> * Abilitare l'accesso al set di dati da Excel.
> * Iniziare a usare il set di dati per creare tabelle pivot, grafici e fogli di foglio

## <a name="prerequisites"></a>Prerequisiti

Per completare questa esercitazione, sono necessari:

* Un account di Power BI. Se non si è ancora iscritti a Power BI, [iscriversi per ottenere una versione di prova gratuita](https://app.powerbi.com/signupredirect?pbi_source=web) prima di iniziare.

* Assicurarsi di avere familiarità con tutti i passaggi descritti nell'esercitazione [Introduzione al servizio Power BI](https://docs.microsoft.com/power-bi/service-get-started).

* Sono necessari un set di dati di Power BI Premium e una licenza di Power BI Pro. Vedere [Che cos'è Power BI Premium?](https://docs.microsoft.com/power-bi/service-premium-what-is) per altre informazioni.

* Per un elenco completo dei prerequisiti, vedere il documento completo [Analizza in Excel](https://docs.microsoft.com/power-bi/service-analyze-in-excel#requirements).

* Una [sottoscrizione di Microsoft Office E5](https://www.microsoft.com/microsoft-365/business/office-365-enterprise-e5-business-software?activetab=pivot%3aoverviewtab) attiva

## <a name="get-started"></a>Inizia

Partendo da Excel, selezionare l'opzione per creare tabelle pivot con dati condivisi di Power BI e passare alla pagina Set di dati di Power BI.

![Pagina Set di dati](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-01.png)

Quando si usa il flusso di lavoro Analizza in Excel, vengono visualizzate diverse richieste. Specificare se è stato completato ogni passaggio per poter proseguire. Se in uno dei passaggi si verificano problemi, selezionare **No** e aggiungere commenti nel modulo corrispondente.

![Istruzioni sul flusso di lavoro](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-02.png)

## <a name="download-and-open-the-odc-file"></a>Scaricare e aprire il file ODC

Scegliere il set di dati dall'elenco corrispondente e l'area di lavoro associata, quindi fare clic su Analizza in Excel. Power BI crea un file ODC e lo scarica dal browser nel computer.

![Selezionare il set di dati](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-03.png)

Quando il file viene aperto in Excel, viene visualizzato un elenco vuoto per Tabelle pivot e Campi con tutte le tabelle, i campi e le misure del set di dati di Power BI. È possibile creare tabelle pivot, grafici e analizzare tale set di dati esattamente come per un set di dati locale in Excel.

## <a name="enable-data-connections"></a>Abilitare le connessioni dati

Per analizzare i dati di Power BI dati in Excel, è possibile che venga richiesto di verificare l'attendibilità della connessione. Dal portale di amministrazione di Power BI gli amministratori possono disabilitare l'uso di Analizza in Excel con i set di dati locali contenuti in database di Analysis Services.

![Abilitare la connessione](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-04.png)

## <a name="install-updates-and-authenticate"></a>Installare aggiornamenti ed eseguire l'autenticazione

La prima volta che si apre un nuovo file ODC, potrebbe anche essere richiesto di eseguire l'autenticazione con l'account di Power BI.  In caso di problemi, vedere il documento completo [Analizza in Excel](https://docs.microsoft.com/power-bi/service-analyze-in-excel#sign-in-to-power-bi ) per altre informazioni oppure fare clic su No durante il flusso di lavoro.

![Abilitare la connessione](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-05.png)

## <a name="analyze-away"></a>Analizzare in qualsiasi luogo

Analogamente ad altre cartelle di lavoro locali, la funzionalità Analizza in Excel consente di creare tabelle pivot, grafici, aggiungere dati e creare fogli di lavoro diversi con visualizzazioni nei dati. L'uso di Analizza in Excel consente a tutti gli utenti che dispongono di un'autorizzazione per il set di dati di visualizzare dati dettagliati. È possibile salvare la cartella di lavoro, ma non è possibile pubblicarla o importarla di nuovo in Power BI oppure condividerla con altri utenti dell'organizzazione. Per altre informazioni e altri casi d'uso, vedere [Analizza in Excel](https://docs.microsoft.com/power-bi/service-analyze-in-excel#analyze-away).

## <a name="clean-up-resources"></a>Pulire le risorse

Le interazioni con il servizio Power BI e la pagina Set di dati devono essere limitate al download del file ODC e alla selezione del flusso di lavoro. In caso di problemi con uno di questi passaggi, specificare **No** nel passaggio appropriato e aggiungere commenti nel modulo collegato. Il modulo contiene un collegamento ad altre informazioni riguardanti il problema. Rivedere la pagina Set di dati per riprovare il processo o selezionare un altro set di dati.

## <a name="next-steps"></a>Passaggi successivi

Potrebbero essere interessanti anche gli articoli seguenti:

* [Usare il drill-through tra report in Power BI Desktop](https://docs.microsoft.com/power-bi/desktop-cross-report-drill-through)

* [Uso dei filtri dei dati in Power BI Desktop](https://docs.microsoft.com/power-bi/visuals/power-bi-visualization-slicers)
