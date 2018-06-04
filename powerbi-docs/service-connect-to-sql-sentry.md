---
title: Connettersi a SQL Sentry con Power BI
description: SQL Sentry per Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 8ad41917c887cff7db991051aa35d5dad6b6a8fa
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34242424"
---
# <a name="connect-to-sql-sentry-with-power-bi"></a>Connettersi a SQL Sentry con Power BI
L'analisi dei dati delle prestazioni raccolti da SQL Sentry è facile con Power BI. Power BI recupera infatti i dati, creando quindi un dashboard predefinito e report correlati basati su tali dati.

Connettersi al [pacchetto di contenuto SQL Sentry](https://app.powerbi.com/groups/me/getdata/services/sql-sentry) per Power BI.

>[!NOTE]
>Per la connessione sono necessari l'accesso a un account SQL Sentry usato per connettersi a http://cloud.sqlsentry.com e un ID del database da monitorare.  Qui di seguito sono disponibili le istruzioni su dove trovare l'ID del database.

## <a name="how-to-connect"></a>Come connettersi
1. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro.
   
   ![](media/service-connect-to-sql-sentry/pbi_getdata.png)
2. Nella casella **Servizi** selezionare **Recupera**.
   
   ![](media/service-connect-to-sql-sentry/pbi_getservices.png) 
3. Selezionare **SQL Sentry \> Recupera**.
   
   ![](media/service-connect-to-sql-sentry/sqlsentry.png)
4. Fornire l' **ID** del database che si vuole monitorare in Power BI. Per informazioni dettagliate su come [trovare questo valore](#FindingParams), vedere più avanti.
   
   ![](media/service-connect-to-sql-sentry/img2400.png)
5. In Metodo di autenticazione selezionare **oAuth2 \> Accedi**.
   
   Quando richiesto, immettere le credenziali di cloud.sqlsentry.com e seguire il processo di autenticazione di SQL Sentry.
   
   ![](media/service-connect-to-sql-sentry/img6400.png)
   
   Alla prima connessione Power BI chiede di consentire l'accesso in sola lettura all'account. Selezionare Consenti per avviare il processo di importazione.  L'operazione di importazione può richiedere qualche minuto a seconda del volume dei dati dell'account.
   
   ![](media/service-connect-to-sql-sentry/img7400.png)
6. Dopo l'importazione dei dati in Power BI, nel riquadro di spostamento sinistro vengono visualizzati il nuovo dashboard, il nuovo report e il nuovo set di dati. I nuovi elementi sono contrassegnati con un asterisco giallo \*:
   
   ![](media/service-connect-to-sql-sentry/img8200.png)
7. Selezionare il dashboard di SQL Sentry.
   
   Si tratta del dashboard predefinito creato da Power BI per visualizzare i dati, che è possibile modificare per visualizzare i dati nel modo desiderato.
   
   ![](media/service-connect-to-sql-sentry/img9dashboard800.png)

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](power-bi-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](service-dashboard-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificare la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="whats-included"></a>Cosa è incluso
I dati seguenti sono disponibili da SQL Sentry in Power BI:

| Nome tabella | Descrizione |
| --- | --- |
| Connessione |Questa tabella fornisce informazioni sulle connessioni SQL Sentry definite. |
| Data<br /> |Questa tabella contiene date dalla data odierna fino alla prima data in cui sono stati raccolti e conservati i dati delle prestazioni. |
| Tempo di inattività<br /> |Questa tabella contiene informazioni relative ai tempi di inattività e di attività per ogni server monitorato nell'ambiente in uso. |
| Utilizzo memoria<br /> |Questa tabella contiene dati sulla quantità di memoria disponibile o libera in ogni server.<br /> |
| Server<br /> |Questa tabella contiene record per ogni server nell'ambiente in uso. |
| Integrità del server<br /> |Questa tabella contiene dati per tutti gli eventi generati da condizioni personalizzate nell'ambiente in uso, tra cui gravità e conteggio. |

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Individuazione dei parametri
È possibile trovare l'**ID database** con l'accesso a <https://cloud.sqlsentry.com> in una nuova finestra del Web browser.  L' **ID database** è elencato nella pagina di panoramica principale:

    ![](media/service-connect-to-sql-sentry/database2.png)

L' **ID database** viene visualizzato anche nella schermata Dettagli database:

    ![](media/service-connect-to-sql-sentry/database.png)


## <a name="troubleshooting"></a>Risoluzione dei problemi
Se i dati di qualche app non vengono visualizzati in Power BI, verificare di stare usando l'ID database corretto e di avere l'autorizzazione a visualizzare i dati. 

Se non si è proprietari del database SQL Sentry in corso di sincronizzazione con <https://cloud.sqlsentry.com>, contattare l'amministratore per verificare di avere l'autorizzazione necessaria a visualizzare i dati raccolti.

## <a name="next-steps"></a>Passaggi successivi
[Introduzione a Power BI](service-get-started.md)

[Recuperare dati per Power BI](service-get-data.md)

