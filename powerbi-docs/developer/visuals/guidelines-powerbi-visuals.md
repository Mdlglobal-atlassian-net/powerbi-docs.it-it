---
title: Linee guida per gli oggetti visivi di Power BI
description: Informazioni su come pubblicare l'oggetto visivo personalizzato in Microsoft AppSource in modo che altri utenti possano individuarlo e usarlo tramite acquisto.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 07/16/2019
ms.openlocfilehash: 1602743230f1a369fe3da48fa37a313b9d9bbea4
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "79435882"
---
# <a name="guidelines-for-power-bi-visuals"></a>Linee guida per gli oggetti visivi di Power BI
Prima di [pubblicare](office-store.md) l'oggetto visivo di Power BI in Microsoft AppSource in modo che altri utenti possano trovarlo e usarlo, seguire con attenzione le linee guida per creare un'esperienza ottimale per gli utenti.

## <a name="power-bi-visuals-with-additional-purchases"></a>Oggetti visivi di Power BI con acquisti aggiuntivi

È possibile inviare oggetti visivi di Power BI gratuiti nel Marketplace (Microsoft AppSource). È possibile inviare in Microsoft AppSource anche oggetti visivi di Power BI con il tag di prezzo "Potrebbe essere necessario un acquisto aggiuntivo". Gli oggetti visivi di Power BI con il tag "Potrebbe essere necessario un acquisto aggiuntivo" sono analoghi ai componenti aggiuntivi con acquisto in-app disponibili in Office Store. 

Come per gli oggetti visivi di Power BI gratuiti, è anche possibile certificare un oggetto visivo di Power BI con acquisto in-app. Prima di inviare l'oggetto visivo di Power BI con acquisto in-app per la certificazione, verificare che sia conforme ai [requisiti di certificazione](power-bi-custom-visuals-certified.md).

### <a name="what-is-a-power-bi-visual-with-iap-features"></a>Che cos'è un oggetto visivo di Power BI con funzionalità con acquisto in-app?

Un oggetto visivo di Power BI con acquisto in-app è un oggetto visivo *gratuito* che offre *funzionalità gratuite*. Include anche alcune funzionalità avanzate per le quali potrebbe essere previsto un costo aggiuntivo. Nella descrizione dell'oggetto visivo di Power BI gli sviluppatori devono segnalare agli utenti la presenza di funzionalità che richiedono un acquisto aggiuntivo per poter essere usate. Attualmente, Microsoft non fornisce API native per supportare l'acquisto di app e componenti aggiuntivi.

Per questo tipo di acquisti, gli sviluppatori possono usare un sistema di pagamento di terze parti. Per altre informazioni, vedere l'[informativa per lo store](https://docs.microsoft.com/legal/marketplace/certification-policies#11002-displaying-ads).


>[!IMPORTANT]  
> Se si aggiorna l'oggetto visivo di Power BI da gratuito a "Potrebbe essere necessario un acquisto aggiuntivo", gli utenti devono ricevere lo stesso livello di funzionalità gratuite concesso loro prima dell'aggiornamento. È possibile aggiungere funzionalità a pagamento avanzate facoltative oltre alle funzionalità gratuite esistenti.

### <a name="watermarks"></a>Filigrane

È possibile usare le filigrane per consentire ai clienti di continuare a usare le funzionalità avanzate con acquisto in-app senza pagare. 

Le filigrane possono essere usate per presentare le funzionalità complete dell'oggetto visivo di Power BI, prima che venga effettuato un acquisto. 

* È possibile applicare le filigrane nelle funzionalità a pagamento usate senza una licenza valida.
* Le filigrane non sono consentite negli oggetti visivi di Power BI con un tag di prezzo *gratuito*.
* Le filigrane non sono consentite negli oggetti visivi con acquisto in-app, quando l'utente usa funzionalità gratuite. 

### <a name="pop-up-window"></a>Finestra popup

