---
title: Quando usare report impaginati in Power BI
description: Informazioni su quando usare report impaginati in Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/04/2020
ms.author: v-pemyer
ms.openlocfilehash: 049b6ac14c6d35d68815eac32520a4eaa654ad42
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/07/2020
ms.locfileid: "78920726"
---
# <a name="when-to-use-paginated-reports-in-power-bi"></a>Quando usare report impaginati in Power BI

Questo articolo è destinato agli autori di report che progettano report per Power BI. Fornisce suggerimenti utili per decidere quando sviluppare [report impaginati di Power BI](../paginated-reports/paginated-reports-report-builder-power-bi.md).

> [!NOTE]
> La pubblicazione di report impaginati di Power BI richiede una sottoscrizione di Power BI Premium. Il rendering dei report viene eseguito solo quando i report si trovano in un'area di lavoro in una capacità dedicata con il [carico di lavoro Report impaginati abilitato](../service-admin-premium-workloads.md#paginated-reports).

I report impaginati di Power BI sono ottimizzati per la **stampa** o la **generazione di PDF**. Consentono inoltre di creare layout molto precisi con formattazione avanzata. I report impaginati sono quindi ideali per la creazione di report operativi, ad esempio le fatture di vendita.

I report di Power BI sono invece ottimizzati per **esplorazione e interattività**. Consentono inoltre di presentare i dati usando una gamma completa di oggetti visivi ultramoderni. I report di Power BI sono quindi ideali per creare report analitici, in quanto consentono agli utenti di esplorare i dati e di individuare relazioni e modelli.

Si consiglia di usare un report impaginato di Power BI quando:

- Si sa che il report deve essere stampato o restituito come documento PDF.
- Può verificarsi l'espansione o il riversamento dei layout delle griglie dei dati. Si consideri che una tabella o una matrice in un report di Power BI non è in grado di ridimensionarsi dinamicamente per visualizzare tutti i dati, ma vengono invece fornite barre di scorrimento. In caso di stampa, tuttavia, non sarà possibile scorrere per visualizzare i dati non inclusi nella visualizzazione.
- Le funzionalità e le caratteristiche dei report impaginati di Power BI sono utili. Più avanti nell'articolo vengono descritti diversi scenari di questo tipo.

## <a name="legacy-reports"></a>Report legacy

Quando si hanno già report [RDL (Report Definition Language)](/sql/reporting-services/reports/report-definition-language-ssrs) di SQL Server Reporting Services (SSRS), è possibile scegliere di svilupparli di nuovo come [report di Power BI](../consumer/end-user-reports.md) oppure di eseguirne la migrazione in Power BI come report impaginati. Per altre informazioni, vedere [Eseguire la migrazione di report di SQL Server Reporting Services in Power BI](migrate-ssrs-reports-to-power-bi.md).

Dopo la pubblicazione in un'area di lavoro di Power BI, i report impaginati sono disponibili affiancati ai report di Power BI. È quindi possibile distribuirli facilmente usando le [app Power BI](../service-create-distribute-apps.md).

È possibile scegliere di sviluppare di nuovo i report SSRS, invece che eseguirne la migrazione. Ciò vale soprattutto per i report che hanno lo scopo di fornire esperienze analitiche. In questi casi, è probabile che i report di Power BI offrano esperienze utente migliori per i report.

## <a name="paginated-report-scenarios"></a>Scenari d'uso dei report impaginati

Ci sono molti scenari interessanti in cui è preferibile sviluppare un report impaginato di Power BI. In molti casi si tratta di funzionalità o caratteristiche non supportate dai report di Power BI.

