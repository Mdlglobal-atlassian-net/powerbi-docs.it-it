---
title: Pubblicare sul Web da Power BI
description: "La funzionalità Pubblica sul Web di Power BI consente di incorporare con facilità visualizzazioni interattive di Power BI online, ad esempio in post di blog, siti Web, via posta elettronica o social media, su qualsiasi dispositivo."
services: powerbi
documentationcenter: 
author: guyinacube
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
ms.date: 11/27/2017
ms.author: asaxton
ms.openlocfilehash: ced24e81271c414101ddd7027a034814e9a7d609
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/06/2017
---
# <a name="publish-to-web-from-power-bi"></a>Pubblicare sul Web da Power BI

La funzionalità **Pubblica sul Web** di Power BI consente di incorporare con facilità visualizzazioni interattive di Power BI online, ad esempio in post di blog, siti Web, via posta elettronica o social media, su qualsiasi dispositivo.

È anche possibile modificare, aggiornare o annullare facilmente la condivisione degli oggetti visivi pubblicati.

> [!WARNING]
> Quando si usa **Pubblica sul Web**, il report o l'oggetto visivo pubblicato può essere visualizzato da qualsiasi utente su Internet. La visualizzazione dei report non richiede alcuna autenticazione. Usare la funzionalità Pubblica sul Web solo con report e dati che possono essere visualizzati da qualsiasi utente su Internet, ovvero da membri non autenticati del pubblico. Sono inclusi i dati di livello dettagliato aggregati nei report. Prima di pubblicare questo report, assicurarsi di avere i diritti per condividere pubblicamente i dati e le visualizzazioni. Non pubblicare informazioni riservate o di proprietà. In caso di dubbio, prima di procedere alla pubblicazione verificare i criteri dell'organizzazione.

## <a name="how-to-use-publish-to-web"></a>Come usare la funzionalità Pubblica sul Web

La funzionalità **Pubblica sul Web** è disponibile nei report presenti nelle aree di lavoro personali o di gruppo che possono essere modificati.  Non è possibile usare Pubblica sul Web con report che non sono stati condivisi con l'utente o con report che si basano sulla sicurezza a livello di riga per proteggere i dati. Vedere la sezione **Limitazioni** più avanti per un elenco completo di casi in cui la funzionalità Pubblica sul Web non è supportata. Prima di usare la funzionalità Pubblica sul Web, vedere l' **Avviso** precedente in questo articolo.

Per informazioni sul funzionamento di questa funzionalità, guardare il *breve video*seguente. Seguire quindi questa procedura per provare a usare la funzionalità.

<iframe width="560" height="315" src="https://www.youtube.com/embed/UF9QtqE7s4Y" frameborder="0" allowfullscreen></iframe>


La procedura seguente illustra come usare la funzionalità **Pubblica sul Web**.

1. In un report modificabile nell'area di lavoro selezionare **File > Pubblica sul Web**.
   
   ![](media/service-publish-to-web/publish_to_web1.png)

2. Verificare i contenuti della finestra di dialogo e selezionare **Crea codice di incorporamento** , come illustrato nella finestra di dialogo seguente.
   
   ![](media/service-publish-to-web/publish_to_web2_ga.png)

3. Esaminare l'avviso mostrato nella finestra di dialogo seguente e confermare che i dati possono essere incorporati in un sito Web pubblico. In caso affermativo, selezionare **Pubblica**.
   
   ![](media/service-publish-to-web/publish_to_web3_ga.png)

4. Viene visualizzata una finestra di dialogo che include un collegamento che può essere inviato tramite posta elettronica, incorporato nel codice, ad esempio un iFrame, o incollato direttamente nella pagina Web o nel blog.
   
   ![](media/service-publish-to-web/publish_to_web4.png)

5. Se è già stato creato codice di incorporamento per il report, il codice di incorporamento verrà visualizzato rapidamente. È possibile creare solo un codice di incorporamento per ogni report.
   
   ![](media/service-publish-to-web/publish_to_web5.png)

## <a name="tips-and-tricks-for-view-modes"></a>Suggerimenti e consigli per le modalità di visualizzazione

