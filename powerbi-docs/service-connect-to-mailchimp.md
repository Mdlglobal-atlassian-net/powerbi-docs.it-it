---
title: Connettersi a MailChimp con Power BI
description: MailChimp per Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 6a62b97a4c7d75644bd3a824118414509ef8438f
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34241183"
---
# <a name="connect-to-mailchimp-with-power-bi"></a>Connettersi a MailChimp con Power BI
Il pacchetto di contenuto Power BI estrae i dati dall'account MailChimp e genera un dashboard, un set di report e un set di dati utili per l'esplorazione dei dati. Integrare le funzionalità di analisi per creare [dashboard MailChimp](https://powerbi.microsoft.com/integrations/mailchimp) e identificare rapidamente le tendenze in campagne, report e singoli sottoscrittori. I dati sono impostati in modo da essere aggiornati quotidianamente.

Connettersi al [pacchetto di contenuto MailChimp](https://app.powerbi.com/getdata/services/mailchimp) per Power BI.

## <a name="how-to-connect"></a>Come connettersi
1. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro.
   
    ![](media/service-connect-to-mailchimp/pbi_getdata.png)
2. Nella casella **Servizi** selezionare **Recupera**.
   
   ![](media/service-connect-to-mailchimp/pbi_getservices.png)
3. Selezionare **MailChimp** \> **Recupera**.
   
   ![](media/service-connect-to-mailchimp/mailchimp.png)
4. In Metodo di autenticazione selezionare **oAuth2** \> **Accedi**.
   
    Quando richiesto, immettere le credenziali di MailChimp e seguire il processo di autenticazione.
   
    Alla prima connessione verrà richiesto di consentire a Power BI l'accesso in sola lettura all'account. Selezionare **Consenti** per avviare il processo di importazione che può richiedere qualche minuto a seconda del volume dei dati dell'account.
   
    ![](media/service-connect-to-mailchimp/allow.png)
5. Dopo l'importazione dei dati in Power BI, nel riquadro di spostamento sinistro vengono visualizzati il nuovo dashboard, il nuovo report e il nuovo set di dati. Si tratta del dashboard predefinito creato da Power BI per visualizzare i dati, che è possibile modificare per visualizzare i dati nel modo desiderato.
   
   ![](media/service-connect-to-mailchimp/pbi_mailchimpnewdash.png)

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](power-bi-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](service-dashboard-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificare la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="next-steps"></a>Passaggi successivi
[Introduzione a Power BI](service-get-started.md)

[Power BI - Concetti di base](service-basic-concepts.md)

