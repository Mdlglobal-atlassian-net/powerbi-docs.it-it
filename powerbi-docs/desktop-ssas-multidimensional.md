---
title: Dati multidimensionali di Analysis Services in Power BI Desktop
description: Dati multidimensionali di SQL Server Analysis Services (SSAS) in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: eac1134ff12025d05cd59e86b7538cde58e3a2ee
ms.sourcegitcommit: 08f65ea314b547b41b51afef6876e56182190266
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2020
ms.locfileid: "76753157"
---
# <a name="connect-to-ssas-multidimensional-models-in-power-bi-desktop"></a>Connettersi ai modelli multidimensionali SSAS in Power BI Desktop

Con Power BI Desktop è possibile accedere ai *modelli multidimensionali di SSAS*, comunemente noti come *MD SSAS*.

Per connettersi a un database MD SSAS, selezionare **Recupera dati**, scegliere **Database** > **Database di SQL Server Analysis Services** e quindi selezionare **Connetti**:

![Database SQL Server Analysis Services (SSAS), finestra di dialogo Recupera dati, Power BI Desktop](media/desktop-ssas-multidimensional/ssas-multidimensional-2.png)

Il servizio Power BI e Power BI Desktop supportano entrambi i modelli multidimensionali SSAS in modalità di connessione dinamica. È possibile pubblicare e caricare i report che usano i **modelli multidimensionali SSAS** in modalità dinamica nel servizio Power BI.

## <a name="capabilities-and-features-of-ssas-md"></a>Caratteristiche e funzionalità di MD SSAS

Nelle sezioni seguenti sono descritte le caratteristiche e le funzionalità di Power BI e delle connessioni SSAS MD.

### <a name="tabular-metadata-of-multidimensional-models"></a>Metadati tabulari dei modelli multidimensionali

Nella tabella seguente viene illustrata la corrispondenza tra gli oggetti multidimensionali e i metadati tabulari restituiti a Power BI Desktop. Power BI esegue query nel modello per ottenere metadati tabulari. Quando si crea una visualizzazione (ad esempio una tabella, una matrice, un grafico o un filtro dei dati), in base ai metadati restituiti, Power BI Desktop esegue query DAX appropriate in SSAS.

| Oggetto BISM-multidimensionale | Metadati tabulari |
| --- | --- |
| Cube |Modello |
| Dimensione cubo |Tabella |
| Attributi dimensione (chiavi) nome |Colonne |
| Gruppo di misure |Tabella |
| Measure |Measure |
| Misure senza gruppo di misure associato |In una tabella denominata *Misure* |
| Relazione gruppo di misure -> dimensione cubo |Relazione |
| Punto di vista |Prospettiva |
| KPI |KPI |
| Gerarchie utente/padre-figlio |Gerarchie |

### <a name="measures-measure-groups-and-kpis"></a>Misure, gruppi di misure e indicatori KPI

I gruppi di misure in un cubo multidimensionale vengono esposti come tabelle nel riquadro **Campi** con accanto un sigma (∑). Le misure calcolate senza un gruppo di misure associato vengono raggruppate in una tabella speciale denominata *Misure* nei metadati tabulari.

Per semplificare i modelli complessi, in un modello multidimensionale è possibile definire l'inserimento di un set di misure o di indicatori KPI di un cubo all'interno di una *cartella di visualizzazione*. Power BI riconosce le cartelle di visualizzazione presenti nei metadati tabulari e mostra le misure e gli indicatori KPI all'interno di tali cartelle. Gli indicatori KPI nei database multidimensionali supportano *Valore*, *Obiettivo*, *Icona stato* e *Icona tendenza*.

### <a name="dimension-attribute-type"></a>Tipo di attributo dimensione

I modelli multidimensionali supportano anche l'associazione degli attributi di dimensione a tipi di attributo di dimensione specifici. Ad esempio nei metadati tabulari viene esposta una dimensione **Geografia** con attributi *Città*, *Provincia*, *Paese* e *Codice postale* ai quali sono associati tipi di elementi geografici appropriati. Power BI riconosce i metadati, consentendo di creare viste mappa. Queste associazioni sono riconoscibili in Power BI dall'icona della *mappa* accanto all'elemento nel riquadro **Campo**.

Power BI può anche visualizzare le immagini di cui viene fornito un campo che contiene gli URL (Uniform Resource Locator) corrispondenti. È possibile specificare questi campi come tipi *ImageURL* in SQL Server Data Tools (o in Power BI). Le informazioni sui tipi vengono quindi fornite a Power BI nei metadati tabulari. Power BI può quindi recuperare tali immagini dall'URL e visualizzarle all'interno di oggetti visivi.