Quando si incorpora contenuto in un post di blog, è in genere necessario adattarlo alle dimensioni specifiche dello schermo.  È anche possibile regolare l'altezza e la larghezza nel tag iFrame in base alla necessità, ma potrebbe essere anche necessario assicurarsi che il report si adatti all'area specifica di iFrame, quindi occorrerà configurare una modalità di visualizzazione appropriata durante la modifica del report.

La tabella seguente include indicazioni sulla modalità di visualizzazione e sul rispettivo aspetto in caso di incorporamento.

| Modalità di visualizzazione | Aspetto dopo l'incorporamento |
| --- | --- |
| ![](media/service-publish-to-web/publish_to_web6b.png) |La modalità **Adatta alla pagina** rispetterà l'altezza e la larghezza della pagina del report. Se si imposta la pagina sulle proporzioni dinamiche come ad esempio 16:9 o 4:3, il contenuto verrà ridimensionato in modo da adattarsi all'interno dell'iFrame fornito. Se si incorpora il report in un iFrame, usando la modalità **Adatta alla pagina** si può ottenere il **letterboxing**, in cui viene visualizzato uno sfondo grigio nelle aree dell'iFrame dopo il ridimensionamento del contenuto per adattarsi all'interno dell'iFrame. Per ridurre il letterboxing, impostare l'altezza e la larghezza dell'iFrame in modo appropriato. |
| ![](media/service-publish-to-web/publish_to_web6d.png) |La modalità **Dimensioni effettive** assicurerà il mantenimento delle dimensioni definite nella pagina del report. È quindi possibile che in iFrame siano presenti barre di scorrimento. Impostare l'altezza e la larghezza dell'iFrame per evitare le barre di scorrimento. |
| ![](media/service-publish-to-web/publish_to_web6c.png) |La modalità **Adatta in larghezza** assicura che i contenuti si adattino all'area orizzontale di iFrame. Verrà visualizzato comunque un bordo, ma i contenuti saranno ridimensionati in modo da usare tutto lo spazio orizzontale disponibile. |

## <a name="tips-and-tricks-for-iframe-height-and-width"></a>Suggerimenti e consigli per l'altezza e la larghezza dell'iFrame

Il codice di incorporamento ricevuto dopo l'uso della funzionalità Pubblica sul Web avrà un aspetto analogo al seguente:

![](media/service-publish-to-web/publish_to_web7.png)

È possibile modificare manualmente la larghezza e l'altezza, per assicurarsi di ottenere esattamente il risultato desiderato nella pagina in cui si incorpora il report.

Per ottenere un risultato ancora migliore, è possibile provare ad aggiungere 56 pixel all'altezza dell'iFrame adattandosi alle dimensioni correnti della barra inferiore. Se la pagina del report usa dimensioni dinamiche, la tabella seguente fornisce alcune dimensioni che è possibile usare per ottenere un adattamento senza letterboxing.

| Proporzioni | Dimensioni | Dimensione (larghezza x altezza) |
| --- | --- | --- |
| 16:9 |Piccole |640 x 416 px |
| 16:9 |Medie |800 x 506 px |
| 16:9 |Grandi |960 x 596 px |
| 4:3 |Piccole |640 x 536 px |
| 4:3 |Medie |800 x 656 px |
| 4:3 |Grandi |960 x 776 px |

## <a name="managing-embed-codes"></a>Gestione dei codici di incorporamento

Dopo avere creato un codice di incorporamento di **Pubblica sul Web** , è possibile gestire i codici creati dal menu **Impostazioni** del servizio Power BI. La gestione dei codici di incorporamento include la possibilità di rimuovere l'oggetto visivo o il report di destinazione per un codice, rendendo inutilizzabile il codice di incorporamento, o la possibilità di ottenere di nuovo il codice di incorporamento.

1. Per gestire i codici di incorporamento **Pubblica sul Web** , aprire l'opzione **Impostazioni** , con icona a forma di ingranaggio, e selezionare **Gestisci codici di incorporamento**.
   
   ![](media/service-publish-to-web/publish_to_web8.png)

2. Viene visualizzato l'elenco di codici di incorporamento creati, come illustrato nell'immagine seguente.
   
   ![](media/service-publish-to-web/publish_to_web9.png)

