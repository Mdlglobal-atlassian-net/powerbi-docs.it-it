---
title: Connettersi a un data warehouse Snowflake Computing in Power BI Desktop
description: Connettersi facilmente a un data warehouse Snowflake Computing e usarlo in Power BI Desktop
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/12/2017
ms.author: davidi
ms.openlocfilehash: bb1c649d62ad9c8a3c4fb854db2478feecc82e70
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-snowflake-in-power-bi-desktop"></a>Connettersi a Snowflake in Power BI Desktop
In Power BI Desktop è possibile connettersi a un data warehouse **Snowflake** Computing e usare i dati sottostanti esattamente come qualsiasi altra origine dati in Power BI Desktop. 

> [!NOTE]
> È anche *necessario* installare il **driver ODBC di Snowflake** nei computer che usano il connettore **Snowflake**, usando l'architettura corrispondente all'installazione di **Power BI Desktop**, a 32 o 64 bit. È sufficiente seguire il collegamento seguente e [scaricare il driver ODBC di Snowflake](http://go.microsoft.com/fwlink/?LinkID=823762).
> 
> 

## <a name="connect-to-a-snowflake-computing-warehouse"></a>Connettersi a un data warehouse Snowflake Computing
Per connettersi a un data warehouse **Snowflake** Computing selezionare **Recupera dati** nella scheda **Home** della barra multifunzione in Power BI Desktop. Quando si seleziona **Database** nelle categorie a sinistra viene visualizzato **Snowflake**.

![](media/desktop-connect-snowflake/connect_snowflake_2b.png)

Nella finestra **Snowflake** che viene visualizzata digitare o incollare il nome del data warehouse Snowflake Computing, quindi selezionare **OK**. Si noti che è possibile scegliere di **importare** i dati direttamente in Power BI oppure usare **DirectQuery**. Per scoprire di più sull'[uso di DirectQuery](desktop-use-directquery.md).

![](media/desktop-connect-snowflake/connect_snowflake_3.png)

Quando richiesto, inserire il nome utente e la password.

![](media/desktop-connect-snowflake/connect_snowflake_4.png)

> [!NOTE]
> Dopo avere inserito il nome utente e la password per un particolare server **Snowflake**, Power BI Desktop usa quelle stesse credenziali nei successivi tentativi di connessione. Le credenziali possono essere modificate selezionando **File > Opzioni e impostazioni > Impostazioni origine dati**.
> 
> 

Una volta stabilita la connessione, viene visualizzata una finestra **Strumento di navigazione** che mostra i dati disponibili sul server, in cui è possibile selezionare uno o più elementi da importare e usare in **Power BI Desktop**.

![](media/desktop-connect-snowflake/connect_snowflake_5.png)

È possibile **caricare** la tabella selezionata, che importa l'intera tabella in **Power BI Desktop**, oppure è possibile **modificare** la query, che consente di aprire **Editor di query** in modo da filtrare e perfezionare il set di dati da usare e quindi caricare il set di dati perfezionato in **Power BI Desktop**.

## <a name="next-steps"></a>Passaggi successivi
È possibile connettersi a molti tipi di dati usando Power BI Desktop. Per altre informazioni sulle origini dati, vedere le risorse seguenti:

* [Introduzione a Power BI Desktop](desktop-getting-started.md)
* [Origini dati in Power BI Desktop](desktop-data-sources.md)
* [Effettuare il data shaping e combinare i dati con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Connettersi a cartelle di lavoro di Excel in Power BI Desktop](desktop-connect-excel.md)   
* [Immettere dati direttamente in Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

