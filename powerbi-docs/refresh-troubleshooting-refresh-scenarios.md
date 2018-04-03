---
title: Scenari per la risoluzione dei problemi di aggiornamento
description: Scenari per la risoluzione dei problemi di aggiornamento
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/24/2018
ms.author: davidi
LocalizationGroup: Data refresh
ms.openlocfilehash: d94e25b78edef2aefaa5e63c788e5f11dc948791
ms.sourcegitcommit: 1fe3ababba34c4e7aea08adb347ec5430e0b38e4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2018
---
# <a name="troubleshooting-refresh-scenarios"></a>Scenari per la risoluzione dei problemi di aggiornamento
In questo articolo è possibile trovare informazioni relative a vari scenari che si possono incontrare durante l'aggiornamento dei dati all'interno del servizio Power BI.

> [!NOTE]
> Se si verifica uno scenario diverso da quelli elencati di seguito e che causa problemi, è possibile richiedere ulteriore assistenza sul [sito della community](http://community.powerbi.com/) oppure creare un [ticket di supporto](https://powerbi.microsoft.com/support/).
> 
> 

## <a name="refresh-using-web-connector-doesnt-work-properly"></a>L'aggiornamento con il connettore Web non funziona correttamente
Nel caso di uno script di connettore Web che usa la funzione [**Web.Page**](https://msdn.microsoft.com/library/mt260924.aspx), se il set di dati o il report è stato aggiornato dopo il 18 novembre 2016, è necessario usare un gateway per il corretto funzionamento dell'aggiornamento.

## <a name="unsupported-data-source-for-refresh"></a>Origine dati non supportata per l'aggiornamento
Quando si configura un set di dati, potrebbe verificarsi un errore che indica che il set di dati usa un'origine dati non supportata per l'aggiornamento. Per dettagli, vedere [Risoluzione dei problemi relativi all'origine dati non supportata per l'aggiornamento](service-admin-troubleshoot-unsupported-data-source-for-refresh.md)

## <a name="dashboard-doesnt-reflect-changes-after-refresh"></a>Il dashboard non riflette le modifiche dopo l'aggiornamento
Attendere 10-15 minuti affinché l'aggiornamento venga applicato nei riquadri del dashboard.  Se ancora non viene visualizzato, riaggiungere la visualizzazione nel dashboard.

## <a name="gatewaynotreachable-when-setting-credentials"></a>GatewayNotReachable durante l'impostazione delle credenziali
Potrebbe venire visualizzato l'errore GatewayNotReachable quando si prova a impostare le credenziali per un'origine dati. L'errore potrebbe essere causato da un gateway non aggiornato.  Installare il gateway più recente e riprovare.

## <a name="processing-error-the-following-system-error-occurred-type-mismatch"></a>Errore di elaborazione: Errore di sistema: Mancata corrispondenza del tipo di dati
Potrebbe essere un errore con lo script M all'interno del file di Power BI Desktop o della cartella di lavoro di Excel.  Potrebbe anche essere dovuto a una versione di Power BI Desktop non aggiornata.

## <a name="tile-refresh-errors"></a>Errori di aggiornamento del riquadro
Per un elenco di errori che possono verificarsi con i riquadri del dashboard e le relative spiegazioni, vedere [Risoluzione degli errori del riquadro](refresh-troubleshooting-tile-errors.md).

## <a name="refresh-fails-when-updating-data-from-sources-that-use-aad-oauth"></a>L'aggiornamento non riesce quando si aggiornano dati da origini che usano il token OAuth di AAD
Il token OAuth di Azure Active Directory (**AAD**), usato da numerose origini dati, scade dopo circa un'ora. Possono verificarsi casi in cui il caricamento dei dati richiede più tempo di quello previsto prima della scadenza dell'app (oltre un'ora), dal momento che il servizio Power BI attende fino a due ore quando si caricano i dati. In questo caso, il processo di caricamento dei dati non riesce e viene restituito un errore di credenziali.

Tra le origini dati che usano il token OAuth di AAD sono inclusi **Microsoft Dynamics CRM Online** e **SharePoint Online** (SPO). Se si esegue la connessione a tali origini dati e viene restituito un errore di credenziali quando il caricamento dei dati richiede più di un'ora, questa potrebbe essere la causa del problema.

Microsoft sta lavorando per individuare una soluzione che consenta al processo caricamento dei dati di aggiornare il token e continuare l'esecuzione. Se però l'istanza di Dynamics CRM Online o SharePoint Online (o di un'altra origine dati che usa un token OAuth di AAD) è di dimensioni tali da superare la soglia di caricamento dei dati, pari a due ore, potrebbe verificarsi anche un timeout del caricamento dati nel servizio Power BI.

Si noti anche che, per il corretto funzionamento dell'aggiornamento, quando ci si connette a un'origine dati di **SharePoint Online** tramite OAuth di AAD, è necessario usare lo stesso account usato per l'accesso al **servizio Power BI**.

## <a name="uncompressed-data-limits-for-refresh"></a>Limiti per l'aggiornamento dei dati non compressi
La dimensione massima per i set di dati importati nel **servizio Power BI** è 1 GB. Questi set di dati sono molto compressi per assicurare prestazioni elevate. Inoltre, nella capacità condivisa, questo servizio pone dei limiti alla quantità di dati non compressi che vengono elaborati durante l'aggiornamento a 10 GB. Questo limite considera la compressione ed è pertanto molto più alto di 1 GB. I set di dati in Power BI Premium non sono soggetti a questi limiti. Se l'aggiornamento nel servizio Power BI si conclude con un errore per questa ragione, ridurre la quantità di dati importati in Power BI e riprovare.

## <a name="scheduled-refresh-timeout"></a>Timeout dell'aggiornamento pianificato
Il timeout di un aggiornamento pianificato per i set di dati importati si verifica dopo due ore. Questo timeout è aumentato fino a cinque ore per i set di dati nelle aree di lavoro **Premium**. Se si riscontra questo limite, è possibile considerare la possibilità di ridurre le dimensioni o la complessità del set di dati oppure di suddividere il set di dati in parti più piccole.

## <a name="next-steps"></a>Passaggi successivi
[Aggiornamento dei dati](refresh-data.md)  
[Risoluzione dei problemi del gateway dati locale](service-gateway-onprem-tshoot.md)  
[Risoluzione dei problemi di Gateway di Power BI - Personale](service-admin-troubleshooting-power-bi-personal-gateway.md)  

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

