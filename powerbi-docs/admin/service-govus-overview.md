---
title: Clienti di Power BI per Governo degli Stati Uniti - Panoramica
description: I clienti del governo degli Stati Uniti possono aggiungere una sottoscrizione Power BI Pro al piano Microsoft 365 Government. Informazioni su come registrarsi e verificare la disponibilità delle funzionalità nella descrizione del servizio.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/07/2020
ms.author: kfollis
LocalizationGroup: Get started
ms.openlocfilehash: aeaaf0e1e8baa70b5159d908ce1e27bb937de372
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83344711"
---
# <a name="power-bi-for-us-government-customers"></a>Clienti di Power BI per Governo degli Stati Uniti
Questo articolo è destinato ai clienti del Governo degli Stati Uniti che distribuiscono Power BI come parte di un piano Office 365 Government. I piani Government sono progettati per le esigenze specifiche delle organizzazioni che devono soddisfare gli standard di conformità e sicurezza degli Stati Uniti. Il servizio Power BI progettato per i clienti del governo degli Stati Uniti è diverso dalla versione commerciale del servizio Power BI. Le differenze delle funzionalità e delle capacità sono descritte nelle sezioni seguenti.

## <a name="add-power-bi-to-your-office-365-government-plan"></a>Aggiungere Power BI al piano Office 365 Government

