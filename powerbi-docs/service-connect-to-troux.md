---
title: Connettersi a Troux con Power BI
description: Troux per Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: dbf3831264a354ec96a38751dfa7a3719c5c9f2a
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34247942"
---
# <a name="connect-to-troux-for-power-bi"></a>Connettersi a Troux per Power BI
Con il pacchetto di contenuto Troux per Power BI è possibile visualizzare il repository Enterprise Architecture in modi completamente nuovi direttamente in Power BI. Il pacchetto di contenuto offre una serie di informazioni sulle funzionalità aziendali, le applicazioni che consentono di distribuire tali funzionalità e le tecnologie che supportano le applicazioni che possono essere completamente personalizzate usando Power BI.

Connettersi al [pacchetto di contenuto Troux](https://app.powerbi.com/getdata/services/troux) per Power BI.

## <a name="how-to-connect"></a>Come connettersi
1. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro.
   
   ![](media/service-connect-to-troux/getdata.png)
2. Nella casella **Servizi** selezionare **Recupera**.
   
   ![](media/service-connect-to-troux/services.png)
3. Selezionare **Troux** \> **Recupera**.
   
   ![](media/service-connect-to-troux/troux.png)
4. Specificare l'URL OData di Troux. Per informazioni dettagliate su come [trovare questi parametri](#FindingParams), vedere più avanti.
   
   ![](media/service-connect-to-troux/params.png)
5. In **Metodo di autenticazione**selezionare **Di base** e fornire il nome utente e la password (distinzione tra maiuscole e minuscole), quindi selezionare **Accedi**.
   
    ![](media/service-connect-to-troux/creds.png)
6. Dopo l'approvazione, il processo di importazione inizierà automaticamente. Al termine nel riquadro di spostamento verranno visualizzati un nuovo dashboard, un nuovo report e un nuovo set di dati. Selezionare il dashboard per visualizzare i dati importati.
   
     ![](media/service-connect-to-troux/dashboard.png)

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](power-bi-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](service-dashboard-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificare la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="system-requirements"></a>Requisiti di sistema
L'accesso al feed OData di Troux e a Troux 9.5.1 o versione successiva è obbligatorio.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Individuazione dei parametri
Il team Servizio clienti può fornire all'utente l'URL del feed OData di Troux univoco

## <a name="troubleshooting"></a>Risoluzione dei problemi
Se viene visualizzato un errore di timeout dopo avere fornito le credenziali, riprovare a connettersi.

## <a name="next-steps"></a>Passaggi successivi
[Introduzione a Power BI](service-get-started.md)

[Recuperare dati in Power BI](service-get-data.md)

