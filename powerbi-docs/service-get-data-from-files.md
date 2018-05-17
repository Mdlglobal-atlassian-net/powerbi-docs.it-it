---
title: Ottenere dati da file
description: Informazioni su come ottenere dati da file di Excel, Power BI Desktop e CSV in Power BI
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: complete
qualitydate: 04/01/2016
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 629eb65b4090023c24df3098ba1b629349edf128
ms.sourcegitcommit: f679c05d029ad0765976d530effde744eac23af5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="get-data-from-files"></a>Ottenere dati da file
![](media/service-get-data-from-files/file_icons.png)

In Power BI, è possibile connettersi a dati e report o importarli da tre tipi di file.

* Microsoft Excel (con estensione xlsx o xlsm)
* Power BI Desktop (con estensione pbix)
* File con valori delimitati da virgole (con estensione csv)

## <a name="what-does-get-data-from-a-file-really-mean"></a>Cosa significa veramente ottenere dati da un file?
In Power BI i dati esplorati provengono da un set di dati, ma per avere un set di dati è prima di tutto necessario ottenere alcuni dati. Per questo articolo, sarà preso in esame l'inserimento di dati dai file.

Per comprendere meglio l'importanza dei set di dati e come si ottengono dati per essi, verrà esaminata un'automobile. Sedersi in auto e guardare il cruscotto è proprio come sedersi davanti al computer e guardare il dashboard in Power BI. Gli strumenti di controllo sul cruscotto mostrano tutte le operazioni eseguite dall'auto: i giri del motore, la temperatura, la marcia innestata, la velocità e così via.

In Power BI, un set di dati è come il motore di un'auto e quindi fornisce i dati, le metriche e le informazioni che vengono visualizzate nel dashboard di Power BI. Naturalmente al motore, cioè in questo caso il set di dati, serve il carburante, che in Power BI è rappresentato dai dati. Un'automobile ha un serbatoio che pompa benzina nel motore. Proprio come in un'auto, in Power BI è necessario un "serbatoio" di dati che possono essere inviati al set di dati. In questo caso, il "serbatoio" è un file di Power BI Desktop, un file di cartella di lavoro di Excel o un file CSV.

Approfondendo ulteriormente il concetto, il serbatoio di una macchina deve essere rifornito di benzina. La "benzina" per il file di Power BI Desktop, Excel o CSV sono i dati provenienti da un'altra origine dati. È possibile ottenere dati da un'altra origine dati e inserirli in un file di Excel, Power BI Desktop o CSV. Se si tratta di una cartella di lavoro di Excel o di un file CSV, è possibile immettere manualmente le righe di dati. In alternativa, è possibile connettersi a un'origine dati esterna per eseguire una query e caricare i dati nel file. Una volta ottenuto un file con alcuni dati, è possibile importarlo in Power BI come set di dati.

> [!NOTE]
> Per essere importati da Power BI, i dati nelle cartelle di lavoro di Excel devono trovarsi in una tabella o nel modello di dati.
> 
> 

## <a name="where-your-file-is-saved-makes-a-difference"></a>La posizione di salvataggio del file fa la differenza
**Locale**: se si salva il file in un'unità locale del computer o in un'altra posizione all'interno dell'organizzazione, da Power BI è possibile *importare* il file in Power BI. Il file in realtà rimane memorizzato nel disco locale, per cui non viene effettivamente importato in Power BI. Viene invece creato un nuovo set di dati nel sito di Power BI, e i dati (e, in alcuni casi, il modello di dati) vengono caricati nel set di dati. Se il file contiene report, verranno visualizzati nel sito Power BI in Report.

**OneDrive for Business**: se si ha OneDrive for Business e si esegue l'accesso con lo stesso account con cui si accede a Power BI, questo è decisamente il modo più efficace per sincronizzare il lavoro in un file di Excel, Power BI Desktop o CSV e il set di dati, i report e i dashboard in Power BI. Dato che sia Power BI che OneDrive sono nel cloud, Power BI si connette al file in OneDrive all'incirca ogni ora. Se vengono rilevate modifiche, il set di dati, i report e i dashboard vengono aggiornati automaticamente in Power BI.

**OneDrive - Personale**: se si salvano i file nel proprio account OneDrive personale, si ottengono molti dei vantaggi offerti da OneDrive for Business. La differenza principale consiste nel fatto che quando ci si connette al file per la prima volta (scegliendo Recupera dati > File > OneDrive - Personale) è necessario accedere a OneDrive con il proprio account Microsoft, che in genere è diverso da quello usato per accedere a Power BI. Quando si accede a OneDrive con l'account Microsoft, assicurarsi di selezionare l'opzione Mantieni l'accesso. In questo modo, Power BI potrà connettersi al file circa ogni ora e verificare che il set di dati in Power BI sia sincronizzato.

**SharePoint - Siti del team**: il salvataggio dei file di Power BI Desktop in SharePoint - Siti del team corrisponde a grandi linee al salvataggio in OneDrive for Business. La differenza principale è rappresentata dalla modalità di connessione al file da Power BI. Si può specificare un URL o connettersi alla cartella radice.

## <a name="ready-to-get-started"></a>Pronto per iniziare?
Per altre informazioni sull'importazione del file in Power BI vedere gli articoli seguenti.

* [Ottenere dati dai file delle cartelle di lavoro di Excel](service-excel-workbook-files.md)
* [Ottenere dati da file di Power BI Desktop](service-desktop-files.md)
* [Ottenere dati da file con valori delimitati da virgole](service-comma-separated-value-files.md)

