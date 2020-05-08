---
title: Suggerimenti sulla progettazione di report nel Generatore report di Power BI
description: Usare i suggerimenti seguenti per progettare i report impaginati in Power BI Report Builder.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: c1490ff0-5b8a-43c1-8d22-e459395db4f6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 13b9e37d4a64493dfdcac02d9df86a1e19a1c24b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "78921172"
---
# <a name="report-design-tips-in-power-bi-report-builder"></a>Suggerimenti sulla progettazione di report nel Generatore report di Power BI
  Usare i suggerimenti seguenti per progettare i report impaginati in Power BI Report Builder.  
  
   
  
##  <a name="designing-reports"></a><a name="DesigningReports"></a> Progettazione di report  
  
-   Un report ben progettato offre le informazioni necessarie per un'azione. Identificare le domande a cui il report deve rispondere. Tenere presenti queste domande durante la progettazione del report.  
  
-   Per progettare visualizzazioni dei dati efficienti, valutare il modo in cui visualizzare informazioni che l'utente del report può comprendere facilmente. Scegliere un'area dati che corrisponda il più possibile ai dati che si vuole visualizzare. Ad esempio, un grafico rappresenta le informazioni di riepilogo e aggregate in modo più efficace rispetto a una tabella estesa su numerose pagine contenenti informazioni dettagliate. È possibile visualizzare i dati di un set di dati in qualsiasi area dati che include grafici, mappe, indicatori, grafici sparkline, barre di dati e dati tabulari in diversi layout griglia basati su una Tablix. 
  
-   Se si intende fornire il report in un formato di esportazione specifico, testare quanto prima il formato di esportazione nella progettazione. Il supporto delle funzionalità varia in base al renderer scelto.  
  
-   Quando si creano layout complessi, creare il layout in fasi. È possibile usare i rettangoli come contenitori per organizzare gli elementi del report. È possibile creare le aree dati direttamente nell'area di progettazione per ingrandire l'area di lavoro e quindi, dopo aver completato ogni area, trascinarla nel contenitore rettangolare. Usando i rettangoli come contenitori, è possibile posizionare tutto il relativo contenuto in un unico passaggio. I rettangoli consentono anche di controllare il rendering degli elementi del report in ogni pagina.  
  
-   Per ridurre il disordine in un report, può essere utile usare la visibilità condizionale per specifici elementi del report e consentire all'utente di scegliere se visualizzare gli elementi. È possibile impostare la visibilità in base a un parametro o a una casella di testo selezionabile. È possibile aggiungere caselle di testo nascosto condizionale per visualizzare i risultati provvisori delle espressioni. Quando un report visualizza dati imprevisti, è possibile visualizzare i risultati provvisori per facilitare il debug delle espressioni.  
  
-   Quando usano elementi nidificati in rettangoli o celle della Tablix, è possibile impostare colori di sfondo diversi per il contenitore e gli elementi contenuti. Per impostazione predefinita, il colore di sfondo è **Nessun colore**. Gli elementi con un colore di sfondo specifico sono visibili attraverso gli elementi con un colore di sfondo impostato su **Nessun colore**. Questa tecnica consente di selezionare l'elemento corretto per impostare le proprietà di visualizzazione, ad esempio la visibilità dei bordi per le celle della Tablix.  
  
 Per altre informazioni sugli aspetti da considerare quando si progetta il report, vedere [Pianificazione di un report nel Generatore report](report-builder-planning-report.md).  
  
##  <a name="naming-conventions-for-reports-data-sources-and-datasets"></a><a name="NamingConventions"></a> Convenzioni di denominazione per report, origini dati e set di dati  
  
-   Usare le convenzioni di denominazione per le origini dati e i set di dati che documentano l'origine dei dati.  
  
    1.  **Origini dati.** Se non si vuole usare un server o un database effettivo per ragioni di sicurezza, usare un alias che indichi all'utente che cos'è l'origine dei dati.  
  
    2.  **Set di dati.** Usare un nome che indichi l'origine dati su cui è basato.  
  
