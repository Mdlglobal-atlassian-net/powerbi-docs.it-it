---
title: Report impaginati nel servizio Power BI
description: Documentazione che descrive i report impaginati e come visualizzarli nel servizio Power BI
author: mihart
ms.reviewer: chris finlan
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: mihart
LocalizationGroup: Common tasks
ms.openlocfilehash: 0ab2ececd4ede03a10094be53a2c08617463cc53
ms.sourcegitcommit: 480bba9c745cb9af2005637e693c5714b3c64a8a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/11/2020
ms.locfileid: "79113108"
---
# <a name="paginated-reports-in-the-power-bi-service"></a>Report impaginati nel servizio Power BI

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

I [report di Power BI](end-user-reports.md) sono già stati presentati e questi sono i tipi di report con i quali ci si troverà più probabilmente a interagire. Esiste tuttavia un altro tipo di report denominato *report impaginato*. I *progettisti* di report possono condividere i report impaginati con altri utenti in un'area di lavoro in una capacità Premium o in un'app da tale area di lavoro. 

## <a name="what-is-a-paginated-report"></a>Che cos'è un report impaginato?

Questi report vengono definiti *impaginati* perché sono formattati in modo da adattarsi meglio alla pagina per la stampa. Uno dei vantaggi è che visualizzano tutti i dati in una tabella, anche se la tabella si estende su più pagine. I report impaginati vengono talvolta definiti "perfetti al pixel" perché i *progettisti* dei report possono controllare esattamente il layout di pagina del report.

Quando i *progettisti* di report creano un report impaginato, creano in effetti una *definizione del report*. che non contiene i dati. La definizione specifica dove ottenere i dati, quali dati ottenere e come visualizzarli. Quando si esegue il report, l'elaboratore di report acquisisce la definizione del report, recupera i dati e li combina con il layout del report per generare il report. In alcuni casi, nel report vengono visualizzati dati predefiniti. In altri casi è necessario immettere i parametri prima che il report possa visualizzare i dati. 

   ![Parametri per il report](./media/end-user-paginated-report/power-bi-report-parameters.png)

Questo è in genere il livello di interazione richiesto, ovvero l'impostazione dei parametri. I responsabili della fatturazione potrebbero usare report impaginati per creare o stampare fatture. Un direttore delle vendite potrebbe usare i report impaginati per visualizzare gli ordini per negozio o venditore. 

Questo report impaginato semplice visualizza i profitti in base all'anno, dopo aver selezionato il parametro **Year**. 

![Semplice report con un solo parametro](./media/end-user-paginated-report/power-bi-report-simple.png)

Rispetto ai report impaginati, i report di Power BI sono molto più interattivi. I report di Power BI consentono di realizzare report ad hoc e supportano molti più tipi di oggetti visivi, inclusi gli oggetti visivi personalizzati.

## <a name="identify-a-paginated-report"></a>Identificare un report impaginato

Negli elenchi di contenuto e nella pagina di destinazione Home i report impaginati possono essere identificati tramite la relativa icona ![icona di report impaginato](media/end-user-paginated-report/power-bi-report-icon.png).  Un report impaginato può essere condiviso direttamente con altri utenti o come parte di un'[app di Power BI](end-user-apps.md). Se il *progettista del report* concede le autorizzazioni, sarà possibile ricondividere il report impaginato e sottoscriverlo per se stessi o altri utenti.

![elenco di report che mostra icone diverse](./media/end-user-paginated-report/power-bi-report-list.png)

## <a name="interact-with-a-paginated-report"></a>Interagire con un report impaginato

La modalità di interazione con un report impaginato è diversa rispetto agli altri report. È possibile eseguire operazioni quali stampa, aggiunta di segnalibri, esportazione e aggiunta di commenti, ma è disponibile una minore interattività. Spesso, i report impaginati richiedono un input da parte dell'utente per popolare il canvas del report.  In altri casi il report visualizza i dati predefiniti ed è possibile immettere i parametri per visualizzare dati diversi.

