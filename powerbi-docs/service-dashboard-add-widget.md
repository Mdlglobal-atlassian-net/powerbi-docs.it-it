---
title: Aggiungere immagini, video e altri elementi al dashboard
description: Documentazione su come usare il widget Aggiungi riquadro per aggiungere un riquadro per immagini, video, caselle di testo, codice Web e dati di streaming a un dashboard.
author: maggiesMSFT
ms.reviewer: ''
featuredvideoid: e2PD8m1Q0vU
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/25/2019
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 0c9e3db46c66fcd440ebd304370d31539dd5c5c7
ms.sourcegitcommit: 313a5a6a01c09038a6152d681103accbd2faf437
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2020
ms.locfileid: "76282026"
---
# <a name="add-images-videos-and-more-to-your-dashboard"></a>Aggiungere immagini, video e altri elementi al dashboard

Aggiungendo un riquadro al dashboard, è possibile inserire un'immagine, una casella di testo, un video, dati in streaming o codice Web al dashboard. 

Nel video Amanda aggiunge riquadri a un dashboard.

   
<iframe width="560" height="315" src="https://www.youtube.com/embed/e2PD8m1Q0vU" frameborder="0" allowfullscreen></iframe>


## <a name="add-an-image-video-or-other-tile"></a>Aggiungere un'immagine, un video o un altro riquadro
È possibile aggiungere un'immagine, una casella di testo, un video, dati in streaming o codice Web direttamente al dashboard.

1. Selezionare **Aggiungi riquadro** nella barra dei menu superiore del dashboard. A seconda delle limitazioni di spazio, potrebbe essere visualizzato solo il segno più ![segno più](media/service-dashboard-add-widget/power-bi-add-tile-icon-small.png).
   
    ![Icona Aggiungi riquadro](media/service-dashboard-add-widget/power-bi-add-tile-icon.png)