##  <a name="working-with-data"></a><a name="Data"></a> Uso dei dati  
  
-   Per prima cosa, visualizzare tutti i dati che si vuole usare nel riquadro dei dati del report. Mentre si definiscono le domande a cui il report deve rispondere, considerare come limitare i dati dei set di dati del report a quelli necessari.  
  
-   In generale, includere solo i dati che verranno visualizzati in un report. Usare le variabili di query nelle query sui set di dati per consentire all'utente di scegliere i dati da visualizzare nel report. Se si stanno creando set di dati condivisi, specificare filtri basati sui parametri del report per offrire la stessa funzionalità.  
  
-   Se si è un autore di query esperto, tenere presente che, per quantità di dati limitate, è possibile che si voglia raggruppare i dati nel report anziché nella query. Se si raggruppano tutti i dati nella query, il report tenderà a essere una presentazione del set di risultati della query. Diversamente, per visualizzare valori aggregati per grandi quantità di dati in un grafico o una matrice, non è necessario includere i dati di dettaglio.  
  
-   A seconda dei requisiti, è possibile visualizzare i nomi e i percorsi delle origini dati del report, il testo del comando di query sul set di dati e i valori dei parametri nel report. Molti nuovi utenti si chiedono innanzitutto da dove provengono i dati. Per ridurre il disordine nel report, è possibile nascondere le caselle di testo in base a questo tipo di informazioni e consentire agli utenti di scegliere se visualizzarle. Provare ad aggiungere queste informazioni nell'ultima pagina del report. Impostare la visibilità della casella di testo in base a un parametro che l'utente può modificare.  
  
##  <a name="interacting-with-the-report-design-surface"></a><a name="DesignSurface"></a> Interazione con l'area di progettazione del report  
 L'area di progettazione del report non è di tipo WYSIWIG. Quando si inseriscono gli elementi del report nell'area di progettazione, la loro posizione relativa influisce sul modo in cui gli elementi vengono visualizzati nella pagina del report visualizzabile. Lo spazio vuoto viene conservato.  
  
-   Usare le guide di allineamento e i pulsanti di layout per allineare e disporre gli elementi nell'area di progettazione del report. Ad esempio, è possibile allineare le parti superiori o i bordi degli elementi selezionati, espandere un elemento in modo che corrisponda alle dimensioni di un altro elemento o regolare la spaziatura tra gli elementi.  
  
-   Usare i tasti di direzione per regolare la posizione e le dimensioni degli elementi selezionati nell'area di progettazione. Ad esempio, le combinazioni di tasti seguenti sono molto utili:  
  
    -   **Tasti di direzione** Consentono di spostare l'elemento del report selezionato.  
  
    -   **CTRL+Tasti di direzione** Consentono di spostare l'elemento del report selezionato di un pixel alla volta.  
  
    -   **CTRL+MAIUSC+Tasti di direzione** Consentono di aumentare o diminuire le dimensioni dell'elemento del report selezionato.  
  
-   Per aggiungere un elemento a un rettangolo, usare la punta superiore sinistra del mouse in modo che punti alla posizione iniziale dell'elemento nel contenitore rettangolare. Usare i tasti di scelta rapida per posizionare gli oggetti selezionati. Il rettangolo si espande automaticamente per adattarsi alle dimensioni degli elementi contenuti.  
  
-   Per aggiungere più elementi a una cella della Tablix, aggiungere innanzitutto un rettangolo e quindi aggiungere gli elementi.  
  
     Per impostazione predefinita, ogni cella della Tablix contiene una casella di testo. Quando si aggiunge un rettangolo a una cella, il rettangolo sostituisce la casella di testo. Ad esempio, posizionare gli indicatori nidificati in un rettangolo in una cella della Tablix per controllare come le dimensioni di un grafico o un indicatore si espandono quando si modifica l'altezza della riga contenente la cella.  
  
