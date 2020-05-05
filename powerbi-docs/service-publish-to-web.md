---
title: Pubblicare sul Web da Power BI
description: Con la funzionalità Pubblica sul Web di Power BI è possibile incorporare con facilità contenuti interattivi di Power BI in post di blog, siti Web, messaggi di posta elettronica o social media.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/25/2020
LocalizationGroup: Share your work
ms.openlocfilehash: 1a3d4c264e343382422cbe2a881b5fcedaa19e13
ms.sourcegitcommit: 20f15ee7a11162127e506b86d21e2fff821a4aee
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2020
ms.locfileid: "82585240"
---
# <a name="publish-to-web-from-power-bi"></a>Pubblicare sul Web da Power BI

Con l'opzione **Pubblica sul Web** di Power BI è possibile incorporare con facilità contenuti interattivi di Power BI in post di blog, siti Web, messaggi di posta elettronica o social media. È anche possibile modificare, aggiornare o interrompere facilmente la condivisione degli oggetti visivi pubblicati.

> [!WARNING]
> Quando si usa **Pubblica sul Web**, chiunque su Internet può visualizzare il report o l'oggetto visivo pubblicato. Per la visualizzazione non è necessaria alcuna autenticazione, nemmeno per i dati di livello dettagliato aggregati nei report. Prima di pubblicare un report, verificare che sia opportuno condividere pubblicamente i dati e le visualizzazioni. Evitare di pubblicare informazioni riservate o di proprietà. In caso di dubbio, prima di procedere alla pubblicazione verificare i criteri dell'organizzazione.

>[!Note]
>È possibile incorporare i contenuti in modo sicuro in un portale o un sito Web interno. Usare l'opzione [Incorpora](service-embed-secure.md) o [Incorpora in SharePoint Online](service-embed-report-spo.md). Queste opzioni assicurano che vengano applicate tutte le autorizzazioni e la sicurezza dei dati quando gli utenti visualizzano i dati interni.

## <a name="create-embed-codes-with-publish-to-web"></a>Creare codice di incorporamento con Pubblica sul Web

La funzionalità **Pubblica sul Web** è disponibile per i report che si possono modificare nelle aree di lavoro personali e di gruppo.  Non è disponibile per i report condivisi con l'utente o quelli in cui la protezione dei dati è basata sulla sicurezza a livello di riga. Vedere la sezione [**Limitazioni**](#limitations) più avanti per un elenco completo di casi in cui la funzionalità **Pubblica sul Web** non è supportata. Prima di usare **Pubblica sul Web** esaminare l'**avviso** riportato in precedenza in questo articolo

e guardare il breve video che segue per vedere come funziona questa funzionalità. Dopo, provare da soli seguendo i passaggi successivi.

<iframe width="560" height="315" src="https://www.youtube.com/embed/UF9QtqE7s4Y" frameborder="0" allowfullscreen></iframe>

La procedura seguente illustra come usare la funzionalità **Pubblica sul Web**.

1. Aprire un report modificabile in un'area di lavoro e selezionare **Altre opzioni (...)**   > **Incorpora** > **Pubblica sul Web (pubblico)** .

   ![Pubblica sul Web in Altre opzioni](media/service-publish-to-web/power-bi-more-options-publish-web.png)
   