È possibile usare una finestra popup per spiegare come acquistare una licenza quando viene usata una licenza non valida (o scaduta) con l'oggetto visivo di Power BI con acquisto in-app.

### <a name="submission-process"></a>Processo di invio

Seguire il [processo di invio](office-store.md#submitting-to-appsource), quindi passare alla scheda *Configurazione prodotto* e selezionare la casella di controllo *Il prodotto richiede l'acquisto di un servizio*.

Dopo aver convalidato e approvato l'oggetto visivo di Power BI, nell'elenco Microsoft AppSource degli oggetti visivi di Power BI con acquisto in-app viene visualizzato "Potrebbe essere necessario un acquisto aggiuntivo" tra le opzioni di prezzo.

## <a name="context-menu"></a>Menu di scelta rapida
Il menu di scelta rapida è il menu visualizzato quando l'utente passa il mouse su un oggetto visivo.
Tutti gli oggetti visivi Power BI dovrebbero includere il menu di scelta rapida per offrire un'esperienza unificata.
Per informazioni su come aggiungere un menu di scelta rapida, leggere [questo articolo](https://github.com/Microsoft/PowerBI-visuals/blob/gh-pages/tutorials/building-bar-chart/adding-context-menu-to-the-bar.md).

## <a name="commercial-logo"></a>Logo commerciale
In questa sezione vengono descritte le specifiche per l'aggiunta di logo commerciali agli oggetti visivi di Power BI. I logo commerciali non sono obbligatori. Se vengono aggiunti, è necessario che rispettino queste linee guida.

> [!NOTE]
> * In questo articolo, con "logo commerciale" si intende qualsiasi icona commerciale aziendale, come descritto nelle immagini seguenti.
> * Il logo commerciale Microsoft viene usato in questo articolo solo come esempio. Usare il proprio logo commerciale con l'oggetto visivo di Power BI.

> [!IMPORTANT]
> I logo commerciali sono consentiti *solo in modalità di modifica*. I logo commerciali *non possono* essere visualizzati in modalità di visualizzazione.

### <a name="commercial-logo-type"></a>Tipo di logo commerciale

Sono disponibili tre tipi di logo commerciali:
* **Logo**: un logo è costituito da due elementi inseparabili, un'icona e un nome.

    ![Logo Microsoft](media/guidelines-powerbi-visuals/microsoft-logo.png)

* **Simbolo**: un elemento grafico senza testo.

    ![Simbolo Microsoft](media/guidelines-powerbi-visuals/microsoft-symbol.png)

* **Logotipo**: un logo senza icona, costituito solo da testo.

    ![Simbolo Microsoft](media/guidelines-powerbi-visuals/microsoft-logotype.png)

### <a name="commercial-logo-color"></a>Colore del logo commerciale

Quando si usa un logo commerciale, il colore del logo deve essere grigio (colore esadecimale #C8C8C8). Non aggiungere al logo commerciale effetti come le sfumature.

* **Logo**

    ![Simbolo Microsoft](media/guidelines-powerbi-visuals/grey-microsoft-logo.png)

* **Simbolo**: un elemento grafico senza testo.

    ![Simbolo Microsoft](media/guidelines-powerbi-visuals/grey-microsoft-symbol.png)

* **Logotipo**: un logo senza icona, costituito solo da testo.

    ![Simbolo Microsoft](media/guidelines-powerbi-visuals/grey-microsoft-logotype.png)

> [!TIP]
> * Se l'oggetto visivo di Power BI contiene un elemento grafico, è consigliabile aggiungere al logo uno sfondo bianco con margini da 10 px.
> * È consigliabile aggiungere al logo un'ombra esterna nera con opacità del 30%.

### <a name="commercial-logo-size"></a>Dimensioni del logo commerciale

Un oggetto visivo di Power BI richiede due logo commerciali, uno per i riquadri di grandi dimensioni e uno per i riquadri di piccole dimensioni. Posizionare il logo all'interno di un rettangolo di selezione situato nell'angolo superiore o inferiore destro, con margini da 4 px.

La tabella seguente illustra le considerazioni sulle dimensioni per gli oggetti visivi di Power BI.

|  |Oggetto visivo di Power BI piccolo  |Oggetto visivo di Power BI grande  |
|---------|---------|---------|
|*Larghezza del logo*    |Fino a 240 px         |Più di 240 px         |
|*Altezza del log*     |Fino a 160 px         |Più di 160 px         |
|*Dimensioni del rettangolo di selezione*     |40 x 15 px         |101 x 30 px         |
|*Esempio di logo commerciale*     |![Simbolo Microsoft](media/guidelines-powerbi-visuals/grey-microsoft-symbol.png)         |![Logo Microsoft](media/guidelines-powerbi-visuals/grey-microsoft-logo.png)         |
|*Esempio di rettangolo di selezione*    |![esempio di logo piccolo](media/guidelines-powerbi-visuals/small-logo-box.png)         |![esempio di logo grande](media/guidelines-powerbi-visuals/big-logo-box.png)         |
|    |         |         |

### <a name="commercial-logo-behavior"></a>Comportamento del logo commerciale

I logo commerciali sono consentiti solo in modalità di modifica. Un logo commerciale, quando si fa clic su di esso, può includere solo le funzionalità seguenti:

* Il clic sul logo commerciale riporta al sito Web.

* Il clic sul logo commerciale apre una finestra popup con informazioni aggiuntive. La finestra popup sarà divisa in due sezioni:
    * Un'area di marketing che può includere il logo commerciale, un oggetto visivo e le classificazioni di mercato.
    * Un'area informativa che può includere informazioni e collegamenti.    


### <a name="things-to-avoid"></a>Cose da evitare

* I logo commerciali non possono essere visualizzati in modalità di visualizzazione.

* Un logo commerciale animato può visualizzare l'animazione per un massimo di cinque secondi.

* Se l'oggetto visivo di Power BI include icone informative (i) in modalità di lettura, è consigliabile che siano conformi al colore, alle dimensioni e alla posizione del logo commerciale, come descritto in precedenza.

* Evitare un logo commerciale colorato o nero. Il logo commerciale deve essere grigio (colore esadecimale #C8C8C8).

    ![Logo colorato non autorizzato](media/guidelines-powerbi-visuals/no-color-logo.png) ![Logo nero non autorizzato](media/guidelines-powerbi-visuals/black-logo.png)

* Logo commerciale con effetti quali sfumature o ombreggiature decise.

    ![Stile logo non autorizzato](media/guidelines-powerbi-visuals/no-style-logo.png)

## <a name="best-practices"></a>Procedure consigliate

Quando si pubblica un oggetto visivo di Power BI, prendere in considerazione i consigli seguenti per offrire agli utenti un'esperienza ottimale.

### <a name="visual-landing-page"></a>Pagina di destinazione dell'oggetto visivo

Usare la pagina di destinazione per spiegare come usare l'oggetto visivo di Power BI e dove acquistare la licenza. Non includere video che si attivano automaticamente. Aggiungere solo materiale che ottimizza l'esperienza dell'utente, ad esempio informazioni o collegamenti su dettagli di acquisto delle licenze o sull'uso delle funzionalità con acquisto in-app.

### <a name="license-key-and-token"></a>Codice di licenza e token

Per comodità dell'utente, aggiungere i campi correlati a codice di licenza o token nella parte superiore del riquadro formato.

## <a name="faq"></a>DOMANDE FREQUENTI

Per altre informazioni sugli oggetti visivi di Power BI, vedere le [domande frequenti sugli oggetti visivi di Power BI con acquisti aggiuntivi](power-bi-custom-visuals-faq.md#visuals-with-additional-purchases).

## <a name="next-steps"></a>Passaggi successivi

Informazioni su come pubblicare l'oggetto visivo di Power BI in [Microsoft AppSource](office-store.md) in modo che altri utenti possano individuarlo e usarlo.