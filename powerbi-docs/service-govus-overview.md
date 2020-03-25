---
title: Power BI per i clienti del Governo degli Stati Uniti - Panoramica
description: I clienti del Governo degli Stati Uniti possono aggiungere una sottoscrizione Power BI Pro al piano Office 365 Government. Informazioni su come registrarsi e verificare la disponibilità delle funzionalità nella descrizione del servizio.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/13/2020
ms.author: kfollis
LocalizationGroup: Get started
ms.openlocfilehash: 349b4d51c1649b714c67e61ac42ddcc49b2eeb12
ms.sourcegitcommit: 2c798b97fdb02b4bf4e74cf05442a4b01dc5cbab
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2020
ms.locfileid: "80114889"
---
# <a name="power-bi-for-us-government-customers"></a>Power BI per i clienti del Governo degli Stati Uniti
Questo articolo è destinato ai clienti del Governo degli Stati Uniti che distribuiscono Power BI come parte di un piano Office 365 Government. I piani Government sono progettati per le esigenze specifiche delle organizzazioni che devono soddisfare gli standard di conformità e sicurezza degli Stati Uniti. Il servizio Power BI progettato per i clienti del Governo degli Stati Uniti è diverso dalla versione commerciale del servizio Power BI. Le differenze delle funzionalità e delle capacità sono descritte nelle sezioni seguenti.

## <a name="add-power-bi-to-your-office-365-government-plan"></a>Aggiungere Power BI al piano Office 365 Government

Prima di poter ottenere una sottoscrizione di Power BI per il Governo degli Stati Uniti e assegnare le licenze agli utenti, è necessario registrarsi in un piano Office 365 Government. Se l'organizzazione ha già un piano Office 365 Government, passare alla sezione [Acquistare una sottoscrizione Power BI Pro Government](#purchase-a-power-bi-pro-government-subscription).

### <a name="enroll-in-office-365-government-plan"></a>Registrarsi in un piano Office 365 Government