3. Per ogni codice di incorporamento di **Pubblica sul Web** disponibile nell'elenco è possibile recuperare il codice di incorporamento o eliminarlo e quindi disattivare eventuali collegamenti a tale report o oggetto visivo.
   
   ![](media/service-publish-to-web/publish_to_web10.png)

4. Se si seleziona **Elimina**, verrà richiesta una conferma dell'eliminazione del codice di incorporamento.
   
   ![](media/service-publish-to-web/publish_to_web11.png)

## <a name="updates-to-reports-and-data-refresh"></a>Aggiornamenti ai report e aggiornamenti dei dati

Dopo la creazione e la condivisione del codice di incorporamento di **Pubblica sul Web** , il report viene aggiornato con eventuali modifiche apportate. È tuttavia importante sapere che la visualizzazione dell'aggiornamento agli utenti potrebbe richiedere del tempo. Per rispecchiare gli aggiornamenti a un report o a un oggetto visivo nei codici di incorporamento di Pubblica sul Web potrebbe essere necessaria circa un'ora.

Quando si usa inizialmente **Pubblica sul Web** per ottenere codice di incorporamento, il collegamento del codice di incorporamento risulta immediatamente attivo e il codice può essere visualizzato da chiunque selezioni il collegamento.  Dopo l'azione Pubblica sul Web iniziale, la visualizzazione agli utenti degli aggiornamenti successivi ai report o agli oggetti visivi a cui fa riferimento il collegamento Pubblica sul Web può richiedere circa un'ora.

Per altre informazioni, vedere la sezione **Come funziona** più avanti in questo articolo. Se è necessario che gli aggiornamenti siano immediatamente disponibili, è possibile eliminare il codice di incorporamento e crearne uno nuovo.

## <a name="data-refresh"></a>Aggiornamento dei dati

Gli aggiornamenti dei dati vengono applicati automaticamente nel report o nell'oggetto visivo incorporato. La visualizzazione dei dati aggiornati dai codici di incorporamento può richiedere circa 1 ora. È possibile disabilitare l'aggiornamento automatico selezionando **Non aggiornare** nella pianificazione per il set di dati usato dal report.  

## <a name="custom-visuals"></a>Oggetti visivi personalizzati

Gli oggetti visivi personalizzati sono supportati in **Pubblica sul Web**. Quando si usa Pubblica sul Web, gli utenti con cui si condividono gli oggetti visivi pubblicati non devono abilitare gli oggetti visivi personalizzati per visualizzare i report.

## <a name="limitations"></a>Limitazioni

La funzionalità **Pubblica sul Web** è supportata per la maggior parte delle origini dati e dei report nel servizio Power BI, ma gli elementi seguenti non sono attualmente supportati o disponibili con Pubblica sul Web:

1. Report che usano la sicurezza a livello di riga
2. Report che usano Analysis Services in modalità tabulare ospitato in locale
3. Report condivisi con l'utente direttamente o con un pacchetto di contenuto aziendale
4. Report in un gruppo in cui non si è un membro a cui sono consentite modifiche
5. Gli oggetti visivi "R" non sono attualmente supportati nei report di Pubblica sul Web

## <a name="tenant-setting"></a>Impostazione del tenant

Gli amministratori di Power BI possono abilitare o disabilitare la funzionalità Pubblica sul Web. Possono anche limitare l'accesso a gruppi specifici. La possibilità di creare un codice di incorporamento dipende da questa impostazione.

|Funzionalità |Abilitata per l'intera organizzazione |Disabilitata per l'intera organizzazione |Gruppi di sicurezza specifici   |
|---------|---------|---------|---------|
|**Pubblica sul Web** nel menu **File** del report.|Abilitata per tutti|Non visibile per tutti|Visibile solo per utenti o gruppi autorizzati.|
|**Gestisci codici di incorporamento** in **Impostazioni**|Abilitata per tutti|Abilitata per tutti|Abilitata per tutti<br><br>Opzione * **Elimina** solo per utenti o gruppi autorizzati.<br>Opzione * **Ottieni i codici** abilitata per tutti.|
|**Incorpora codici** nel portale di amministrazione|Lo stato sarà uno dei seguenti:<br>* Attivo<br>* Non supportato<br>* Bloccato|Lo stato sarà **Disabilitato**|Lo stato sarà uno dei seguenti:<br>* Attivo<br>* Non supportato<br>* Bloccato<br><br>Se un utente non è autorizzato in base alla configurazione del tenant, lo stato sarà **Violazione**.|
|Report pubblicati esistenti|Tutti abilitati|Tutti disabilitati|Il rendering di tutti i report viene continuato per tutti.|

