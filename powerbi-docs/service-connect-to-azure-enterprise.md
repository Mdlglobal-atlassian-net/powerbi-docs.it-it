---
title: Connettersi a Microsoft Azure Enterprise con Power BI
description: Microsoft Azure Enterprise per Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 4cedeac37a47ffaa41ff9088c9ef36c37b4c784e
ms.sourcegitcommit: 750f0bfab02af24c8c72e6e9bbdd876e4a7399de
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54008282"
---
# <a name="connect-to-microsoft-azure-enterprise-with-power-bi"></a>Connettersi a Microsoft Azure Enterprise con Power BI
Esplorare e monitorare i dati di Microsoft Azure Enterprise in Power BI con il pacchetto di contenuto Power BI. I dati verranno aggiornati automaticamente una volta al giorno.

Connettersi al [pacchetto di contenuto Microsoft Azure Enterprise](https://app.powerbi.com/getdata/services/azure-enterprise) per Power BI.

## <a name="how-to-connect"></a>Come connettersi
1. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro.
   
    ![](media/service-connect-to-azure-enterprise/getdata.png)
2. Nella casella **Servizi** selezionare **Recupera**.
   
   ![](media/service-connect-to-azure-enterprise/services.png)
3. Selezionare **Microsoft Azure Enterprise** \> **Recupera**.
   
   ![](media/service-connect-to-azure-enterprise/mazureenterprise.png)
4. Fornire l'URL dell'ambiente Azure, il numero dei mesi di dati che si vogliono importare e il numero di iscrizione di Azure Enterprise. L'URL dell'ambiente Azure sarà `https://ea.azure.com` o `https://ea.windowsazure.cn`. Per informazioni dettagliate su [come trovare questi parametri](#FindingParams), vedere più avanti.
   
    ![](media/service-connect-to-azure-enterprise/params.png)
5. Specificare la chiave di accesso per la connessione. La chiave per l'iscrizione è reperibile nel portale Azure EA.
   
    ![](media/service-connect-to-azure-enterprise/creds.png)
6. Il processo di importazione inizierà automaticamente. Al termine nel riquadro di spostamento verranno visualizzati un nuovo dashboard, un nuovo report e un nuovo set di dati. Selezionare il dashboard per visualizzare i dati importati.
   
   ![](media/service-connect-to-azure-enterprise/dashboard.png)

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](consumer/end-user-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](consumer/end-user-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificarne la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="whats-included"></a>Cosa è incluso
Il pacchetto di contenuto Azure Enterprise include dati di report mensili per l'intervallo di mesi specificato durante il flusso di connessione. L'intervallo è una finestra mobile, quindi le date incluse vengono aggiornate quando viene aggiornato il set di dati.

## <a name="system-requirements"></a>Requisiti di sistema
Il pacchetto di contenuto richiede l'accesso alle funzionalità aziendali nel portale di Azure.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Individuazione dei parametri
I report di Power Bi sono disponibili per EA Direct, partner e clienti indiretti che riescono a visualizzare le informazioni di fatturazione. Leggere di seguito per informazioni dettagliate su come trovare i valori previsti dal flusso di connessione.

**URL dell'ambiente Azure**

* Questo valore corrisponde in genere a https://ea.azure.com, tuttavia è possibile controllare l'URL dopo l'accesso per confermarlo.
  
    ![](media/service-connect-to-azure-enterprise/params3.png)

**Numero di mesi**

* Deve essere un numero compreso tra 1 e 36 che rappresenta il numero di mesi di dati (dalla data odierna) che si vuole importare.

**Numero di registrazione**

* Si tratta del numero di registrazione di Azure Enterprise indicato nella schermata iniziale di [Azure Enterprise Portal](https://ea.azure.com/) in "Dettagli della registrazione".
  
    ![](media/service-connect-to-azure-enterprise/params2.png)

**Chiave di accesso**

* La chiave è reperibile nel portale di Azure Enterprise, in "Scarica utilizzo" > "Chiave di accesso API"
  
    ![](media/service-connect-to-azure-enterprise/creds2.png)

**Guida aggiuntiva**

* Per informazioni aggiuntive sulla configurazione del pacchetto Azure Enterprise per Power BI, accedere ad Azure Enterprise Portal per visualizzare il file della Guida dell'API disponibile in "Guida". Altre informazioni sono disponibili in Report -> Scarica utilizzo -> Chiave di accesso API.

## <a name="next-steps"></a>Passaggi successivi
[Introduzione a Power BI](service-get-started.md)

[Recuperare dati in Power BI](service-get-data.md)