-   Usare il controllo **Zoom** per modificare la visualizzazione dell'area di progettazione. È possibile usare la pagina intera o sezioni più piccole della pagina.  
  
-   Per trascinare i campi dal riquadro dei dati del report al riquadro di raggruppamento, evitare di trascinare il campo attraverso altri elementi del report nell'area di progettazione perché verrebbero selezionati e verrebbe deselezionata l'area dati della Tablix. Trascinare il campo verso il basso nel riquadro dei dati del report e quindi nel riquadro di raggruppamento.  
  
###  <a name="selecting-items"></a><a name="Selecting"></a> Selezione degli elementi  
 Per selezionare l'oggetto desiderato nell'area di progettazione del report, usare il tasto ESC, il menu di scelta rapida, il riquadro Proprietà e il riquadro di raggruppamento.  
  
-   -   Premere ESC per scorrere lo stack di elementi del report che occupano lo stesso spazio nell'area di progettazione.  
  
    -   In alcuni elementi del report, provare a usare il menu di scelta rapida per selezionare l'elemento del report o la parte dell'elemento del report desiderata.  
  
    -   Il riquadro Proprietà visualizzate le proprietà per la selezione corrente.  
  
    -   Per usare gruppi di righe e gruppi di colonne in un'area dati della Tablix, selezionare il gruppo dal riquadro di raggruppamento.  

  
##  <a name="working-with-specific-types-of-report-items"></a><a name="ReportItems"></a> Uso di tipi specifici di elementi del report  
  
###  <a name="working-with-parameters"></a><a name="Parameters"></a> Uso dei parametri  
  
-   Lo scopo principale dei parametri del report è filtrare i dati nell'origine dati e recuperare solo quelli necessari per il report.  
  
-   Per i parametri del report, trovare un equilibrio tra abilitare l'interattività e consentire a un utente di ottenere i risultati desiderati. Ad esempio, è possibile impostare i valori predefiniti per un parametro su valori usati di frequente.  
  
###  <a name="working-with-text"></a><a name="Text"></a> Uso del testo  
  
-   Quando si incollano più righe in una casella di testo, il testo viene aggiunto come un'unica sequenza. Ogni sequenza di testo può essere formattata solo come unità. Per formattare ogni riga in modo indipendente, inserire una nuova riga premendo INVIO nella sequenza in base alle esigenze. È quindi possibile applicare stili e formattazione a ogni riga di testo indipendente nella casella di testo.  
  
-   È possibile impostare le proprietà relative al formato e le azioni in una casella di testo o in un testo segnaposto nella casella di testo. Se è presente una sola riga di testo, è consigliabile impostare le proprietà nella casella di testo anziché nel testo.  
  
###  <a name="working-with-expressions"></a><a name="Expressions"></a> Uso delle espressioni  
  
-   Di seguito sono descritti i formati di espressioni semplici e complesse. È possibile digitare il formato dell'espressione semplice direttamente nelle caselle di testo, le proprietà nel riquadro Proprietà o nelle posizioni nelle finestre di dialogo che accettano un'espressione.
  
-   Quando si crea un'espressione, è utile creare ogni parte indipendentemente e verificarne il valore. È quindi possibile combinare tutte le parti in un'espressione finale. Una tecnica utile è aggiungere una casella di testo in una cella di matrice, visualizzare ogni parte dell'espressione e impostare la visibilità condizionale nella casella di testo. Per controllare lo stile del bordo e il colore quando la casella di testo è nascosta, posizionare innanzitutto la casella di testo in un rettangolo e quindi impostare lo stile del bordo e il colore del rettangolo in modo che corrisponda alla matrice.  
  
###  <a name="working-with-indicators"></a><a name="Indicators"></a> Uso degli indicatori  
  
