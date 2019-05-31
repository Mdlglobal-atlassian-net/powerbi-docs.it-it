---
title: Sottoscrivere i report impaginati nel servizio Power BI
description: In questo articolo descrive aspetti da tenere a mente sulla sottoscrizione di report impaginati nel servizio Power BI.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 05/24/2019
ms.openlocfilehash: ccec6658808d94728f2a4f14de67c36da0f51def
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222186"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>Sottoscrivere i report impaginati nel servizio Power BI se stessi e ad altri utenti 

È ora possibile configurare sottoscrizioni tramite posta elettronica per se stessi e ad altri utenti per i report impaginati nel servizio Power BI. In generale, il processo è identico [sottoscrizione di report e dashboard nel servizio Power BI](service-report-subscribe.md). Questo articolo illustra in dettaglio le differenze e considerazioni. 

Nell'impostazione di sottoscrizioni, scegliere la frequenza con cui si desidera ricevere messaggi di posta elettronica: giornaliera, settimanale o ogni ora. Se si sceglie giornaliera o settimanale, è possibile scegliere l'ora si preferisce l'esecuzione della sottoscrizione. In tutti, è possibile impostare fino a 24 sottoscrizioni diverse per ogni giorno per ogni report. 

## <a name="considerations-for-paginated-report-subscriptions"></a>Considerazioni relative alle sottoscrizioni di report impaginato 

- A differenza delle sottoscrizioni per i dashboard o report di Power BI, la sottoscrizione contiene un allegato dell'output intero report.  Sono supportati i seguenti tipi di attacco: PDF, presentazione di PowerPoint (PPTX), cartella di lavoro di Excel (XLSX), il documento di Word (DOCX), file CSV e XML.

- Non vi è alcuna immagine di anteprima del report nel corpo del messaggio di posta elettronica.  Ma è previsto che l'immagine della prima pagina del report come un elemento facoltativo. 

- La dimensione massima dei report dell'allegato è 25 MB. 

- È possibile sottoscrivere altri utenti per i report impaginati che si connettono a tutte le origini dati attualmente supportate, inclusi i set di dati di Power BI o Azure Analysis Services. Tenere a mente che l'allegato del report riflette i dati di base delle autorizzazioni, come avviene per SQL Server Reporting Services oggi stesso. 

- Le sottoscrizioni di pagina report sono collegate al nome del report.  

- Sottoscrizioni tramite posta elettronica vengono inviate con valori predefiniti dei parametri del report. 

- È presente alcun **dopo l'aggiornamento dati** opzione per la frequenza con i report impaginati. È sempre possibile ottenere i valori più recenti dall'origine dati sottostante. 

## <a name="next-steps"></a>Passaggi successivi

[Sottoscrivere autonomamente e altri report e dashboard nel servizio Power BI](service-report-subscribe.md)

[Che cosa sono i report impaginati in Power BI Premium? (anteprima)](paginated-reports-report-builder-power-bi.md)
