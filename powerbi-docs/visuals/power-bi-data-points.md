---
title: Set di dati di grandi dimensioni, limiti dei punti dati e strategie per i dati
description: Limiti dei dati per gli oggetti visivi e strategie per la riduzione dei dati
author: mihart
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/02/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: b45d0fb20dbb9a697e6d079a6b28c0fc86290627
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73881068"
---
# <a name="data-point-limits-and-strategies-by-visual-type"></a>Limiti dei dati per gli oggetti visivi e strategie in base al tipo di oggetto visivo

Durante il rendering di un oggetto visivo in Power BI, la visualizzazione deve essere veloce e accurata. Ciò richiede la configurazione di algoritmi sottostanti per ogni tipo di oggetto visivo. Gli oggetti visivi in Power BI devono essere sufficientemente flessibili da gestire diverse dimensioni dei set di dati. Alcuni set di dati includono solo pochi punti dati, mentre altri set di dati ne includono svariati petabyte. Questo articolo illustra le strategie usate da Power BI per il rendering delle visualizzazioni.

## <a name="data-reduction-strategies"></a>Strategie di riduzione dei dati
Ogni oggetto visivo usa una o più *strategie di riduzione dei dati* per gestire i volumi dei dati analizzati potenzialmente di grandi dimensioni. Anche una tabella semplice adotta una strategia per evitare di caricare l'intero set di dati nel client.  La strategia di riduzione usata varia in base al tipo di oggetto visivo. Ogni oggetto visivo seleziona una delle *strategie di riduzione dei dati* supportate come parte della generazione della richiesta di dati inviata al server. 

Ogni oggetto visivo controlla i parametri di tali strategie per influenzare la quantità complessiva di dati.   

## <a name="strategies"></a>Strategie
Per ogni strategia esistono impostazioni predefinite in base alla forma e al tipo di dati visualizzati. Le impostazioni predefinite possono comunque essere sostituite nel riquadro di formattazione di Power BI, per offrire l'esperienza utente appropriata. 

* **Windowing dei dati** (segmentazione): consentire agli utenti di scorrere tra i dati in un oggetto visivo caricando progressivamente frammenti del set di dati complessivo.
* **PrimiN**: visualizzare solo i primi N elementi
* **Campione semplice**: visualizzare il primo elemento, l'ultimo elemento e N elementi intermedi con distribuzione uniforme.
* **UltimiN**: visualizzare solo gli ultimi N elementi.  Utile per il monitoraggio di dati aggiornati di frequente.
* **Campionamento ad alta densità**: un algoritmo di campionamento migliorato che rispetta meglio gli outlier e/o la forma di una curva.
    * **Campionamento della linea di creazione dei contenitori**: campionare i punti dati in base agli outlier nei contenitori in un asse
    * **Campionamento di punti sovrapposti**: campionare punti dati in base ai valori sovrapposti per mantenere gli outlier

## <a name="statistics"></a>Statistiche
Alcuni modelli possono offrire dati statistici sul numero di valori per determinate colonne. Quando tali informazioni sono presenti, vengono sfruttate per offrire un bilanciamento migliorato tra più gerarchie, se un oggetto visivo non sostituisce in modo esplicito il conteggio dei valori per una strategia.

