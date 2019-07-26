---
title: Sottoscrivere report impaginati nel servizio Power BI
description: In questo articolo vengono illustrati aspetti importanti sulla sottoscrizione di report impaginati nel servizio Power BI.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 07/15/2019
ms.openlocfilehash: 2d48892450bbf6ab09a4bc88cd2be9a58bbdc863
ms.sourcegitcommit: 9d13ef7a257b5006fca5f92acf5b611f5cd143a2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/18/2019
ms.locfileid: "68307074"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>Sottoscrivere per se stessi e altri utenti un report impaginato nel servizio Power BI 

È ora possibile configurare la sottoscrizione per se stessi e altri utenti di report impaginati nel servizio Power BI tramite un messaggio di posta elettronica. Il processo è generalmente identico a quello previsto per la [sottoscrizione di report e dashboard nel servizio Power BI](service-report-subscribe.md). Questo articolo illustra nel dettaglio differenze e considerazioni. 

Durante la configurazione delle sottoscrizioni, è possibile scegliere la frequenza di ricezione dei messaggi di posta elettronica: giornaliera, settimanale oppure oraria. Se si sceglie la frequenza giornaliera o settimanale, è possibile scegliere gli orari in cui eseguire la sottoscrizione. In tutto, è possibile impostare fino a 24 sottoscrizioni diverse al giorno, per ogni report. 

## <a name="considerations-for-paginated-report-subscriptions"></a>Considerazioni per le sottoscrizioni di report impaginati 

- A differenza delle sottoscrizioni per dashboard o report di Power BI, la sottoscrizione contiene un allegato dell'output dell'intero report.  Sono supportati i tipi di allegato seguenti: PDF, presentazione di PowerPoint (PPTX), cartella di lavoro di Excel (XLSX), documento di Word (DOCX), file CSV e XML.

- Nel corpo del messaggio di posta elettronica è possibile inserire un'immagine di anteprima del report.  Questa operazione è facoltativa e l'immagine può variare leggermente rispetto alla prima pagina del documento del report allegato, a seconda del formato di allegato selezionato. 

- Le dimensioni del report allegato non possono superare i 25 MB. 

- È possibile sottoscrivere altri utenti per report impaginati che si connettono a una qualsiasi origine dati attualmente supportata, tra cui Azure Analysis Services o set di dati di Power BI. Considerare che l'allegato del report riflette i dati in base alle autorizzazioni, come avviene attualmente per SQL Server Reporting Services. 

- Le sottoscrizioni tramite posta elettronica possono essere inviate con i parametri attualmente selezionati o i parametri predefiniti per il report.  È possibile impostare valori di parametro diversi per ogni sottoscrizione creata per il report. 

- Se l'autore del report ha impostato parametri basati su espressioni (ad esempio, il valore predefinito è sempre la data odierna), la sottoscrizione userà questo tipo di parametri come valore predefinito. Sebbene sia possibile modificare altri valori di parametro e scegliere di usare i valori correnti, se il valore non viene modificato in modo esplicito, la sottoscrizione userà il parametro basato su espressione.

- Con i report impaginati, non esiste l'opzione di frequenza **Dopo l'aggiornamento dei dati**. Si ottengono sempre i valori più recenti dall'origine dati sottostante. 

## <a name="next-steps"></a>Passaggi successivi

[Sottoscrivere per se stessi e altri utenti report e dashboard nel servizio Power BI](service-report-subscribe.md)

[Che cosa sono i report impaginati in Power BI Premium?](paginated-reports-report-builder-power-bi.md)