Se si è un nuovo cliente, è necessario convalidare l'idoneità dell'organizzazione prima di effettuare la registrazione in un piano Government.  Per iniziare, compilare il [modulo per la convalida dell'idoneità di Office 365 for Government](https://www.microsoft.com/microsoft-365/government/eligibility-validation). Per assicurarsi di selezionare il piano appropriato per l'organizzazione, vedere le [descrizioni del servizio Office 365 US Government](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/office-365-us-government).

> [!NOTE]
> Se Power BI è già stato distribuito in un ambiente commerciale e si vuole eseguire la migrazione al cloud del Governo degli Stati Uniti, è necessario aggiungere una nuova sottoscrizione di Power BI Pro al piano Office 365 Government. Successivamente, replicare i dati commerciali nel servizio Power BI per il Governo degli Stati Uniti, rimuovere le assegnazioni di licenze commerciali dagli account utente e quindi assegnare una licenza di Power BI Pro Government agli account utente.
>
>

### <a name="government-cloud-instances"></a>Istanze del cloud del Governo
Office 365 offre diversi ambienti per gli enti pubblici per soddisfare requisiti di conformità diversi. Vedere le descrizioni dei servizi collegati per informazioni dettagliate sulle funzionalità offerte da ogni ambiente.

* [Office 365 Government Community Cloud (GCC)](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc) è progettato per enti pubblici federali, statali e locali.

* [Office 365 Government Community Cloud High (GCC-High)](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) è progettato per gli enti pubblici federali, il settore della difesa, il settore aerospaziale e altre organizzazioni che trattano informazioni non classificate controllate. Questo ambiente è adatto per le organizzazioni e le aziende di sicurezza nazionale con requisiti ITAR (International Traffic in Arms Regulations) o DFARS (Defense Federal Acquisition Regulations Supplement).

* L'[ambiente Office 365 DoD (Department of Defense)](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) è progettato esclusivamente per il Dipartimento della difesa degli Stati Uniti. 

### <a name="purchase-a-power-bi-pro-government-subscription"></a>Acquistare una sottoscrizione Power BI Pro Government

Dopo aver distribuito Office 365, è possibile aggiungere una sottoscrizione di Power BI. Seguire le istruzioni dettagliate riportate in [Registrare l'organizzazione governativa statunitense](service-govus-signup.md#existing-office-government-cloud-customers) per acquistare il servizio Power BI Pro Government. Acquistare un numero di licenze sufficiente per tutti gli utenti che devono usare Power BI, quindi assegnare le licenze ai singoli account utente.

> [!IMPORTANT]
> Power BI US Government non è disponibile come licenza gratuita. A ogni utente deve essere assegnata una licenza Pro per poter accedere a Government Community Cloud. Se a un account utente è assegnata una licenza gratuita, l'utente è autorizzato ad accedere solo al cloud commerciale e si verificheranno problemi di autenticazione e accesso. Se è stato acquistato Power BI Premium, non è necessario assegnare licenze Pro per abilitare l'accesso utente.  Tutti gli utenti dell'organizzazione possono accedere ai report condivisi con loro purché il report venga pubblicato in una capacità Premium. Per esaminare le differenze tra i tipi di licenza, vedere [Funzionalità del servizio Power BI in base al tipo di licenza](service-features-license-type.md).
>
>

## <a name="connect-to-power-bi-for-us-government"></a>Connettersi a Power BI per Governo degli Stati Uniti

Per connettersi a Power BI per Governo degli Stati Uniti si usa un URL diverso da quello usato dagli utenti commerciali. Per accedere a Power BI, usare gli URL seguenti:

| URL della versione commerciale | URL della versione US Government | URL del Governo degli Stati Uniti per GCC High |
| --- | --- | --- |
| https://app.powerbi.com/ |[https://app.powerbigov.us](https://app.powerbigov.us) | [https://app.high.powerbigov.us](https://app.high.powerbigov.us) |

È possibile che sia stato effettuato il provisioning dell'account per più di un cloud. In tal caso, quando si usa Power BI Desktop, è possibile scegliere il cloud a cui connettersi quando si esegue l'accesso.

## <a name="connectivity-between-government-and-global-azure-cloud-services"></a>Connettività tra il servizio cloud di Azure globale e il servizio per enti pubblici

Azure viene distribuito in più cloud. Per impostazione predefinita, è possibile abilitare le regole del firewall per aprire una connessione a un'istanza di cloud specifica, ma la connessione a più cloud è un'operazione diversa.  Per stabilire una comunicazione tra i servizi nel cloud pubblico e i servizi in Government Community Cloud, è necessario configurare regole del firewall specifiche. Se ad esempio si vuole accedere a istanze del cloud pubblico di SQL dalla distribuzione del cloud per enti pubblici di Power BI, è necessaria una regola del firewall in SQL. Configurare regole del firewall specifiche in SQL per consentire le connessioni al cloud Azure per enti pubblici per i data center seguenti:

* USGov Iowa
* USGov Virginia
* USGov Texas
* USGov Arizona

Nel cloud pubblico gli intervalli IP sono disponibili. Per ottenere gli intervalli IP del cloud per il Governo degli Stati Uniti, scaricare il file [Azure IP Ranges and Service Tags - US Government Cloud](https://www.microsoft.com/download/details.aspx?id=57063). 

Per configurare i firewall in SQL, seguire i passaggi per [Creare e gestire regole del firewall IP](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure#create-and-manage-ip-firewall-rules).

## <a name="power-bi-feature-availability"></a>Disponibilità delle funzionalità di Power BI

Per soddisfare i requisiti dei clienti del cloud per enti pubblici, esistono alcune differenze tra i piani per enti pubblici e i piani commerciali. Fare riferimento alla tabella seguente per conoscere le funzionalità disponibili in ogni ambiente per enti pubblici.

|Feature |   |GCC |GCC-High |DoD|
|------|------|------|------|------|
|Administration|Licenze gratuite|Non disponibile|Non disponibile|Non disponibile|
|  |Impostazione di limiti di archiviazione dati|Disponibile|Disponibile|Disponibile|
|  |Uso di gruppi di Active Directory per il controllo di condivisione e accesso|Disponibile|Disponibile|Disponibile|
|  |Controllo tramite il centro conformità e sicurezza di Office 365|Disponibile|Disponibile|Disponibile|
|  |Condivisione degli utenti esterni|Disponibile|Disponibile|Disponibile|
|  |Metriche di utilizzo per report e dashboard|Non disponibile|Non disponibile|Non disponibile|
|  |Azure B2B tra GCC e cloud commerciale|Non disponibile|Non disponibile|Non disponibile|
|Creazione di report|Creare e visualizzare dashboard e report|Disponibile|Disponibile|Disponibile|
|  |Aggiornamento dati pianificato|Disponibile|Disponibile|Disponibile|
|  |Dashboard del team aggiornabili|Disponibile|Disponibile|Disponibile|
|  |Report impaginati|Disponibile|Disponibile|Nella roadmap|
|  |App modello|Non disponibile|Non disponibile|Non disponibile|
|Connettersi ai dati|Importazione di dati e report da Excel|Disponibile|Disponibile|Disponibile|
|  |Importazione di dati da file CSV|Disponibile|Disponibile|Disponibile|
|  |Importazione di dati da file di Power BI Desktop|Disponibile|Disponibile|Disponibile|
|  |Connettività a CDS|Disponibile|Non disponibile|Non disponibile|
|  |Connettore di Azure Data Lake Storage Gen2|Disponibile|Non disponibile|Non disponibile|
|Gestione dei dati|Gateway di gestione dati|Disponibile|Disponibile|Disponibile|
|  |Crittografia dei dati in Azure SQL|Disponibile|Disponibile|Disponibile|
|  |Crittografia dei dati nell'archiviazione BLOB per Power BI|Disponibile|Disponibile|Disponibile|
|Integrazione tra prodotti|Incorporamento in SharePoint Online tramite la Web part Power BI|Non disponibile|Non disponibile|Non disponibile|
|  |Incorporamento in SharePoint Online tramite la Web part Embed|Disponibile|Disponibile|Disponibile|
|  |Flussi di dati e funzioni di intelligenza artificiale|Non disponibile|Non disponibile|Non disponibile|
|  |Connettività Power Automate per avvisi basati sui dati|Non disponibile|Non disponibile|Non disponibile|
|  |Scheda Power BI nei team|Disponibile|Non disponibile|Non disponibile|
|  |Funzionalità automatizzate di Machine Learning|Non disponibile|Non disponibile|Non disponibile|
|  |Servizi cognitivi|Non disponibile|Non disponibile|Non disponibile|
|  |Azure ML|Non disponibile|Non disponibile|Non disponibile|

## <a name="next-steps"></a>Passaggi successivi

* [Iscrizione a Power BI per il Governo degli Stati Uniti](service-govus-signup.md)
* [Microsoft Power Apps per US Government](https://docs.microsoft.com/power-platform/admin/powerapps-us-government)
* [Power Automate US Government](https://docs.microsoft.com/power-automate/us-govt)
* <a href="https://channel9.msdn.com/Blogs/Azure/Cognitive-Services-HDInsight-and-Power-BI-on-Azure-Government">Demo di Power BI per il Governo degli Stati Uniti</a>
