---
title: Uso dei filtri dei dati in Power BI Desktop
description: È possibile usare i filtri dei dati in Power BI Desktop per filtrare, evidenziare e personalizzare i report
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 05/08/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 2ee3f5aa5416e69646756b1028ea64f1e273d0df
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34226484"
---
# <a name="using-slicers-power-bi-desktop"></a>Uso dei filtri dei dati in Power BI Desktop

È possibile usare un **filtro dei dati** in **Power BI Desktop** per filtrare i risultati degli oggetti visivi nella pagina del report. Con i filtri dei dati è anche possibile modificare facilmente il filtro applicato interagendo con il filtro dei dati stesso. È anche possibile specificare opzioni per la modalità di visualizzazione del filtro dei dati e le modalità di interazione. La figura seguente mostra un filtro dei dati con il relativo menu a discesa del *tipo* visibile. 

![Filtri dei dati in Power BI Desktop](media/desktop-slicers/desktop-slicers_01.png)

Un filtro dei dati può essere visualizzato da uno di vari tipi:

* Elenco
* Menu a discesa
* Tra
* Minore o uguale a
* Maggiore o uguale a

È possibile aggiungere un filtro dei dati a un report facendo clic sull'oggetto visivo **filtro dei dati** nel riquadro **Visualizzazioni**.

![Tipo di oggetto visivo filtro dei dati](media/desktop-slicers/desktop-slicers_02.png)

I filtri dei dati hanno un comportamento analogo in **Power BI Desktop** e nel **servizio Power BI**. Per un articolo sull'uso dei filtri dei dati, vedere [Filtri dei dati in Power BI (esercitazione)](power-bi-visualization-slicers.md).

## <a name="synchronize-slicers-across-report-pages"></a>Sincronizzare i filtri dei dati nelle pagine del report

In **Power BI Desktop** è possibile sincronizzare i filtri dei dati in più pagine del report. Per sincronizzare i filtri dei dati, nel riquadro **Visualizza** nella barra multifunzione selezionare **Sincronizza filtri dei dati**. Quando si sincronizzano i filtri dei dati, viene visualizzato il riquadro **Sincronizza filtri dei dati**, come illustrato nella figura seguente.

![Visualizzazione riquadro Sincronizza filtri dei dati](media/desktop-slicers/desktop-slicers_03.png)

Nel riquadro **Sincronizza filtri dei dati** è possibile specificare la modalità di sincronizzazione del filtro dei dati nelle pagine del report. È possibile specificare se ogni filtro dei dati deve essere **applicato** a ogni singola pagina del report e se il filtro dei dati deve essere **visibile** in ogni singola pagina del report.

Ad esempio, è possibile inserire un filtro dei dati nella **pagina 2** del report, come illustrato nella figura seguente. È quindi possibile specificare se tale filtro dei dati si *applica* a ogni pagina selezionata e se deve essere *visibile* in ogni pagina selezionata nel report. È possibile applicare qualsiasi combinazione di queste opzioni per ogni filtro dei dati. 

![Sincronizza filtri dei dati](media/desktop-slicers/desktop-slicers_04.png)

Se si usa il collegamento **Aggiungi a tutti** nel riquadro, il filtro dei dati selezionato viene applicato a tutte le pagine nel report.


Si noti che le selezioni visualizzate nel riquadro **Sincronizza filtri dei dati** si applicano solo al *filtro dei dati selezionato*. È possibile applicare più filtri dei dati a varie pagine e usare il riquadro per definire come applicare ogni filtro dei dati singolarmente nelle varie pagine del report. 

Anche se è possibile sincronizzare i filtri dei dati selezionati, altre selezioni *non* vengono sincronizzate, ad esempio l'applicazione di stili, le modifiche e l'eliminazione. 

## <a name="advanced-options-for-slicers"></a>Opzioni avanzate per i filtri dei dati

È anche possibile applicare un **nome gruppo** a una raccolta di filtri dei dati nella sezione **Opzioni avanzate** del riquadro **Sincronizza filtri dei dati**, in modo che i filtri dei dati che condividono lo stesso gruppo siano sincronizzati tra le pagine. 

![Nome del gruppo per i filtri dei dati](media/desktop-slicers/desktop-slicers_05.png)

Questa funzionalità consente di creare un gruppo personalizzato di filtri dei dati da mantenere sincronizzati. Viene specificato un nome predefinito, ma è possibile usare qualsiasi nome desiderato. 

Il nome del gruppo offre una maggiore flessibilità con i filtri dei dati. È possibile creare gruppi separati per sincronizzare i filtri dei dati che usano lo stesso campo o inserire i filtri dei dati che usano campi diversi nello stesso gruppo. 


## <a name="next-steps"></a>Passaggi successivi

Potrebbero essere interessanti anche gli articoli seguenti:

* [Filtri dei dati in Power BI (esercitazione)](power-bi-visualization-slicers.md)
* [Usare il filtro dei dati per l'intervallo numerico in Power BI Desktop](desktop-slicer-numeric-range.md)
* [Usare un filtro dei dati e un filtro per la data relativa in Power BI Desktop](desktop-slicer-filter-date-range.md)

