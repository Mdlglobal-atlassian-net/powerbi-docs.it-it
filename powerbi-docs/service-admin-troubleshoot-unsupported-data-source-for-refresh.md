---
title: Risoluzione dei problemi relativi all'origine dati non supportata per l'aggiornamento
description: Risoluzione dei problemi relativi all'origine dati non supportata per l'aggiornamento
author: mgblythe
manager: kfile
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: bd0ea66b8caf32e3244ed4e5eef648100fc5169e
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61188055"
---
# <a name="troubleshooting-unsupported-data-source-for-refresh"></a>Risoluzione dei problemi relativi all'origine dati non supportata per l'aggiornamento
Durante la configurazione di un set di dati per l'aggiornamento pianificato è possibile che venga visualizzato un errore.

        You cannot schedule refresh for this dataset because it gets data from sources that currently don’t support refresh.

Questo problema si verifica quando l'origine dati usata in Power BI Desktop non è supportata per l'aggiornamento. È quindi necessario trovare l'origine dati usata e verificare se è presente nell'elenco delle origini dati supportate in [Aggiornare i dati in Power BI](refresh-data.md). 

## <a name="find-the-data-source"></a>Individuare l'origine dati
Se non si è sicuri dell'origine dati usata, è possibile individuarla eseguendo la procedura seguente in Power BI Desktop.  

1. In Power BI Desktop verificare che il riquadro attivo sia **Report** .  
   ![Riquadro Report di Power BI Desktop](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-report-pane.png)
2. Selezionare **Modifica query** dalla barra multifunzione.  
   ![Modifica query](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-edit-queries.png)
3. Selezionare **Editor avanzato**.  
   ![Editor avanzato](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-advanced-editor.png)
4. Prendere nota del provider indicato per l'origine.  In questo esempio il provider è ActiveDirectory.  
   ![Provider dell'origine dati](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-provider.png)
5. Confrontare il provider con l'elenco delle origini dati supportate in [Aggiornare i dati in Power BI](refresh-data.md).  Notare che Active Directory è un'origine dati non supportata per l'aggiornamento.  

## <a name="next-steps"></a>Passaggi successivi
[Aggiornamento dei dati](refresh-data.md)  
[Power BI Gateway - Personale](service-gateway-personal-mode.md)  
[On-premises data gateway (Gateway dati locale)](service-gateway-onprem.md)  
[Risoluzione dei problemi del gateway dati locale](service-gateway-onprem-tshoot.md)  
[Risoluzione dei problemi di Gateway di Power BI - Personale](service-admin-troubleshooting-power-bi-personal-gateway.md)  

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