Per altre informazioni, vedere [Novità di Analysis Services](https://docs.microsoft.com/sql/analysis-services/what-s-new-in-analysis-services?view=sql-server-2017)

## <a name="dynamic-limits"></a>Limiti dinamici
Oltre alle strategie di cui sopra, gli oggetti visivi con due gerarchie di colonne di raggruppamento (asse e legenda o categoria e serie) usano una strategia aggiuntiva denominata *limiti dinamici*.  I limiti dinamici sono progettati per un miglior bilanciamento dei punti dati 

e offrono una selezione di punti migliori per i dati di tipo sparse rispetto ai limiti statici. Ad esempio, un oggetto visivo può essere configurato per selezionare 100 categorie e 10 serie con un totale di 1000 punti, ma i dati effettivi includono 50 categorie e 20 serie.  In fase di esecuzione di query, i limiti dinamici selezionano tutte le 20 serie per riempire i 1000 punti richiesti.

I limiti dinamici vengono applicati automaticamente quando il server è in grado, come indicato di seguito:

* In Power BI Desktop con SSAS 2016 locale o versioni successive [sfruttando le funzionalità SuperDax del server](https://blogs.msdn.microsoft.com/analysisservices/2015/09/02/whats-new-in-microsoft-sql-server-analysis-services-tabular-models-in-sql-server-2016-ctp-2-3/)

* In Power BI Desktop e nel servizio Power BI quando si usa un modello importato, DirectQuery, una connessione dinamica al servizio o una connessione dinamica ad AS PaaS. 

* Nel servizio Power BI, quando ci si connette tramite un gateway da sito locale a SSAS locale, non è possibile usare i limiti dinamici. Il gateway locale non supporta completamente la strategia basata sui limiti dinamici che restituisce una struttura diversa dei set di risultati da SSAS locale.  

## <a name="strategies-and-data-point-limits-by-visual-type"></a>Strategie e limiti dei punti dati in base al tipo di oggetto visivo

### <a name="area-chart"></a>Grafico ad aree
Vedere [Funzionamento del nuovo algoritmo di campionamento di linee](../desktop-high-density-sampling.md#how-the-new-line-sampling-algorithm-works)

### <a name="barcolumn-chart"></a>Grafico a barre/istogramma
- In modalità per categorie
    - Categorie: virtualizzazione con finestra di 500 righe alla volta
    - Serie: prime 60
    - In modalità scalare (potrebbero essere usati limiti dinamici)
        - Max punti: 10.000
        - Categorie: campione di 500 valori
        - Serie: primi 20 valori

### <a name="card-multirow"></a>Scheda (con più righe) 
- Valori: virtualizzazione con finestra di 200 righe alla volta

### <a name="combo-chart"></a>Grafico combinato
 Usa le stesse strategie dell'istogramma. Si noti che la linea nel **grafico combinato** non usa l'algoritmo ad alta densità usato dal **grafico a linee**.

### <a name="custom-visuals"></a>Oggetti visivi personalizzati
Si può arrivare fino a 30.000, ma sta agli autori dell'oggetto visivo indicare quali strategie usare

### <a name="doughnut"></a>Anello
- Max punti: 3.500
- Gruppo: primi 500
- Dettagli: primi 20

### <a name="filled-map-choropleth"></a>Mappa colorata coropletica 
La mappa colorata può usare statistiche o limiti dinamici. Power BI tenta di usare la riduzione nell'ordine seguente: limiti dinamici, statistiche e infine configurazione. 
- Max punti: 10000
- Categorie: primi 500
- Serie (se sono presenti sia X che Y): primi 20

### <a name="funnel"></a>Grafico a imbuto
- Max punti: 3.500
- Categorie: primi 3.500

### <a name="kpi"></a>Indicatore KPI
- Asse tendenza
- Ultimi 3.500

### <a name="line-chart"></a>Grafico a linee
Vedere [Funzionamento del nuovo algoritmo di campionamento di linee](../desktop-high-density-sampling.md#how-the-new-line-sampling-algorithm-works)

### <a name="line-chart-high-density"></a>Grafico a linee, alta densità
Vedere [Campionamento ad alta densità](../desktop-high-density-sampling.md)

### <a name="map"></a>Mappa 
- Max punti: 3.500

A seconda della configurazione, una mappa può avere:
- Posizione: primi 3.500
- Posizione, dimensioni: primi 3.500
- Aggregazioni di posizione, latitudine e longitudine (+/-dimensioni): primi 3.500
- Latitudine, longitudine: vedere [Campionamento ad alta densità nei grafici a dispersione](desktop-high-density-scatter-charts.md)
- Latitudine, longitudine, dimensioni: primi 3.500
- Legenda, latitudine, longitudine: vedere [Campionamento ad alta densità nei grafici a dispersione](desktop-high-density-scatter-charts.md)
- Legenda, latitudine, longitudine, dimensioni: prime 233 legende, primi 15 valori di latitudine e longitudine (potrebbero essere usati limiti dinamici o statistiche)
- Posizione, legenda, longitudine e latitudine come aggregazioni (+/-dimensioni): prime 233 posizioni, prime 15 legende (potrebbero essere usati limiti dinamici o statistiche)

### <a name="matrix"></a>Matrice
- Righe: virtualizzazione con finestra di 500 righe alla volta
- Colonne: prime 100 colonne di raggruppamento 
- Valori: i valori multipli non contano per la riduzione dei dati

### <a name="radial-gauge"></a>Misuratore radiale
Nessuna strategia di riduzione

### <a name="slicer"></a>Filtro dei dati
- Valori: virtualizzazione con finestra di 200 righe alla volta

### <a name="scatter-chart-high-density"></a>Grafico a dispersione (ad alta densità)
Vedere [Campionamento ad alta densità nei grafici a dispersione](https://docs.microsoft.com/power-bi/visuals/desktop-high-density-scatter-charts)

### <a name="pie"></a>Torta
- Max punti: 3.500
- Gruppo: primi 500
- Dettagli: primi 20

### <a name="r--python-visuals"></a>Oggetti visivi R e Python
Limitati a 150.000 righe. Se vengono selezionate più di 150.000 righe, vengono usate solo le prime 150.000 righe

### <a name="ribbon-chart"></a>Grafico a nastri
- In modalità per categorie
    - Categorie: Virtualizzazione (windowing dei dati) usando una finestra di 500 righe alla volta
    - Serie: prime 60
    - In modalità scalare (potrebbero essere usati limiti dinamici)
        - Max punti: 10.000
        - Categorie: campione di 500 valori
        - Serie: primi 20 valori

### <a name="shape-map-preview"></a>Forme mappe (anteprima)
L'opzione forme mappe può usare statistiche o limiti dinamici. 
- Max punti: 1.500
- Categorie: primi 500
- Serie (se sono presenti sia X che Y): primi 20

### <a name="table"></a>Tabella
- Valori: Virtualizzazione (windowing dei dati) usando una finestra di 500 righe alla volta

### <a name="tree-map-could-use-statistics-or-dynamic-limits"></a>Mappa ad albero (potrebbero essere usati limiti dinamici o statistiche)
- Max punti: 3.500
- Gruppo: primi 500
- Dettagli: primi 20

### <a name="waterfall-chart"></a>Grafico a cascata
- Quando è presente solo il bucket della categoria
    - Max punti: 3.500
    - Solo categoria - primi 3.500
- Quando sono presenti sia categoria che scomposizione
    - Categoria: virtualizzazione (windowing dei dati) usando una finestra di 30 righe alla volta
    - Scomposizione - Primi 200 valori


## <a name="next-steps"></a>Passaggi successivi
[Tipi di visualizzazione](power-bi-report-visualizations.md)
