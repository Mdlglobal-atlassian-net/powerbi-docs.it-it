---
title: Suggerimenti per la progettazione di un dashboard di Power BI ottimale
description: Suggerimenti per la progettazione di un dashboard di Power BI ottimale
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/14/2019
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 95170ec36c5b4da0314c858ae415c3bbcb2ab556
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73877416"
---
# <a name="tips-for-designing-a-great-power-bi-dashboard"></a>Suggerimenti per la progettazione di un dashboard di Power BI ottimale
Dopo avere creato un dashboard e aggiunto alcuni riquadri, è opportuno fare in modo che il dashboard non sia solo di gradevole da vedere, ma anche funzionale. Questo, in generale, significa mettere in risalto le informazioni più importanti in modo pulito e ordinato.

![Dashboard di esempio Marketing and sales](media/service-dashboards-design-tips/power-bi-marketing-sample-dashboard.png)

> [!TIP]
> Questo dashboard può essere scaricato insieme ai relativi report da AppSource. Passare a **Scarica i dati** > **Servizi**. Cercare **Microsoft Sample - Sales & Marketing** > **Scarica adesso**.

Ecco alcuni suggerimenti per i dashboard.

## <a name="dashboard-design-best-practices-video"></a>Video sulle procedure consigliate per la progettazione di dashboard

