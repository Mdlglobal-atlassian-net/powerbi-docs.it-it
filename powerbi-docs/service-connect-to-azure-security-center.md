---
title: Connettersi al Centro sicurezza di Azure con Power BI
description: Centro sicurezza di Azure per Power BI
services: powerbi
documentationcenter: 
author: joeshoukry
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
ms.author: yshoukry
ms.openlocfilehash: d052bc054e55eabfab53ad3b1ac9229f0a750785
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-azure-security-center-with-power-bi"></a>Connettersi al Centro sicurezza di Azure con Power BI
Usare Power BI per collegarsi ai dati sulla sicurezza di Azure e trovare informazioni approfondite sulla sicurezza del carico di lavoro di Azure. Power BI crea automaticamente un dashboard e un report aggiornati con i dati del Centro sicurezza di Azure che consentono di analizzare ed esplorare i dati.

Connettersi al [pacchetto di contenuto Centro sicurezza di Azure](https://app.powerbi.com/getdata/services/azure-security-center) per Power BI.

## <a name="how-to-connect"></a>Come connettersi
1. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro.
   
   ![](media/service-connect-to-azure-security-center/getdata.png)
2. Nella casella **Servizi** selezionare **Recupera**.
   
   ![](media/service-connect-to-azure-security-center/services.png)
3. Selezionare **Centro sicurezza di Azure** \> **Recupera**.
   
   ![](media/service-connect-to-azure-security-center/asc.png)
4. Specificare l’ID sottoscrizione. Per informazioni dettagliate su come [trovare questi parametri](#FindingParams), vedere più avanti.
   
   ![](media/service-connect-to-azure-security-center/params.png)
5. In **Metodo di autenticazione** selezionare **oAuth2** \> **Accedi**. Quando richiesto digitare le credenziali di Azure.
   
    ![](media/service-connect-to-azure-security-center/creds.png)
6. Dopo l'approvazione, il processo di importazione inizierà automaticamente. Al termine nel riquadro di spostamento verranno visualizzati un nuovo dashboard, un nuovo report e un nuovo set di dati. Selezionare il dashboard per visualizzare i dati importati.
   
     ![](media/service-connect-to-azure-security-center/dashboard.png)

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](service-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](service-dashboard-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificare la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="whats-included"></a>Cosa è incluso
Il pacchetto di contenuto contiene informazioni riguardanti lo stato della sicurezza delle risorse, l’analisi di avvisi e prevenzione.

## <a name="system-requirements"></a>Requisiti di sistema
Per usare il pacchetto di contenuto è necessario l’accesso ad un ID sottoscrizione e l’abilitazione del Centro sicurezza di Azure. Vedere altri dettagli nel [Centro sicurezza di Azure](https://portal.azure.com/#blade/Microsoft_Azure_Security/SecurityDashboardStartBladeV2) nel Portale di Azure.

Il pacchetto di contenuto richiede che l'utente si connetta con un account aziendale (non un account personale).

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Individuazione dei parametri
È possibile trovare l'ID sottoscrizione in due semplici modi.

1. Da https://portal.azure.com -&gt; Esplora -&gt; Sottoscrizioni -&gt; ID sottoscrizione
2. Da https://manage.windowsazure.com -&gt; Impostazioni  -&gt; ID sottoscrizione

L'ID sottoscrizione sarà un lungo set di numeri e caratteri, simile a quello nell'esempio del punto \#4 sopra riportato. 

## <a name="troubleshooting"></a>Risoluzione dei problemi
A seconda della dimensione dell'account, il caricamento dei dati potrebbe richiedere tempo. In caso di errore durante l’accesso, controllare i parametri e verificare che il Centro sicurezza di Azure sia abilitato.

Se il pacchetto di contenuto viene caricato, ma non visualizza tutti i dati, verificare che la connessione sia stata stabilita con un account aziendale. Anche se gli account personali sono supportati dal Centro sicurezza di Azure, l'API (e pertanto il pacchetto di contenuto) non restituisce i valori previsti se l'utente si connette con un account non aziendale. Specificare l'accesso a un account aziendale e provare nuovamente a connettersi.

## <a name="next-steps"></a>Passaggi successivi
[Introduzione a Power BI](service-get-started.md)

[Recuperare dati in Power BI](service-get-data.md)

