---
title: Connettersi a Windows Dev Center con Power BI
description: Windows Dev Center per Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 81498dff9c70deaf8135faf244db96509b1cf18d
ms.sourcegitcommit: 750f0bfab02af24c8c72e6e9bbdd876e4a7399de
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54008834"
---
# <a name="connect-to-windows-dev-center-with-power-bi"></a>Connettersi a Windows Dev Center con Power BI
Esplorare e monitorare i dati di analisi delle app di Windows Dev Center in Power BI con il pacchetto di contenuto Power BI. I dati verranno aggiornati automaticamente una volta al giorno.

Connettersi al [pacchetto di contenuto Windows Dev Center](https://app.powerbi.com/getdata/services/devcenter) per Power BI.

## <a name="how-to-connect"></a>Come connettersi
1. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro.
   
   ![](media/service-connect-to-windows-dev-center/getdata.png)
2. Nella casella **Servizi** selezionare **Recupera**.
   
   ![](media/service-connect-to-windows-dev-center/services.png)
3. Selezionare **Windows Dev Center** \>  **Recupera**.
   
   ![](media/service-connect-to-windows-dev-center/windowsdev.png)
4. Immettere l'ID applicazione di una delle proprie app e fare clic su Avanti. Per informazioni dettagliate su come [trovare questi parametri](#FindingParams), vedere più avanti.
   
   ![](media/service-connect-to-windows-dev-center/params.png)
5. In **Metodo di autenticazione** selezionare **oAuth2** \> **Accedi**. Quando richiesto, immettere le credenziali di Azure Active Directory associate all'account di Windows Dev Center. Per altre informazioni, vedere [Requisiti di sistema](#Requirements).
   
    ![](media/service-connect-to-windows-dev-center/creds.png)
   
    ![](media/service-connect-to-windows-dev-center/creds2.png)
6. Dopo l'approvazione, il processo di importazione inizierà automaticamente. Al termine nel riquadro di spostamento verranno visualizzati un nuovo dashboard, un nuovo report e un nuovo set di dati. Selezionare il dashboard per visualizzare i dati importati e scegliere un riquadro per passare ai report sottostanti.
   
    ![](media/service-connect-to-windows-dev-center/dashboard.png)
   
    ![](media/service-connect-to-windows-dev-center/report.png)

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](consumer/end-user-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](consumer/end-user-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificarne la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="whats-included"></a>Cosa è incluso
Il pacchetto di contenuto Dev Center Power BI include dati di analisi per l'app e le acquisizioni IAP, le classificazioni, le revisioni e l'integrità dell'applicazione. I dati sono limitati agli ultimi 3 mesi. Questo intervallo è una finestra mobile e quindi le date incluse vengono aggiornate quando viene aggiornato il set di dati.

<a name="Requirements"></a>

## <a name="system-requirements"></a>Requisiti di sistema
Questo pacchetto di contenuto richiede almeno un'app pubblicata in Windows Store e un account di Windows Dev Center. Per altre informazioni, vedere [qui](https://msdn.microsoft.com/windows/uwp/publish/manage-account-users).

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Individuazione dei parametri
È possibile trovare l'ID applicazione per un'app visitando la relativa pagina di identità nella gestione delle app.

L'ID applicazione si trova alla fine dell'URL di Windows 10 Store, https://www.microsoft.com/store/apps/ **{applicationId}**

## <a name="next-steps"></a>Passaggi successivi
[Introduzione a Power BI](service-get-started.md)

[Recuperare dati in Power BI](service-get-data.md)

