---
title: Insegnare a Domande e risposte di Power BI a riconoscere le domande e i termini usati nelle query
description: Come usare Domande e risposte di Power BI per esplorare i dati
author: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/21/2020
ms.author: maggies
LocalizationGroup: Ask questions of your datadefintion
ms.openlocfilehash: e5b870201943b93bfdaec2881005785c2f3c470b
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/06/2020
ms.locfileid: "82865803"
---
# <a name="teach-qa-to-understand-questions-and-terms-in-power-bi-qa"></a>Insegnare a Domande e risposte di Power BI a riconoscere le domande e i termini usati nelle query

Nella sezione **Insegna a Domande e risposte** in Configurazione di Domande e risposte, è possibile sottoporre a training il motore di Domande e risposte per consentirgli di comprendere le domande e i termini in linguaggio naturale che non è stato in grado di riconoscere. Per iniziare, inviare una domanda contenente una o più parole che il motore di Domande e risposte non è stato in grado di riconoscere. Domande e risposte chiederà di definire il termine. Immettere un filtro o un nome di campo che corrisponda a ciò che rappresenta tale parola. Domande e risposte reinterpreterà la domanda originale. Se si è soddisfatti dei risultati, è possibile salvarli.

> [!NOTE]
> La funzionalità Insegna a Domande e risposte supporta solo la modalità di importazione. Inoltre, non supporta ancora la connessione a un'origine dati locale o di Azure Analysis Services. Questa limitazione dovrebbe essere rimossa nelle versioni successive di Power BI.

## <a name="start-to-teach-qa"></a>Iniziare a insegnare a Domande e risposte

1. In Power BI Desktop, sulla scheda **Modellazione** della barra multifunzione, selezionare **Configurazione di Domande e risposte** > **Insegna a Domande e risposte**.

    ![Termine evidenziato in rosso in Insegna a Domande e risposte](media/q-and-a-tooling-teach-q-and-a/qna-tooling-teach-synonym-red.png)

2. Digitare una frase con un termine che Domande e risposte non riconosce e selezionare **Invia**.

3. Selezionare la parola sottolineata in rosso. 

    Domande e risposte offre suggerimenti e chiede di specificare la definizione corretta del termine. 
    
3. In **Definire i termini non riconosciuti da Domande e risposte** immettere una definizione.

    ![Anteprima di sinonimo in Insegna a Domande e risposte](media/q-and-a-tooling-teach-q-and-a/qna-tooling-teach-fixpreview.png)

4. Selezionare **Salva** per visualizzare in anteprima l'oggetto visivo aggiornato.

5. Immettere la domanda successiva oppure selezionare la **X** per chiudere.

I consumer del report non vedranno questa modifica finché il report non verrà pubblicato nel servizio.

## <a name="define-nouns-and-adjectives"></a>Definire sostantivi e aggettivi

È possibile insegnare a Domande e risposte due tipi di termini:

- Sostantivi
- Aggettivi

### <a name="define-a-noun-synonym"></a>Definire il sinonimo di un sostantivo

Quando si lavora con i dati, possono spesso essere presenti nomi di campi a cui è possibile fare riferimento con nomi alternativi. Un esempio può essere "vendite". Numerose parole o frasi possono fare riferimento al concetto di vendite, ad esempio "ricavi". Se una colonna è denominata "vendite" e i consumer del report digitano "ricavi", Domande e risposte potrebbe non riuscire a selezionare la colonna corretta per rispondere alla domanda in modo appropriato. In tal caso, è opportuno indicare a Domande e risposte che "domande" e "ricavi" fanno riferimento allo stesso concetto.

Domande e risposte rileva automaticamente che una parola non riconosciuta è un sostantivo usando informazioni di Microsoft Office. Se Domande e risposte rileva un sostantivo, chiede di specificare un sinonimo nel modo seguente:

- <your term> **fa riferimento a** 

Immettere nella casella il termine presente nei propri dati.

![Richiesta di sinonimo in Insegna a Domande e risposte](media/q-and-a-tooling-teach-q-and-a/qna-tooling-synonym-prompt.png)

Se si specifica un termine diverso da un campo del modello di dati, è possibile ottenere risultati indesiderati.

### <a name="define-an-adjective-filter-condition"></a>Definire una condizione di filtro con aggettivo

In alcuni casi può essere opportuno definire termini che hanno una funzione di condizione per i dati sottostanti. Un esempio può essere "Editori eccezionali". "Eccezionale" potrebbe essere una condizione che seleziona solo gli editori che hanno pubblicato un determinato numero di prodotti. Domande e risposte prova a rilevare gli aggettivi mostrando un messaggio di richiesta diverso:

- <field name> **che hanno**  

Specificare la condizione nella casella.

![Richiesta di sinonimo in Insegna a Domande e risposte](media/q-and-a-tooling-teach-q-and-a/qna-tooling-adjectives.png)

Di seguito sono riportate alcune condizioni di esempio che è possibile definire:

- Country which is USA
- Country which is not USA
- Products > 100
- Products greater than 100
- Products = 100
- Products is 100
- Products < 100
- Products smaller than 100

In questi esempi,'Products' può essere un nome di colonna o una misura. 

È anche possibile specificare un'aggregazione nell'espressione di Domande e risposte. Ad esempio, se si definiscono 'popolari' i prodotti con almeno 100 unità vendute, è possibile definire i prodotti con 'sum of units sold > 100' come popolari.  

:::image type="content" source="media/q-and-a-tooling-teach-q-and-a/power-bi-qna-popular-products.png" alt-text="Definire i prodotti popolari":::

In Strumenti è possibile definire una sola condizione. Per definire condizioni più complesse, usare DAX per creare una colonna o una misura calcolata e quindi usare la sezione degli strumenti per creare una singola condizione per tale colonna o misura.

## <a name="manage-terms"></a>Gestisci termini

Dopo aver specificato le definizioni, è possibile tornare indietro per visualizzare tutte le correzioni apportate e modificarle o eliminarle. 

1. In **Configurazione di Domande e risposte** passare alla sezione **Gestisci termini**.

2. Eliminare i termini che non si vogliono più usare. Al momento non è possibile modificare i termini. Per ridefinire un termine, eliminarlo e definirlo di nuovo.

    ![Gestisci termini in Domande e risposte](media/q-and-a-tooling-teach-q-and-a/qna-manage-terms.png)

## <a name="next-steps"></a>Passaggi successivi

Per migliorare il motore del linguaggio naturale è disponibile una serie di procedure consigliate. Per altre informazioni, vedere [Procedure consigliate per Domande e risposte](q-and-a-best-practices.md).
