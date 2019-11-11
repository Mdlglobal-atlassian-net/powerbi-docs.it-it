---
title: Tipi di informazioni dettagliate supportate da Power BI
description: Informazioni rapide e Visualizza informazioni dettagliate con Power BI.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 10/31/2019
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 75462c2414854d0848254a36b89bcdd1de365ec5
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73863475"
---
# <a name="types-of-insights-supported-by-power-bi"></a>Tipi di informazioni dettagliate supportate da Power BI

Il servizio Power BI può cercare automaticamente informazioni dettagliate nei dashboard o nei report.

## <a name="how-does-insights-work"></a>Funzionamento delle informazioni dettagliate
Power BI cerca rapidamente diversi subset del set di dati. Durante la ricerca, Power BI applica un set di algoritmi sofisticati per individuare informazioni potenzialmente interessanti. Power BI analizza il maggior numero possibile di set di dati in un periodo di tempo stabilito.

È possibile eseguire le informazioni dettagliate rispetto a un set di dati o a un riquadro del dashboard.   

## <a name="what-types-of-insights-can-we-find"></a>Tipi di informazioni possibili
Questi sono alcuni degli algoritmi utilizzati:

## <a name="category-outliers-topbottom"></a>Category outlier (dall'alto al basso)
Evidenzia i casi in cui, per una misura nel modello, uno o due membri di una dimensione prevedono valori molto più grandi di altri membri della dimensione.  

![Esempio di outlier categoria](./media/end-user-insight-types/pbi-auto-insight-types-category-outliers.png)

## <a name="change-points-in-a-time-series"></a>Punti di modifica in una serie temporale
Evidenzia quando vi sono modifiche significative nelle tendenze in una serie temporale di dati.

![Esempio di punti di modifica nella serie temporale](./media/end-user-insight-types/pbi-auto-insight-types-changepoint.png)

## <a name="correlation"></a>Correlazione
Consente di rilevare i casi in cui più misure mostrano una correlazione tra loro quando vengono tracciate in una dimensione del set di dati.

![Esempio di correlazione](./media/end-user-insight-types/pbi-auto-insight-types-correlation.png)

## <a name="low-variance"></a>Varianza bassa
Consente di rilevare i casi in cui i punti dati non sono distanti dalla media.

![Esempio di varianza bassa](./media/end-user-insight-types/power-bi-low-variance.png)

## <a name="majority-major-factors"></a>Maggioranza (fattori principali)
Consente di trovare casi in cui la maggior parte di un valore totale può essere attribuita a un fattore singolo quando ripartito da un'altra dimensione.  

![Esempio di fattori principali](./media/end-user-insight-types/pbi-auto-insight-types-majority.png)

## <a name="overall-trends-in-time-series"></a>Tendenze generali nella serie temporale
Rileva le tendenze verso l'alto o verso il basso nei dati della serie temporale.

![Esempio di tendenze generali nella serie temporale](./media/end-user-insight-types/pbi-auto-insight-types-trend.png)

## <a name="seasonality-in-time-series"></a>Stagionalità nella serie temporale
Trova modelli periodici nei dati della serie temporale, ad esempio stagionalità settimanale, mensile o annuale.

![Esempio di stagionalità](./media/end-user-insight-types/pbi-auto-insight-types-seasonality-new.png)

## <a name="steady-share"></a>Condivisione stabile
Evidenzia i casi in cui è presente una correlazione padre-figlio tra la condivisione di un valore figlio in relazione al valore complessivo dell'elemento padre in una variabile continua.

![Esempio di condivisione stabile](./media/end-user-insight-types/pbi-auto-insight-types-steadyshare.png)

## <a name="time-series-outliers"></a>Outlier della serie temporale
Per i dati in una serie temporale, viene rilevato quando sono presenti date o orari specifichi con valori sostanzialmente diversi da quella di altri valori di data/ora.

![Esempio di outlier della serie temporale](./media/end-user-insight-types/pbi-auto-insight-types-time-series-outliers.png)

## <a name="next-steps"></a>Passaggi successivi
[Informazioni dettagliate di Power BI](end-user-insights.md)

Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)

