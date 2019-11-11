---
ms.openlocfilehash: 4ea1b2141cf9a072f11a3a62789c7c0ec5b500a4
ms.sourcegitcommit: a5853ef44ed52e80eabee3757bb6887fa400b75b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73799931"
---
Esistono due calcoli principali che è possibile creare con DAX:

* **Colonne calcolate**
* **Misure calcolate**

Prima di approfondire la creazione di questi due calcoli, è importante avere una piena comprensione della sintassi DAX per le tabelle e le colonne che verranno usate per la creazione delle **colonne calcolate** o delle **misure calcolate**.

## <a name="dax-table-and-column-name-syntax"></a>Sintassi del nome di tabella e di colonna DAX
È importante conoscere il formato generale dei nomi di tabella DAX sia per la creazione di una nuova colonna che di una nuova misura:

    'Table Name'[ColumnName]

Se sono presenti spazi nel nome di tabella (come illustrato sopra), è obbligatorio racchiudere il nome di tabella tra virgolette singole. Se il nome di tabella non contiene spazi, è possibile omettere le virgolette singole e la sintassi sarà simile alla seguente:

    TableName[ColumnName]

La figura seguente mostra una formula DAX creata in Power BI:

![](media/7-2-dax-calculation-types/dax-calc-types_1.png)

È anche possibile omettere completamente il nome della tabella e usare solo il nome della colonna. Non è tuttavia una procedura ottimale per scrivere funzioni chiare e di conseguenza ottenere un codice DAX chiaro. I nomi di colonna devono sempre includere le parentesi quadre.

È consigliabile osservare *sempre* le indicazioni seguenti:

* Non includere spazi nei nomi di tabella
* Includere sempre il nome di tabella nelle formule (non ometterlo, anche se consentito da DAX)

## <a name="creating-calculated-columns"></a>Creazione di colonne calcolate
Le **colonne calcolate** sono utili quando si vuole filtrare in base al valore oppure se si vuole un calcolo per ogni riga nella tabella.

È possibile creare colonne calcolate in Power BI Desktop selezionando **Nuova colonna** nella scheda **Creazione di modelli**. È preferibile usare la vista Dati (anziché la vista Report o **Relazioni**), perché è possibile visualizzare la nuova colonna creata e la **barra della formula** viene popolata ed è pronta per la formula DAX.

![](media/7-2-dax-calculation-types/dax-calc-types_2a.png)

Dopo aver selezionato il pulsante **Nuova colonna**, la **barra della formula** viene popolata con un nome di colonna di base (che naturalmente è possibile modificare in base alla formula usata) e con l'operatore **=** e la nuova colonna viene visualizzata nella griglia dati, come illustrato nella figura seguente.

![](media/7-2-dax-calculation-types/dax-calc-types_3.png)

Di seguito sono riportati gli elementi necessari per una colonna calcolata:

* Un nuovo nome di colonna
* Almeno una funzione o un'espressione

Se si fa riferimento a una tabella o una colonna nella formula della colonna calcolata, non è necessario specificare una riga nella tabella, perché Power BI calcolerà la colonna per la riga corrente per ogni calcolo.

## <a name="creating-calculated-measures"></a>Creazione di misure calcolate
Usare una **misura calcolata** quando si calcolano percentuali o rapporti oppure sono necessarie aggregazioni complesse. Per creare una misura usando una formula DAX, selezionare il pulsante **Nuova misura** nella scheda **Creazione di modelli**. Anche in questo caso è consigliabile usare la vista **Dati** di Power BI Desktop perché mostra la **barra della formula** e consente di scrivere facilmente la formula DAX.

![](media/7-2-dax-calculation-types/dax-calc-types_4.png)

Con le **misure** viene visualizzata una nuova icona di misura nel riquadro **Campi** con il nome della misura. La **barra della formula** viene popolata con il nome della formula DAX (in questo caso con la misura).

![](media/7-2-dax-calculation-types/dax-calc-types_5.png)

Gli elementi necessari per una misura calcolata sono uguali a quelli per la colonna calcolata:

* Un nuovo nome di misura
* Almeno una funzione o un'espressione

> Contenuto video fornito da [Alberto Ferrari, SQLBI](https://www.sqlbi.com/learning-dax)
> 
> 

