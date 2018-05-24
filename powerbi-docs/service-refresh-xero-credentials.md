---
title: Come aggiornare le credenziali del pacchetto di contenuto Xero
description: Se si usa il pacchetto di contenuto Xero di Power BI, potrebbe essersi verificato un problema con l'aggiornamento giornaliero del pacchetto di contenuto a causa di un recente evento imprevisto del servizio Power BI.
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 08/10/2017
ms.author: sarinas
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 5978443f05e039c34ff023f235624968b5eb8a3e
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="how-to-refresh-your-xero-content-pack-credentials-if-refresh-failed"></a>Come aggiornare le credenziali del pacchetto di contenuto Xero se l'aggiornamento non è riuscito
Se si usa il pacchetto di contenuto Xero di Power BI, potrebbero essersi verificati alcuni problemi con l'aggiornamento giornaliero del pacchetto di contenuto a causa di un recente evento imprevisto del servizio Power BI.

Per verificare che il pacchetto di contenuto sia stato aggiornato correttamente, controllare lo stato dell'ultimo aggiornamento del set di dati Xero, come illustrato nella schermata seguente.

![](media/service-refresh-xero-credentials/powerbi-xero-refresh-failed.png)

Se indica che tale aggiornamento non è riuscito, come illustrato sopra, seguire questa procedura per rinnovare le credenziali per il pacchetto di contenuto.

1. Fare clic sui puntini di sospensione (...) accanto al set di dati Xero, quindi fare clic su **Pianifica aggiornamento**. Verrà visualizzata la pagina delle impostazioni per il pacchetto di contenuto Xero.
   
    ![](media/service-refresh-xero-credentials/powerbi-xero-schedule-refresh.png)
2. Nella pagina **Impostazioni per Xero** selezionare **Credenziali origine dati** > **Modifica credenziali**.
   
    ![](media/service-refresh-xero-credentials/powerbi-xero-settings-page.png)
3. Immettere il nome dell'organizzazione > **Avanti**.
   
    ![](media/service-refresh-xero-credentials/powerbi-xero-configure.png)
4. Accedere con l'account Xero.
   
    ![](media/service-refresh-xero-credentials/powerbi-xero-welcome.png)
5. Dopo aver aggiornato le credenziali, assicurarsi di aver pianificato l'esecuzione giornaliera dell'aggiornamento. Per verificarlo, fare clic sui puntini di sospensione (...) accanto al set di dati Xero, quindi fare di nuovo clic su **Pianifica aggiornamento**.
   
    ![](media/service-refresh-xero-credentials/powerbi-xero-refresh-schedule.png)
6. È anche possibile scegliere di aggiornare immediatamente il set di dati. Fare clic sui puntini di sospensione (...) accanto al set di dati Xero, quindi fare clic su **Aggiorna adesso**.
   
    ![](media/service-refresh-xero-credentials/powerbi-xero-refresh-now.png)

Se si verificano ancora problemi di aggiornamento, non esitare a contattare Microsoft all'indirizzo [http://support.powerbi.com](http://support.powerbi.com) 

Per altre informazioni sul pacchetto di contenuto Xero per Power BI, visitare la [pagina della Guida del pacchetto di contenuto Xero](service-connect-to-xero.md).

### <a name="next-steps"></a>Passaggi successivi
* Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

