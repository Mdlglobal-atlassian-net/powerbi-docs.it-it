---
title: Connettersi a comScore Digital Analytix con Power BI
description: comScore Digital Analytix per Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 01/30/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 49ac1f917a5f3095c1dbc13c644061859389fe74
ms.sourcegitcommit: 7df786871b196725a1c5422ee561c7557660894e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/31/2019
ms.locfileid: "55482684"
---
# <a name="connect-to-comscore-digital-analytix-with-power-bi"></a>Connettersi a comScore Digital Analytix con Power BI
Visualizzare ed esplorare i dati di comScore Digital Analytix in Power BI con il pacchetto di contenuto Power BI. I dati verranno aggiornati automaticamente una volta al giorno.

Connettersi al [pacchetto di contenuto comScore per Power BI](https://app.powerbi.com/getdata/services/comscore).

>[!NOTE]
>Per la connessione al pacchetto di contenuto è necessario un account utente di comScore DAx e l'accesso al'API comScore. Altre [informazioni](#Requirements) sono disponibili di seguito.

## <a name="how-to-connect"></a>Come connettersi
1. Selezionare Recupera dati nella parte inferiore del riquadro di spostamento sinistro.
   
   ![](media/service-connect-to-connect-to/getdata.png)
2. Nella casella **Servizi** selezionare **Recupera**.
   
   ![](media/service-connect-to-connect-to/services.png)
3. Selezionare **comScore Digital Analytix** \> **Recupera**.
   
   ![](media/service-connect-to-connect-to/comscore.png)
4. Fornire il data center, l'ID client comScore e il sito al quale connettersi. Per altri dettagli su come trovare questi valori, vedere la sezione seguente [Individuazione dei parametri comScore](#FindingParams).
   
   ![](media/service-connect-to-connect-to/parameters.png)
5. Fornire il nome utente e la password comScore per la connessione. Per informazioni dettagliate sull'individuazione di questo valore, vedere più avanti.
   
   ![](media/service-connect-to-connect-to/creds.png)
6. Il processo di importazione inizierà automaticamente. Al termine nel riquadro di spostamento verranno visualizzati un nuovo dashboard, un nuovo report e un nuovo set di dati. Selezionare il dashboard per visualizzare i dati importati.

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](consumer/end-user-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](consumer/end-user-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificarne la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

<a name="Requirements"></a>

## <a name="system-requirements"></a>Requisiti di sistema
Per la connessione è necessario un account utente di comScore DAx e l'accesso al'API comScore DAx. Contattare l'amministratore di comScore DAx per confermare l'account.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Individuazione dei parametri
I dettagli su come individuare ciascuno dei parametri comScore sono disponibili più avanti.

**Data center**

Il data center al quale connettersi viene determinato dall'URL aperto in comScore.

![](media/service-connect-to-connect-to/comscore_url.png) 

**Client**

Il client è uguale a quello fornito durante l'accesso a comScore DAx.

![](media/service-connect-to-connect-to/comscore_signin.png) 

**Sito**

Il sito comScore determina il sito da cui visualizzare i dati. Per un elenco di siti, vedere l'account comScore.

![](media/service-connect-to-connect-to/comscore_sites.png)

## <a name="next-steps"></a>Passaggi successivi
[Introduzione a Power BI](service-get-started.md)

[Recuperare dati in Power BI](service-get-data.md)

