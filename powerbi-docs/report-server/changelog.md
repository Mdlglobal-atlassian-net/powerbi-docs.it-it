---
title: Log delle modifiche per il server di report Power BI
description: "Questo log delle modifiche è relativo al server di report di Power BI ed elenca i nuovi elementi e le correzioni di bug per ogni versione."
services: powerbi
documentationcenter: 
author: jtarquino
manager: jonhp
backup: maggies
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/11/2017
ms.author: tankas
ms.openlocfilehash: ced415662c2dc39b6491cb79d121f3cd77719fe4
ms.sourcegitcommit: be55922d7f43f458aea0160ec8fdfb1a0b5a0c00
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2017
---
# <a name="changelog-for-power-bi-report-server"></a>Log delle modifiche per il server di report Power BI

Questo log delle modifiche è relativo al server di report di Power BI ed elenca i nuovi elementi e le correzioni di bug per ogni versione.

Per informazioni dettagliate sulle nuove funzionalità, vedere [Novità del Server di report di Power BI](whats-new.md).

## <a name="october-2017"></a>Ottobre 2017

- **Server di report Power BI**
    - *Versione 1.1.6551.5155 (build 14.0.600.438), data di rilascio: 11 dicembre 2017*
        - Correzioni di bug
            - Errore durante il salvataggio dei dati dopo l'aggiornamento per determinati report di Power BI Desktop.

    - *Versione 1.1.6530.30789 (build 14.0.600.437), data di rilascio: 17 novembre 2017*
        - Correzioni di bug
            - Correzione per gli scenari di autenticazione di base 
            - Correzione per i giorni della settimana che non erano selezionabili nella pagina della pianificazione per le sottoscrizioni, i piani di aggiornamento della cache e gli snapshot della cronologia nel portale
            - Per i report impaginati (RDL), è stata apportata una correzione per le espressioni nella casella di testo con la proprietà CanGrow impostata su false che comportavano la mancata visualizzazione dei colori e la visualizzazione non corretta dei tipi di carattere
            - Per i report di Power BI (PBIX) è stata apportata una correzione per l'aggiunta delle legende ai grafici a linee che mostrano un oggetto visivo vuoto

    - *Versione 1.1.6514.9163 (build 14.0.600.434), data di rilascio: 1 novembre 2017*
        - Correzioni di bug
            - Soluzione per i problemi di affidabilità per i report PBIX di dimensioni superiori a 500 MB
            - Soluzione per i problemi di caricamento dati per i report PBIX di dimensioni superiori a 1 GB

    - *Versione 1.1.6513.3500 (build 14.0.600.433), data di rilascio: 31 ottobre 2017*
        - Funzionalità
            - Supporto per il modello di dati incorporato
            - Visualizzazione della cartella di lavoro di Excel (con integrazione di Office Online Server abilitata)
            - Aggiornamento pianificato dei dati (PBIX)
            - Supporto per DirectQuery
            - Supporto per file di grandi dimensioni (fino a 2 GB)
            - API REST pubblica
            - Supporto per set di dati condivisi in Power BI Desktop (tramite OData)
            - Supporto del parametro URL per i file PBIX
            - Miglioramenti all'accessibilità

- **Power BI Desktop (ottimizzato per il server di report di Power BI)**
    - *Versione: 2.51.4885.1423 (ottobre 2017), data di rilascio: 17 novembre 2017*
        - Correzioni di bug
            - Correzione alla versione di Power BI Desktop a 32 bit che non può essere eseguita nei sistemi operativi x86
            - Per i report di Power BI (PBIX) è stata apportata una correzione per mostrare le linee della griglia dell'asse x
            - Altre correzioni di bug minori

    - *Versione: 2.51.4885.1041 (ottobre 2017), data di rilascio: 31 ottobre 2017*
        - Funzionalità
            - Include modifiche necessarie per la connessione al server di report di Power BI (ottobre 2017)

## <a name="june-2017"></a>Giugno 2017

- **Server di report Power BI**
    - *Build 14.0.600.305, data di rilascio: 19 settembre 2017*  
        - Correzioni di bug
            - Aggiornamento al [controllo Web di Bing Maps](https://msdn.microsoft.com/library/mt712542.aspx) più recente

    - *Build 14.0.600.301, data di rilascio: 11 luglio 2017*
        - Correzioni di bug
            - Il tag {{UserId}} si risolve nelle credenziali archiviate anziché nell'utente che esegue il report in Report di Power BI
            - Non è possibile eseguire il rendering di alcune immagini nei report del server di report di Power BI
            - Non è possibile modificare il nome di un report di Power BI nel server di report di Power BI
            - Non è possibile caricare gli oggetti visivi personalizzati nell'applicazione Power BI per dispositivi mobili (è necessario reinstallare l'app mobile per cancellare la cache locale)

    - *Build 14.0.600.271, data di rilascio: 12 giugno 2017*
        - Versione iniziale del server di report di Power BI

## <a name="next-steps"></a>Passaggi successivi

[Manuale per l'utente](user-handbook-overview.md)  
[Manuale per l'amministratore](admin-handbook-overview.md)  
[Avvio rapido: installazione del Server di report di Power BI](quickstart-install-report-server.md)  
[Installare Generatore report](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Scaricare SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)