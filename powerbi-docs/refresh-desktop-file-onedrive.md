---
title: Aggiornare un set di dati creato da un file di Power BI Desktop in OneDrive o SharePoint Online
description: Aggiornare un set di dati creato da un file di Power BI Desktop in OneDrive o SharePoint Online
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Data refresh
ms.openlocfilehash: 2c52dd30a2b0dc911adbf706ec5007bb553f2717
ms.sourcegitcommit: 001ea0ef95fdd4382602bfdae74c686de7dc3bd8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38925283"
---
# <a name="refresh-a-dataset-stored-on-onedrive-or-sharepoint-online"></a>Aggiornare un set di dati memorizzato in OneDrive o SharePoint Online
Importare i file da OneDrive o SharePoint Online nel servizio Power BI è un modo efficace per garantire la sincronizzazione delle operazioni in **Power BI Desktop** con il servizio Power BI.

## <a name="advantages-of-storing-a-power-bi-desktop-file-on-onedrive-or-sharepoint-online"></a>Vantaggi dell'aggiornamento di un file di Power BI Desktop in OneDrive o SharePoint Online
Quando si archivia un file di **Power BI Desktop** in OneDrive o SharePoint Online, i dati caricati nel modello di file vengono importati nel set di dati e i report creati nel file vengono caricati in **Report** nel servizio Power BI. Quando si modifica il file in OneDrive o SharePoint Online, ad esempio si aggiungono nuove misure, si modificano i nomi delle colonne oppure si modificano le visualizzazioni, dopo il salvataggio del file le modifiche vengono aggiornate anche nel servizio Power BI, in genere entro circa un'ora.

È possibile eseguire un aggiornamento singolo manuale direttamente in Power BI Desktop selezionando Aggiorna nella scheda Home della barra multifunzione. Quando si seleziona Aggiorna, i dati nel modello di *file* vengono aggiornati con dati aggiornati provenienti dall'origine dati originale. Questo tipo di aggiornamento, completamente interno all'applicazione di Power BI Desktop, è diverso da un aggiornamento manuale o pianificato in Power BI ed è importante comprendere la differenza.

![](media/refresh-desktop-file-onedrive/pbix-refresh.png)

Quando si importa il file di Power BI Desktop da OneDrive o SharePoint Online, i dati e le altre informazioni sul modello vengono caricati in un set di dati in Power BI. Nel servizio Power BI, e non in Power BI Desktop, è opportuno aggiornare i dati nel set di dati perché i report nel servizio Power BI si basano su di essi. Dal momento che le origini dati sono esterne, è possibile aggiornare manualmente il set di dati usando **Aggiorna ora** o configurare una pianificazione dell'aggiornamento usando **Pianifica aggiornamenti**.

Quando si aggiorna il set di dati, Power BI non si connette al file in OneDrive o SharePoint Online per eseguire query per i dati aggiornati. Usa le informazioni nel set di dati per connettersi direttamente alle origini dati per eseguire query per i dati aggiornati, quindi li carica nel set di dati. I dati aggiornati nel set di dati non vengono sincronizzati di nuovo con il file in OneDrive o SharePoint Online.

## <a name="whats-supported"></a>Che cosa è supportato?
Le opzioni Aggiorna ora e Pianifica aggiornamenti in Power BI sono supportate per i set di dati creati dai file di Power BI Desktop importati da un'unità locale in cui viene usato Recupera dati/Editor di query per connettersi e caricare i dati da una delle origini dati seguenti:

### <a name="power-bi-gateway---personal"></a>Power BI Gateway - Personal
* Tutte le origini dati online visualizzate in Recupera dati ed Editor di query di Power BI Desktop.
* Tutte le origini dati locali visualizzate in Recupera dati ed Editor di query di Power BI Desktop, tranne il file Hadoop (HDFS) e Microsoft Exchange.

<!-- Refresh Data sources-->
[!INCLUDE [refresh-datasources](./includes/refresh-datasources.md)]

> [!NOTE]
> un gateway deve essere installato e in esecuzione per connettere Power BI alle origini dati locali e aggiornare il set di dati.
> 
> 

## <a name="onedrive-or-onedrive-for-business-whats-the-difference"></a>OneDrive o OneDrive for Business. Qual è la differenza?
Se si ha un account OneDrive personale e OneDrive for Business, è consigliabile mantenere tutti i file da importare in Power BI in OneDrive for Business. Motivo: è probabile che verranno usati due account diversi per l'accesso.

La connessione a OneDrive for Business in Power BI in genere non crea problemi perché l'account usato per accedere a Power BI spesso coincide con quello usato per accedere a OneDrive for Business. Invece, con l'account OneDrive personale, l'accesso viene solitamente eseguito con un altro [account Microsoft](https://account.microsoft.com).

Quando si accede con l'account Microsoft, assicurarsi di selezionare Mantieni l'accesso. Power BI può quindi sincronizzare tutti gli aggiornamenti apportati nel file di Power BI Desktop con i set di dati in Power BI  
    ![](media/refresh-desktop-file-onedrive/refresh_signin_keepmesignedin.png)

Se si apportano modifiche al file in OneDrive che non possono essere sincronizzate con il set di dati o i report in Power BI perché le credenziali dell'account Microsoft sono state modificate, è necessario connettersi e importare di nuovo il file dall'account OneDrive personale.

## <a name="how-do-i-schedule-refresh"></a>Come si pianifica l'aggiornamento?
Quando si configura una pianificazione dell'aggiornamento, Power BI si connetterà direttamente alle origini dati usando le informazioni e le credenziali di connessione nel set di dati per eseguire query per i dati aggiornati e quindi caricherà i dati aggiornati nel set di dati. Vengono aggiornate anche le visualizzazioni nei report e nei dashboard basati sul set di dati nel servizio Power BI.

Per informazioni dettagliate su come configurare l'aggiornamento pianificato, vedere [Configurare l'aggiornamento pianificato](refresh-scheduled-refresh.md).

## <a name="when-things-go-wrong"></a>In caso di errore
In caso di errori, il problema in genere è dovuto al fatto che Power BI non riesce ad accedere alle origini dati oppure, se il set di dati si connette a un'origine dati locale, al fatto che il gateway è offline. Assicurarsi che Power BI possa accedere alle origini dati. Se una password usata per accedere a un'origine dati viene modificata oppure Power BI viene disconnesso da un'origine dati, provare a effettuare di nuovo l'accesso alle origini dei dati in Credenziali origine dati.

Se si modifica e si salva il file di Power BI Desktop in OneDrive e le modifiche non vengono riportate in Power BI entro circa un'ora, Power BI potrebbe non riuscire a connettersi a OneDrive. Riprovare a connettersi al file in OneDrive. Se viene chiesto di effettuare l'accesso, assicurarsi di selezionare Mantieni l'accesso. La connessione di Power BI a OneDrive per la sincronizzazione con il file non è riuscita, quindi è necessario importare nuovamente il file.

Assicurarsi di lasciare selezionato **Inviami il messaggio di notifica di aggiornamento non riuscito** . È opportuno sapere immediatamente se un aggiornamento pianificato non riesce.

## <a name="troubleshooting"></a>Risoluzione dei problemi
A volte, l'aggiornamento dei dati non funziona come previsto. In genere si tratta di un problema relativo al gateway. Consultare gli articoli sulla risoluzione dei problemi del gateway per individuare gli strumenti utili e i problemi noti.

[Risoluzione dei problemi del gateway dati locale](service-gateway-onprem-tshoot.md)

[Risoluzione dei problemi di Gateway di Power BI - Personale](service-admin-troubleshooting-power-bi-personal-gateway.md)

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