### <a name="print-a-paginated-report"></a>Stampare un report impaginato

I report *impaginati* sono formattati in modo da adattarsi perfettamente a una pagina e per la stampa. Ciò che viene visualizzato nel browser è quello che si ottiene nella stampa. Inoltre, se il report include una tabella estesa, viene stampata l'intera tabella anche se si estende su più pagine. 

I report impaginati possono avere molte pagine. Ad esempio, questo report contiene 563 pagine. Ogni pagina ha un layout esatto, con una pagina per ogni fattura e intestazioni e piè di pagina ripetuti. Quando si stampa questo report, si otterranno interruzioni di pagina tra le fatture.

   ![Pagina di un report impaginato per Tailspin Toys](./media/end-user-paginated-report/power-bi-paginated-500.png)


### <a name="navigate-the-paginated-report"></a>Spostarsi all'interno del report impaginato

In questo report degli ordini di vendita sono disponibili tre parametri: Business type, Reseller e Order (numero). 

![report con tre parametri](./media/end-user-paginated-report/power-bi-parameter.png)

Per modificare le informazioni visualizzate, immettere nuovi valori per i tre parametri e selezionare **Visualizza report**. In questo esempio sono stati selezionati i valori **Specialty bike shop**, **Alpine Ski House** e il numero di ordine **SO46085**. Selezionando **Visualizza report** viene aggiornato il canvas del report con questo nuovo ordine di vendita.

![modificare i parametri](./media/end-user-paginated-report/power-bi-order.png)

Viene visualizzato il nuovo ordine di vendita con i parametri selezionati. 

![un nuovo ordine di vendita](./media/end-user-paginated-report/power-bi-new-order.png)

Alcuni report impaginati possono includere molte pagine.  Usare i controlli della pagina per spostarsi nel report. 

![controlli della pagina](./media/end-user-paginated-report/power-bi-page.png)

### <a name="export-the-paginated-report"></a>Esportare il report impaginato
Sono disponibili diverse opzioni per l'esportazione di report impaginati, tra cui PDF, Word, XML, PowerPoint, Excel e altro ancora. Con l'esportazione viene mantenuta la maggior parte della formattazione possibile. I report impaginati esportati in Excel, Word, PowerPoint, MHTML e PDF, ad esempio, mantengono la formattazione "perfetta al pixel". 

![un nuovo ordine di vendita](./media/end-user-paginated-report/power-bi-exporting.png)

![quattro tipi di esportazione diversi](./media/end-user-paginated-report/power-bi-four.png)

### <a name="subscribe-to-the-paginated-report"></a>Sottoscrivere il report impaginato
Quando si sottoscrive un report impaginato, Power BI invia un messaggio di posta elettronica con il report come allegato. Durante la configurazione della sottoscrizione, è possibile scegliere la frequenza di ricezione dei messaggi di posta elettronica: giornaliera, settimanale, oraria oppure mensile. La sottoscrizione contiene un allegato con l'output dell'intero report, con dimensioni massime di 25 MB. Esportare l'intero report o scegliere i parametri in anticipo. È possibile scegliere tra diversi tipi di allegati, tra cui Excel, PDF, PowerPoint e altro ancora.  

![Formati per la sottoscrizione](./media/end-user-paginated-report/power-bi-export-list.png)

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi

- Un report impaginato può essere vuoto fino a quando non si selezionano i parametri e si sceglie **Visualizza report**.

- Se non sono presenti report impaginati, è possibile che nessuno abbia condiviso questo tipo di report. Potrebbe anche significare che l'amministratore di sistema non ha abilitato i report impaginati. 

 

## <a name="next-steps"></a>Passaggi successivi
- [Report di Power BI](end-user-reports.md)
- Altre domande? Provare la [Community di Power BI](https://community.powerbi.com/).

