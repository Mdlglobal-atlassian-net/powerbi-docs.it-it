---
title: Log delle modifiche per il server di report Power BI
description: Questo log delle modifiche è relativo al server di report di Power BI ed elenca i nuovi elementi e le correzioni di bug per ogni versione.
author: jtarquino
manager: kfile
ms.reviewer: maggies
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 03/31/2018
ms.author: jtarquino
ms.openlocfilehash: 41f48e886c376f6cc00a76313538e5a6b9ac1c3b
ms.sourcegitcommit: a764e4b9d06b50d9b6173d0fbb7555e3babe6351
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2018
ms.locfileid: "49641943"
---
# <a name="changelog-for-power-bi-report-server"></a>Log delle modifiche per il server di report Power BI

Questo log delle modifiche è relativo al server di report di Power BI ed elenca i nuovi elementi e le correzioni di bug per ogni versione.

Per informazioni dettagliate sulle nuove funzionalità, vedere [Novità del Server di report di Power BI](whats-new.md). 

## <a name="august-2018"></a>Agosto 2018
- **Server di report Power BI**
    - *Versione 1.3.6816.37243 (build 15.0.2.557), data di rilascio: 30 agosto 2018*
        - Correzioni di bug
            - Risolto un problema a causa del quale un reindirizzamento dell'associazione non veniva aggiornato durante l'aggiornamento dalle versioni precedenti di Server di report di Power BI e i clienti vedevano:      
            *`
            Failed to load expression host assembly. Details: Could not load file or assembly 'Microsoft.ReportingServices.ProcessingObjectModel, Version=2018.7.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040) (rsErrorLoadingExprHostAssembly)
             `*
             
            - Il bug relativo alla trasparenza dell'etichetta dati è stato corretto.
            
    - *Versione 1.3.6801.38816 (build 15.0.2.540), data di rilascio: 15 agosto 2018*
        - Funzionalità
            - È ora disponibile il supporto di DirectQuery SSO SAP HANA per i report di Power BI
            - API per oggetti visivi personalizzati fornita con questa versione - Versione 1.13.0
            - Per gli oggetti visivi personalizzati verrà eseguito il fallback a una versione precedente compatibile con la versione corrente dell'API server (se disponibile)

- **Power BI Desktop (ottimizzato per il server di report di Power BI)**
    - *Versione: 2.61.5192.641 (agosto 2018), data di rilascio: 15 agosto 2018*
        - Include modifiche necessarie per la connessione a Server di report di Power BI (agosto 2018)         
        
## <a name="march-2018"></a>Marzo 2018
- **Server di report Power BI**
    - *Versione 1.2.6690.34729 (build 15.0.2.402), data di rilascio: 27 aprile 2018*
        - Correzioni di bug
            - Abilitazione della migrazione dei cataloghi di SQL Server Reporting Services 2017
            - Per i report di Power BI (PBIX)
                - Possibilità di aggiornare i report quando un server è configurato per l'uso dell'autenticazione personalizzata
                - La modifica delle proprietà di un report non comporta la reimpostazione delle credenziali dell'origine dati
            - Per i report impaginati (RDL)
                - L'uso di `Lookup()` o di funzioni derivate come `LookupSet()` e `MultiLookup()` nelle espressioni RDL non genera più un risultato `#Error`
                - I report collegati rispettano le dimensioni di pagina del report di destinazione durante la stampa
                - Possibilità di creare sottoscrizioni per i report collegati che usano parametri a cascata
                - Possibilità di modificare i valori predefiniti dei parametri multivalore quando si usa Internet Explorer 11
                - Possibilità di modificare le opzioni di recapito delle sottoscrizioni guidate dai dati
                - Possibilità di visualizzare e modificare le sottoscrizioni durante l'esecuzione della sottoscrizione
                - L'impostazione delle credenziali dell'origine dati non comporta la rimozione delle stringhe di connessione basate su espressioni
            - Per gli indicatori KPI
                - Le linee di tendenza vengono aggiornate quando vengono aggiornati i dati
            - Miglioramenti generali alla stabilità​​

    - *Versione 1.2.6660.39920 (build 15.0.2.389), data di rilascio: 28 marzo 2018*
        - Correzioni di bug
            - Per i report di Power BI (PBIX), correzione per l'esportazione dei dati non funzionanti da oggetti visivi di Power BI
            - Per i report di Power BI (PBIX), correzione per i filtri URL non funzionanti
            - Per i report impaginati (RDL), correzione per la visualizzazione non corretta delle immagini in Internet Explorer 11 dopo l'aggiornamento alla versione di marzo del Server di report di Power BI

    - *Versione 1.2.6648.38132 (build 15.0.2.378), data di rilascio: 19 marzo 2018*
        - Aggiornamenti della sicurezza
        - Miglioramenti all'accessibilità
        - Correzioni di bug
            - Per i report impaginati (RDL), correzione della visibilità di parametri in un report collegato che viene ripristinato dopo la modifica delle proprietà
            - Correzione del portale web con l'autenticazione personalizzata basata su form che ignora il cookie di scadenza scorrevole
            - Correzione dell'esportazione in Word che consente di creare altezze di righe diverse se il contenuto delle righe è vuoto
            - Per i report impaginati (RDL), correzione della stringa di connessione basata sull'espressione che viene eliminata quando vengono modificate le credenziali della sorgente dati
            - Correzione della capacità di usare l'indicatore KPI con valori di testo
            - Per i report impaginati (RDL), correzione della capacità di assegnare un nuovo set di dati a un report impaginato (RDL) esistente
            - Altre correzioni di stabilità e usabilità

