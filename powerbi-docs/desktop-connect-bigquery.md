---
title: Connettersi a un database Google BigQuery in Power BI Desktop
description: Connettersi a Google BigQuery e usarlo con facilità in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: b88be05c1e3890dd8ac63503d9279f51b1d9eec9
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73876512"
---
# <a name="connect-to-a-google-bigquery-database-in-power-bi-desktop"></a>Connettersi a un database Google BigQuery in Power BI Desktop
In Power BI Desktop è possibile connettersi a un database Google **BigQuery** e usare i dati sottostanti esattamente come qualsiasi altra origine dati in Power BI Desktop.

## <a name="connect-to-google-bigquery"></a>Connettersi a Google BigQuery
Per connettersi a un database Google **BigQuery** selezionare **Recupera dati** nella barra multifunzione **Home** in Power BI Desktop. Quando si seleziona **Database** nelle categorie a sinistra, compare **Google BigQuery**.

![Finestra di dialogo Recupera dati per Google BigQuery](media/desktop-connect-bigquery/connect_bigquery_01.png)

Nella finestra **Google BigQuery** visualizzata accedere al proprio account Google BigQuery e selezionare **Connetti**.

![Accedere a Google BigQuery](media/desktop-connect-bigquery/connect_bigquery_02.png)

Dopo l'accesso, viene visualizzata la finestra seguente, che indica l'avvenuta autenticazione. 

![Accesso a Google eseguito](media/desktop-connect-bigquery/connect_bigquery_02b.png)

Una volta stabilita la connessione, viene visualizzata una finestra **Strumento di navigazione** che mostra i dati disponibili sul server, in cui è possibile selezionare uno o più elementi da importare e usare in **Power BI Desktop**.

![Dati da Google BigQuery](media/desktop-connect-bigquery/connect_bigquery_03.png)

## <a name="considerations-and-limitations"></a>Considerazioni e limitazioni
Il connettore Google **BigQuery** presenta alcune limitazioni di cui tenere conto e dà adito ad alcune considerazioni:

* Il connettore Google BigQuery è disponibile in Power BI Desktop e nel servizio Power BI. Nel servizio Power BI, il connettore è accessibile tramite la connessione da cloud a cloud da Power BI a Google BigQuery.

È possibile usare Power BI con i **progetti di fatturazione** di Google BigQuery. Per impostazione predefinita, Power BI usa il primo progetto nell'elenco restituito per l'utente. Per personalizzare il comportamento del progetto di fatturazione quando viene usato con Power BI, procedere come segue:

 * Specificare l'opzione che segue nel valore M sottostante nel passaggio Source. L'opzione che può essere personalizzata tramite **Editor di Power Query** in Power BI Desktop:

    ```Source = GoogleBigQuery.Database([BillingProject="Include-Billing-Project-Id-Here"])```

## <a name="next-steps"></a>Passaggi successivi
È possibile connettersi a molti tipi di dati usando Power BI Desktop. Per altre informazioni sulle origini dati, vedere le risorse seguenti:

* [Che cos'è Power BI Desktop?](desktop-what-is-desktop.md)
* [Origini dati in Power BI Desktop](desktop-data-sources.md)
* [Effettuare il data shaping e combinare i dati con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Connettersi a cartelle di lavoro di Excel in Power BI Desktop](desktop-connect-excel.md)   
* [Immettere dati direttamente in Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

