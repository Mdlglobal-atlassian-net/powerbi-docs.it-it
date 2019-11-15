---
title: Che cosa sono le app modello di Power BI?
description: Questo articolo è una panoramica del programma delle app modello di Power BI. Informazioni su come compilare app di Power BI con un uso minimo o nullo di codice e su come distribuire le app a qualsiasi cliente Power BI.
author: teddybercovitz
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: tebercov
ms.openlocfilehash: 4b4e32f787d2d262d604ff0745f8c028e9fff949
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73871331"
---
# <a name="what-are-power-bi-template-apps"></a>Che cosa sono le app modello di Power BI?

Le nuove *app modello* di Power BI consentono ai partner Power BI di creare app Power BI con un uso minimo o nullo di codice e quindi di distribuire le app a qualsiasi cliente Power BI.  Questo articolo è una panoramica del programma delle app modello di Power BI.

Le app modello sostituiscono gli attuali pacchetti di contenuto dei servizi. I partner Power BI sono in grado di creare set di contenuti predefiniti per i clienti e di pubblicarli personalmente.  

È possibile compilare app modello che consentono ai clienti di connettersi e creare un'istanza con i propri account. In qualità di esperti di dominio, possono sbloccare i dati in modo da renderli facilmente utilizzabili dai loro utenti aziendali.  

Le app modello vengono inviate al portale Cloud Partner. e diventano quindi disponibili pubblicamente nella raccolta di app di Power BI (app.powerbi.com/getdata/services) e in Microsoft AppSource (appsource.microsoft.com). Di seguito viene riportata una presentazione generale dell'esperienza di creazione di un'app modello pubblica.  

## <a name="process"></a>Processo
Il processo generale di sviluppo e invio di un'app modello comporta diverse fasi. Alcune fasi possono includere più attività allo stesso tempo.


| Fase | Power BI Desktop |  |Servizio Power BI  |  |Portale Cloud Partner  |
|---|--------|--|---------|---------|---------|
| **1** | Compilare un modello di dati e un report in un file con estensione pbix |  | Creare un'area di lavoro. Importare un file con estensione pbix. Creare un dashboard complementare  |  | Registrarsi come partner |
| **2** |  |  | Creare un pacchetto di test ed eseguire la convalida interna        |  | |
| **3** | |  | Alzare al livello di pre-produzione il pacchetto di test per la convalida al di fuori del tenant di Power BI e inviarlo ad AppSource  |  | Con il pacchetto di pre-produzione, creare un'offerta di app modello di Power BI e avviare il processo di convalida |
| **4** | |  | Alzare al livello di produzione il pacchetto di pre-produzione |  | Procedere alla pubblicazione |

## <a name="before-you-begin"></a>Prima di iniziare

Per creare l'app modello, sono necessarie autorizzazioni specifiche. Per informazioni dettagliate, vedere Impostazioni app modello nel portale di amministrazione di Power BI. 

Per pubblicare un'app modello nel servizio Power BI e in AppSource, è necessario soddisfare i requisiti per [diventare un editore del Marketplace cloud](https://docs.microsoft.com/azure/marketplace/become-publisher).
 
## <a name="high-level-steps"></a>Passaggi di alto livello

Ecco i passaggi di alto livello. 

1. [Rivedere i requisiti](#requirements) per assicurarsi di soddisfarli. 

1. Creare un report in Power BI Desktop. Usare parametri, in modo che sia possibile salvare il report come file utilizzabile anche da altri utenti. 

1. Creare un'area di lavoro per l'app modello nel proprio tenant nel servizio Power BI (app.powerbi.com). 

1. Importare il file con estensione pbix e aggiungere contenuto, ad esempio un dashboard nell'app. 

1. Creare un pacchetto di test per testare l'app modello all'interno dell'organizzazione. 

1. Alzare l'app di test al livello di pre-produzione per inviarla alla convalida in AppSource e testarla al di fuori del proprio tenant. 

1. Inviare il contenuto alla piattaforma Cloud Partner per la pubblicazione. 

1. Pubblicare l'offerta in AppSource e passare l'app in produzione in Power BI.
2. È ora possibile iniziare a sviluppare la versione successiva nella stessa area di lavoro, in fase di pre-produzione. 

## <a name="requirements"></a>Requisiti

Per creare l'app modello, sono necessarie autorizzazioni specifiche. Per informazioni dettagliate, vedere [Impostazioni app modello nel portale di amministrazione](service-admin-portal.md#template-apps-settings) di Power BI. 

Per pubblicare un'app modello nel servizio Power BI e in AppSource, è necessario soddisfare i requisiti per [diventare un editore del Marketplace cloud](https://docs.microsoft.com/azure/marketplace/become-publisher).
 > [!NOTE] 
 > Gli invi di app modello vengono gestiti nel [portale Cloud Partner](https://cloudpartner.azure.com). Usare lo stesso account di registrazione del Centro per sviluppatori Microsoft per l'accesso. È necessario un solo account Microsoft per le offerte in AppSource. Gli account non devono essere specifici per singoli servizi o offerte.

## <a name="tips"></a>Suggerimenti 

- Assicurarsi che l'app includa dati di esempio per consentire a tutti gli utenti di iniziare nel più breve tempo possibile. 
- Esaminare attentamente l'applicazione installandola nel proprio tenant e in un tenant secondario. Assicurarsi che i clienti possano visualizzare solo ciò che si vuole che visualizzino. 
- Usare AppSource come store online per ospitare l'applicazione. In questo modo può essere individuata da tutti gli utenti che usano Power BI. 
- Valutare la possibilità di offrire più app modello per scenari univoci separati. 
- Abilitare la personalizzazione dei dati, ad esempio supportare la personalizzazione delle connessioni e la configurazione dei parametri tramite il programma di installazione.

Per altri suggerimenti, vedere [Suggerimenti per la creazione di app modello in Power BI](service-template-apps-tips.md).

## <a name="support"></a>Supporto
Per il supporto durante lo sviluppo, usare [https://powerbi.microsoft.com/support](https://powerbi.microsoft.com/support). Questo sito viene monitorato e gestito attivamente. Le richieste dei clienti vengono indirizzate rapidamente al team appropriato.

## <a name="next-steps"></a>Passaggi successivi

[Creare un'app modello](service-template-apps-create.md)
