---
title: Dati dei report nel Generatore report di Power BI
description: Il primo passaggio della progettazione di un report in Power BI Report Builder consiste nel creare origini dati e set di dati che rappresentano i dati del report sottostanti.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.custom: seodec18
ms.date: 06/06/2019
ms.openlocfilehash: fea4e4927b009e30bc040593f9237cc49ff73956
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "78921448"
---
# <a name="report-data-in-power-bi-report-builder"></a>Dati dei report nel Generatore report di Power BI

I dati del report possono provenire da più origini dati dell'organizzazione. Il primo passaggio della progettazione di un report di Generatore report impaginati di Power BI consiste nel creare origini dati e set di dati che rappresentano i dati del report sottostanti. Ogni origine dati include le informazioni di connessione dati. Ogni set di dati include un comando di query che definisce il set di campi da usare come dati di un'origine dati. Per visualizzare i dati di ogni set di dati, aggiungere un'area dati, ad esempio una tabella, una matrice, un grafico o una mappa. Durante l'elaborazione del report, le query vengono eseguite sull'origine dati e ogni area dati viene espansa in base alle esigenze per visualizzare i risultati della query per il set di dati.  

Per informazioni, vedere [Creare un'origine dati incorporata per i report impaginati nel Generatore report di Power BI](paginated-reports-embedded-data-source.md).


##  <a name="terms"></a><a name="BkMk_ReportDataTerms"></a> Termini  
  
- **Connessione dati.** Chiamata anche *origine dati*. Una connessione dati include un nome e le proprietà di connessione che dipendono dal tipo di connessione. Per impostazione predefinita, una connessione dati non include le credenziali. Una connessione dati non specifica i dati da recuperare dall'origine dati esterna. A tale scopo, specificare una query quando si crea un set di dati.  
  
- **Stringa di connessione.** Una stringa di connessione è una versione stringa delle proprietà di connessione necessarie per connettersi a un'origine dati. Le proprietà di connessione variano in base al tipo di connessione dati.  
  
- **Origine dati incorporata.** Chiamata anche *origine dati specifica del report*. Un'origine dati definita in un report e usata solo da quel report.  
  
- **Credenziali.** Le credenziali sono le informazioni di autenticazione che devono essere fornite per consentire l'accesso ai dati esterni.  
  
##  <a name="tips-for-specifying-report-data"></a><a name="BkMk_ReportDataTips"></a> Suggerimenti per la specifica dei dati del report

 Usare le informazioni seguenti per progettare la strategia relativa ai dati del report.  
  
- **Filtrare i dati** I dati del report possono essere filtrati nella query o nel report. È possibile usare set di dati e variabili di query per creare parametri a catena e offrire all'utente la possibilità di ridurre le migliaia di selezioni possibili a un numero più gestibile. È possibile filtrare i dati in una tabella o un grafico in base a valori di parametro o altri valori specificati.  
  
- **Parametri** I comandi di query del set di dati che includono automaticamente le variabili di query creano parametri di report corrispondenti. È anche possibile creare i parametri manualmente. Quando si visualizza un report, la barra degli strumenti del report visualizza i parametri. Gli utenti possono selezionare i valori per controllare i dati o l'aspetto del report. Per personalizzare i dati del report per destinatari specifici, è possibile creare set di parametri di report con valori predefiniti diversi collegati alla stessa definizione di report o usare il campo predefinito **UserID**. 
  
- **Raggruppare e aggregare i dati** I dati del report possono essere raggruppati e aggregati nella query o nel report. Se si aggregano i valori nella query, è possibile continuare a combinare i valori nel report all'interno dei vincoli di ciò che è significativo.  
  
- **Ordinare i dati** I dati del report possono essere ordinati nella query o nel report. Nelle tabelle è anche possibile aggiungere un pulsante di ordinamento interattivo per consentire all'utente di controllare l'ordinamento.  
  
- **Dati basati su un'espressione** Poiché la maggior parte delle proprietà del report possono essere basate su un'espressione e le espressioni possono includere riferimenti a campi di set di dati e a parametri del report, è possibile scrivere espressioni efficaci per controllare i dati e l'aspetto del report. È possibile offrire all'utente la possibilità di controllare i dati visualizzati tramite la definizione di parametri.  
  
- **Visualizzare i dati di un set di dati** I dati di un set di dati sono in genere visualizzati in una o più aree dati, ad esempio una tabella e un grafico.  
  
- **Visualizzare i dati di più set di dati** È possibile scrivere espressioni in un'area dati basata su un set di dati che cercano valori o aggregazioni in altri set di dati. È possibile includere sottoreport in una tabella basata su un set di dati per visualizzare i dati di un'origine dati diversa.  
  
 Usare l'elenco seguente per definire le origini dati di un report.  
  
- Comprendere l'architettura dei livelli dati software dell'organizzazione e i problemi potenziali derivanti dai tipi di dati. Comprendere in che modo le estensioni per i dati e le estensioni per l'elaborazione dati possono influire sui risultati delle query. I tipi di dati variano a seconda dell'origine dati, dei provider di dati e dei tipi di dati archiviati nel file di definizione del report (file con estensione rdl).  
  
- Le origini dati e i set di dati vengono creati in un report e pubblicati nel servizio Power BI. Dopo la pubblicazione, le credenziali possono essere configurate direttamente nel servizio Power BI o nel gateway aziendale. 

## <a name="next-steps"></a>Passaggi successivi

- [Che cosa sono i report impaginati in Power BI Premium?](paginated-reports-report-builder-power-bi.md)  
- [Linee guida per il recupero dei dati per i report impaginati](../guidance/report-paginated-data-retrieval.md)
