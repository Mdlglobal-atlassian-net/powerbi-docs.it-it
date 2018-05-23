---
title: Connettersi a Planview Enterprise con Power BI
description: Planview Enterprise per Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 4641fc0c36ad7fb64cc5da08ee8eda180f4ccc31
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="connect-to-planview-enterprise-with-power-bi"></a>Connettersi a Planview Enterprise con Power BI
Con il pacchetto di contenuto Planview Enterprise per Power BI è possibile visualizzare i dati di gestione risorse e lavoro in modi completamente nuovi direttamente in Power BI. Usare le credenziali di accesso a Planview Enterprise per vedere in modo interattivo gli investimenti per il portfolio comprendere lo stato del budget e controllare l'allineamento dei progetti alle priorità strategiche aziendali. È anche possibile estendere il dashboard e i report predefiniti per ottenere le informazioni più importanti.

Connettersi al [pacchetto di contenuto Planview Enterprise in Power BI](https://app.powerbi.com/getdata/services/planview-enterprise)

>[!NOTE]
>Per importare i dati di Planview Enterprise in Power BI è necessario essere un utente di Planview Enterprise con la funzionalità Reporting Portal Viewer abilitata nel proprio ruolo. Vedere i requisiti aggiuntivi indicati di seguito.

## <a name="how-to-connect"></a>Come connettersi
1. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro.
   
    ![](media/service-connect-to-planview/get.png)
2. Nella casella **Servizi** selezionare **Recupera**.
   
    ![](media/service-connect-to-planview/services.png)
3. Nella pagina di Power BI, selezionare **Planview Enterprise**, quindi selezionare **Recupera**:  
    ![](media/service-connect-to-planview/planview.png)
4. Nella casella di testo Planview Enterprise URL immettere l'URL per il server di Planview Enterprise che si vuole usare. Nella casella di testo Planview Enterprise Database immettere il nome del database di Planview Enterprise, quindi fare clic su Avanti.  
    ![](media/service-connect-to-planview/params.png)
5. Nell'elenco di Metodo di autenticazione, selezionare **Basic** se non è già selezionato. Immettere il **nome utente** e la **password** per il proprio account e selezionare **Accedi**.  
   ![](media/service-connect-to-planview/creds.png)
6. Nel riquadro a sinistra, selezionare Planview Enterprise dall'elenco dei dashboard.  
     Power BI Importa i dati di Planview Enterprise nel dashboard. Si noti che il caricamento dei dati può richiedere un po' di tempo.  
    ![](media/service-connect-to-planview/dashboard.png)

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](power-bi-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](service-dashboard-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificare la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="system-requirements"></a>Requisiti di sistema
Per importare i dati di Planview Enterprise in Power BI è necessario essere un utente di Planview Enterprise con la funzionalità Reporting Portal Viewer abilitata nel proprio ruolo. Vedere i requisiti aggiuntivi indicati di seguito.

Questa procedura presuppone che sia stato già effettuato l'accesso alla home page di Microsoft Power BI con un account Power BI. Se non si ha un account Power BI, creare un nuovo account Power BI gratuito nella home page di Power BI e quindi fare clic su Recupera dati.

## <a name="next-steps"></a>Passaggi successivi:

[Introduzione a Power BI](service-get-started.md)

[Recuperare dati per Power BI](service-get-data.md)