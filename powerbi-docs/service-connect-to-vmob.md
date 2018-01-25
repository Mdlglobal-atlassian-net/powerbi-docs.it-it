---
title: Connettersi a VMob con Power BI
description: VMob per Power BI
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
ms.openlocfilehash: 09bd84fc320b550ccdaa0771f747a19bc1003150
ms.sourcegitcommit: d803e85bb0569f6b357ba0586f5702c20d27dac4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="connect-to-vmob-with-power-bi"></a>Connettersi a VMob con Power BI
Tenere traccia ed esplorare i dati di VMob è facile con Power BI e il pacchetto di contenuto VMob. Power BI recupera i dati seguenti: Statistiche utenti per tutti i tempi e negli ultimi 30 giorni, indicatore KPI di vendita al dettaglio per gli ultimi 30 giorni e le prestazioni della campagna per gli ultimi 30 giorni.

Connettersi al [pacchetto di contenuto VMob](https://app.powerbi.com/getdata/services/vmob) per Power BI.

## <a name="how-to-connect"></a>Come connettersi
1. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro.
   
    ![](media/service-connect-to-vmob/getdata.png)
2. Nella casella **Servizi** selezionare **Recupera**.
   
   ![](media/service-connect-to-vmob/services.png)
3. Selezionare **VMob** \> **Recupera**.
   
   ![](media/service-connect-to-vmob/vmob.png)
4. Quando richiesto, immettere l'URL VMob e fare clic sul pulsante Avanti. Questo URL viene fornito da VMob separatamente.
   
    ![](media/service-connect-to-vmob/params.png)
5. Scegliere l’opzione **Basic** nell'elenco a discesa del metodo di autenticazione, immettere il nome utente VMob e la password e fare clic sul pulsante **Accedi** .
   
    ![](media/service-connect-to-vmob/creds.png)
6. Il processo di importazione verrà avviato automaticamente e Power BI recupererà i dati VMob per creare un dashboard pronto all’uso e il report per l'utente.
   
   ![](media/service-connect-to-vmob/dashboard2.png)

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](power-bi-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](service-dashboard-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificare la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="next-steps"></a>Passaggi successivi
[Introduzione a Power BI](service-get-started.md)

[Recuperare dati in Power BI](service-get-data.md)