## <a name="understanding-the-embed-code-status-column"></a>Informazioni sulla colonna dello stato del codice di incorporamento

Quando si visualizza la pagina **Gestisci codici di incorporamento** per i codici di incorporamento di **Pubblica sul Web** viene fornita una colonna relativa allo stato. I codici di incorporamento sono attivi per impostazione predefinita, ma potrebbe essere visualizzato uno degli stati elencati di seguito.

| Stato | Descrizione |
| --- | --- |
| **Attivo** |Il report è disponibile per la visualizzazione e l'interazione da parte degli utenti Internet. |
| **Bloccato** |Il contenuto del report viola le [Condizioni d'uso di Power BI](https://powerbi.microsoft.com/terms-of-service). Viene bloccato da Microsoft. Se si ritiene che il contenuto sia stato bloccato per errore, contattare il supporto tecnico. |
| **Non supportato** |Il set di dati del report usa la sicurezza a livello di riga o un'altra configurazione non supportata. Vedere la sezione **Limitazioni** per un elenco completo. |
| **Violazione** |Il codice di incorporamento non rientra nei criteri definiti per il tenant. Questo problema si verifica in genere quando un codice di incorporamento viene creato e quindi viene modificata l'impostazione Pubblica sul Web del tenant in modo da escludere l'utente proprietario del codice di incorporamento. Se l'impostazione del tenant è disabilitata o se l'utente non è più autorizzato a creare codici di incorporamento, lo stato dei codici di incorporamento esistenti sarà **Violazione**. |

## <a name="how-to-report-a-concern-with-publish-to-web-content"></a>Come segnalare un problema relativo al contenuto di Pubblica sul Web

Per segnalare un problema relativo a contenuto di **Pubblica sul Web** incorporato in un sito Web o blog, usare l'icona **Flag** sulla barra inferiore, illustrata nell'immagine seguente. Verrà richiesto di inviare un messaggio di posta elettronica a Microsoft per illustrare il problema. Microsoft valuterà il contenuto in base alle Condizioni per l'utilizzo del servizio Power BI e intraprenderà le azioni appropriate.

Per segnalare un problema, selezionare l'icona **Flag** sulla barra inferiore del report di Pubblica sul Web visualizzato.

![](media/service-publish-to-web/publish_to_web12_ga.png)

## <a name="licensing-and-pricing"></a>Gestione delle licenze e prezzi

Per usare la funzionalità **Pubblica sul Web**, è necessario essere utenti di Microsoft Power BI. Gli utilizzatori del report, ovvero gli utenti che leggono o visualizzano il report, non devono necessariamente essere utenti di Power BI.

## <a name="how-it-works-technical-details"></a>Come funziona (dettagli tecnici)

Quando si crea un codice di incorporamento usando **Pubblica sul Web**, il report viene reso disponibile agli utenti su Internet. Essendo disponibile pubblicamente, è probabile che in futuro gli utenti condividano il report attraverso i social media. Quando gli utenti visualizzano il report, selezionando l'URL pubblico diretto o visualizzandolo incorporato in una pagina Web o un blog, Power BI memorizza nella cache la definizione del report e i risultati delle query necessarie per visualizzare il report. Questo approccio assicura che il report possa essere visualizzato da migliaia di utenti concorrenti, senza impatti sulle prestazioni.  

La cache è di lunga durata, quindi se si aggiorna la definizione del report, ad esempio se si cambia la modalità di visualizzazione, o si aggiornano i dati del report, la visualizzazione dei cambiamenti nella versione del report visualizzata dagli utenti può richiedere circa un'ora. È quindi consigliabile eseguire anticipatamente lo staging del lavoro e creare il codice di incorporamento di **Pubblica sul Web** solo quando si è soddisfatti delle impostazioni.

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)