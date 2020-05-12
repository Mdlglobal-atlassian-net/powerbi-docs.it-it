---
title: Che cosa sono le app modello di Power BI?
description: Questo articolo è una panoramica del programma delle app modello di Power BI. Informazioni su come compilare app di Power BI con un uso minimo o nullo di codice e su come distribuire le app a qualsiasi cliente Power BI.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 05/04/2020
ms.author: painbar
ms.openlocfilehash: 466e7cb842244104b004c4f65f82dafe13dc9725
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82781318"
---
# <a name="what-are-power-bi-template-apps"></a>Che cosa sono le app modello di Power BI?

Le nuove *app modello* di Power BI consentono ai partner Power BI di creare app Power BI con un uso minimo o nullo di codice e quindi di distribuire le app a qualsiasi cliente Power BI.  Questo articolo è una panoramica del programma delle app modello di Power BI.

I partner Power BI possono creare set di contenuti predefiniti per i clienti e pubblicarli personalmente.  

È possibile compilare app modello che consentono ai clienti di connettersi e creare un'istanza con i propri account. Gli esperti di dominio possono sbloccare i dati in modo da renderli facilmente utilizzabili dagli utenti aziendali.  

Si inviano le app modello al Centro per i partner. Le app diventano quindi disponibili pubblicamente nel [marketplace di app per Power BI](https://app.powerbi.com/getdata/services) e in [Microsoft AppSource](https://appsource.microsoft.com/?product=power-bi). Di seguito viene riportata una presentazione generale dell'esperienza di creazione di un'app modello pubblica.

## <a name="power-bi-apps-marketplace"></a>Marketplace di app per Power BI

Le app modello in Power BI consentono agli utenti Power BI Pro o Power BI Premium di ottenere informazioni immediate attraverso dashboard e report predefiniti che possono essere connessi a origini dati attive. Molte app per Power BI sono già disponibili nel [marketplace di app per Power BI](https://app.powerbi.com/getdata/services).

|  |
|     :---:      |
| [![App Web Microsoft Project](./media/service-template-apps-overview/project-web.png)](https://app.powerbi.com/groups/me/getapps/services/pbi_msprojectonline.pbi-microsoftprojectwebapp) [![App Web Microsoft 365 Usage Analytics](./media/service-template-apps-overview/microsoft365-usage-analytics.png)](https://app.powerbi.com/groups/me/getapps/services/cia_microsoft365.microsoft-365-usage-analytics) [![App Web Dynamic 365 Business Central - Sales](./media/service-template-apps-overview/dynamics-sales.png)](https://app.powerbi.com/groups/me/getapps/services/microsoftdynsmb.businesscentral_sales) [![App Web Microsoft Forms Pro Customer Satisfaction](./media/service-template-apps-overview/forms-pro.png)](https://app.powerbi.com/groups/me/getapps/services/msfp.formsprocustomersatisfaction) |
|  |

## <a name="process"></a>Process
Il processo generale di sviluppo e invio di un'app modello comporta diverse fasi. Alcune fasi possono includere più attività allo stesso tempo.


| Fase | Power BI Desktop |  |Servizio Power BI  |  |Centro per i partner  |
|---|--------|--|---------|---------|---------|
| **1** | Compilare un modello di dati e un report in un file con estensione pbix |  | Creare un'area di lavoro. Importare un file con estensione pbix. Creare un dashboard complementare  |  | Registrarsi come partner |
| **2** |  |  | Creare un pacchetto di test ed eseguire la convalida interna        |  | |
| **3** | |  | Alzare al livello di pre-produzione il pacchetto di test per la convalida al di fuori del tenant di Power BI e inviarlo ad AppSource  |  | Con il pacchetto di pre-produzione, creare un'offerta di app modello di Power BI e avviare il processo di convalida |
| **4** | |  | Alzare al livello di produzione il pacchetto di pre-produzione |  | Passare in produzione |

## <a name="before-you-begin"></a>Prima di iniziare

Per creare l'app modello, sono necessarie autorizzazioni specifiche. Per informazioni dettagliate, vedere Impostazioni app modello nel portale di amministrazione di Power BI. 

Per pubblicare un'app modello nel servizio Power BI e in AppSource, è necessario soddisfare i requisiti per [diventare un editore del Centro per i partner](https://docs.microsoft.com/azure/marketplace/become-publisher).
 
## <a name="high-level-steps"></a>Procedure generali

Ecco i passaggi di alto livello. 

1. [Rivedere i requisiti](#requirements) per assicurarsi di soddisfarli. 

2. Creare un report in Power BI Desktop. Usare parametri, in modo che sia possibile salvare il report come file utilizzabile anche da altri utenti. 

3. Creare un'area di lavoro per l'app modello nel proprio tenant nel servizio Power BI (app.powerbi.com). 

4. Importare il file con estensione pbix e aggiungere contenuto, ad esempio un dashboard nell'app. 

5. Creare un pacchetto di test per testare l'app modello all'interno dell'organizzazione. 

6. Alzare l'app di test al livello di pre-produzione per inviarla alla convalida in AppSource e testarla al di fuori del proprio tenant. 

7. Inviare il contenuto al [Centro per i partner](https://docs.microsoft.com/azure/marketplace/partner-center-portal/create-power-bi-app-offer) per la pubblicazione. 

8. Pubblicare l'offerta in AppSource e passare l'app in produzione in Power BI.

9. È ora possibile iniziare a sviluppare la versione successiva nella stessa area di lavoro, in fase di pre-produzione. 

## <a name="requirements"></a>Requisiti

Per creare l'app modello, sono necessarie autorizzazioni specifiche. Per informazioni dettagliate, vedere [Impostazioni app modello nel portale di amministrazione](service-admin-portal.md#template-apps-settings) di Power BI.

Per pubblicare un'app modello nel servizio Power BI e in AppSource, è necessario soddisfare i requisiti per [diventare un editore del Centro per i partner](https://docs.microsoft.com/azure/marketplace/become-publisher).
 > [!NOTE] 
 > Gli invii di app modello vengono gestiti nel [Centro per i partner](https://docs.microsoft.com/azure/marketplace/partner-center-portal/create-power-bi-app-offer). Usare lo stesso account di registrazione del Centro per sviluppatori Microsoft per l'accesso. È necessario un solo account Microsoft per le offerte in AppSource. Gli account non devono essere specifici per singoli servizi o offerte.

## <a name="tips"></a>Suggerimenti 

- Assicurarsi che l'app includa dati di esempio per consentire a tutti gli utenti di iniziare nel più breve tempo possibile. 
- Esaminare attentamente l'applicazione installandola nel proprio tenant e in un tenant secondario. Assicurarsi che i clienti possano visualizzare solo ciò che si vuole che visualizzino. 
- Usare AppSource come store online per ospitare l'applicazione. In questo modo può essere individuata da tutti gli utenti che usano Power BI. 
- Valutare la possibilità di offrire più app modello per scenari univoci separati. 
- Abilitare la personalizzazione dei dati, ad esempio supportare la personalizzazione delle connessioni e la configurazione dei parametri tramite il programma di installazione.

Per altri suggerimenti, vedere [Suggerimenti per la creazione di app modello in Power BI](service-template-apps-tips.md).

## <a name="known-limitations"></a>Limitazioni note

| Funzionalità | Limitazione nota |
|---------|---------|
|Contenuto:  Set di dati   | È necessario che sia presente un solo set di dati. Sono consentiti solo i set di dati creati in Power BI Desktop (file con estensione pbix). <br>Non supportato: Set di dati di altre app modello, set di dati di più aree di lavoro, report impaginati (file con estensione rdl), cartelle di lavoro di Excel |
|Contenuto: Dashboard | Non sono consentiti riquadri in tempo reale (in altre parole, non è disponibile il supporto per set di dati di push o di streaming) |
|Contenuto: Flussi di dati | Non supportato: Flussi di dati |
|Contenuti dei file | Sono supportati solo i file PBIX. <br>Non supportati: file con estensione rdl (report impaginati), cartelle di lavoro di Excel   |
| Origini dati | Le origini dati supportate per l'aggiornamento dati pianificato nel cloud sono consentite. <br>Non supportati: <li> DirectQuery</li><li>Connessioni dinamiche (non Azure AD)</li> <li>Origini dati locali (i gateway personali e aziendali non sono supportati)</li> <li>Tempo reale (nessun supporto per set di dati di push)</li> <li>Modelli compositi</li></ul> |
| Set di dati: di più aree di lavoro | Non sono consentiti set di dati di più aree di lavoro  |
| Parametri di query | Non supportato: Parametri di tipo "Any" o "Binary" bloccano l'operazione di aggiornamento per il set di dati |
| Oggetti visivi di Power BI | Sono supportati solo gli oggetti visivi di Power BI disponibili pubblicamente. Gli [oggetti visivi di Power BI dell'organizzazione](developer/visuals/power-bi-custom-visuals-organization.md) non sono supportati |
| Cloud sovrani | Le app modello non sono disponibili nei cloud sovrani |

## <a name="support"></a>Supporto
Per il supporto durante lo sviluppo, usare [https://powerbi.microsoft.com/support](https://powerbi.microsoft.com/support). Questo sito viene monitorato e gestito attivamente. Le richieste dei clienti vengono indirizzate rapidamente al team appropriato.

## <a name="next-steps"></a>Passaggi successivi

[Creare un'app modello](service-template-apps-create.md)