2. Se l'amministratore di Power BI non ha autorizzato la creazione di codice di incorporamento, potrebbe essere necessario contattarlo.

   ![Contattare l'amministratore di Power BI](media/service-publish-to-web/publish_to_web_admin_prompt.png)
   
   Per informazioni su come trovare la persona che possa abilitare la funzionalità Pubblica sul Web all'interno dell'organizzazione, vedere [Trovare l'amministratore di Power BI](#find-your-power-bi-administrator) più avanti in questo articolo.

3. Esaminare il contenuto della finestra di dialogo e selezionare **Crea codice di incorporamento**.

   ![Verifica del codice di incorporamento in un sito Web pubblico](media/service-publish-to-web/publish_to_web2_ga.png)

4. Esaminare l'avviso, come indicato qui, e verificare che i dati si possano incorporare in un sito Web pubblico. In caso affermativo, selezionare **Pubblica**.

   ![Esaminare l'avviso](media/service-publish-to-web/publish_to_web3_ga.png)

5. Viene visualizzata una finestra di dialogo con un collegamento. Selezionare il collegamento per inviarlo tramite posta elettronica o copiare il codice HTML. È possibile incorporarlo nel codice, ad esempio un iFrame, o incollarlo direttamente in una pagina Web o un blog.

   ![Operazione riuscita: collegamento e codice HTML](media/service-publish-to-web/publish_to_web4.png)

6. Se in precedenza si è creato un codice di incorporamento per un report e si seleziona **Pubblica sul web**, le finestre di dialogo dei passaggi da 2 a 4 non vengono visualizzate. Viene invece visualizzata la finestra **Codice di incorporamento**:

   ![Finestra di dialogo Codice di incorporamento](media/service-publish-to-web/publish_to_web5.png)

   È possibile creare solo un codice di incorporamento per ogni report.


### <a name="tips-for-view-modes"></a>Suggerimenti per le modalità di visualizzazione

Quando si incorpora contenuto in un post di blog, è in genere necessario adattarlo alle dimensioni specifiche dello schermo.  È possibile modificare l'altezza e la larghezza nel tag iFrame in base alle esigenze. Tuttavia, è necessario assicurarsi che il report si adatti all'area dell'iFrame specificata, quindi è necessario anche impostare una modalità di visualizzazione appropriata quando si modifica il report.

La tabella seguente include indicazioni sulla modalità di visualizzazione e sul rispettivo aspetto in caso di incorporamento.

| Modalità di visualizzazione | Aspetto dopo l'incorporamento |
| --- | --- |
| ![PtW6b](media/service-publish-to-web/publish_to_web6b.png) |**Adatta alla pagina** rispetta l'altezza e la larghezza della pagina del report. Se si imposta la pagina su proporzioni *dinamiche*, ad esempio 16:9 o 4:3, il contenuto viene ridimensionato in modo da adattarsi all'interno dell'iFrame. Se si incorpora il report in un iFrame, usando la modalità **Adatta alla pagina** si può ottenere il *letterboxing*, in cui viene visualizzato uno sfondo grigio nelle aree dell'iFrame dopo che il contenuto viene ridimensionato in modo che si adatti all'interno dell'iFrame. Per ridurre il letterboxing, impostare l'altezza e la larghezza dell'iFrame in modo appropriato. |
| ![PtW6d](media/service-publish-to-web/publish_to_web6d.png) |La modalità **Dimensioni effettive** garantisce che vengano mantenute le dimensioni definite nella pagina del report. È quindi possibile che nell'iFrame siano visualizzate barre di scorrimento. Impostare l'altezza e la larghezza dell'iFrame per evitare le barre di scorrimento. |
| ![PtW6c](media/service-publish-to-web/publish_to_web6c.png) |La modalità **Adatta in larghezza** assicura che i contenuti occupino l'area orizzontale dell'iFrame. Viene comunque visualizzato un bordo, ma il contenuto viene ridimensionato in modo da usare tutto lo spazio orizzontale disponibile. |

### <a name="tips-for-iframe-height-and-width"></a>Suggerimenti per l'altezza e la larghezza dell'iFrame

Un codice di incorporamento di **Pubblica sul Web** è simile all'esempio seguente:

![PtW7](media/service-publish-to-web/publish_to_web7.png)
 
È possibile modificare manualmente la larghezza e l'altezza per assicurarsi di ottenere esattamente il risultato desiderato nella pagina in cui si incorpora il report.

Per perfezionare ulteriormente il risultato, provare ad aggiungere 56 pixel all'altezza dell'iFrame per adattarla alla dimensione corrente della barra inferiore. Se la pagina del report usa dimensioni dinamiche, la tabella seguente specifica alcune dimensioni che è possibile usare per adattare gli oggetti senza letterboxing.

| Proporzioni | Dimensione | Dimensione (larghezza x altezza) |
| --- | --- | --- |
| 16:9 |Piccola |640 x 416 px |
| 16:9 |Media |800 x 506 px |
| 16:9 |Grande |960 x 596 px |
| 4:3 |Piccola |640 x 536 px |
| 4:3 |Media |800 x 656 px |
| 4:3 |Grande |960 x 776 px |

## <a name="manage-embed-codes"></a>Gestisci codici di incorporamento

Dopo avere creato un codice di incorporamento di **Pubblica sul Web**, è possibile gestire i codici dal menu **Impostazioni** di Power BI. La gestione dei codici di incorporamento include la possibilità di rimuovere l'oggetto visivo o il report di destinazione per un codice, rendendo inutilizzabile il codice di incorporamento, o di ottenere il codice di incorporamento.

1. Per gestire i codici di incorporamento **Pubblica sul Web** , aprire l'opzione **Impostazioni** , con icona a forma di ingranaggio, e selezionare **Gestisci codici di incorporamento**.

   ![Gestisci codici di incorporamento](media/service-publish-to-web/publish_to_web8.png)

2. Vengono visualizzati i codici di incorporamento.

   ![PtW9](media/service-publish-to-web/publish_to_web9.png)

3. È possibile recuperare o eliminare un codice di incorporamento. L'eliminazione disabilita tutti i collegamenti a quel report o oggetto visivo.

   ![PtW10](media/service-publish-to-web/publish_to_web10.png)

4. Se si seleziona **Elimina**, viene richiesta una conferma.

   ![PtW11](media/service-publish-to-web/publish_to_web11.png)

## <a name="updates-to-reports-and-data-refresh"></a>Aggiornamenti ai report e aggiornamenti dei dati

Dopo la creazione e la condivisione del codice di incorporamento di **Pubblica sul Web**, il report viene aggiornato con eventuali modifiche apportate e il collegamento al codice di incorporamento è immediatamente attivo. Gli utenti che aprono il collegamento possono visualizzarlo. Dopo questa azione iniziale, tuttavia, gli aggiornamenti dei report o degli oggetti visivi possono richiedere da due a tre ore prima di diventare visibili agli utenti. Per altre informazioni, vedere la sezione [**Come funziona**](#howitworks) più avanti in questo articolo. 

### <a name="data-refresh"></a>Aggiornamento dei dati

Gli aggiornamenti dei dati vengono applicati automaticamente nel report o nell'oggetto visivo incorporato. La visualizzazione dei dati aggiornati dai codici di incorporamento può richiedere circa un'ora. Per disabilitare l'aggiornamento automatico, selezionare **Non aggiornare** nella pianificazione per il set di dati usato dal report.  

## <a name="power-bi-visuals"></a>Oggetti visivi di Power BI

Gli oggetti visivi di Power BI sono supportati in **Pubblica sul Web**. Quando si usa **Pubblica sul Web**, gli utenti con cui si condividono gli oggetti visivi pubblicati non hanno bisogno di abilitare gli oggetti visivi di Power BI per visualizzare i report.

## <a name="understanding-the-embed-code-status-column"></a>Informazioni sulla colonna dello stato del codice di incorporamento

>[!Note]
>È necessario esaminare periodicamente i codici di incorporamento pubblicati, rimuovendo quelli che non devono più essere disponibili pubblicamente.

La pagina **Gestisci codici di incorporamento** include una colonna di stato. Per impostazione predefinita, lo stato dei codici di incorporamento è **Attivo**, ma può essere anche uno degli stati elencati di seguito.

| Stato | Descrizione |
| --- | --- |
| **Attivo** |Il report è disponibile per la visualizzazione e l'interazione da parte degli utenti Internet. |
| **Bloccato** |Il contenuto del report viola le [Condizioni d'uso di Power BI](https://powerbi.microsoft.com/terms-of-service). Microsoft lo ha bloccato. Se si ritiene che il contenuto sia stato bloccato per errore, contattare il supporto tecnico. |
| **Non supportato** |Il set di dati del report usa la sicurezza a livello di riga o un'altra configurazione non supportata. Vedere la sezione [**Limitazioni**](#limitations) per un elenco completo. |
| **Violazione** |Il codice di incorporamento non rientra nei criteri definiti per il tenant. Questo stato si verifica in genere quando viene creato un codice di incorporamento e successivamente l'impostazione **Pubblica sul Web** del tenant viene modificata in modo da escludere l'utente proprietario del codice di incorporamento. Se l'impostazione del tenant è disabilitata o se l'utente non è più autorizzato a creare codici di incorporamento, lo stato dei codici di incorporamento esistenti sarà **Violazione**. Per informazioni dettagliate, vedere la sezione [Trovare l'amministratore di Power BI](#find-your-power-bi-administrator) in questo articolo. |

## <a name="report-a-concern-with-publish-to-web-content"></a>Segnalare un problema relativo al contenuto di Pubblica sul Web

Per segnalare un problema relativo a contenuto di **Pubblica sul Web** incorporato in un sito Web o un blog, selezionare l'icona **Flag** sulla barra inferiore del report **Pubblica sul Web**.

![PtW12](media/service-publish-to-web/publish_to_web12_ga.png)

Viene chiesto di inviare un messaggio di posta elettronica a Microsoft per illustrare il problema. Microsoft valuta il contenuto in base alle [Condizioni per l'utilizzo del servizio Power BI](https://powerbi.microsoft.com/terms-of-service) e prende le misure appropriate.

## <a name="licensing"></a>Gestione delle licenze

Per usare la funzionalità **Pubblica sul Web**, è necessario essere utenti di Microsoft Power BI. Per visualizzare i report non è invece necessario essere utenti di Power BI.

<a name="howitworks"></a>
## <a name="how-it-works-technical-details"></a>Come funziona (dettagli tecnici)

Quando si crea un codice di incorporamento usando **Pubblica sul Web**, il report viene reso disponibile agli utenti di Internet. Essendo disponibile pubblicamente, è probabile che in futuro gli utenti condividano il report attraverso i social media. Quando gli utenti visualizzano il report, selezionando l'URL pubblico diretto o visualizzandolo incorporato in una pagina Web o un blog, Power BI memorizza nella cache la definizione del report e i risultati delle query necessarie per visualizzare il report. La memorizzazione nella cache garantisce che migliaia di utenti possano visualizzare contemporaneamente il report senza influire sulle prestazioni.

La cache è di lunga durata, quindi se si aggiorna la definizione del report, ad esempio se si cambia la modalità di visualizzazione, o si aggiornano i dati del report, la visualizzazione dei cambiamenti nella versione del report visualizzata dagli utenti può richiedere circa un'ora. Pertanto, è consigliabile eseguire anticipatamente lo staging del lavoro e creare il codice di incorporamento di **Pubblica sul Web** solo quando si è soddisfatti delle impostazioni.

## <a name="find-your-power-bi-administrator"></a>Trovare l'amministratore di Power BI

Il portale di amministrazione di Power BI include impostazioni che consentono di specificare chi può pubblicare contenuti sul Web. Per modificare l'impostazione [Pubblica sul Web](service-admin-role.md) del tenant nel portale di amministrazione, è necessario collaborare con l'[amministratore di Power BI](service-admin-portal.md#publish-to-web) dell'organizzazione.

Per le organizzazioni più piccole o gli utenti singoli iscritti a Power BI, potrebbe non essere ancora presente un amministratore di Power BI. Seguire la nostra [procedura per l'acquisizione del ruolo di amministratore del tenant](https://docs.microsoft.com/azure/active-directory/users-groups-roles/domains-admin-takeover). Dopo essere stato individuato, l'amministratore di Power BI può abilitare la creazione dei codici incorporati.

Le organizzazioni avviate in genere hanno già un amministratore di Power BI. Le persone in possesso di uno qualsiasi dei ruoli seguenti possono agire come amministratori di Power BI:

- Amministratori di Office 365
- Amministratori di Azure Active Directory
- Utenti con il ruolo di amministratore del servizio Power BI in Azure Active Directory

È necessario [trovare una di queste persone](https://docs.microsoft.com/office365/admin/admin-overview/admin-overview#who-has-admin-permissions-in-my-business) all'interno dell'organizzazione e chiederle di aggiornare le [impostazioni di Pubblica sul Web per il tenant](service-admin-portal.md#publish-to-web) nel portale di amministrazione.

## <a name="limitations"></a>Limitazioni

La funzionalità **Pubblica sul Web** è supportata per la maggior parte delle origini dati e dei report nel servizio Power BI, tuttavia i tipi di report seguenti non sono attualmente supportati o disponibili con **Pubblica sul Web**:

- Report che usano la sicurezza a livello di riga.
- Report che usano le origini dati della connessione dinamica, inclusi Analysis Services in modalità tabulare ospitato in locale, Analysis Service in modalità multidimensionale e Azure Analysis Services.
- Report che usano un [set di dati condiviso](service-datasets-across-workspaces.md) archiviato in un'area di lavoro diversa dal report.
- [Set di dati certificati e condivisi](service-datasets-share.md).
- Report condivisi con l'utente direttamente o con un pacchetto di contenuto aziendale
- Report in un'area di lavoro in cui non si è un membro a cui sono consentite modifiche.
- Gli oggetti visivi "R" non sono attualmente supportati nei report di **Pubblica sul Web**.
- Esportazione di dati da oggetti visivi in un report pubblicato sul Web.
- Oggetti visivi ArcGIS Maps for Power BI.
- Report che contengono misure DAX a livello di report.
- Modelli di query di dati Single Sign-On.
- Proteggere le informazioni riservate o di proprietà.
- La funzionalità di autenticazione automatica fornita con l'opzione **Incorpora** non funziona con l'API JavaScript di Power BI. Per l'API JavaScript di Power BI, usare l'approccio all'incorporamento [dati di proprietà dell'utente](developer/embedded/embed-sample-for-your-organization.md).

## <a name="next-steps"></a>Passaggi successivi

- [Web part report di SharePoint Online](service-embed-report-spo.md) 

- [Incorporare report in un portale o un sito Web sicuro](service-embed-secure.md)

Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)
