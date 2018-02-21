---
title: Connettersi a ServiceNow con Power BI
description: ServiceNow per Power BI
services: powerbi
documentationcenter: 
author: SarinaJoan
manager: kfile
backup: maggiesMSFT
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: sarinas
ms.openlocfilehash: acb564c72bcec4ba36e24f87dc52de004e03c189
ms.sourcegitcommit: c24e5d7bd1806e0d637e974b5143ab5125298fc6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2018
---
# <a name="connect-to-servicenow-with-power-bi-for-incident-reporting"></a>Connettersi a ServiceNow con Power BI per la segnalazione di eventi imprevisti
ServiceNow offre più prodotti e soluzioni per la gestione commerciale, operativa e IT che consentono di migliorare il business. Questo pacchetto di contenuto include vari report e approfondimenti sugli eventi aperti, risolti di recente e chiusi di recente.  

Connettersi al pacchetto di contenuto Power BI per [ServiceNow Incidents](https://app.powerbi.com/getdata/services/servicenow).

## <a name="how-to-connect"></a>Come connettersi
1. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro.
   
   ![](media/service-connect-to-servicenow/pbi_getdata.png) 
2. Nella casella **Servizi** selezionare **Recupera**.
   
   ![](media/service-connect-to-servicenow/pbi_getservices.png) 
3. Selezionare **ServiceNow Incidents** \> **Scarica**.
   
   ![](media/service-connect-to-servicenow/connect.png)
4. Specificare l'URL dell'istanza di ServiceNow e l'intervallo di giorni/record da includere. Tenere presente che l'importazione si interrompe quando viene raggiunto un limite.
   
   ![](media/service-connect-to-servicenow/params.png)
5. Quando richiesto, immettere le credenziali **Basic** per ServiceNow. Si noti che l'accesso Single Sign-On non è attualmente supportato. Più avanti sono fornite informazioni più dettagliate sui requisiti di sistema.
   
   ![](media/service-connect-to-servicenow/creds.png)
6. Al termine del flusso di accesso, verrà avviato il processo di importazione. Al termine nel riquadro di spostamento verranno visualizzati un nuovo dashboard, un nuovo report e un nuovo set di dati. Selezionare il dashboard per visualizzare i dati importati.
   
    ![](media/service-connect-to-servicenow/dashboard.png)

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](power-bi-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](service-dashboard-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificare la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="system-requirements"></a>Requisiti di sistema
Per connettersi è necessario:  

* Un account che abbia accesso a yourorganization.service-now.com con l'autenticazione di base (l'accesso Single Sign-On non è supportato in questa versione)  
* Un account con il ruolo rest_service e l'accesso in lettura alla tabella degli eventi  

## <a name="troubleshooting"></a>Risoluzione dei problemi
Se si verifica un errore relativo alle credenziali durante il caricamento, esaminare i requisiti di accesso riportati sopra. Se si hanno le autorizzazioni appropriate ma i problemi persistono, rivolgersi all'amministratore di ServiceNow per ottenere le autorizzazioni aggiuntive che potrebbero essere necessarie per l'istanza personalizzata.

Se il caricamento richiede molto tempo, verificare il numero di eventi e il numero di giorni specificati durante la connessione e provare a ridurli.

## <a name="next-steps"></a>Passaggi successivi
[Introduzione a Power BI](service-get-started.md)

[Power BI - Concetti di base](service-basic-concepts.md)

