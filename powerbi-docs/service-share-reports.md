---
title: Filtrare un report e condividerlo con i collaboratori - Power BI
description: Informazioni su come filtrare un report di Power BI e condividerlo con i colleghi all'interno dell'organizzazione.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/24/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 5f3808884e63521ec1dd775d876f1cf707bbe56b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "64770693"
---
# <a name="filter-a-power-bi-report-and-share-it-with-coworkers"></a>Filtrare un report di Power BI e condividerlo con i colleghi
La *condivisione* è un approccio valido per consentire ad alcuni utenti di accedere ai dashboard e ai report. Cosa accade se si vuole condividere una versione filtrata di un report? Ad esempio, un report che mostri solo i dati relativi a una città, un venditore o un anno specifici. Provare a filtrare un report e condividerlo o la creazione di un URL personalizzato. Quando i destinatari aprono il report per la prima volta, questo verrà filtrato. I destinatari possono rimuovere il filtro modificando l'URL. 

Power BI offre anche [diversi altri modi per collaborare a report e distribuirli](service-how-to-collaborate-distribute-dashboards-reports.md). Con la condivisione, l'utente e i destinatari necessitano di una [licenza Power BI Pro](service-features-license-type.md). In caso contrario, il contenuto deve avere una [capacità Premium](service-premium-what-is.md). 

## <a name="two-ways-to-filter-a-report"></a>Due modi per filtrare un report

### <a name="set-a-filter"></a>Impostare un filtro

Aprire il report in [Visualizzazione di modifica](consumer/end-user-reading-view.md), applicare il filtro e salvare il report.
   
In questo esempio viene filtrato l'[esempio di analisi delle vendite al dettaglio](sample-tutorial-connect-to-the-samples.md) in modo da visualizzare solo i valori in cui **Territory** equivale a **NC**.
   
![Riquadro Filtro report](media/service-share-reports/power-bi-filter-report2.png)

### <a name="create-a-filter-in-the-url"></a>Creare un filtro nell'URL

Aggiungere quanto segue alla fine dell'URL della pagina del report:
   
?filter=*tablename*/*fieldname* eq *value*
   
Il campo deve essere di tipo numero, data/ora o stringa. I valori *tablename* o *fieldname* non possono contenere spazi.
   
In questo esempio, il nome della tabella è **Store**, il nome del campo è **Territory** e il valore a cui applicare il filtro è **NC**:
   
?filter=Store/Territory eq 'NC'
   
![URL del report filtrato](media/service-share-reports/power-bi-filter-url3.png)
   
Il browser aggiunge dei caratteri speciali per rappresentare barre, spazi e apostrofi, quindi si otterrà il risultato seguente:
   
app.powerbi.com/groups/me/reports/010ae9ad-a9ab-4904-a7a1-xxxxxxxxxxxx/ReportSection2?filter=Store%252FTerritory%20eq%20%27NC%27

Vedere l'articolo [filtrare un report usando i parametri della stringa di query nell'URL](service-url-filters.md) per molti altri dettagli.

## <a name="share-the-filtered-report"></a>Condividere il report filtrato

1. Quando si [condivide il report](service-share-dashboards.md)deselezionare la **invia notifica tramite posta elettronica ai destinatari** casella di controllo.

    ![Finestra di dialogo Condividi report](media/service-share-reports/power-bi-share-report-dialog.png)

4. Inviare il collegamento con il filtro creato in precedenza.

## <a name="next-steps"></a>Passaggi successivi
* Per inviare suggerimenti, passare al [sito della community di Power BI](https://community.powerbi.com/).
* [Come si condividono i dashboard e i report e in che modo ci si collabora?](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Share a dashboard (Condividi un dashboard)](service-share-dashboards.md)
* Altre domande? [Provare la community di Power BI](http://community.powerbi.com/).