-   Per impostazione predefinita, un indicatore visualizza almeno tre stati. Dopo aver aggiunto un indicatore a un report, è possibile configurarlo aggiungendo o rimuovendo gli stati. Per facilitare la visualizzazione agli utenti, scegliere un indicatore che varia di colore e forma.  
  
##  <a name="controlling-the-rendering-of-report-items-on-the-report-page"></a><a name="Rendering"></a> Controllo del rendering degli elementi del report nella pagina del report  
  
-   Nell'area di progettazione del report gli elementi del report aumentano per contenere il contenuto del set di dati, dell'espressione, del sottoreport o del testo associato.  
  
    -   Quando si posiziona un elemento nella pagina del report, la distanza tra l'elemento e tutti gli elementi che iniziano a destra dell'elemento diventa la distanza minima che deve essere mantenuta man mano che la dimensione dell'elemento del report aumenta orizzontalmente. Analogamente, la distanza tra un elemento e l'elemento sopra di esso diventa la distanza minima che deve essere mantenuta man mano che l'elemento superiore aumenta verticalmente.  
  
    -   Un elemento in un report aumenta per contenere i dati e spinge gli elementi peer (elementi nello stesso contenitore padre) all'esterno usando le regole seguenti:  
  
    -   Ogni elemento si sposta verso il basso per mantenere la distanza minima dagli elementi che terminano sopra l'elemento.  
  
    -   Ogni elemento si sposta verso destra per mantenere la distanza minima dagli elementi che terminano a sinistra dell'elemento. Per i sistemi con layout da destra a sinistra, ogni elemento si sposta a sinistra per mantenere la distanza minima dagli elementi che terminano a destra dell'elemento.  
  
    -   I contenitori si espandono per adattarsi all'aumento degli elementi figlio. Per un elemento selezionato, nel riquadro Proprietà la proprietà Parent identifica il contenitore per l'elemento. È anche possibile usare il riquadro Struttura documento per visualizzare la gerarchia di contenimento degli elementi del report.  
  
    -   La barra degli strumenti **Layout** offre più pulsanti per facilitare l'allineamento di bordi, centri e spaziatura per gli elementi del report. Per abilitare la barra degli strumenti **Layout**, dal menu **Visualizza** scegliere **Barre degli strumenti** e quindi fare clic su **Layout**.  
  
-   Se si intende salvare il report come file con estensione pdf, la larghezza del report deve essere impostata esplicitamente su un valore che offre i risultati desiderati nel formato di file di esportazione. Ad esempio, impostare la larghezza della pagina del report su esattamente 7,9375 pollici e i margini sinistro e destro su 0,5 pollici.  
  
-   Usare **Layout di stampa** e **Imposta pagina** nella barra degli strumenti del visualizzatore report per eseguire il rendering di un report in una visualizzazione compatibile con la stampa. Per facilitare la rimozione delle pagine vuote non necessarie, eseguire le operazioni seguenti:  
  
    1.  Rimuovere tutti gli spazi vuoti aggiuntivi tra le aree dati e i bordi del report.  
  
    2.  Ridurre i margini di pagina nella finestra di dialogo **Proprietà report**.  
  
    3.  Usare i **Rettangoli** come contenitori per controllare il rendering degli elementi del report.  
  
    4.  Nelle intestazioni di colonna modificare la proprietà della casella di testo WritingMode per usare il testo verticale.  

 Per altre informazioni, vedere [Evitare le pagine vuote durante la stampa di report impaginati](../guidance/report-paginated-blank-page.md).

 Questo comportamento, le proprietà di larghezza e altezza degli elementi del report, le dimensioni del corpo del report, la definizione dell'altezza e della larghezza della pagina, le impostazioni dei margini del report padre e il supporto specifico del renderer per l'impaginazione determinano insieme gli elementi del report che vengono inseriti in una pagina di cui viene eseguito il rendering.
 
## <a name="next-steps"></a>Passaggi successivi

- [Che cosa sono i report impaginati in Power BI Premium?](paginated-reports-report-builder-power-bi.md)  
