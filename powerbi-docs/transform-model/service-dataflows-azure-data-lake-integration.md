---
title: Integrazione di flussi di dati e Azure Data Lake
description: Panoramica delle modalità di integrazione di flussi di dati di Power BI con Azure Data Lake Storage Gen2
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/02/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 5b13fdc1f65fe2650ea0fb4fee1be20611ac3e8b
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83307498"
---
# <a name="dataflows-and-azure-data-lake-integration-preview"></a>Integrazione di flussi di dati e Azure Data Lake (anteprima)

Per impostazione predefinita, i dati usati con Power BI vengono archiviati nello spazio di archiviazione interno fornito da Power BI. Con l'integrazione di flussi di dati e Azure Data Lake Storage Gen2 (ADLS Gen2), è possibile archiviare i flussi di dati nell'account di Azure Data Lake Storage Gen2 della propria organizzazione. 

![flussi di dati in archiviazione di Azure](media/service-dataflows-azure-data-lake-integration/dataflows-azure-integration_01.jpg)

## <a name="how-cdm-folders-relate-to-dataflows"></a>Relazione tra cartelle CDM e flussi di dati

Con i **flussi di dati**, utenti e organizzazioni possono unificare i dati da origini diverse e prepararli per la modellazione. Grazie al modello CDM (Common Data Model) le organizzazioni possono usare un formato di dati che offre coerenza semantica tra applicazioni e distribuzioni. Con Azure Data Lake Storage gen2 (ADLS Gen2), inoltre, è possibile applicare procedure dettagliate di controllo degli accessi e delle autorizzazioni ai data lake in Azure. Questi elementi in combinazione offrono funzionalità avanzate per dati centralizzati, dati strutturati, controllo di accesso con granularità fine e coerenza semantica per app e iniziative nell'intera organizzazione.

I dati archiviati in formato CDM offrono coerenza semantica tra applicazioni e distribuzioni in un'organizzazione. Con l'integrazione di CDM con ADLS Gen2, è possibile applicare la stessa coerenza strutturale e semantica ai dati archiviati in ADLS Gen2 usando cartelle CDM che contengono dati schematizzati in formato CDM standard. I metadati standardizzati e i dati auto-descrittivi in un Azure Data Lake facilitano l'individuazione dei metadati e l'interoperabilità tra i produttori dei dati e consumer come Power BI, Azure Data Factory, Azure Data Lake, Databricks e Azure Machine Learning (ML). 

I flussi di dati archiviano definizioni e dati nelle cartelle CDM, nei formati seguenti:

**Model.json**
* Il file di descrizione dei metadati **Model.json** contiene informazioni semantiche sui record di entità e gli attributi, oltre a collegamenti ai file di dati sottostanti. L'esistenza del file Model.json indica la conformità con il formato di metadati CDM e può includere le entità standard che dispongono di dati semantici predefiniti aggiuntivi utilizzabili dalle applicazioni.
* Power BI archivia anche le informazioni su ogni origine dati insieme alle **query e alle trasformazioni** generate dall'esperienza dell'editor del flusso di dati nel servizio Power BI. Le password per le origini dati non vengono archiviate nel file del modello.

**File di dati**
* I file di dati vengono inclusi nella cartella CDM con una struttura e un formato ben definiti (le sottocartelle sono facoltative, come descritto più avanti in questo articolo) e si fa riferimento a tali file nel file Model.json. Attualmente, i file di dati devono essere in formato CSV, ma potrebbero essere supportati formati aggiuntivi nei prossimi aggiornamenti. 

Il diagramma seguente mostra una cartella CDM di esempio, creata da un flusso di dati di Power BI, che contiene tre entità:

![flussi di dati in archiviazione di Azure](media/service-dataflows-azure-data-lake-integration/dataflows-azure-integration_01.jpg)

Il file Model.json o il file di metadati nell'immagine precedente fornisce i puntatori ai file di dati di entità in tutta la cartella CDM.

## <a name="power-bi-organizes-cdm-folders-in-the-data-lake"></a>Power BI organizza le cartelle CDM nel data lake

Con i flussi di dati di Power BI e l'integrazione con ADLS Gen2, Power BI può produrre dati in un data lake. Come produttore di dati, Power BI deve creare una cartella CDM per ogni flusso di dati che contiene il file Model.json e i relativi file di dati associati. Power BI archivia i dati in modo isolato dagli altri produttori di dati nel data lake usando *file system*. Altre informazioni sui file system e lo spazio dei nomi gerarchico di Azure Data Lake Storage Gen2 sono disponibili [in questo articolo](https://docs.microsoft.com/azure/storage/data-lake-storage/namespace).

Power BI usa le sottocartelle per risolvere eventuali ambiguità e per garantire un'organizzazione dei dati migliore per la presentazione nel **servizio Power BI**. La struttura e la denominazione delle cartelle rappresentano aree di lavoro (cartelle) e flussi di dati (cartelle CDM). Il diagramma seguente mostra come può essere strutturato un data lake condiviso da Power BI e altri produttori di dati. Ogni servizio, in questo caso di Dynamics 365, Dynamics 365 for Finance and Operations e Power BI, crea e gestisce un file system proprio. A seconda dell'esperienza in ogni servizio, vengono create sottocartelle per organizzare al meglio le cartelle CDM all'interno del file system. 

