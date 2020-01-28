---
title: Eseguire attività di query comuni in Power BI Desktop
description: Eseguire attività di query comuni in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/09/2020
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 8921737fac842d040d014244e2ce80e9bc158b23
ms.sourcegitcommit: 0ae9328e7b35799d5d9613a6d79d2f86f53d9ab0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2020
ms.locfileid: "76040264"
---
# <a name="perform-common-query-tasks-in-power-bi-desktop"></a>Eseguire attività di query comuni in Power BI Desktop

Nella finestra dell'editor di Power Query di Power BI Desktop sono disponibili alcune attività usate comunemente. Questo articolo illustra queste attività comuni e offre i collegamenti per accedere a ulteriori informazioni.

Le attività di query comuni illustrate in questo documento sono:

* Connettersi ai dati
* Effettuare il data shaping e combinare i dati
* Raggruppare le righe
* Trasformare colonne tramite Pivot
* Creare colonne personalizzate
* Eseguire query su formule

Per completare queste attività, verranno usate alcune connessioni dati. I dati sono disponibili per il download o la connessione, nel caso in cui si voglia provare a eseguire autonomamente queste attività.

La prima connessione dati è [una cartella di lavoro di Excel](https://download.microsoft.com/download/5/7/0/5701F78F-C3C2-450C-BCCE-AAB60C31051D/PBI_Edu_ELSi_Enrollment_v2.xlsx) che è possibile scaricare e salvare in locale. L'alta è una risorsa Web che viene usata anche in altri articoli di Power BI Desktop:

<https://www.bankrate.com/retirement/best-and-worst-states-for-retirement/>

Le attività di query iniziano nei passaggi necessari per connettersi a entrambe queste origini dati.

## <a name="connect-to-data"></a>Connettersi ai dati

Per connettersi ai dati in Power BI Desktop, selezionare **Home** e quindi **Recupera dati**. Power BI Desktop visualizza un menu con le origini dati più comuni. Per un elenco completo delle origini dati a cui Power BI Desktop può connettersi, selezionare **Altro** in fondo al menu. Per altre informazioni, vedere [Origini dati in Power BI Desktop](desktop-data-sources.md).

![Menu delle origini dati più comuni, pulsante Recupera dati, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_getdata.png)

Per iniziare, selezionare **Excel**, specificare la cartella di lavoro di Excel menzionata in precedenza e quindi selezionare **Apri**. Query esamina la cartella di lavoro, quindi visualizza i dati che ha rilevato nella finestra **Strumento di navigazione** dopo la selezione di una tabella.

![Origine dati Excel, finestra di dialogo Strumento di navigazione, Recupera dati, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_navigator.png)

È possibile selezionare **Trasforma dati** per modificare i dati o effettuare il *data shaping* prima di caricare i dati in Power BI Desktop. La modifica è particolarmente utile quando si lavora con grandi set di dati e si vuole ridurli prima del caricamento.

Connettersi a diversi tipi di dati è molto semplice. Può anche essere utile connettersi a una risorsa Web. Scegliere **Recupera dati** > **Altro**, quindi selezionare **Altro** > **Web** > **Connetti**.

![Origine dati Web, finestra di dialogo Recupera dati, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_getdata_other.png)

Viene visualizzata la finestra **Da Web** in cui è possibile digitare l'URL della pagina Web.

![Finestra di dialogo Da Web, origine dati Web, Recupera dati, Power BI Desktop](media/desktop-common-query-tasks/datasources_fromwebbox.png)

Seleziona **OK**. Come in precedenza, Power BI Desktop esamina i dati della pagina Web e visualizza le opzioni di anteprima nella finestra di dialogo **Strumento di navigazione**. Quando si seleziona una tabella, viene visualizzata un'anteprima dei dati.

Le altre connessioni dati sono simili. Se per stabilire una connessione dati è necessaria l'autenticazione, Power BI Desktop richiederà di immettere le credenziali appropriate.

Per informazioni dettagliate sulla connessione ai dati in Power BI Desktop, vedere [Connettersi ai dati in Power BI Desktop](desktop-connect-to-data.md).

## <a name="shape-and-combine-data"></a>Effettuare il data shaping e combinare i dati

L'editor di Power Query consente di effettuare il data shaping e di combinare i dati con facilità. Questa sezione include alcuni esempi su come effettuare il data shaping. Per una dimostrazione più completa delle procedure di data shaping e combinazione dei dati, vedere [Data shaping e combinazione dei dati in Power BI Desktop](desktop-shape-and-combine-data.md).

Nella sezione precedente sono stati caricati due set di dati: una cartella di lavoro di Excel e una risorsa Web. Dopo aver caricato i dati nell'editor di Power Query, selezionare la query della pagina Web dalle query disponibili nel riquadro **Query**, come indicato di seguito:

![Riquadro Query, editor di Power Query, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_querypaneloaded.png)

Quando si effettua il data shaping, si modifica la forma e il formato di un'origine dati in base a esigenze specifiche.

Nell'editor di Power Query molti comandi sono disponibili nella barra multifunzione e nei menu di scelta rapida. Quando, ad esempio, si fa clic con il pulsante destro del mouse su una colonna, il menu di scelta rapida consente di rimuovere la colonna. È anche possibile selezionare una colonna e quindi selezionare il pulsante **Rimuovi colonne** dalla scheda **Home** della barra multifunzione.

![Comando Rimuovi colonne, editor di Power Query, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_removecolumns.png)

Il data shaping può essere eseguito in molti altri modi in questa query. È possibile rimuovere qualsiasi numero di righe partendo dall'alto o dal basso. Oppure aggiungere colonne, suddividere colonne, sostituire valori ed eseguire altre operazioni di data shaping. Con queste funzionalità l'utente può indicare all'editor di Power Query il modo in cui vuole ottenere i dati.

## <a name="group-rows"></a>Raggruppare le righe

Nell'editor di Power Query è possibile raggruppare i valori di molte righe in un unico valore. Questa funzionalità può essere utile ad esempio quando si vuole riepilogare il numero di prodotti offerti, le vendite totali o il numero di studenti.

In questo esempio vengono raggruppate le righe di un set di dati relativo alle iscrizioni scolastiche. I dati provengono dalla cartella di lavoro di Excel. Il data shaping è stato eseguito nell'editor di Power Query in modo da ottenere solo le colonne necessarie, rinominare la tabella e apportare alcune altre modifiche.

Si deve scoprire quante Agenzie ha ogni stato. Le agenzie possono includere distretti scolastici, altri enti di formazione come i distretti regionali e altro ancora. Selezionare la colonna **Agency ID - NCES Assigned\[ District\] Latest available year**, quindi scegliere il pulsante **Raggruppa per** nella scheda **Trasforma** o la scheda **Home** della barra multifunzione. Il pulsante **Raggruppa per** è disponibile in entrambe le schede.

![Finestra di dialogo Raggruppa per, editor di Power Query, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_groupby.png)

Viene visualizzata la finestra di dialogo **Raggruppa per**. Quando l'editor di Power query raggruppa le righe, crea una nuova colonna in cui inserisce i risultati di **Raggruppa per**. Per modificare il funzionamento di **Raggruppa per** , è possibile usare:

1. L'elenco a discesa senza etichetta specifica la colonna da raggruppare. L'editor di Power Query imposta come valore predefinito la colonna selezionata, ma è possibile cambiare e scegliere un'altra colonna della tabella.
2. **Nome nuova colonna**: L'editor di Power Query suggerisce per la nuova colonna un nome basato sull'operazione applicata alla colonna raggruppata, ma è possibile assegnare alla nuova colonna qualsiasi nome.
3. **Operation**: È possibile scegliere l'operazione applicata dall'editor di Power Query, ad esempio **Somma**, **Mediana** o **Conteggio righe distinte**. Il valore predefinito è **Conteggio righe**.
4. **Aggiungi raggruppamento** e **Aggiungi aggregazione**: Questi pulsanti sono disponibili solo se si seleziona l'opzione **Avanzate**. In un'unica operazione è possibile eseguire operazioni di raggruppamento (azioni **Raggruppa per**) su molte colonne e creare diverse aggregazioni usando questi pulsanti. In base alle selezioni effettuate in questa finestra di dialogo, l'editor di Power Query crea una nuova colonna che opera su più colonne.

Selezionare **Aggiungi raggruppamento** o **Aggiungi aggregazione** per aggiungere più raggruppamenti o aggregazioni a un'operazione **Raggruppa per**. Per rimuovere un raggruppamento o un'aggregazione, selezionare l'icona dei puntini di sospensione ( **...** ) a destra della riga e quindi **Elimina**. Continuare e provare a eseguire l'operazione **Raggruppa per** usando i valori predefiniti per vedere cosa succede.

![Finestra di dialogo Raggruppa per, editor di Power Query, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_groupbynumbered.png)

Quando si seleziona **OK** Query esegue l'operazione **Raggruppa per** e restituisce i risultati. Esaminando l'esempio, è ora possibile notare la presenza di oltre 1000 agenzie in Ohio, Texas, Illinois e California.

![Colonna Conteggio, operazione Raggruppa per, editor di Power Query, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_groupedresult.png)

E con l'editor di Power Query è sempre possibile rimuovere l'ultima operazione di shaping. Nel riquadro **Impostazioni query**, in **Passaggi applicati**, selezionare la **X** accanto al passaggio appena completato. Continuare e sperimentare. Ripetere il passaggio se i risultati non sono soddisfacenti, finché i dati nell'editor di Power Query non sono quelli voluti.

## <a name="pivot-columns"></a>Trasformare colonne tramite Pivot

È possibile creare colonne pivot e creare una tabella che contiene i valori aggregati per ogni valore univoco di una colonna. Ad esempio, se si vuole sapere quanti prodotti diversi sono presenti in ogni categoria di prodotto, è possibile creare rapidamente una tabella per scoprirlo.

Esaminiamo un esempio. La tabella **Products_by_Categories** seguente è stata impostata in modo da visualizzare solo prodotti univoci (per nome) e la categoria a cui appartengono. Per creare una nuova tabella che visualizza il numero di prodotti presenti in ogni categoria, in base alla colonna **CategoryName**, selezionare la colonna, quindi **Trasforma** > **Colonna pivot**.

![Comando Colonna pivot, editor di Power Query, Power BI Desktop](media/desktop-common-query-tasks/pivotcolumns_pivotbutton.png)

Viene visualizzata la finestra di dialogo **Colonna pivot**, che consente di sapere quali valori della colonna verranno usati per creare nuove colonne (1). Se il nome della colonna di **CategoryName** non è visualizzato, selezionarlo dall'elenco a discesa. Quando si espande **Opzioni avanzate** (2), è possibile selezionare la funzione che verrà applicata ai valori aggregati (3).

![Finestra di dialogo Colonna pivot, editor di Power Query, Power BI Desktop](media/desktop-common-query-tasks/pivotcolumns_pivotdialog.png)

Quando si seleziona **OK**, Query visualizza la tabella in base alle istruzioni di trasformazione specificate nella finestra di dialogo **Colonna pivot**.

![Risultato colonna pivot, editor di Power Query, Power BI Desktop](media/desktop-common-query-tasks/pivotcolumns_pivotcomplete.png)

## <a name="create-custom-columns"></a>Creare colonne personalizzate

Nell'editor di Power Query è possibile creare formule personalizzate che operano su più colonne della tabella. Quindi i risultati delle formule possono essere inseriti in una nuova colonna (personalizzata). Con l'editor di Power Query creare colonne personalizzate è semplicissimo.

Con i dati della cartella di lavoro di Excel nell'editor di Power Query, accedere alla scheda **Aggiungi colonna** della barra multifunzione e quindi selezionare **Colonna personalizzata**.

![Comando Aggiungi colonna personalizzata, editor di Power Query, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_customcolumn.png)

Viene visualizzata la finestra di dialogo seguente. In questo esempio viene creata una colonna personalizzata denominata *Percent ELL* che calcola la percentuale di studenti totali che studiano inglese.

![Finestra di dialogo Colonna personalizzata, editor di Power Query, Power BI Desktop](media/desktop-common-query-tasks/customcolumn_addcustomcolumndialog.png)

Come per qualsiasi altro passaggio previsto nell'editor di Power Query, se la nuova colonna personalizzata non contiene i dati che si stanno cercando, è possibile eliminare il passaggio. Nel riquadro **Impostazioni query**, in **Passaggi applicati**, selezionare la **X** accanto al passaggio **Aggiunta colonna personalizzata**.

![Passaggi applicati, riquadro Impostazioni query, editor di Power Query, Power BI Desktop](media/desktop-common-query-tasks/customcolumn_addedappliedstep.png)

## <a name="query-formulas"></a>Eseguire query su formule

I passaggi generati dall'editor di Power Query possono essere modificati. È anche possibile creare formule personalizzate, che consentono di connettersi ai dati ed eseguire il data shaping in modo più preciso. Ogni volta che l'editor di Power Query esegue un'azione sui dati, la formula associata all'azione viene visualizzata nella barra della formula. Per visualizzare la barra della formula, accedere alla scheda **Visualizza** della barra multifunzione e quindi selezionare **Barra della formula**.

![Opzione Barra della formula, editor di Power Query, Power BI Desktop](media/desktop-common-query-tasks/queryformulas_formulabar.png)

Nell'editor di Power Query tutti i passaggi applicati per ogni query vengono mantenuti in formato testo che è possibile visualizzare o modificare. È possibile visualizzare o modificare il testo per tutte le query usando l'**editor avanzato**. Selezionare **Visualizza** e quindi **Editor avanzato**.

![Comando Editor avanzato, editor di Power Query, Power BI Desktop](media/desktop-common-query-tasks/queryformulas_advancededitorbutton.png)

Questa è la finestra dell'**editor avanzato** con i passaggi associati alla query **USA\_StudentEnrollment**. Questi passaggi vengono creati nel linguaggio delle formule di Power Query, noto anche come *M*. Per altre informazioni, vedere [Informazioni sulle formule di Power Query](https://support.office.com/article/learn-about-power-query-formulas-6bc50988-022b-4799-a709-f8aafdee2b2f). Per visualizzare la specifica del linguaggio, vedere [Specifica del linguaggio M di Power Query](/powerquery-m/power-query-m-language-specification).

![Finestra di dialogo Editor avanzato, editor di Power Query, Power BI Desktop](media/desktop-common-query-tasks/queryformulas_advancededitor.png)

In Power BI Desktop è disponibile un set completo di categorie di formule. Per altri dettagli e informazioni di riferimento complete su tutte le formule dell'editor di Power Query, vedere [Informazioni di riferimento sulle funzioni M di Power Query](/powerquery-m/power-query-m-function-reference).

## <a name="next-steps"></a>Passaggi successivi

Power BI Desktop offre infinite possibilità. Per altre informazioni sulle funzionalità disponibili, vedere le risorse seguenti:

* [Che cos'è Power BI Desktop?](desktop-what-is-desktop.md)
* [Panoramica delle query con Power BI Desktop](desktop-query-overview.md)
* [Origini dati in Power BI Desktop](desktop-data-sources.md)
* [Connettersi ai dati in Power BI Desktop](desktop-connect-to-data.md)
* [Effettuare il data shaping e combinare i dati con Power BI Desktop](desktop-shape-and-combine-data.md)
