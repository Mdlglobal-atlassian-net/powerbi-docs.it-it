---
title: Connettersi a Projectplace con Power BI
description: Projectplace per Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: cd478abbac94c6b8aaf5aaa087dbfa4840e05fd7
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/30/2019
ms.locfileid: "70184544"
---
# <a name="connect-to-projectplace-by-planview-with-power-bi"></a>Connettersi a Projectplace di Planview con Power BI
Con il pacchetto di contenuto Projectplace di Planview è possibile visualizzare i dati di un progetto di collaborazione in modi del tutto nuovi direttamente in Power BI. Usare le credenziali di accesso a Projectplace per visualizzare in modo interattivo statistiche di progetto di importanza fondamentale, scoprire chi sono i membri del team più attivi e produttivi e identificare schede e le attività a rischio per i progetti nell'account Projectplace. È anche possibile estendere il dashboard e i report predefiniti per ottenere le informazioni più importanti.

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

[Connettersi al pacchetto di contenuto Projectplace per Power BI](https://app.powerbi.com/getdata/services/projectplace)

>[!NOTE]
>Per importare i dati di Projectplace in Power BI è necessario essere un utente di Projectplace. Vedere i requisiti aggiuntivi indicati di seguito.

## <a name="how-to-connect"></a>Come connettersi
1. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro.
   
    ![](media/service-connect-to-projectplace/get.png)
2. Nella casella **Servizi** selezionare **Recupera**.
   
    ![](media/service-connect-to-projectplace/services.png)
3. Nella pagina di Power BI, selezionare **Projectplace by Planview**, quindi selezionare **Recupera**:  
   
    ![](media/service-connect-to-projectplace/projectplace.png)
4. Nella casella di testo URL feed OData immettere l'URL per il feed OData di Projectplace che si vuole usare, come illustrato nella figura seguente:
   
    ![](media/service-connect-to-projectplace/params.png)
5. Nell'elenco di Metodo di autenticazione, selezionare **OAuth** se non è già selezionato. Premere **Accedi** e seguire il flusso di accesso.  
   
   ![](media/service-connect-to-projectplace/creds.png)
6. Nel riquadro a sinistra, selezionare **Projectplace** dall'elenco dei dashboard. Power BI Importa i dati di Projectplace nel dashboard. Si noti che il caricamento dei dati può richiedere un po' di tempo.  
   
    Il dashboard contiene riquadri che consentono di visualizzare i dati dal database Projectplace. L'immagine seguente illustra un esempio del dashboard Projectplace predefinito in Power BI.
   
    ![](media/service-connect-to-projectplace/dashboard.png)

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](consumer/end-user-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](consumer/end-user-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificarne la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="system-requirements"></a>Requisiti di sistema
Per importare i dati di Projectplace in Power BI è necessario essere un utente di Projectplace. Questa procedura presuppone che sia stato già effettuato l'accesso alla home page di Microsoft Power BI con un account Power BI. Se non si dispone di un account Power BI, andare a [powerbi.com](https://powerbi.microsoft.com/get-started/) e in **Power BI - Collaborazione e condivisione nel cloud**, selezionare **Prova gratuitamente**. Quindi fare clic su **Recupera dati**.

## <a name="next-steps"></a>Passaggi successivi
[Che cos'è Power BI?](power-bi-overview.md)

[Concetti di base sulle finestre di progettazione del servizio Power BI](service-basic-concepts.md)

