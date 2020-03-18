---
title: Capacità e SKU per le funzionalità di analisi incorporata di Power BI
description: Informazioni sulla capacità e sugli SKU per le funzionalità di analisi incorporata di Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/11/2020
ms.openlocfilehash: 27d6ddd9b24e09805bd22150a22347e5cd93c8e0
ms.sourcegitcommit: a175faed9378a7d040a08ced3e46e54503334c07
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "79492837"
---
# <a name="capacity-and-skus-in-power-bi-embedded-analytics"></a>Capacità e SKU per le funzionalità di analisi incorporata di Power BI

Quando si passa all'ambiente di produzione, le funzionalità di analisi incorporata di Power BI richiedono una capacità dedicata (SKU *A*, *EM* o *P*) per la pubblicazione di contenuto di Power BI incorporato.

Per capacità si intende un set dedicato di risorse riservate per l'uso esclusivo. La capacità consente di pubblicare dashboard, report e set di dati per gli utenti, senza dover acquistare licenze per utente. Offre inoltre prestazioni affidabili e coerenti per il contenuto.

>[!NOTE]
>Per la pubblicazione, è necessario un account Power BI Pro.

## <a name="what-is-embedded-analytics"></a>Che cos'è l'analisi incorporata?

Le funzionalità di analisi incorporata di Power BI includono due soluzioni:
* *Power BI Embedded*: offerta di Azure
* Incorporamento di Power BI come parte di *Power BI Premium*: offerta di Office

### <a name="power-bi-embedded"></a>Power BI Embedded

Power BI Embedded è una soluzione destinata agli ISV e agli sviluppatori che vogliono incorporare oggetti visivi nelle proprie applicazioni.

Le applicazioni che usano Power BI Embedded consentono agli utenti di usare contenuto archiviato nella capacità di Power BI Embedded.

### <a name="power-bi-premium"></a>Power BI Premium

[Power BI Premium](../../service-premium-what-is.md) è una soluzione destinata alle aziende che necessitano di una soluzione di business intelligence completa che offra una visione centralizzata dell'organizzazione, dei partner, dei clienti e dei fornitori.

Power BI Premium è un prodotto SaaS che permette agli utenti di usufruire del contenuto tramite app per dispositivi mobili, app sviluppate internamente o il portale di Power BI (servizio Power BI). Power BI Premium può quindi offrire una soluzione per le applicazioni destinate ai clienti sia interni che esterni.

## <a name="capacity-and-skus"></a>Capacità e SKU

Ogni capacità offre una selezione di SKU e ogni SKU fornisce livelli di risorse diversi per memoria e potenza di calcolo. Il tipo di SKU necessario dipende dal tipo di soluzione che si vuole distribuire.

Per informazioni sui carichi di lavoro supportati per ogni livello, vedere l'articolo [Configurare i carichi di lavoro in una capacità Premium](../../service-admin-premium-workloads.md)

