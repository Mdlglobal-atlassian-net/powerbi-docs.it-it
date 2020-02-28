---
title: Connettersi a un data warehouse Snowflake Computing in Power BI Desktop
description: Connettersi facilmente a un data warehouse Snowflake Computing e usarlo in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: e7534fd0da2039a2dafaf3ca80ee6957fa8d8754
ms.sourcegitcommit: cde65bb8b1bed1ee8cf512651afeb829ddc155de
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2020
ms.locfileid: "77464302"
---
# <a name="connect-to-a-snowflake-computing-warehouse-in-power-bi-desktop"></a>Connettersi a un data warehouse Snowflake Computing in Power BI Desktop
In Power BI Desktop è possibile connettersi a un data warehouse **Snowflake** Computing e usare i dati sottostanti esattamente come qualsiasi altra origine dati in Power BI Desktop. 

> [!NOTE]
> È anche *necessario* installare il **driver ODBC di Snowflake** nei computer che usano il connettore **Snowflake**, usando l'architettura corrispondente all'installazione di **Power BI Desktop**, a 32 o 64 bit. È sufficiente seguire il collegamento seguente e [scaricare il driver ODBC di Snowflake](https://go.microsoft.com/fwlink/?LinkID=823762).
> 
> 

## <a name="connect-to-a-snowflake-computing-warehouse"></a>Connettersi a un data warehouse Snowflake Computing
Per connettersi a un data warehouse **Snowflake Computing**, selezionare **Recupera dati** nella scheda **Home** della barra multifunzione in Power BI Desktop. Quando si seleziona **Database** nelle categorie a sinistra viene visualizzato **Snowflake**.

![](media/desktop-connect-snowflake/connect-snowflake-2b.png)

Nella finestra **Snowflake** che viene visualizzata digitare o incollare il nome del data warehouse Snowflake Computing, quindi selezionare **OK**. Si noti che è possibile scegliere di **importare** i dati direttamente in Power BI oppure usare **DirectQuery**. Per scoprire di più sull'[uso di DirectQuery](desktop-use-directquery.md). Si noti che l'accesso SSO con credenziali AAD supporta solo DirectQuery.

![](media/desktop-connect-snowflake/connect-snowflake-3.png)

Quando richiesto, inserire il nome utente e la password.

![](media/desktop-connect-snowflake/connect-snowflake-4.png)

> [!NOTE]
> Dopo avere inserito il nome utente e la password per un particolare server **Snowflake**, Power BI Desktop usa quelle stesse credenziali nei successivi tentativi di connessione. Le credenziali possono essere modificate selezionando **File > Opzioni e impostazioni > Impostazioni origine dati**.
> 
> 

Se si vuole usare l'opzione con account Microsoft, l'integrazione di AAD con Snowflake deve essere configurata sul lato Snowflake. A tale scopo, leggere la sezione introduttiva della [documentazione di Snowflake sull'argomento](https://docs.snowflake.net/manuals/user-guide/oauth-powerbi.html#power-bi-sso-to-snowflake).

![Tipo di autenticazione tramite account Microsoft nel connettore Snowflake.](media/desktop-connect-snowflake/connect-snowflake-6.png)


Una volta stabilita la connessione, viene visualizzata una finestra **Strumento di navigazione** che mostra i dati disponibili sul server, in cui è possibile selezionare uno o più elementi da importare e usare in **Power BI Desktop**.

![Errore ODBC 28000 che causa un errore di connessione.](media/desktop-connect-snowflake/connect-snowflake-5.png)

È possibile **caricare** la tabella selezionata, che importa l'intera tabella in **Power BI Desktop**, oppure è possibile **modificare** la query, che consente di aprire **Editor di query** in modo da filtrare e perfezionare il set di dati da usare e quindi caricare il set di dati perfezionato in **Power BI Desktop**.

## <a name="next-steps"></a>Passaggi successivi
È possibile connettersi a molti tipi di dati usando Power BI Desktop. Per altre informazioni sulle origini dati, vedere le risorse seguenti:

* [Che cos'è Power BI Desktop?](desktop-what-is-desktop.md)
* [Origini dati in Power BI Desktop](desktop-data-sources.md)
* [Effettuare il data shaping e combinare i dati con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Connettersi a cartelle di lavoro di Excel in Power BI Desktop](desktop-connect-excel.md)   
* [Immettere dati direttamente in Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