- **Risultato pronto per la stampa**: i report impaginati sono ottimizzati per la stampa o la generazione di PDF. Quando necessario, le aree dati consentono l'espansione e il riversamento in più pagine in modo controllato. I layout dei report consentono di definire margini, nonché intestazioni e piè di pagina.
- **Formati di rendering**: Power BI consente di eseguire il rendering dei report impaginati in formati diversi. I formati includono Microsoft Excel, Microsoft Word, Microsoft PowerPoint, PDF, CSV, XML e MHTML. Il formato MHTML viene usato dal servizio Power BI per eseguire il rendering dei report. Gli utenti dei report possono decidere di eseguire l'esportazione nel formato appropriato.
- **Layout di precisione**: è possibile progettare layout molto precisi con formattazione avanzata, scegliendo le dimensioni e la posizione esatte, con precisione di frazioni di pollici o centimetri.
- **Layout dinamico**: è possibile produrre layout molto reattivi impostando numerose proprietà del report per l'uso di espressioni VB.NET. Le espressioni possono accedere a molte librerie .NET Framework principali.
- **Layout specifico del rendering**: è possibile usare le espressioni per modificare il layout del report in base al formato di rendering applicato. Ad esempio, è possibile progettare il report in modo da disabilitare l'opzione per attivare o disattivare la visibilità (per eseguire il drill-down e il drill-up) quando viene eseguito il rendering usando un formato non interattivo, come PDF.
- **Query native**: non è necessario sviluppare prima un set di dati di Power BI. È possibile creare query native (o usare stored procedure) per qualsiasi [origine dati supportata](../paginated-reports/paginated-reports-data-sources.md). Le query possono includere la parametrizzazione.
- **Progettazione query con interfaccia grafica**: Power BI Report Builder include strumenti di progettazione di query con interfaccia grafica che aiutano a scrivere e testare le query sui set di dati.
- **Set di dati statici**: è possibile definire un set di dati e immettere i dati direttamente nella definizione di report. Questa funzionalità è particolarmente utile per supportare una demo o per la distribuzione di un modello di verifica.
- **Integrazione dei dati**: è possibile combinare dati da origini dati diverse o con set di dati statici. A tale scopo, è possibile creare campi personalizzati usando espressioni VB.NET.
- **Parametrizzazione**: è possibile progettare esperienze di parametrizzazione con un elevato livello di personalizzazione, inclusi parametri basati sui dati e a cascata. È anche possibile definire i valori predefiniti dei parametri. Queste esperienze possono essere progettate per aiutare gli utenti dei report a impostare rapidamente i filtri appropriati. Non è inoltre necessario che i parametri filtrino i dati del report. Possono essere usati per supportare scenari di simulazione oppure stili o filtri dinamici.
- **Dati di tipo immagine**: il report consente di eseguire il rendering delle immagini quando sono archiviate in formato binario in un'origine dati.
- **Codice personalizzato**: è possibile sviluppare blocchi di codice di funzioni VB.NET nel report e usarli in qualsiasi espressione del report.
- **Sottoreport**: è possibile incorporare altri report impaginati di Power BI (inclusi nella stessa area di lavoro) nel report.
- **Griglie dati flessibili**: è possibile disporre di controllo con granularità fine sui layout delle griglie usando l'area dati Tablix. Sono supportati anche i layout complessi, inclusi i gruppi annidati e adiacenti. È inoltre possibile eseguire la configurazione in modo da ripetere le intestazioni quando la stampa occupa più pagine. È infine possibile incorporare un sottoreport o altre visualizzazioni, tra cui barre dei dati, grafici sparkline e indicatori.
- **Tipi di dati spaziali**: l'area dati della mappa può visualizzare [tipi di dati spaziali di SQL Server](/sql/relational-databases/spatial/spatial-data-sql-server). È quindi possibile usare i tipi di dati GEOGRAPHY e GEOMETRY per visualizzare punti, linee o poligoni. È anche possibile visualizzare i poligoni definiti nei file di forma ESRI.
- **Misuratori moderni**: è possibile usare misuratori radiali e lineari per visualizzare lo stato e i valori degli indicatori KPI. I misuratori possono anche essere incorporati nelle aree dati della griglia, ripetendoli all'interno dei gruppi.
- **Rendering HTML**: è possibile visualizzare il testo in formato RTF quando viene archiviato come HTML.
- **Stampa unione**: è possibile usare caselle di testo segnaposto per inserire i valori dei dati nel testo. In questo modo, si genera un report di tipo stampa unione.
- **Funzionalità di interattività**: le funzionalità interattive includono attivazione/disattivazione della visibilità (per eseguire il drill-down e il drill-up), collegamenti, ordinamento interattivo e descrizioni comandi. È anche possibile aggiungere collegamenti che consentono il drill-through nei report di Power BI o in altri report impaginati di Power BI. I collegamenti possono rimandare anche a un'altra posizione all'interno dello stesso report.
- **Sottoscrizioni**: Power BI consente di recapitare report impaginati in base a una pianificazione come messaggi di posta elettronica con report allegati in qualsiasi formato supportato.
- **Layout per utente**: è possibile creare layout di report reattivi in base all'utente autenticato che apre il report. È possibile progettare il report per filtrare i dati in modo diverso, nascondere aree dati o visualizzazioni, applicare formati diversi o impostare valori predefiniti per i parametri specifici dell'utente.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni correlate a questo articolo, vedere le risorse seguenti:

- [Che cosa sono i report impaginati in Power BI Premium?](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- [Eseguire la migrazione di report di SQL Server Reporting Services in Power BI](migrate-ssrs-reports-to-power-bi.md)
- Domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
- Se si hanno suggerimenti, [Contribuire con idee per migliorare Power BI](https://ideas.powerbi.com/)
