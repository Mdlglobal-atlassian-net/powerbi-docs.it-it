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
ms.date: 05/24/2019
ms.openlocfilehash: 472606fcb3b823cdcb722c9d8d6421d0ec652d24
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2019
ms.locfileid: "66839568"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>Sottoscrivere per se stessi e altri utenti un report impaginato nel servizio Power BI 

È ora possibile configurare la sottoscrizione per se stessi e altri utenti di report impaginati nel servizio Power BI tramite un messaggio di posta elettronica. Il processo è generalmente identico a quello previsto per la [sottoscrizione di report e dashboard nel servizio Power BI](service-report-subscribe.md). Questo articolo illustra nel dettaglio differenze e considerazioni. 

Durante la configurazione delle sottoscrizioni, è possibile scegliere la frequenza di ricezione dei messaggi di posta elettronica: giornaliera, settimanale oppure oraria. Se si sceglie la frequenza giornaliera o settimanale, è possibile scegliere gli orari in cui eseguire la sottoscrizione. In tutto, è possibile impostare fino a 24 sottoscrizioni diverse al giorno, per ogni report. 

## <a name="considerations-for-paginated-report-subscriptions"></a>Considerazioni per le sottoscrizioni di report impaginati 

- A differenza delle sottoscrizioni per dashboard o report di Power BI, la sottoscrizione contiene un allegato dell'output dell'intero report.  Sono supportati i tipi di allegato seguenti: PDF, presentazione di PowerPoint (PPTX), cartella di lavoro di Excel (XLSX), documento di Word (DOCX), file CSV e XML.

- Il corpo del messaggio di posta elettronica non contiene un'immagine di anteprima del report.  È previsto l'inserimento dell'immagine della prima pagina del report come elemento facoltativo. 

- Le dimensioni del report allegato non possono superare i 25 MB. 

- È possibile sottoscrivere altri utenti per report impaginati che si connettono a una qualsiasi origine dati attualmente supportata, tra cui Azure Analysis Services o set di dati di Power BI. Considerare che l'allegato del report riflette i dati in base alle autorizzazioni, come avviene attualmente per SQL Server Reporting Services. 

- Le sottoscrizioni alle pagine dei report sono associate al nome del report.  

- Le sottoscrizioni tramite posta elettronica vengono inviate con i valori dei parametri predefiniti. 

- Con i report impaginati, non esiste l'opzione di frequenza **Dopo l'aggiornamento dei dati**. Si ottengono sempre i valori più recenti dall'origine dati sottostante. 

## <a name="next-steps"></a>Passaggi successivi

[Sottoscrivere per se stessi e altri utenti report e dashboard nel servizio Power BI](service-report-subscribe.md)

[Che cosa sono i report impaginati in Power BI Premium?](paginated-reports-report-builder-power-bi.md)
