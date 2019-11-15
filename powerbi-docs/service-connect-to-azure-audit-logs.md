---
title: Connettersi ai log di controllo di Azure con Power BI
description: Log di controllo di Azure per Power BI
author: SarinaJoan
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: d0bd4e90dac6e71d95c38bed83f1c9507acc4fd3
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73855381"
---
# <a name="connect-to-azure-audit-logs-with-power-bi"></a>Connettersi ai log di controllo di Azure con Power BI
Con il pacchetto di contenuto Log di controllo di Azure è possibile analizzare e visualizzare le informazioni archiviate nei log di controllo. Power BI recupera i dati, crea un dashboard predefinito e report basati su tali dati.

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

[Connettersi al pacchetto di contenuto Log di controllo di Azure](https://app.powerbi.com/getdata/services/azure-audit-logs) oppure ottenere altre informazioni sull'[integrazione di Log di controllo di Azure](https://powerbi.microsoft.com/integrations/azure-audit-logs) con Power BI.

## <a name="how-to-connect"></a>Come connettersi
1. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento.  
   
    ![](media/service-connect-to-azure-audit-logs/getdata.png)
2. Nella casella **Servizi** selezionare **Recupera**.  
   
    ![](media/service-connect-to-azure-audit-logs/services.png) 
3. Selezionare **Log di controllo di Azure**  > **Recupera**.  
   
   ![](media/service-connect-to-azure-audit-logs/azureauditlogs.png)
4. Quando richiesto, immettere l'**ID sottoscrizione di Azure**. Di seguito sono riportate informazioni dettagliate su come trovare il proprio [ID sottoscrizione](#FindingParams).   
   
    ![](media/service-connect-to-azure-audit-logs/parameters.png)
5. In **Metodo di autenticazione** selezionare **oAuth2** \> **Accedi**.
   
    ![](media/service-connect-to-azure-audit-logs/creds.png)
6. Immettere le credenziali dell'account per terminare il processo di accesso.
   
    ![](media/service-connect-to-azure-audit-logs/login.png)
7. Power BI recupererà i dati dei Log di controllo di Azure e creerà automaticamente un dashboard e un report pronti da usare. 
   
    ![](media/service-connect-to-azure-audit-logs/dashboard.png)

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](consumer/end-user-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](consumer/end-user-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificarne la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="system-requirements"></a>Requisiti di sistema
Il pacchetto di contenuto Log di controllo di Azure richiede l'accesso ai log di controllo nel portale di Azure. Altre informazioni sono disponibili [qui](/azure/azure-resource-manager/resource-group-audit/).

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Individuazione dei parametri
È possibile trovare l'ID sottoscrizione in due semplici modi.

1. Da https://portal.azure.com -&gt; Esplora -&gt; Sottoscrizioni -&gt; ID sottoscrizione
2. Da https://manage.windowsazure.com -&gt; Impostazioni  -&gt; ID sottoscrizione

L'ID sottoscrizione sarà un lungo set di numeri e caratteri, simile a quello nell'esempio del punto \#4 sopra riportato. 

## <a name="troubleshooting"></a>Risoluzione dei problemi
Se viene visualizzato un errore di credenziali o un errore durante il tentativo di aggiornamento a causa di credenziali non valide, provare a eliminare tutte le istanze del pacchetto di contenuto Log di controllo di Azure e a ricollegarsi.

## <a name="next-steps"></a>Passaggi successivi
[Che cos'è Power BI?](fundamentals/power-bi-overview.md)  
[Concetti di base sulle finestre di progettazione del servizio Power BI](service-basic-concepts.md)  

