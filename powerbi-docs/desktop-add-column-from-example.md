---
title: Aggiungere una colonna da un esempio in Power BI Desktop
description: Creare rapidamente una nuova colonna in Power BI Desktop usando le colonne esistenti come esempi.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/16/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: b10bbaa4158e6c5392cb6ed937c54bdbb5d555d2
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "76538522"
---
# <a name="add-a-column-from-examples-in-power-bi-desktop"></a>Aggiungere una colonna dagli esempi in Power BI Desktop
Con *Aggiungi colonna da esempi* nell'editor di Power Query è possibile aggiungere nuove colonne al modello di dati semplicemente specificando uno o più valori di esempio per le nuove colonne. È possibile creare gli esempi per le nuove colonne da una selezione oppure fornire un input basato su tutte le colonne esistenti nella tabella.

![](media/desktop-add-column-from-example/add-column-from-example_01.png)

L'uso di *Aggiungi colonna da esempi* consente di creare rapidamente e facilmente nuove colonne ed è ideale nelle situazioni seguenti:

- Si conoscono i dati che si vogliono ottenere nella nuova colonna, ma non si è certi di quale trasformazione, o raccolta di trasformazioni, consenta di ottenerli.
- Si sa già qual è la trasformazione necessaria, ma non si è sicuri di che cosa selezionare nell'interfaccia utente per eseguirla.
- Si hanno tutte le informazioni sulle trasformazioni necessarie grazie a un'espressione *Colonna personalizzata* nel linguaggio *M*, ma una o più espressioni non sono disponibili nell'interfaccia utente.

L'aggiunta di una colonna da un esempio è davvero molto semplice, come verrà illustrato nelle sezioni successive.

## <a name="add-a-new-column-from-examples"></a>Aggiungere una nuova colonna da esempi

Per ottenere dati di esempio da Wikipedia, selezionare **Recupera dati** > **Web** nella scheda **Home** della barra multifunzione di Power BI Desktop. 

![Recuperare i dati dal Web](media/desktop-add-column-from-example/add-column-from-example_02.png)

Incollare l'URL seguente nella finestra di dialogo visualizzata e selezionare **OK**: 

*https:\//wikipedia.org/wiki/List_of_states_and_territories_of_the_United_States*

Nella finestra di dialogo **Strumento di navigazione** selezionare la tabella **States of the United States of America** e quindi selezionare **Trasforma dati**. La tabella verrà aperta nell'editor di Power Query.

In alternativa, per aprire i dati già caricati da Power BI Desktop, selezionare **Modifica query** nella scheda **Home** della barra multifunzione. I dati verranno aperti nell'editor di Power Query. 

![Selezionare Modifica query in Power BI Desktop](media/desktop-add-column-from-example/add-column-from-example_05.png)

Dopo aver aperto i dati di esempio nell'editor di Power Query, selezionare la scheda **Aggiungi colonna** nella barra multifunzione e quindi selezionare **Colonna da esempi**. Selezionare l'icona **Colonna da esempi** per creare la colonna da tutte le colonne esistenti oppure selezionare la freccia a discesa per scegliere tra **Da tutte le colonne** o **Dalla selezione**. Per questa procedura dettagliata, usare **Da tutte le colonne**.

![Selezionare Aggiungi colonna da esempi](media/desktop-add-column-from-example/add-column-from-example_03.png)

## <a name="add-column-from-examples-pane"></a>Riquadro Aggiungi colonna da esempi
Quando si seleziona **Aggiungi colonna** > **Colonna da esempi**, si apre il riquadro **Aggiungi colonna da esempi** nella parte superiore della tabella. La nuova **Colonna 1** viene visualizzata a destra delle colonne esistenti. Potrebbe essere necessario scorrere per visualizzarle tutte. Quando si immettono i valori di esempio nelle celle vuote di **Colonna 1**, Power BI crea regole e trasformazioni corrispondenti agli esempi e le usa per riempire il resto della colonna.

Si noti che anche **Colonna da esempi** viene visualizzato in **Passaggi applicati** nel riquadro **Impostazioni query**. Come sempre, l'editor di Power Query registra i passaggi della trasformazione e li applica alla query in quest'ordine.

