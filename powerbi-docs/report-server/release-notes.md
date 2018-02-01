---
title: Note sulla versione del Server di report di Power BI
description: Questo argomento descrive le limitazioni e i problemi del server di report di Power BI.
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/01/2017
ms.author: maghan
ms.openlocfilehash: 7f59e3788b24344b5f86b146fb41e440eb0a2098
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/30/2018
---
# <a name="power-bi-report-server-release-notes"></a>Note sulla versione del Server di report di Power BI
Questo argomento descrive le limitazioni e i problemi del server di report di Power BI.

Per scaricare il server di report di Power BI e Power BI Desktop ottimizzati per il server di report di Power BI, visitare [Creazione di report in locale con il server di report di Power BI](https://powerbi.microsoft.com/report-server/).

## <a name="october-2017"></a>Ottobre 2017
* Supporto per i dati importati nei report di Power BI
* Possibilità di visualizzare le cartelle di lavoro di Excel nel portale Web. Questo risultato viene ottenuto tramite la configurazione di Office Online Server.
* Supporto per i nuovi oggetti visivi di tipo tabella e matrice di Power BI.
* Supporto per le API REST

## <a name="june-2017"></a>Giugno 2017
* Nessun nuovo elemento per giugno 2017.

## <a name="may-2017"></a>Maggio 2017
* Per il corretto funzionamento nel server di report di Power BI, i report di Power BI devono essere creati con Power BI Desktop ottimizzato per il server di report di Power BI. È possibile scaricare Power BI Desktop dal collegamento di download nella parte superiore della pagina.
* I report di Power BI supportano solo connessioni dinamiche ad Analysis Services (tabulari o multidimensionali).
* Nessun supporto per gli oggetti visivi R.

**Problema e impatto sul cliente**: se sullo stesso computer sono installati sia SQL Server Reporting Services che il server di report di Power BI e se ne disinstalla uno solo, non sarà più possibile connettersi al server di report rimanente con Report Server Configuration Manager.

**Soluzione alternativa** per risolvere questo problema, è necessario eseguire le operazioni seguenti dopo la disinstallazione di uno dei server.

1. Avviare un prompt dei comandi in modalità amministratore.
2. Passare alla directory in cui è installato il server di report rimanente.
   
    *Il percorso predefinito del server di report di Power BI è: C\Programmi\Server di report di Power BI*
   
    *Il percorso predefinito per SQL Server Reporting Services è: C:\Programmi\Microsoft SQL Server Reporting Services*
3. Quindi passare alla cartella successiva. A seconda del server rimanente, questa sarà *SSRS* o *PBIRS*.
4. Passare alla cartella WMI.
5. Eseguire il comando seguente:
   
    ```
    regsvr32 /i ReportingServicesWMIProvider.dll
    ```
   
    Se viene visualizzato, è possibile ignorare l'errore seguente.
   
    ```
    The module "ReportingServicesWMIProvider.dll" was loaded but the entry-point DLLInstall was not found. Make sure that "ReportingServicesWMIProvider.dll" is a valid DLL or OCX file and then try again.
    ```

## <a name="next-steps"></a>Passaggi successivi
[Novità del Server di report di Power BI](whats-new.md)  
[Manuale per l'utente](user-handbook-overview.md)  
[Manuale per l'amministratore](admin-handbook-overview.md)  
[Avvio rapido: installazione del Server di report di Power BI](quickstart-install-report-server.md)  
[Installare Generatore report](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Scaricare SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)