![flussi di dati da vari servizi in archiviazione di Azure](media/service-dataflows-azure-data-lake-integration/dataflows-azure-integration_02.jpg)

## <a name="power-bi-protects-data-in-the-data-lake"></a>Power BI protegge i dati nel data lake

Power BI usa le funzionalità dei token *Active Directory OAuth Bearer* e degli *ACL POSIX* rese disponibili da Azure Data Lake Storage Gen2. Queste funzionalità consentono di definire l'ambito di accesso di Power BI al file system gestito nel data lake, nonché di definire l'ambito di accesso degli utenti solo ai flussi di dati o alle cartelle CDM da loro creati. 

Per creare e gestire le cartelle CDM all'interno del file system di Power BI, sono necessarie autorizzazioni di lettura, scrittura ed esecuzione per il file system. Ogni flusso di dati creato in Power BI viene archiviato nella relativa cartella CDM e al proprietario del flusso di dati viene concesso l'accesso di sola lettura alla cartella CDM e al relativo contenuto. Questo approccio consente di proteggere l'integrità dei dati generati da Power BI e offre agli amministratori la possibilità di monitorare gli utenti che accedono alla cartella CDM mediante i log di controllo. 

### <a name="authorizing-users-or-services-for-cdm-folders"></a>Autorizzazioni per utenti o servizi per le cartelle CDM

La condivisione delle cartelle CDM con i consumer di dati, ad esempio utenti o servizi che devono leggere i dati, viene semplificata tramite token di Active Directory OAuth Bearer e ACL POSIX. In questo modo, gli amministratori hanno la possibilità di monitorare gli accessi alle cartelle CDM. L'unica azione richiesta è la concessione dell'accesso a un oggetto di Active Directory a scelta (ad esempio, un gruppo di utenti o un servizio) per la cartella CDM. È consigliabile che tutti gli accessi alla cartella CDM, per qualsiasi identità diversa dal produttore dei dati, siano di sola lettura. In questo modo è possibile proteggere l'integrità dei dati generati dal producer.

Per aggiungere cartelle CDM a Power BI, l'utente che aggiunge la cartella CDM deve avere ACL di accesso in *lettura* sia pe la cartella CDM stessa che per qualsiasi file o cartella in essa inclusi. Sono inoltre richiesti ACL di accesso in *esecuzione* per la cartella CDM stessa e le eventuali sottocartelle. Per altre informazioni, è consigliabile leggere sia l'articolo [Elenchi di controllo di accesso per file e directory](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-access-control#access-control-lists-on-files-and-directories) che l'articolo [Procedure consigliate per l'uso di Azure Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-best-practices).


### <a name="alternative-forms-of-authorization"></a>Forme alternative di autorizzazione

Persone o servizi all'esterno di Power BI possono anche sfruttare forme alternative di autorizzazione. Queste alternative consentono ai titolari della chiave di accedere a *tutte* le risorse nell'account, l'accesso completo a tutte le risorse nel lake e non possano avere un ambito limitato a file system o cartelle CDM. Possono essere semplici modi per concedere l'accesso, ma limitano la possibilità di condividere risorse specifiche nel data lake e non offrono informazioni di controllo agli utenti per gli accessi allo spazio di archiviazione. Per dettagli completi sugli schemi di autorizzazione disponibili, vedere [Access control in Azure Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-access-control
) (Controllo di accesso in Azure Data Lake Storage Gen2).


## <a name="next-steps"></a>Passaggi successivi

In questo articolo è stata presentata una panoramica dell'integrazione di flussi di dati di Power BI, cartelle CDM e Azure Data Lake Storage Gen2. Per altre informazioni, vedere gli articoli seguenti:

Per altre informazioni su flussi di dati, CDM e Azure Data Lake Storage Gen2, vedere gli articoli seguenti:

* [Configurare le impostazioni del flusso di dati dell'area di lavoro (anteprima)](service-dataflows-configure-workspace-storage-settings.md)
* [Aggiungere una cartella CDM a Power BI come flusso di dati (anteprima)](service-dataflows-add-cdm-folder.md)
* [Connettere Azure Data Lake Storage Gen2 per l'archiviazione dei flussi di dati (anteprima)](service-dataflows-connect-azure-data-lake-storage-gen2.md)

Per informazioni sui flussi di dati in generale, vedere questi articoli:

* [Creare e usare flussi di dati in Power BI](service-dataflows-create-use.md)
* [Uso delle entità calcolate in Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Uso di flussi di dati con origini dati locali](service-dataflows-on-premises-gateways.md)
* [Risorse per sviluppatori per i flussi di dati Power BI](service-dataflows-developer-resources.md)

Per altre informazioni sull'archiviazione di Azure, è possibile leggere questi articoli:
* [Guida alla sicurezza di Archiviazione di Azure](https://docs.microsoft.com/azure/storage/common/storage-security-guide)
* [Esempi ed esercitazioni di GitHub per Servizi dati di Azure](https://aka.ms/cdmadstutorial)

Per altre informazioni sul modello CDM (Common Data Model), è possibile leggere l'articolo di panoramica:
* [Panoramica del modello CDM (Common Data Model)](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [Cartelle CDM](https://go.microsoft.com/fwlink/?linkid=2045304)
* [Definizione del file del modello CDM](https://go.microsoft.com/fwlink/?linkid=2045521)

È inoltre sempre possibile provare a [porre domande alla Community di Power BI](https://community.powerbi.com/).
