---
title: Pubblicare sul Web da Power BI
description: La funzionalità Pubblica sul Web di Power BI consente di incorporare con facilità visualizzazioni interattive di Power BI online, ad esempio in post di blog, siti Web, via posta elettronica o social media, su qualsiasi dispositivo.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/16/2019
LocalizationGroup: Share your work
ms.openlocfilehash: 1b5dfc0b05595e96c9a297a5be3700e71cdbe229
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051576"
---
# <a name="publish-to-web-from-power-bi"></a>Pubblicare sul Web da Power BI

Con Power BI **pubblica sul web** opzione, è possibile incorporare con facilità visualizzazioni interattive di Power BI online, ad esempio in post di blog, siti Web, tramite posta elettronica o social media, da qualsiasi dispositivo. È anche possibile modificare, aggiornare o annullare facilmente la condivisione degli oggetti visivi pubblicati.

> [!WARNING]
> Quando si usa **pubblica sul web**, chiunque in Internet può visualizzare il report pubblicato o l'oggetto visivo. Ciò non richiede alcuna autenticazione e include la visualizzazione di dati a livello di dettaglio dei report aggregati. Prima di pubblicare un report, assicurarsi che sia accettabile per consentirti di condividere pubblicamente i dati e le visualizzazioni. Non pubblicare informazioni riservate o di proprietà. In caso di dubbio, prima di procedere alla pubblicazione verificare i criteri dell'organizzazione.

>[!Note]
>Per incorporare il contenuto in modo sicuro in un portale o un sito Web interno, usare le opzioni [Incorpora](service-embed-secure.md) oppure [Incorpora in SharePoint Online](service-embed-report-spo.md). Ciò assicura che vengano applicate tutte le autorizzazioni e la sicurezza dei dati quando gli utenti visualizzano i dati interni.

## <a name="how-to-use-publish-to-web"></a>Come usare la funzionalità Pubblica sul Web

**Pubblica sul web** è disponibile per i report nelle aree di lavoro personale o di gruppo è possibile modificare.  Non è disponibile per i report condivisi con l'utente oppure quelli affidarsi alla sicurezza a livello di riga per proteggere i dati. Vedere le [ **limitazioni** ](#limitations) sezione di seguito per un elenco completo dei case in cui **pubblica sul web** non è supportato. Rivedere le **avviso** più indietro in questo articolo prima di usare **pubblica sul web**.

Quanto segue *breve video* viene illustrato il funzionamento di questa funzionalità. Quindi, è possibile provarlo autonomamente nei passaggi successivi

<iframe width="560" height="315" src="https://www.youtube.com/embed/UF9QtqE7s4Y" frameborder="0" allowfullscreen></iframe>

La procedura seguente illustra come usare la funzionalità **Pubblica sul Web**.

1. Aprire un report nell'area di lavoro che è possibile modificare e selezionare **File > Pubblica sul web**.

   ![PtW1](media/service-publish-to-web/publish_to_web1.png)

2. Esaminare la finestra di dialogo del contenuto e seleziona **crea codice di incorporamento**.

   ![PtW2](media/service-publish-to-web/publish_to_web2_ga.png)

3. Esaminare l'avviso, come illustrato di seguito e verificare che i dati sono possono essere incorporati in un sito Web pubblico. Se è disponibile, selezionare **pubblica**.

   ![PtW3](media/service-publish-to-web/publish_to_web3_ga.png)

4. Viene visualizzata una finestra di dialogo con un collegamento. È possibile inviare questo collegamento tramite posta elettronica, incorporarlo nel codice, ad esempio un iFrame o incollare il codice direttamente in una pagina web o blog.

   ![PtW4](media/service-publish-to-web/publish_to_web4.png)

5. Se un codice di incorporamento per un report creato in precedenza e si seleziona **pubblica sul web**, non saranno visualizzati le finestre di dialogo nei passaggi da 2 a 4. Al contrario, il **il codice di incorporamento** viene visualizzata la finestra:

   ![PtW5](media/service-publish-to-web/publish_to_web5.png)

   È possibile creare solo un codice di incorporamento per ogni report.


## <a name="tips-and-tricks-for-view-modes"></a>Suggerimenti e consigli per le modalità di visualizzazione

