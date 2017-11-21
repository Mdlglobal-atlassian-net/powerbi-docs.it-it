---
title: Condividere i report di Power BI con i colleghi
description: Informazioni su come condividere report di Power BI e report filtrati con i colleghi all'interno dell'organizzazione.
services: powerbi
documentationcenter: 
author: maggiesMSFT
manager: kfile
backup: ajayan
editor: 
tags: 
featuredvideoid: 0tUwn8DHo3s
qualityfocus: complete
qualitydate: 06/22/2016
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/14/2017
ms.author: maggies
ms.openlocfilehash: 022f085d12d7dc872052ca9205deca264b1c0418
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2017
---
# <a name="share-power-bi-reports-with-your-coworkers"></a>Condividere i report di Power BI con i colleghi
La *condivisione* è un approccio valido per consentire ad alcuni utenti di accedere ai dashboard e ai report. Power BI offre [diversi modi per collaborare ai report e distribuirli](service-how-to-collaborate-distribute-dashboards-reports.md). La condivisione è solo uno di essi.

Con la condivisione, l'utente e i destinatari necessitano di una [licenza Power BI Pro](service-free-vs-pro.md). In caso contrario, il contenuto deve avere una [capacità Premium](service-premium.md). Se si hanno suggerimenti, il team di Power BI è sempre lieto di ricevere commenti da parte degli utenti, tramite il [sito della community di Power BI](https://community.powerbi.com/).

È possibile condividere un report con i colleghi nello stesso dominio di posta elettronica dell'utente, dall'area di lavoro personale o dall'area di lavoro di un'app. Quando si condivide un report, gli utenti che lo condividono possono visualizzarlo e interagire con esso, ma non possono modificarlo. Essi vedranno gli stessi dati che l'utente vede nel report, a meno che non sia stata applicata la [sicurezza a livello di riga](service-admin-rls.md). 

## <a name="share-a-power-bi-report"></a>Condividere un report di Power BI
1. Nel servizio Power BI, [creare un dashboard](service-dashboard-create.md) con almeno un riquadro che si collega al report che si vuole condividere. 
   
    Anche se si vuole condividere solo il report, è prima necessario creare un dashboard che si collega al report e poi condividerlo. 

1. Nell'angolo in alto a destra del dashboard selezionare **Condividi**.

     ![Seleziona Condividi](media/service-share-reports/power-bi-share-upper-right.png)
  
2. Inviarlo ai destinatari desiderati. Se non si vuole inviare posta elettronica relativa al dashboard, deselezionare la casella di controllo **Invia notifica tramite posta elettronica ai destinatari**.

     ![Deselezionare la casella di controllo Invia notifica tramite posta elettronica ai destinatari](media/service-share-reports/power-bi-share-dont-send-mail.png)

4. Seleziona **Condividi**.

      Gli utenti con cui si condivide il dashboard saranno ora autorizzati a visualizzare il report sottostante. 

1. Aprire il report nel servizio Power BI, copiare l'URL della pagina del report e inviarlo ai colleghi. 
   
    Quando i colleghi selezionano il collegamento, Power BI apre una versione del report di sola lettura.

## <a name="share-a-filtered-version-of-a-report"></a>Condividere una versione filtrata di un report
Cosa accade se si vuole condividere una versione filtrata di un report? Ad esempio, un report che mostri solo i dati relativi a una città, un venditore o un anno specifici. Questa operazione può essere eseguita creando un URL personalizzato.

1. Aprire il report in [Visualizzazione di modifica](service-reading-view-and-editing-view.md), applicare il filtro e salvare il report.
   
   In questo esempio viene filtrato il dashboar [Retail Analysis Sample](sample-tutorial-connect-to-the-samples.md) in modo da mostrare solo i valori in cui il campo **Territory** corrisponde a **NC**.
   
   ![Riquadro Filtro report](media/service-share-reports/power-bi-filter-report2.png)
2. Aggiungere quanto segue alla fine dell'URL della pagina del report:
   
   ?filter=*tablename*/*fieldname* eq *value*
   
    Il campo deve essere di tipo **stringa** e né *tablename* né *fieldname* possono contenere spazi.
   
   In questo esempio, il nome della tabella è **Store**, il nome del campo è **Territory** e il valore a cui applicare il filtro è **NC**:
   
    ?filter=Store/Territory eq NC
   
   ![URL del report filtrato](media/service-share-reports/power-bi-filter-url3.png)
   
   Il browser aggiunge dei caratteri speciali per rappresentare barre e spazi, quindi si avrà:
   
   app.powerbi.com/groups/me/reports/010ae9ad-a9ab-4904-a7a1-10a61f70f2f5/ReportSection2?filter=Store%252FTerritory%20eq%20NC
3. Inviare questo URL ai colleghi. 
   
   Quando i colleghi selezionano il collegamento, Power BI apre una versione del report filtrato.

## <a name="next-steps"></a>Passaggi successivi
* Per inviare suggerimenti, passare al [sito della community di Power BI](https://community.powerbi.com/).
* [Come si condividono i dashboard e i report e in che modo ci si collabora?](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Share a dashboard (Condividi un dashboard)](service-share-dashboards.md)
* Altre domande? [Provare la community di Power BI](http://community.powerbi.com/).

