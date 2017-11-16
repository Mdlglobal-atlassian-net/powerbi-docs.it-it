---
title: Connettersi a un database Amazon Redshift in Power BI Desktop
description: "Connettersi con facilità e usare un database Amazon Redshift in Power BI Desktop"
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
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: 1321a4d9c7022de95135f3dbbe33a1cf8d80b38f
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-amazon-redshift-in-power-bi-desktop"></a>Connettersi ad Amazon Redshift in Power BI Desktop
In **Power BI Desktop** è possibile connettersi a un database **Amazon Redshift** e usare i dati sottostanti esattamente come qualsiasi altra origine dati in Power BI Desktop.

## <a name="connect-to-an-amazon-redshift-database"></a>Connettersi a un database Amazon Redshift
Per connettersi a un database **Amazon Redshift** selezionare **Recupera dati** nella barra multifunzione **Home** in Power BI Desktop. Quando si seleziona **Database** nelle categorie a sinistra viene visualizzato **Amazon Redshift**.

![](media/desktop-connect-redshift/connect_redshift_3.png)

Nella finestra **Amazon Redshift** che viene visualizzata digitare o incollare il nome del server e del database **Amazon Redshift**. Nel campo *Server* gli utenti possono specificare un ordinamento nel seguente formato: *ServerURL:Port*

![](media/desktop-connect-redshift/connect_redshift_4.png)

Quando richiesto, inserire il nome utente e la password.

![](media/desktop-connect-redshift/connect_redshift_5.png)

Una volta stabilita la connessione, viene visualizzata una finestra **Strumento di navigazione** che mostra i dati disponibili sul server, in cui è possibile selezionare uno o più elementi da importare e usare in **Power BI Desktop**.

![](media/desktop-connect-redshift/connect_redshift_6.png)

Dopo avere effettuato le selezioni nella finestra **Strumento di navigazione** è possibile scegliere **Carica** per caricare i dati o **Modifica** per modificarli.

* Se si sceglie **Carica**, verrà chiesto se usare la modalità *importazione* o *DirectQuery* per caricare i dati. Per altre informazioni, vedere l'[articolo che descrive DirectQuery](desktop-use-directquery.md).
* Se si sceglie **Modifica**, viene visualizzato l'**Editor di Query** in cui è possibile applicare trasformazioni e filtri di vario tipo ai dati, molti dei quali vengono applicati al database **Amazon Redshift** stesso sottostante (se supportato).

## <a name="next-steps"></a>Passaggi successivi
È possibile connettersi a molti tipi di dati usando Power BI Desktop. Per altre informazioni sulle origini dati, vedere le risorse seguenti:

* [Introduzione a Power BI Desktop](desktop-getting-started.md)
* [Origini dati in Power BI Desktop](desktop-data-sources.md)
* [Effettuare il data shaping e combinare i dati con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Connettersi a cartelle di lavoro di Excel in Power BI Desktop](desktop-connect-excel.md)   
* [Immettere dati direttamente in Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