Quando si incorpora contenuto all'interno di un post di blog, in genere necessario adattarlo alle dimensioni schermata specifica.  È possibile modificare l'altezza e la larghezza nel tag iFrame in base alle esigenze. Tuttavia, è necessario assicurarsi che il report si adatti all'interno dell'area specificata iFrame, pertanto è necessario anche impostare una modalità di visualizzazione appropriata durante la modifica del report.

La tabella seguente include indicazioni sulla modalità di visualizzazione e sul rispettivo aspetto in caso di incorporamento.

| Modalità di visualizzazione | Aspetto dopo l'incorporamento |
| --- | --- |
| ![PtW6b](media/service-publish-to-web/publish_to_web6b.png) |**Adatta alla pagina** rispetterà l'altezza della pagina e la larghezza del report. Se si imposta la pagina ai rapporti 'Dynamic', ad esempio 16:9 o 4:3 il contenuto verrà ridimensionato per adattarsi all'interno dell'iFrame. Se si incorpora in un iFrame, usando **adatta alla pagina** può comportare **letterboxing**, in cui uno sfondo grigio viene visualizzato nelle aree di iFrame dopo il contenuto come ridimensionati per adattarsi all'interno dell'iFrame. Per ridurre il letterboxing, impostare l'altezza e la larghezza dell'iFrame in modo appropriato. |
| ![PtW6d](media/service-publish-to-web/publish_to_web6d.png) |**Dimensioni effettive** garantisce il mantenimento delle dimensioni definite nella pagina del report. Ciò può comportare le barre di scorrimento di iFrame. Impostare l'iFrame altezza e larghezza per evitare le barre di scorrimento. |
| ![PtW6c](media/service-publish-to-web/publish_to_web6c.png) |**Adatta in larghezza** assicura il contenuto si adatta all'area orizzontale di iFrame. Viene visualizzato ancora un bordo, ma il contenuto viene per utilizzare tutto lo spazio orizzontale disponibile. |

## <a name="tips-and-tricks-for-iframe-height-and-width"></a>Suggerimenti e consigli per l'altezza e la larghezza dell'iFrame

Oggetto **pubblica sul web** incorporare codice è il seguente:

![PtW7](media/service-publish-to-web/publish_to_web7.png)
 
È possibile modificare la larghezza e altezza manualmente per assicurarsi che sia esattamente come desiderato per adattare nella pagina in cui si incorpora il report.

Per ottenere più propriamente adatto, è possibile aggiungere 56 pixel all'altezza dell'iFrame in base alla dimensione corrente della barra inferiore. Se la pagina del report usa dimensioni dinamiche, la tabella seguente fornisce alcune dimensioni che è possibile usare per ottenere un adattamento senza letterboxing.

| Proporzioni | Dimensioni | Dimensione (larghezza x altezza) |
| --- | --- | --- |
| 16:9 |Piccole |640 x 416 px |
| 16:9 |Medie |800 x 506 px |
| 16:9 |Grandi |960 x 596 px |
| 4:3 |Piccole |640 x 536 px |
| 4:3 |Medie |800 x 656 px |
| 4:3 |Grandi |960 x 776 px |

## <a name="manage-embed-codes"></a>Gestisci codici di incorporamento

Dopo aver creato un **pubblica sul web** incorporare il codice, è possibile gestire i tuoi codici dalle **impostazioni** menu in Power BI. La gestione dei codici di incorporamento include la possibilità di rimuovere la destinazione visual o il report per il codice (rendendo inutilizzabile il codice di incorporamento), o per ottenere il codice di incorporamento.

1. Per gestire i codici di incorporamento **Pubblica sul Web** , aprire l'opzione **Impostazioni** , con icona a forma di ingranaggio, e selezionare **Gestisci codici di incorporamento**.

   ![PtW8](media/service-publish-to-web/publish_to_web8.png)

2. Vengono visualizzati i codici di incorporamento.

   ![PtW9](media/service-publish-to-web/publish_to_web9.png)

3. È possibile recuperare o eliminare un codice di incorporamento. L'eliminazione Disabilita tutti i collegamenti al report o oggetto visivo.

   ![PtW10](media/service-publish-to-web/publish_to_web10.png)

