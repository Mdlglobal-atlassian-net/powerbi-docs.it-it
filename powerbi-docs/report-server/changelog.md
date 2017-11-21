---
title: Log delle modifiche per il server di report Power BI
description: "Questo log delle modifiche è relativo al server di report di Power BI ed elenca i nuovi elementi e le correzioni di bug per ogni versione."
services: powerbi
documentationcenter: 
author: jtarquino
manager: jonhp
backup: asaxton
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/19/2017
ms.author: jaimeta
ms.openlocfilehash: 9fdc757fca252c5c35d308dcd0b326098683b159
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2017
---
# <a name="changelog-for-power-bi-report-server"></a>Log delle modifiche per il server di report Power BI
Questo log delle modifiche è relativo al server di report di Power BI ed elenca i nuovi elementi e le correzioni di bug per ogni versione.

Per informazioni dettagliate sulle nuove funzionalità, vedere [Novità del Server di report di Power BI](whats-new.md).

## <a name="october-2017"></a>Ottobre 2017
* **Server di report Power BI**
  * *Versione 1.1.6514.9163 (build 14.0.600.434), data di rilascio: 1 novembre 2017*
    * Correzioni di bug
      * Soluzione per i problemi di affidabilità per i report PBIX di dimensioni superiori a 500 MB
      * Soluzione per i problemi di caricamento dati per i report PBIX di dimensioni superiori a 1 GB
  * *Versione 1.1.6513.3500 (build 14.0.600.433), data di rilascio: 31 ottobre 2017*
    * Funzionalità
      * Supporto per il modello di dati incorporato
      * Visualizzazione della cartella di lavoro di Excel (con integrazione di Office Online Server abilitata)
      * Aggiornamento pianificato dei dati (PBIX)
      * Supporto per DirectQuery
      * Supporto per file di grandi dimensioni (fino a 2 GB)
      * API REST pubblica
        * Supporto per set di dati condivisi in Power BI Desktop (tramite OData)
      * Supporto del parametro URL per i file PBIX
      * Miglioramenti all'accessibilità
* **Power BI Desktop (ottimizzato per il server di report di Power BI)**
  * *Versione: 2.51.4885.1041 (ottobre 2017), data di rilascio: 31 ottobre 2017*
    * Include modifiche necessarie per la connessione al server di report di Power BI (ottobre 2017)

## <a name="june-2017"></a>Giugno 2017
* **Server di report Power BI**
  
  * *Build 14.0.600.305, data di rilascio: 19 settembre 2017*  
    
    * Correzioni di bug
      * Aggiornamento al [controllo Web di Bing Maps](https://msdn.microsoft.com/library/mt712542.aspx) più recente
  * *Build 14.0.600.301, data di rilascio: 11 luglio 2017*
    
    * Correzioni di bug
      * Il tag {{UserId}} si risolve nelle credenziali archiviate anziché nell'utente che esegue il report in Report di Power BI
      * Non è possibile eseguire il rendering di alcune immagini nei report del server di report di Power BI
      * Non è possibile modificare il nome di un report di Power BI nel server di report di Power BI
      * Non è possibile caricare gli oggetti visivi personalizzati nell'applicazione Power BI per dispositivi mobili (è necessario reinstallare l'app mobile per cancellare la cache locale)
  * *Build 14.0.600.271, data di rilascio: 12 giugno 2017*
    
    * Versione iniziale del server di report di Power BI

## <a name="next-steps"></a>Passaggi successivi
[Manuale per l'utente](user-handbook-overview.md)  
[Manuale per l'amministratore](admin-handbook-overview.md)  
[Avvio rapido: installazione del Server di report di Power BI](quickstart-install-report-server.md)  
[Installare Generatore report](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Scaricare SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)