![Riquadro Aggiungi colonna da esempi](media/desktop-add-column-from-example/add-column-from-example_04.png)

Mentre si digita il proprio esempio nella nuova colonna, Power BI mostra un'anteprima dell'aspetto del resto della colonna, in base alle trasformazioni create. Se ad esempio si digita *Alabama* nella prima riga, questo corrisponde al valore **Alabama** nella prima colonna della tabella: Non appena si preme INVIO, Power BI riempie il resto della nuova colonna in base al valore della prima colonna e assegna alla colonna il nome **Name & postal abbreviation[12] - Copy**.

Passare ora alla riga **Massachusetts[E]** della nuova colonna ed eliminare la parte **[E]** della stringa. Power BI rileva la modifica e usa l'esempio per creare una trasformazione. Power BI descrive le trasformazioni nel riquadro **Aggiungi colonna da esempi** e rinomina la colonna in **Text Before Delimiter**. 

![Colonna trasformata da esempi](media/desktop-add-column-from-example/add-column-from-example_06.png)

Mentre si continua a fornire esempi, l'editor di Power Query aggiunge altre trasformazioni. Quando si è soddisfatti, selezionare **OK** per salvare le modifiche. 

È possibile rinominare la nuova colonna come desiderato facendo doppio clic sull'intestazione della colonna oppure facendo clic con il pulsante destro del mouse su di essa e scegliendo **Rinomina**. 

Guardare questo video per vedere la funzionalità **Aggiungi colonna da esempi** in azione con l'origine dati di esempio: 

[Power BI Desktop: Add Column From Examples](https://www.youtube.com/watch?v=-ykbVW9wQfw) (Power BI Desktop: Aggiungi colonna da esempi). 

## <a name="list-of-supported-transformations"></a>Elenco di trasformazioni supportate
Quando si usa **Aggiungi colonna da esempi** sono disponibili molte trasformazioni, ma non tutte. L'elenco seguente mostra le trasformazioni supportate:

**Generale**

- Colonna condizionale

**Riferimento**
  
- Riferimento a una colonna specifica, incluse le trasformazioni di taglio, pulizia e maiuscole/minuscole

**Trasformazioni di testo**

- Combina (supporta la combinazione di stringhe letterali e di interi valori di colonna)
- Replace
- Length
- Extract   
  - Primi caratteri
  - Ultimi caratteri
  - Intervallo
  - Testo prima del delimitatore
  - Testo dopo il delimitatore
  - Testo racchiuso tra delimitatori
  - Length
  - Rimuovi caratteri
  - Mantieni caratteri

> [!NOTE]
> Tutte le trasformazioni di *testo* tengono conto dell'eventuale necessità di tagliare, pulire o di applicare una trasformazione di maiuscole/minuscole al valore della colonna.

**Trasformazioni di data**

- Giorno
- Day of Week
- Nome giorno della settimana
- Giorno dell'anno
- Month
- Month Name
- Trimestre dell'anno
- Settimana del mese
- Settimana dell'anno
- Year
- Age
- Inizio dell'anno
- Fine dell'anno
- Inizio del mese
- Fine del mese
- Inizio del trimestre
- Giorni del mese
- Fine del trimestre
- Inizio della settimana
- Fine della settimana
- Giorno del mese
- Inizio della giornata
- Fine della giornata

**Trasformazioni di ora**

- Ora
- Minuto
- Second  
- In Ora Locale

> [!NOTE]
> Tutte le trasformazioni di *data* e *ora* prendono in considerazione l'eventuale necessità di convertire il valore della colonna in *Date*, *Time* o *DateTime*.

**Trasformazioni di numero** 

- Valore assoluto
- Arcocoseno
- Arcoseno
- Arcotangente
- Converti in numero
- Coseno
- Cubo
- Dividi
- Esponente
- Fattoriale
- Divisione intera
- È pari
- È dispari
- Ri
- Logaritmo in base 10
- Modulo
- Moltiplica
- Arrotonda per difetto
- Arrotonda per eccesso
- Segno
- Seno
- Radice quadrata
- Square
- Sottrai
- SUM
- Tangente
- Bucket/Intervalli