- **Power BI Desktop (ottimizzato per il server di report di Power BI)**
    - Versione: 2.56.5023.1043 (marzo 2018), data di rilascio: 19 marzo 2018
        - Include modifiche necessarie per la connessione al server di report di Power BI (marzo 2018)

## <a name="october-2017"></a>Ottobre 2017

- **Server di report Power BI**
    - *Versione 1.1.6582.41691 (build 14.0.600.442), data di rilascio: 10 gennaio 2018*
        - Aggiornamenti della sicurezza
        - Correzioni di bug
            - Correzione di Model.GetParameters che restituisce l'errore 400
            - Correzione dell'impostazione del set di dati condiviso sui report impaginati esistenti (RDL)
            - Correzione di ExecutionNotFoundException durante l'esportazione in formato PDF di report con valori di parametri diversi

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
    - *Versione: 2.51.4885.3981 (ottobre 2017), rilascio: 10 aprile 2018*
        - Aggiornamenti della sicurezza

    - *Versione: 2.51.4885.2501 (ottobre 2017), rilascio: 10 gennaio 2018*
        - Aggiornamenti della sicurezza

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
    - *Build 14.0.600.309, data di rilascio: 10 gennaio 2018*
        - Aggiornamenti della sicurezza

    - *Build 14.0.600.305, data di rilascio: 19 settembre 2017*  
        - Correzioni di bug
            - Aggiornamento al [controllo Web di Bing Maps](https://msdn.microsoft.com/library/mt712542.aspx) più recente

    - *Build 14.0.600.301, data di rilascio: 11 luglio 2017*
        - Correzioni di bug
            - Il tag `{{UserId}}` si risolve nelle credenziali archiviate anziché nell'utente che esegue il report in Report di Power BI
            - Non è possibile eseguire il rendering di alcune immagini nei report del server di report di Power BI
            - Non è possibile modificare il nome di un report di Power BI nel server di report di Power BI
            - Non è possibile caricare gli oggetti visivi personalizzati nell'applicazione Power BI per dispositivi mobili (è necessario reinstallare l'app mobile per cancellare la cache locale)

    - *Build 14.0.600.271, data di rilascio: 12 giugno 2017*
        - Versione iniziale del server di report di Power BI

- **Power BI Desktop (ottimizzato per il server di report di Power BI)**
    - *Versione: 2.47.4766.4901 (giugno 2017), data di rilascio: 10 gennaio 2018*
        - Aggiornamenti della sicurezza

## <a name="next-steps"></a>Passaggi successivi

[Che cos'è Server di report di Power BI?](get-started.md)
[Panoramica amministratore](admin-handbook-overview.md)  
[Installare il server di report di Power BI](install-report-server.md)  
[Installare Generatore report](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Scaricare SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
