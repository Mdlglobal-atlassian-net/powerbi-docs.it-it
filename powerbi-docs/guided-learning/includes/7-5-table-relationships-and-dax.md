---
ms.openlocfilehash: cd6ea6fd52f929e2cd254214cf0e8c96e858f6c2
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61273392"
---
Power BI consente di creare relazioni tra più tabelle, incluse quelle provenienti da origini dati completamente diverse. È possibile visualizzare tali relazioni per qualsiasi modello di dati nella visualizzazione **Relazioni** di Power BI Desktop.

![](media/7-5-table-relationships-and-dax/dax-relationships_1.png)

## <a name="dax-relational-functions"></a>Funzioni relazionali DAX
DAX include **funzioni relazionali** che permettono di interagire con le tabelle tra cui esistono relazioni definite.

È possibile restituire il valore di una colonna oppure è possibile restituire tutte le righe in una relazione usando le funzioni DAX.

Ad esempio, la funzione **RELATED** segue le relazioni e restituisce il valore di una colonna, mentre **RELATEDTABLE** segue le relazioni e restituisce un'intera tabella che viene filtrata in modo da includere solo le righe correlate.

![](media/7-5-table-relationships-and-dax/dax-relationships_2.png)

La funzione **RELATED** viene usata in relazioni *molti-a-uno*, mentre **RELATEDTABLE** è destinata a relazioni *uno-a-molti*.

È possibile usare funzioni relazionali per creare espressioni che includono valori di più tabelle. DAX restituirà un risultato con queste funzioni, indipendentemente dalla lunghezza della catena della relazione.

> Contenuto video fornito da [Alberto Ferrari, SQLBI](http://www.sqlbi.com/learning-dax)
> 
> 