4. Se si seleziona **eliminare**, viene chiesta una conferma.

   ![PtW11](media/service-publish-to-web/publish_to_web11.png)

## <a name="updates-to-reports-and-data-refresh"></a>Aggiornamenti ai report e aggiornamenti dei dati

Dopo aver creato il **pubblica sul web** codice di incorporamento e la condivisione, il report viene aggiornata con tutte le modifiche apportate e il collegamento di codice di incorporamento risulta immediatamente attivo e gli utenti che aprono il collegamento può visualizzarlo. Dopo questa azione iniziale, tuttavia, gli aggiornamenti per gli oggetti visivi o report possono richiedere circa un'ora prima di diventare visibili agli utenti. Se è necessario che gli aggiornamenti siano immediatamente disponibili, è possibile eliminare il codice di incorporamento e crearne uno nuovo. Per altre informazioni, vedere la [ **funzionamento** ](#howitworks) sezione più avanti in questo articolo. 

## <a name="data-refresh"></a>Aggiornamento dei dati

Gli aggiornamenti dei dati vengono applicati automaticamente nel report o nell'oggetto visivo incorporato. La visualizzazione dei dati aggiornati dai codici di incorporamento può richiedere circa 1 ora. Per disabilitare l'aggiornamento automatico, è possibile selezionare **non aggiornare** in base alla pianificazione per il set di dati nel report viene utilizzata.  

## <a name="custom-visuals"></a>Oggetti visivi personalizzati

Gli oggetti visivi personalizzati sono supportati in **Pubblica sul Web**. Quando si usa **pubblica sul web**, gli utenti con cui si condivide l'oggetto visivo pubblicato non sono necessario abilitare oggetti visivi personalizzati visualizzare il report.

## <a name="limitations"></a>Limitazioni

**Pubblica sul web** è supportata per la maggior parte dei dati di origini e report nel servizio Power BI, tuttavia, di seguito vengono **non sono attualmente supportati o disponibili** con **pubblica sul web** :

- Report che usano la sicurezza a livello di riga
- Report che usano le origini dati della connessione dinamica, inclusi Analysis Services in modalità tabulare ospitato in locale, Analysis Service in modalità multidimensionale e Azure Analysis Services.
- Report condivisi con l'utente direttamente o con un pacchetto di contenuto aziendale
- Report in un gruppo in cui non si è un membro a cui sono consentite modifiche
- Gli oggetti visivi "R" non sono attualmente supportati **pubblica sul web** i report.
- Esportazione dei dati da oggetti visivi in un report, che è stato pubblicato sul Web.
- ArcGIS Maps for Power BI gli oggetti visivi.
- Report che contengono le misure DAX a livello di report.
- Dati del servizio Single sign-on di eseguire query su modelli.
- [Proteggere informazioni riservate o proprietarie](#publish-to-web-from-power-bi).
- La funzionalità di autenticazione automatica fornita con l'opzione **Incorpora** non funziona con l'API JavaScript di Power BI. Per l'API JavaScript di Power BI, usare l'approccio all'incorporamento [dati di proprietà dell'utente](developer/embed-sample-for-your-organization.md). Altre informazioni sull'approccio [dati di proprietà dell'utente](developer/embed-sample-for-your-organization.md).

## <a name="tenant-setting"></a>Impostazione del tenant

Gli amministratori di Power BI possono abilitare o disabilitare il **pubblica sul web** funzionalità. È anche possibile limitare l'accesso a gruppi specifici, che possono influire sulla possibilità di creare un codice di incorporamento.

|Feature |Abilitata per l'intera organizzazione |Disabilitata per l'intera organizzazione |Gruppi di sicurezza specifici   |
|---------|---------|---------|---------|
|**Pubblica sul web** nell'area del rapporto **File** menu|Abilitata per tutti|Non visibile per tutti|Visibile solo per utenti o gruppi autorizzati.|
|**Gestisci codici di incorporamento** in **Impostazioni**|Abilitata per tutti|Abilitata per tutti|Abilitato per tutti.<br><br>Opzione * **Elimina** solo per utenti o gruppi autorizzati.<br>Opzione * **Ottieni i codici** abilitata per tutti.|
|**Incorpora codici** nel portale di amministrazione|Lo stato sarà uno dei seguenti:<br>* Attivo<br>* Non supportato<br>* Bloccato|Lo stato sarà **Disabilitato**|Lo stato sarà uno dei seguenti:<br>* Attivo<br>* Non supportato<br>* Bloccato<br><br>Se un utente non è autorizzato in base alla configurazione del tenant, lo stato sarà **Violazione**.|
|Report pubblicati esistenti|Tutti abilitati|Tutti disabilitati|Il rendering di tutti i report viene continuato per tutti.|