Prima di poter ottenere una sottoscrizione di Power BI per Governo degli Stati Uniti e assegnare le licenze agli utenti, è necessario registrarsi in un piano Office 365 Government. Se l'organizzazione ha già un piano Office 365 Government, passare alla sezione relativa all'[acquisto di una sottoscrizione Power BI Pro per i clienti del settore pubblico](#buy-a-power-bi-pro-subscription-for-government-customers).

### <a name="enroll-in-an-office-365-government-plan"></a>Registrarsi in un piano Office 365 Government

Se si è un nuovo cliente, è necessario convalidare l'idoneità dell'organizzazione prima di effettuare la registrazione in un piano Office 365 Government.  Per iniziare, compilare il [modulo per la convalida dell'idoneità di Office 365 for Government](https://www.microsoft.com/microsoft-365/government/eligibility-validation). Per assicurarsi di selezionare il piano appropriato per l'organizzazione, vedere le [descrizioni del servizio Office 365 US Government](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/office-365-us-government).

> [!NOTE]
> Se Power BI è già stato distribuito in un ambiente commerciale e si vuole eseguire la migrazione al cloud del governo degli Stati Uniti, è necessario aggiungere una nuova sottoscrizione di Power BI Pro al piano Office 365 Government. Successivamente, replicare i dati commerciali nel servizio Power BI per il governo degli Stati Uniti, rimuovere le assegnazioni di licenze commerciali dagli account utente e quindi assegnare una licenza di Power BI Pro Government agli account utente.
>
>
## <a name="government-cloud-instances"></a>Istanze del cloud del Governo
Office 365 offre diversi ambienti per gli enti pubblici per soddisfare requisiti di conformità diversi. Per altre informazioni ogni ambiente, vedere:

* [Office 365 Government Community Cloud (GCC)](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc) è progettato per enti pubblici federali, statali e locali.

* [Office 365 Government Community Cloud High (GCC High)](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) è progettato per gli enti pubblici federali, il settore della difesa, il settore aerospaziale e altre organizzazioni che trattano informazioni non classificate controllate. Questo ambiente è adatto per le organizzazioni e le aziende di sicurezza nazionale con requisiti ITAR (International Traffic in Arms Regulations) o DFARS (Defense Federal Acquisition Regulations Supplement).

* L'[ambiente Office 365 DoD (Department of Defense)](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) è progettato esclusivamente per il Dipartimento della difesa degli Stati Uniti. 

## <a name="connect-to-power-bi-for-us-government"></a>Connettersi a Power BI per Governo degli Stati Uniti

L'URL per la connessione a Power BI per gli utenti governativi è diverso da quello per gli utenti commerciali. Per accedere a Power BI, usare gli URL seguenti:

| Versione commerciale  | GCC  | GCC High | DoD |
| --- | --- | --- | --- |
| [https://app.powerbi.com/](https://app.powerbi.com) |[https://app.powerbigov.us](https://app.powerbigov.us) | [https://app.high.powerbigov.us](https://app.high.powerbigov.us) | [https://app.mil.powerbigov.us](https://app.mil.powerbigov.us) |

L'account potrebbe essere configurato in più di un cloud. Se l'account ha una configurazione di questo tipo, quando si accede a Power BI Desktop è possibile scegliere il cloud a cui connettersi.

## <a name="buy-a-power-bi-pro-subscription-for-government-customers"></a>Acquistare una sottoscrizione a Power BI Pro per i clienti di enti pubblici

Dopo aver distribuito Office 365, è possibile aggiungere una sottoscrizione di Power BI Pro. Seguire le istruzioni dettagliate riportate in [Registrare l'organizzazione governativa statunitense](service-govus-signup.md) per acquistare il servizio Power BI Pro per enti pubblici. Acquistare un numero di licenze sufficiente per tutti gli utenti che devono usare Power BI e quindi assegnare le licenze ai singoli account utente.

> [!IMPORTANT]
> Power BI per il Governo degli Stati Uniti non è disponibile come licenza *gratuita*. Per accedere a Government Community Cloud, è necessario assegnare a ogni utente una licenza *Pro*. Se a un account utente è stata assegnata una licenza gratuita, l'utente è autorizzato ad accedere solo al cloud commerciale e si verificheranno problemi di autenticazione e accesso. Se è stato acquistato Power BI Premium, non è necessario assegnare licenze Pro per abilitare l'accesso utente.  Gli utenti dell'organizzazione possono accedere ai report condivisi con loro purché i report siano pubblicati in una capacità Premium. Per esaminare le differenze tra i tipi di licenza, vedere [Funzionalità del servizio Power BI in base al tipo di licenza](../fundamentals/service-features-license-type.md).
>

## <a name="connect-government-and-global-azure-cloud-services"></a>Connettere il servizio cloud di Azure globale e il servizio per enti pubblici

Azure viene distribuito in più cloud. Per impostazione predefinita, è possibile abilitare le regole del firewall per aprire una connessione a un'istanza di cloud specifica, ma la connessione a più cloud è un'operazione diversa.  Per stabilire una comunicazione tra i servizi nel cloud pubblico e i servizi in Government Community Cloud, è necessario configurare regole del firewall specifiche. Se ad esempio si vuole accedere a istanze del cloud pubblico di un database SQL dalla distribuzione del cloud per enti pubblici di Power BI, è necessaria una regola del firewall nel database SQL. Configurare regole del firewall specifiche per i database SQL per consentire le connessioni al cloud Azure per enti pubblici per i data center seguenti:

* USGov Iowa
* USGov Virginia
* USGov Texas
* USGov Arizona

Nel cloud pubblico gli intervalli IP sono disponibili. Per ottenere gli intervalli IP del cloud per il governo degli Stati Uniti, scaricare il file [Azure IP Ranges and Service Tags - US Government Cloud](https://www.microsoft.com/download/details.aspx?id=57063). 

Per configurare i firewall per i database SQL, vedere [Creare e gestire regole del firewall IP](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure#create-and-manage-ip-firewall-rules).

## <a name="power-bi-feature-availability"></a>Disponibilità delle funzionalità di Power BI

Per soddisfare i requisiti dei clienti del cloud per enti pubblici, esistono alcune differenze tra i piani per enti pubblici e i piani commerciali. Per sapere quali sono le funzionalità disponibili in ogni ambiente per enti pubblici, fare riferimento alla tabella seguente:

|Feature |   |GCC |GCC High |DoD|
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
|  |Report impaginati|Disponibile|Nella roadmap|Nella roadmap|
|  |App modello|Non disponibile|Non disponibile|Non disponibile|
|Connettersi ai dati|Importazione di dati e report da Excel|Disponibile|Disponibile|Disponibile|
|  |Importazione di dati da file CSV|Disponibile|Disponibile|Disponibile|
|  |Importazione di dati da file di Power BI Desktop|Disponibile|Disponibile|Disponibile|
|  |Connettività a CDS|Disponibile|Non disponibile|Non disponibile|
|  |Connettore di Azure Data Lake Storage Gen2|Disponibile|Non disponibile|Non disponibile|
|Gestione dei dati|Gateway di gestione dati|Disponibile|Disponibile|Disponibile|
|  |Crittografia dei dati nel database Azure SQL|Disponibile|Disponibile|Disponibile|
|  |Crittografia dei dati nell'archiviazione BLOB per Power BI|Disponibile|Disponibile|Disponibile|
|Integrazione tra prodotti|Incorporamento in SharePoint Online tramite la Web part Power BI|Non disponibile|Non disponibile|Non disponibile|
|  |Incorporamento in SharePoint Online tramite la Web part Embed|Disponibile|Disponibile|Disponibile|
|  |Flussi di dati e funzioni di intelligenza artificiale|Non disponibile|Non disponibile|Non disponibile|
|  |Connettività Power Automate per avvisi basati sui dati|Non disponibile|Non disponibile|Non disponibile|
|  |Scheda Power BI nei team|Disponibile|Non disponibile|Non disponibile|
|  |Funzionalità automatizzate di Machine Learning|Non disponibile|Non disponibile|Non disponibile|
|  |Servizi cognitivi di Azure|Non disponibile|Non disponibile|Non disponibile|
|  |Azure Machine Learning|Non disponibile|Non disponibile|Non disponibile|

## <a name="next-steps"></a>Passaggi successivi

* [Iscrizione a Power BI per Governo degli Stati Uniti](service-govus-signup.md)
* [Microsoft Power Apps per US Government](https://docs.microsoft.com/power-platform/admin/powerapps-us-government)
* [Power Automate US Government](https://docs.microsoft.com/power-automate/us-govt)
* <a href="https://channel9.msdn.com/Blogs/Azure/Cognitive-Services-HDInsight-and-Power-BI-on-Azure-Government">Demo di Power BI per il Governo degli Stati Uniti</a>
