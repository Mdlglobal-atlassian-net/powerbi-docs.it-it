---
title: Estrarre dati da una pagina Web da un esempio in Power BI Desktop
description: Estrarre dati da una pagina Web fornendo un esempio di ciò di cui si vuole eseguire il pull
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 10/23/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 9d7012006ca18cf43c530c4d79ed02e6ed73f33f
ms.sourcegitcommit: a739a99e1006834a0f56e387c0bd9d945fb8a76b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51679270"
---
# <a name="get-data-from-a-web-page-by-providing-an-example"></a>Acquisire dati da una pagina Web fornendo un esempio

L'acquisizione di dati da una pagina Web consente agli utenti di estrarre con facilità dati da pagine Web e importarli in **Power BI Desktop**. Spesso, tuttavia, i dati nelle pagine Web non sono disposti in tabelle ordinate facili da estrarre, pertanto l'acquisizione da tali pagine può risultare complessa, anche se i dati sono strutturati e coerenti. 

Ma esiste una soluzione. Con la funzionalità per l'**acquisizione dei dati dal Web da un esempio**, è essenzialmente possibile indicare a **Power BI Desktop** i dati da estrarre, fornendo uno o più esempi nella finestra di dialogo del connettore, in modo che proceda alla raccolta di altri dati nella pagina corrispondenti agli esempi. Con questa soluzione è possibile estrarre tutti i tipi di dati dalle pagine Web, inclusi quelli nelle tabelle *e* altri dati non presenti nelle tabelle. 

![Acquisizione dei dati dal Web da un esempio](media/desktop-connect-to-web-by-example/web-by-example_01.png)



## <a name="using-get-data-from-web-by-example"></a>Uso della funzionalità per l'acquisizione dei dati dal Web da un esempio

Per usare la funzionalità per l'**acquisizione dei dati dal Web da un esempio**, selezionare **Dati** dalla barra multifunzione **Home**. Nella finestra visualizzata selezionare **Altro** dalle categorie nel riquadro sinistro e quindi selezionare **Web**.

![Selezionare Web in Recupera dati](media/desktop-connect-to-web-by-example/web-by-example_03.png)

Da qui, immettere l'URL della pagina Web da cui si vogliono estrarre i dati. In questo articolo verrà usata la pagina Web Microsoft Store e sarà illustrato il funzionamento di questo connettore. 

Se si vuole seguire questa procedura, è possibile usare l'[URL di Microsoft Store](https://www.microsoft.com/store/top-paid/games/xbox?category=classics) usato in questo articolo:

    https://www.microsoft.com/store/top-paid/games/xbox?category=classics

![Finestra di dialogo Da Web](media/desktop-connect-to-web-by-example/web-by-example_04.png)

Quando si sceglie **OK**, viene visualizzata la finestra di dialogo **Strumento di navigazione**, in cui sono presentate le eventuali tabelle rilevate automaticamente dalla pagina Web. Nel caso illustrato nell'immagine riportata di seguito non sono state trovate tabelle, ma nella parte inferiore della pagina è disponibile il pulsante **Estrai la tabella usando gli esempi** che consente di fornire esempi.


![Finestra Strumento di navigazione](media/desktop-connect-to-web-by-example/web-by-example_05.png)

Facendo clic su **Estrai la tabella usando gli esempi**, compare una finestra interattiva in cui è possibile visualizzare in anteprima il contenuto della pagina Web e immettere i valori di esempio dei dati da estrarre. 

In questo esempio verranno estratti il *nome* e il *prezzo* per ognuno dei giochi presenti nella pagina. È possibile eseguire questa operazione specificando un paio di esempi dalla pagina per ogni colonna, come illustrato nella figura seguente. Di pari passo con l'inserimento di questi esempi, **Power Query** (ovvero la tecnologia sottostante che estrae i dati dalla pagina Web) è in grado di estrarre i dati che corrispondono allo schema delle voci di esempio usando algoritmi avanzati di estrazione dei dati.

![Dati da un esempio](media/desktop-connect-to-web-by-example/web-by-example_06.png)

> Nota: i suggerimenti di valore includono solo valori minori o uguali a 128 caratteri di lunghezza.

Quando l'estrazione dei dati dalla pagina Web è conclusa, scegliere **OK** per andare all'**Editor di query**, in cui è possibile applicare altre trasformazioni o definire nuove forme per i dati, ad esempio combinandoli con altri dati o altre origini.

![Dati da un esempio](media/desktop-connect-to-web-by-example/web-by-example_07.png)

Da qui, è possibile creare oggetti visivi o usare i dati della pagina Web in modi differenti durante la creazione di report di **Power BI Desktop**.


## <a name="next-steps"></a>Passaggi successivi
È possibile connettersi a molti tipi di dati usando **Power BI Desktop**. Per altre informazioni sulle origini dati, vedere le risorse seguenti:

* [Aggiungere una colonna da un esempio](desktop-add-column-from-example.md)
* [Connettersi a una pagina Web](desktop-connect-to-web.md)
* [Origini dati in Power BI Desktop](desktop-data-sources.md)
* [Effettuare il data shaping e combinare i dati con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Connettersi a cartelle di lavoro di Excel in Power BI Desktop](desktop-connect-excel.md)   
* [Connettersi a file CSV in Power BI Desktop](desktop-connect-csv.md)   
* [Immettere dati direttamente in Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