## <a name="understanding-the-embed-code-status-column"></a>Informazioni sulla colonna dello stato del codice di incorporamento

Il **Gestisci codici di incorporamento** pagina include una colonna di stato. Per impostazione predefinita, i codici di incorporamento vengono **Active**, ma potrebbe anche essere uno degli stati elencati di seguito.

| Stato | Descrizione |
| --- | --- |
| **Attivo** |Il report è disponibile per la visualizzazione e l'interazione da parte degli utenti Internet. |
| **Bloccato** |Il contenuto del report viola le [del servizio di Power BI termini](https://powerbi.microsoft.com/terms-of-service). Microsoft ha bloccato lo. Se si ritiene che il contenuto sia stato bloccato per errore, contattare il supporto tecnico. |
| **Non supportato** |Il set di dati del report usa la sicurezza a livello di riga o un'altra configurazione non supportata. Vedere le [ **limitazioni** ](#limitations) sezione per un elenco completo. |
| **Violazione** |Il codice di incorporamento non rientra i criteri definiti per il tenant. Ciò si verifica in genere quando è stato creato un codice di incorporamento e quindi il **pubblica sul web** impostazione del tenant è stato modificato per escludere l'utente proprietario del codice di incorporamento. Se l'impostazione del tenant sia disabilitato oppure che l'utente non è autorizzato a creare codici di incorporamento, Mostra i codici di incorporamento esistenti un' **violazione** dello stato. |

## <a name="how-to-report-a-concern-with-publish-to-web-content"></a>Come segnalare un problema relativo al contenuto di Pubblica sul Web

Per segnalare un problema relativo al **pubblica sul web** contenuto incorporato in un sito Web o blog, usare il **Flag** icona nella barra inferiore, come illustrato nell'immagine seguente. Verrà chiesto di inviare un messaggio di posta elettronica a Microsoft che spiega il problema. Microsoft esaminerà il contenuto si basa sulle condizioni del servizio Power BI e intraprendere l'azione appropriata.

Per segnalare un problema, selezionare la **flag** icona nella barra inferiore del **pubblica sul web** report viene visualizzato.

![PtW12](media/service-publish-to-web/publish_to_web12_ga.png)

## <a name="licensing-and-pricing"></a>Gestione delle licenze e prezzi

Per usare la funzionalità **Pubblica sul Web**, è necessario essere utenti di Microsoft Power BI. Visualizzatori del report non sono necessario essere utenti di Power BI.

<a name="howitworks"></a>
## <a name="how-it-works-technical-details"></a>Come funziona (dettagli tecnici)

Quando si crea un codice di incorporamento usando **pubblica sul web**, il report viene reso disponibile agli utenti di Internet. È disponibile pubblicamente, pertanto è possibile prevedere gli utenti condividano il report attraverso i social media in futuro. Quando gli utenti visualizzano il report, selezionando l'URL pubblico diretto o visualizzandolo incorporato in una pagina Web o un blog, Power BI memorizza nella cache la definizione del report e i risultati delle query necessarie per visualizzare il report. Ciò garantisce che migliaia di utenti simultanei possa visualizzare il report senza alcun impatto sulle prestazioni.

La cache è di lunga durata, in modo che se si aggiorna la definizione del report (ad esempio, se si modifica la modalità di visualizzazione) o aggiornano i dati del report, può richiedere circa un'ora prima che le modifiche si riflettono nella versione del report visualizzato dagli utenti. È quindi consigliabile eseguire anticipatamente lo staging del lavoro e creare il codice di incorporamento di **Pubblica sul Web** solo quando si è soddisfatti delle impostazioni.

## <a name="next-steps"></a>Passaggi successivi

- [Web part report di SharePoint Online](service-embed-report-spo.md) 

- [Incorporare report in un portale o un sito Web sicuro](service-embed-secure.md)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)