### <a name="parent-child-hierarchies"></a>Gerarchie padre-figlio

I modelli multidimensionali supportano le gerarchie padre-figlio, che vengono presentate sotto forma di *gerarchia* nei metadati tabulari, all'interno dei quali ogni livello della gerarchia padre-figlio viene esposto come colonna nascosta. L'attributo chiave della dimensione padre-figlio non viene esposto nei metadati tabulari.

### <a name="dimension-calculated-members"></a>Membri calcolati della dimensione

I modelli multidimensionali supportano la creazione di vari tipi di *membri calcolati*. I due tipi più comuni di membri calcolati sono:

* Membri calcolati in gerarchie di attributi non di pari livello di *Tutti*
* Membri calcolati in gerarchie utente

I modelli multidimensionali espongono i *membri calcolati in gerarchie di attributi* come valori di una colonna. Se si espongono membri calcolati di questo tipo, sono disponibili alcune opzioni e alcuni vincoli aggiuntivi:

* Tra gli attributi della dimensione può essere presente l'attributo facoltativo *UnknownMember*.

* Un attributo contenente membri calcolati può essere l'attributo chiave della dimensione solo se è l'unico attributo della dimensione stessa.

* Un attributo contenente membri calcolati non può essere un attributo padre-figlio.

I membri calcolati delle gerarchie utente non vengono esposti in Power BI. È invece possibile connettersi a un cubo contenente membri calcolati nelle gerarchie utente. Non sarà tuttavia possibile visualizzare i membri calcolati se non soddisfano i vincoli indicati nell'elenco puntato precedente.

### <a name="security"></a>Security

I modelli multidimensionali supportano la sicurezza a livello di dimensione e di cella per mezzo di *ruoli*. Quando ci si connette a un cubo con Power BI, vengono eseguite l'autenticazione e la valutazione per l'assegnazione all'utente delle autorizzazioni appropriate. Se a un utente si applica la *sicurezza delle dimensioni*, i membri delle dimensioni interessate non sono visibili dall'utente in Power BI. Quando tuttavia per un utente è definito un tipo di autorizzazione *sicurezza delle celle* che applica restrizioni ad alcune celle, l'utente non può connettersi al cubo tramite Power BI.

## <a name="considerations-and-limitations"></a>Considerazioni e limiti

Esistono alcune limitazioni all'uso di MD SSAS:

* Solo le edizioni Enterprise e BI di SQL Server 2014 supportano le connessioni dinamiche. Per l'edizione standard di SQL Server, è necessario SQL Server 2016 o versione successiva per le connessioni dinamiche.

* *Azioni* e *set denominati* non sono esposti a Power BI. Per creare oggetti visivi e report, è comunque possibile connettersi a cubi che contengono anche azioni o set denominati.

* Quando Power BI Visualizza i metadati per un modello SSAS, talvolta non è possibile recuperare i dati dal modello. Questo scenario può verificarsi se è stata installata la versione a 32 bit del provider MSOLAP, ma non la versione a 64 bit. Il problema viene in genere risolto con l'installazione della versione a 64 bit.

* Non è possibile creare misure *a livello di report* quando si crea un report con connessione dinamica a un modello multidimensionale di SSAS. Le uniche misure disponibili sono quelle definite nel modello MD.

## <a name="supported-features-of-ssas-md-in-power-bi-desktop"></a>Funzionalità supportate di SSAS MD in Power BI Desktop

L'utilizzo degli elementi seguenti è supportato in questa versione di SSAS MD. Per altre informazioni su queste funzionalità, vedere [Informazioni su Power View per modelli multidimensionali](/sql/analysis-services/multidimensional-models/understanding-power-view-for-multidimensional-models?view=sql-server-2014).

* Membri predefiniti
* Attributi dimensione
* Tipi di attributi della dimensione
* Membri calcolati della dimensione, che:
  * devono essere un membro reale singolo quando la dimensione presenta più di un attributo.
  * non possono essere l'attributo chiave della dimensione a meno che non siano l'unico attributo.
  * non possono essere un attributo padre-figlio.
* Sicurezza delle dimensioni
* Cartelle di visualizzazione
* Gerarchie
* ImageUrl
* KPI
* Tendenze degli indicatori KPI
* Misure (con o senza gruppi di misure)
* Misure di tipo Variant

## <a name="troubleshooting"></a>Risoluzione dei problemi

L'elenco seguente descrive tutti i problemi noti relativi alla connessione a SQL Server Analysis Services (SSAS).

* **Errore: Non è stato possibile caricare lo schema del modello** - Questo errore si verifica in genere quando l'utente che si connette ad Analysis Services non ha accesso al database o al cubo.