2. Selezionare il tipo di riquadro da aggiungere: 

    **[Contenuto Web](#add-web-content)**

    **[Immagine](#add-an-image)**

    **[Casella di testo](#add-a-text-box-or-dashboard-heading)**

    **[Video](#add-a-video)**

    **[Dati in streaming personalizzati](#add-streaming-data)**
   
    ![Finestra Aggiungi riquadro](media/service-dashboard-add-widget/power-bi-add-tile.png)

## <a name="add-an-image"></a>Aggiungere un'immagine
Se si vuole aggiungere il logo aziendale o un'altra immagine al dashboard, salvare il file di immagine online e aggiungere un collegamento a esso. Assicurarsi che non siano necessarie credenziali di sicurezza per accedere al file di immagine. Ad esempio OneDrive e SharePoint richiedono l'autenticazione, quindi le immagini archiviate in queste posizioni non possono essere aggiunte a un dashboard in questo modo.  

1. Nella finestra **Aggiungi riquadro** selezionare **Immagine** > **Avanti**.

2. Nella finestra **Aggiungi riquadro immagine** aggiungere le informazioni sull'immagine:   
   
   a. Per visualizzare un titolo sopra l'immagine, selezionare **Mostra titolo e sottotitolo** e immettere i valori per **Titolo** e, facoltativamente, **Sottotitolo**.

   b. Immettere l'**URL** per l'immagine.

   c. Per trasformare il riquadro in un collegamento ipertestuale, selezionare **Imposta collegamento personalizzato** e immettere il valore per **URL**. 

      Quando i colleghi fanno clic sull'immagine o sul titolo, verrà aperta la pagina corrispondente all'URL.

   d. Selezionare **Applica**. 

      ![Finestra Aggiungi riquadro immagine](media/service-dashboard-add-widget/pbi-widget-add-image-new.png)

3. Nel dashboard ridimensionare e spostare l'immagine in base alla necessità.
     
     ![Immagine nel dashboard](media/service-dashboard-add-widget/power-bi-add-image-dash.png)

## <a name="add-a-text-box-or-dashboard-heading"></a>Aggiungere un'intestazione per una casella di testo o un dashboard

per aggiungere l'intestazione di un dashboard, digitarne il nome nella casella di testo e aumentare il tipo di carattere.

1. Nella finestra **Aggiungi riquadro** selezionare **Casella di testo** > **Avanti**.

2. Formattare la casella di testo:
   
   a. Per visualizzare un titolo sopra la casella di testo, selezionare **Mostra titolo e sottotitolo** e immettere i valori per **Titolo** e, facoltativamente, **Sottotitolo**.

   b. Immettere e formattare il testo della casella di testo in **Contenuto**.  

   c. Facoltativamente, impostare un collegamento personalizzato per il titolo. Un collegamento personalizzato può essere un sito esterno o un dashboard oppure un report nell'area di lavoro. In questo esempio, tuttavia, sono stati aggiunti collegamenti ipertestuali all'interno della casella di testo, quindi l'opzione **Imposta collegamento personalizzato** deve rimanere deselezionata.

   d. Selezionare **Applica**. 

     ![Finestra Aggiungi riquadro casella di testo](media/service-dashboard-add-widget/power-bi-add-textbox.png)
   
3. Nel dashboard ridimensionare e spostare la casella di testo in base alla necessità.
   
   ![Dashboard con immagine e casella di testo](media/service-dashboard-add-widget/pbi-widget-text-added-new.png)

## <a name="add-a-video"></a>Aggiungere un video
Quando si aggiunge un riquadro video di YouTube o Vimeo al dashboard, il video viene riprodotto direttamente nel dashboard.

1. Nella finestra **Aggiungi riquadro** selezionare **Video** > **Avanti**.
2. Aggiungere le informazioni sul video nella finestra **Aggiungi riquadro video**:   
   
   a. Per visualizzare un titolo e un sottotitolo nella parte superiore del riquadro del video, selezionare **Mostra titolo e sottotitolo** e immettere i valori per **Titolo** e, facoltativamente, **Sottotitolo**. In questo esempio si aggiungeranno le informazioni per **Sottotitolo** e il contenuto verrà quindi convertito in un collegamento ipertestuale all'intera playlist su YouTube.

   b. Immettere il valore di **URL video** per il video.

   c. Aggiungere un collegamento ipertestuale per **Titolo** e **Sottotitolo** in modo che i colleghi possano visualizzare l'intera playlist su YouTube dopo aver guardato il video incorporato. A tale scopo, in **Funzionalità** selezionare **Imposta collegamento personalizzato** e quindi immettere il valore di **URL** per la playlist.

   d. Selezionare **Applica**.  

   ![Finestra Aggiungi riquadro video](media/service-dashboard-add-widget/power-bi-add-video-new.png)

3. Nel dashboard ridimensionare e spostare il video in base alla necessità.
     
   ![Dashboard con riquadro video aggiunto](media/service-dashboard-add-widget/pbi-widget-video-added-new.png)
4. Selezionare il riquadro video per riprodurre il video.
5. Selezionare il sottotitolo per visitare la playlist su YouTube.

## <a name="add-streaming-data"></a>Aggiungere lo streaming di dati
È possibile usare PubNub per aggiungere dati in streaming, ad esempio feed di Twitter o dati dei sensori, a un riquadro nel dashboard. Power BI ha creato un'integrazione per ottenere i dati da PubNub. In questo video Will spiega come funziona.
   

<iframe width="560" height="315" src="https://www.youtube.com/embed/kOuINwgkEkQ" frameborder="0" allowfullscreen></iframe>

1. Nella finestra **Aggiungi riquadro** selezionare **Dati in streaming personalizzati** > **Avanti**.
2. Selezionare **Aggiungi set di dati di streaming**.
3. Scegliere **Nuovo set di dati di streaming** per creare un nuovo set di dati in streaming usando l'API Power BI o PubNub.
4. Inserire le informazioni nei campi **Nome set di dati**, **Chiave sottoscrizione** e **Nome del canale**. Se si tratta di una connessione sicura, è presente anche una chiave di autorizzazione. È possibile usare i valori di esempio di PubNub per provare.
5. Selezionare **Avanti**.
    Verranno visualizzati i campi disponibili nel set di dati, con i relativi tipi di dati e il formato JSON.
6. Selezionare **Connetti**.
    È stato creato un set di dati in streaming.
7. Tornare al dashboard e selezionare di nuovo **Aggiungi riquadro** > **Dati in streaming personalizzati** > **Avanti**.
8. Selezionare il set di dati del sensore creato > **Avanti**.
9. Selezionare il tipo di oggetto visivo desiderato. Spesso per questi dati è appropriato un grafico a linee.
10. Selezionare **Asse**, **Legenda** e **Valori**.
11. Stabilire la quantità di tempo da visualizzare, in secondi, minuti o ore.
12. Selezionare **Avanti**.
13. Immettere i valori per **Titolo** e **Sottotitolo**, se si desidera.
14. Aggiungere l'oggetto al dashboard.


1. Nella finestra **Aggiungi riquadro** selezionare **Dati in streaming personalizzati** > **Avanti**.

2. Selezionare **Aggiungi set di dati di streaming**.

3. Scegliere **Nuovo set di dati di streaming** per creare un nuovo set di dati in streaming usando l'API Power BI o PubNub.

4. Inserire le informazioni nei campi **Nome set di dati**, **Chiave sottoscrizione** e **Nome del canale**. Se si tratta di una connessione sicura, è presente anche una chiave di autorizzazione. È possibile usare i valori di esempio di PubNub per provare.

5. Selezionare **Avanti**.

   Verranno visualizzati i campi disponibili nel set di dati, con i relativi tipi di dati e il formato JSON.

6. Selezionare **Connetti**.

   È stato creato un set di dati in streaming.

7. Tornare al dashboard e selezionare di nuovo **Aggiungi riquadro** > **Dati in streaming personalizzati** > **Avanti**.

8. Selezionare il set di dati del sensore creato > **Avanti**.

9. Selezionare il tipo di oggetto visivo desiderato. Spesso per questi dati è appropriato un grafico a linee.

10. Selezionare **Asse**, **Legenda** e **Valori**.

11. Stabilire la quantità di tempo da visualizzare, in secondi, minuti o ore.

12. Selezionare **Avanti**.

13. Facoltativamente, immettere i valori per **Titolo** e **Sottotitolo**.

14. Aggiungere l'oggetto al dashboard.

## <a name="add-web-content"></a>Aggiungere contenuto Web
È possibile incollare o digitare qualsiasi contenuto HTML, come riquadro, nel report o nel dashboard. Immettere il codice di incorporamento manualmente oppure copiare e incollare da siti come Twitter, YouTube, embed.ly e così via.

1. Nella finestra **Aggiungi riquadro** selezionare **Contenuto Web** > **Avanti**.

2. Aggiungere le informazioni nella finestra **Aggiungi riquadro contenuto Web**:
   
   a. Per visualizzare un titolo sopra il riquadro, selezionare **Mostra titolo e sottotitolo** e immettere i valori per **Titolo** e, facoltativamente, **Sottotitolo**.

   b. Immettere il codice di incorporamento. In questo esempio viene copiato e incollato un feed di Twitter.

   c. Selezionare **Applica**.

   ![Finestra Aggiungi riquadro contenuto Web](media/service-dashboard-add-widget/power-bi-add-web-content.png)
   

3. Nel dashboard ridimensionare e spostare il contenuto Web in base alla necessità.
     
   ![Dashboard con quattro riquadri](media/service-dashboard-add-widget/pbi-widget-code-added-new.png)

### <a name="tips-for-embedding-web-content"></a>Suggerimenti per l'incorporamento di contenuto Web
* Per iframes, usare un'origine sicura. Se si immette il codice di incorporamento iframe e si ottiene un riquadro vuoto, controllare se è stato usato *http* per l'origine iframe. In questo caso, modificare in *https*.
  
  ```html
  <iframe src="https://xyz.com">
  ```
* Modificare le informazioni su larghezza e altezza. Il codice di incorporamento incorpora un video e imposta il lettore video su 560 x 315 pixel. Queste dimensioni non cambiano quando si ridimensiona il riquadro.
  
  ```html
  <iframe width="560" height="315"
  src="https://www.youtube.com/embed/Cle_rKBpZ28" frameborder="0"
   allowfullscreen></iframe>
  ```
  
  Se si vuole che il lettore venga ridimensionato per adattarlo al riquadro, impostare larghezza e altezza su 100%.
  
  ```html
  <iframe width="100%" height="100%"
  src="https://www.youtube.com/embed/Cle_rKBpZ28" frameborder="0"
   allowfullscreen></iframe>
  ```
* Questo codice incorpora un tweet e mantiene, come collegamenti separati nel dashboard, collegamenti per il podcast AFK, per la pagina Twitter di \@GuyInACube, per #analytics e per le opzioni Segui, Rispondi, Retweet e Mi piace.  Selezionando il riquadro si raggiunge il podcast su Twitter.
  
  ```html
  <blockquote class="twitter-tweet" data-partner="tweetdeck">
  <p lang="en" dir="ltr">Listen to
  <a href="https://twitter.com/GuyInACube">@GuyInACube</a> talk to
  us about making videos about Microsoft Business Intelligence
  platform
  <a href="https://t.co/TmRgalz7tv">https://t.co/TmRgalz7tv </a>
  <a href="https://twitter.com/hashtag/analytics?src=hash">
  #analytics</a></p>&mdash; AFTK Podcast (@aftkpodcast) <a
  href="https://twitter.com/aftkpodcast/status/693465456531771392">
  January 30, 2016</a></blockquote> <script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>
  ```

## <a name="edit-a-tile"></a>Modifica di un riquadro
Per modificare un riquadro esistente:

1. Passare il puntatore nell'angolo in alto a destra del riquadro e selezionare **Altre opzioni** (...).
   
    ![Selezionare i puntini di sospensione del riquadro](media/service-dashboard-add-widget/pbi_ellipses.png)
2. Selezionare **Modifica dettagli** per visualizzare la finestra **Dettagli riquadro** e apportare le modifiche.
   
    ![Modifica dettagli](media/service-dashboard-add-widget/pbi-edit.png)

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi
* Per semplificare lo spostamento del riquadro nel dashboard, aggiungere un titolo e un sottotitolo facoltativo.
* Se si vuole incorporare un contenuto da un sito Web, che però non fornisce il codice di incorporamento da copiare e incollare, vedere embed.ly per indicazioni su come generare il codice di incorporamento.

## <a name="next-steps"></a>Passaggi successivi
[Introduzione ai riquadri del dashboard per le finestre di progettazione di Power BI](service-dashboard-tiles.md)

Altre domande? [Provare la community di Power BI](https://community.powerbi.com/).