Per pianificare e testare la capacità, usare i collegamenti seguenti:
* [Pianificazione della capacità](embedded-capacity-planning.md)
* [Approcci di test](../../service-premium-capacity-optimize.md#testing-approaches)

### <a name="power-bi-embedded-skus"></a>SKU di Power BI Embedded

Power BI Embedded viene fornito con uno [SKU *a*](../../service-admin-premium-purchase.md#purchase-a-skus-for-testing-and-other-scenarios).

### <a name="power-bi-premium-skus"></a>SKU di Power BI Premium

Power BI Premium offre due SKU, *P* ed *EM*.
* [Informazioni sulle differenze tra gli SKU *P* ed *EM*](../../service-premium-what-is.md#subscriptions-and-licensing)
* [Acquistare uno SKU Premium](../../service-admin-premium-purchase.md)

### <a name="which-sku-should-i-use"></a>Quale SKU è opportuno usare?

Questa tabella fornisce un riepilogo delle funzionalità, la capacità che richiedono e lo specifico SKU necessario per ciascuna di esse. 

</br>
<table>
<col width="20%">
<col width="20%">
<col width="20%">
<col width="20%">
<col width="20%">
<tbody>
<tr>
<td style="text-align: center"; colspan="2"><p><b>Funzionalità</b></p></td>
<td style="text-align: center">
<p><b>Power BI Embedded</b></p>
</td>
<td style="text-align: center"; colspan="2">
<p><b>Power BI Premium</b></p>
</td>
</tr>
<tr>
<td><p><em>Che cosa viene utilizzato?</em><p></td>
<td><p><em>Da quale servizio o applicazione?</em><p></td>
<td style="text-align: center"><p><em>SKU A</br>(Azure)</em></p></td>
<td style="text-align: center"><p><em>SKU EM</br>(Office)</em></p></td>
<td style="text-align: center"><p><em>SKU P</br>(Office)</em></p></td>
</tr>
<tr>
<td>Incorporamento di artefatti di un'area di lavoro di Power BI</td>
<td>
</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td rowspan="2">Report di Power BI</td>
<td>Un'applicazione incorporata per l'organizzazione</br>(i dati sono di proprietà dell'utente)</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td>Un'applicazione incorporata per i clienti</br>(i dati sono di proprietà dell'app)</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td rowspan="3">Contenuto di Power BI<br>(con una licenza gratuita per Power BI)</td>
<td>Servizio Power BI</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td>Power BI per dispositivi mobili</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td>App di Microsoft Office</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
</tbody>
</table>

### <a name="capacity-considerations"></a>Considerazioni sulla capacità

La tabella seguente include un riepilogo dei dati relativi ai pagamenti e all'utilizzo per capacità.

</br>
<table>
<tbody>
<tr>
<td></td>
<td style="text-align: center;"><p><strong>Power BI Embedded</strong></p></td>
<td style="text-align: center;" colspan="2"><p><strong>Power BI Premium</strong></p></td>
</tr>
<tr>
<td><p><strong>Offerta</strong></p></td>
<td style="text-align: center;"><p>Azure</p></td>
<td style="text-align: center;" colspan="2"><p>Office</p></td>
</tr>
<tr>
<td><p><strong>SKU</strong></p></td>
<td style="text-align: center;"><p>A</p></td>
<td style="text-align: center;"><p>EM</p></td>
<td style="text-align: center;"><p>P</p></td>
</tr>
<tr>
<td><p><strong>Fatturazione</strong></td>
<td style="text-align: center;">Ogni ora</td>
<td style="text-align: center;">Ogni mese</td>
<td style="text-align: center;">Ogni mese</td>
</tr>
<tr>
<td><p><strong>Impegno</strong></td>
<td style="text-align: center;">Nessuno</td>
<td style="text-align: center;">Annuale</td>
<td style="text-align: center;">Mensile o annuale</td>
</tr>
<tr>
<td valign="top"><p><strong>Utilizzo</strong></td>
<td style="text-align: center;">Le risorse di Azure possono essere:</br>- <a href="azure-pbie-scale-capacity.md">Ridimensionate</a></br>- <a href="azure-pbie-pause-start.md">Sospese e riprese</a>
</td>
<td style="text-align: center;">Incluso nelle app e nelle</br> applicazioni Microsoft</td>
<td style="text-align: center;">Incluso nelle app e</br> nel servizio Power BI</td>
</tr>
</tbody>
</table>

### <a name="sku-memory-and-computing-power"></a>Memoria e potenza di calcolo degli SKU

La tabella seguente descrive le risorse e i limiti di ogni SKU.

| Nodi delle capacità | Totale vCore | vCore back-end | RAM (GB) | vCore front-end | Connessione dinamica/DirectQuery (al secondo) | Parallelismo di aggiornamento dei modelli |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0.5 | 2.5 | 0.5 | 3,75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7,5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| P4 | 64 | 32 | 200 | 32 | 240 | 48 |
| P5 | 128 | 64 | 400 | 64 | 480 | 96 |
| | | | | | | |

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
>[Incorporamento per i clienti](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Incorporare contenuto per l'organizzazione](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [Incorporare contenuti dalle app](embed-from-apps.md)