Guardare il video [Dashboard design best practices in Power BI](https://www.youtube.com/watch?v=-tdkUYrzrio) (Procedure consigliate per la progettazione di dashboard in Power BI), per suggerimenti sulla progettazione di Marco Russo di SQLBI.com.

## <a name="consider-your-audience"></a>Considerare i destinatari
Quali sono le metriche chiave che agevoleranno il processo decisionale? Come verrà usato il dashboard? Quali presupposti specialistici o culturali possono incidere sulle scelte di progettazione? Di quali informazioni hanno bisogno i destinatari per ottenere buoni risultati?

Tenere presente che il dashboard offre una panoramica, ovvero una posizione unica da cui controllare lo stato corrente dei dati. Il dashboard è basato sui report e sui set di dati sottostanti, i quali possono contenere moltissimi dettagli. I lettori possono esaminare i report dal dashboard. Quindi non è opportuno inserire dettagli nel dashboard, a meno che non si tratti proprio di ciò che i lettori devono monitorare.

Dove verrà visualizzato il dashboard? Se viene visualizzato su un monitor di grandi dimensioni, è possibile inserirvi più contenuti, ma, se i lettori lo visualizzano sui tablet, un dashboard con meno riquadri sarà più leggibile.

## <a name="tell-a-story-on-one-screen"></a>Raccontare una storia in una schermata
Dato che lo scopo dei dashboard è quello di presentare informazioni importanti a colpo d'occhio, è preferibile che tutti i riquadri si trovino in una sola schermata. Si possono evitare le barre di scorrimento nel dashboard?

Il dashboard è troppo disordinato?  Rimuovere tutto ciò che non rappresenta informazioni essenziali facili da leggere e interpretare.

## <a name="make-use-of-full-screen-mode"></a>Uso della modalità a schermo intero
Quando si presenta un dashboard, visualizzarlo in [modalità a schermo intero](consumer/end-user-focus.md), senza distrazioni.

## <a name="accent-the-most-important-information"></a>Evidenziare le informazioni più importanti
Se il testo e le visualizzazioni nel dashboard hanno tutti la stessa dimensione, sarà difficile per il lettore distinguere cosa è più importante. Ad esempio, le visualizzazioni a scheda sono un ottimo modo per mettere in evidenza un numero importante:  
![Visualizzazione scheda](media/service-dashboards-design-tips/pbi_card.png)

Fornire contesto.  

Leggere l'argomento relativo alla [creazione di un riquadro con solo un numero](visuals/power-bi-visualization-card.md).

## <a name="place-the-most-important-information"></a>Posizionare le informazioni più importanti
La maggior parte delle persone legge dall'alto verso il basso. Quindi posizionare il livello di massimo dettaglio nell'angolo in alto a sinistra e aggiungere dettagli procedendo nella direzione seguita dai destinatari per la lettura (da sinistra a destra, dall'alto verso il basso).

## <a name="use-the-right-visualization-for-the-data"></a>Usare la visualizzazione giusta per i dati
Evitare di usare visualizzazioni diverse per il puro gusto di variare.  Le visualizzazioni devono essere rappresentative e facili da "leggere" e interpretare.  Per alcuni dati e alcune visualizzazioni, è sufficiente una semplice visualizzazione grafica. Altri dati, invece, possono richiedere una visualizzazione più complessa. Usare titoli ed etichette e altre personalizzazioni per agevolare il lettore.  

* Prestare attenzione all'uso di oggetti visivi che possono avere un aspetto gradevole, ma non sono ottimali per la lettura, ad esempio i grafici 3D. 
* Può essere deludente venire a sapere che i grafici a torta, i grafici ad anello, i misuratori e altri tipi di grafico circolare non sono ottimali per la visualizzazione dei dati. I grafici a torta sono ideali in presenza di meno di otto categorie. Data l'impossibilità di confrontare i valori affiancati, il confronto tra valori è più difficile in un grafico a torta rispetto ai grafici a barre o agli istogrammi. I grafici a torta possono essere una buona soluzione per visualizzare le relazioni tra una parte e l'insieme anziché tra parti diverse. I grafici a misuratore sono ottimi per visualizzare lo stato corrente nell'ambito di un obiettivo.
* Le scale dei grafici sugli assi, l'ordinamento delle dimensioni dei grafici e anche i colori usati per i valori delle dimensioni all'interno dei grafici devono essere coerenti.
* Codificare i dati quantitativi in modo leggibile. Non usare più di tre o quattro numerali per visualizzare i numeri. Visualizzare le misure con uno o due numerali a sinistra del separatore decimale e usare la scala per le migliaia o i milioni, ad esempio indicare 3,4 milioni anziché 3.400.000.
* Non usare livelli di precisione e temporali diversi. Fare in modo che gli intervalli di tempo siano ben chiari. Non affiancare un grafico del mese scorso ad altri grafici filtrati di un determinato mese dell'anno.
* Non mescolare misure grandi e piccole sulla stessa scala, ad esempio su un grafico a linee o un grafico a barre. Ad esempio, una misura può essere in milioni e l'altra in migliaia. Con una scala così ampia, sarebbe difficile vedere le differenze della misura in migliaia. Se è necessario mescolarle, scegliere una visualizzazione che consenta di usare un secondo asse.
* Non riempire i grafici con etichette dati superflue. I valori nei grafici a barre sono generalmente comprensibili anche senza visualizzare il numero effettivo.
* Prestare attenzione all’[ordinamento dei grafici](consumer/end-user-change-sort.md). Se si vuole attirare l'attenzione sul numero più alto o più basso, ordinare in base alla misura. Per agevolare la ricerca di una determinata categoria all'interno di molte altre, ordinare in base all'asse.  

Per altre indicazioni specifiche sulle visualizzazioni, vedere [Tipi di visualizzazione in Power BI](visuals/power-bi-visualization-types-for-reports-and-q-and-a.md).  

## <a name="learn-more-about-dashboard-design"></a>Approfondimento sulla progettazione dei dashboard
Per progettare dashboard di altissimo livello, è utile apprendere i principi basilari della Gestalt sulla percezione visiva e sulla comunicazione immediata di informazioni fruibili in contesto. Sono disponibili moltissime risorse a questo proposito, sia in pubblicazioni dedicate che nei nostri blog. Ecco alcune pubblicazioni che possono essere utili:

* *Information Dashboard Design* di Stephen Few  
* *Show Me the Numbers* di Stephen Few  
* *Now You See It* di Stephen Few  
* *Envisioning Information* di Edward Tufte  
* *Advanced Presentations by Design* di Andrew Abela   

## <a name="next-steps"></a>Passaggi successivi
[Creare un dashboard da un report](service-dashboard-create.md)  
[Concetti di base sulle finestre di progettazione del servizio Power BI](service-basic-concepts.md)  
Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)
