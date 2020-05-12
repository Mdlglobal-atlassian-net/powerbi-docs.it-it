---
title: Oggetti visivi di Power BI certificati
description: Requisiti e processo di invio di un oggetto visivo personalizzato per la certificazione ed elenco di oggetti visivi di Power BI certificati.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 03/08/2020
ms.openlocfilehash: b759d19046ddb375646743a50025689ab9a566c0
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82613535"
---
# <a name="get-a-power-bi-visual-certified"></a>Ottenere un oggetto visivo Power BI certificato

Gli oggetti visivi di Power BI certificati sono oggetti visivi di Power BI disponibili in [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?page=1&product=power-bi-visuals) che soddisfano i [requisiti di codice](#certification-requirements) del team di Microsoft Power BI. Questi oggetti visivi vengono testati per verificare che non accedano a servizi o risorse esterni e che seguano criteri e linee guida di scrittura del codice protetti.

Dopo la certificazione, un oggetto visivo di Power BI offre più funzionalità. È ad esempio possibile [esportarlo in PowerPoint](../../consumer/end-user-powerpoint.md) o visualizzare l'oggetto visivo nei messaggi di posta elettronica ricevuti quando un utente [sottoscrive pagine di report](../../consumer/end-user-subscribe.md).

Il processo di certificazione è facoltativo. Gli oggetti visivi di Power BI non certificati, non sono necessariamente oggetti visivi di Power BI non sicuri. Alcuni oggetti visivi di Power BI non vengono certificati perché non sono conformi a uno o più [requisiti di certificazione](power-bi-custom-visuals-certified.md#certification-requirements), ad esempio un oggetto visivo mappa di Power BI che si connette a un servizio esterno o un oggetto visivo di Power BI che usa librerie commerciali.

> [!NOTE]
> Microsoft non è l'autore di oggetti visivi di Power BI di terze parti. Per verificare la funzionalità degli oggetti visivi di terze parti, contattare direttamente l'autore.

## <a name="certification-requirements"></a>Requisiti di certificazione

Per ottenere la [certificazione](#get-a-power-bi-visual-certified), l'oggetto visivo di Power BI deve soddisfare i requisiti elencati in questa sezione. 

### <a name="general-requirements"></a>Requisiti generali

L'oggetto visivo di Power BI deve essere approvato dal Centro per i partner. È consigliabile che l'oggetto visivo di Power BI sia già disponibile in [AppSource](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals). Per informazioni su come pubblicare un oggetto visivo di Power BI in AppSource, vedere [Pubblicare oggetti visivi di Power BI nel Centro per i partner](office-store.md).

Prima di inviare l'oggetto visivo di Power BI da certificare, verificare che sia conforme alle [linee guida per gli oggetti visivi di Power BI](guidelines-powerbi-visuals.md).

Quando si invia l'oggetto visivo di Power BI, assicurarsi che il pacchetto compilato corrisponda esattamente al pacchetto inviato.

### <a name="code-repository-requirements"></a>Requisiti del repository di codice

Sebbene il codice non debba essere condiviso pubblicamente in GitHub, è necessario che il repository di codice sia disponibile per essere rivisto dal team di Power BI. A tal proposito è consigliabile mettere a disposizione il codice sorgente JavaScript o TypeScript in GitHub.

Il repository deve contenere quanto segue:
* Codice per un solo oggetto visivo di Power BI. Non può contenere codice per più oggetti visivi di Power BI o codice non correlato.
* Un ramo denominato **certificazione** (in minuscolo). Il codice sorgente in questo ramo deve corrispondere al pacchetto inviato. Questo codice può essere aggiornato solo durante il processo di invio successivo, se si invia nuovamente l'oggetto visivo di Power BI.

Se l'oggetto visivo di Power BI usa pacchetti npm privati o moduli secondari GIT, è necessario specificare l'accesso ai repository aggiuntivi che contengono questo codice.

Per informazioni su come visualizzare un repository di oggetti visivi di Power BI, vedere il repository GitHub per il [grafico a barre di esempio degli oggetti visivi di Power BI](https://github.com/microsoft/PowerBI-visuals-sampleBarChart).

### <a name="file-requirements"></a>Requisiti dei file

Usare la versione più recente dell'API per scrivere l'oggetto visivo di Power BI.

Il repository deve includere i file seguenti:
* **.gitignore**: aggiungere `node_modules`, `.tmp` e `dist` a questo file. Il codice non può includere le cartelle *node_modules*, *.tmp* o *dist*.
* **capabilities.json**: se si invia una versione più recente dell'oggetto visivo di Power BI con le modifiche apportate alle proprietà in questo file, assicurarsi di non interrompere i report per gli utenti esistenti.
* **pbiviz.json** 
* **package.json**. È necessario che nell'oggetto visivo siano installati i pacchetti seguenti:
   * ["tslint"](https://www.npmjs.com/package/tslint): versione 5.18.0 o successiva
   * ["typescript"](https://www.npmjs.com/package/typescript): versione 3.0.0 o successiva
   * ["tslint-microsoftcontrib"](https://www.npmjs.com/package/tslint-microsoft-contrib): versione 6.2.0 o successiva
   * Il file deve contenere un comando per l'esecuzione del linter: `"lint": "tslint -c tslint.json -p tsconfig.json"`
* **package-lock.json**
* **tsconfig.json**

### <a name="command-requirements"></a>Requisiti dei comandi

Verificare che i comandi seguenti non restituiscano errori.

* `npm install`
* `pbiviz package`
* `npm audit`: non deve restituire avvisi con livello elevato o moderato.
* [TSlint da Microsoft](https://www.npmjs.com/package/tslint-microsoft-contrib) con [la configurazione richiesta](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/tslint.json). Questo comando non deve restituire alcun errore lint.

### <a name="compiling-requirements"></a>Requisiti di compilazione

Usare la versione più recente di [powerbi-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools) per scrivere l'oggetto visivo di Power BI.

È necessario compilare l'oggetto visivo di Power BI con `pbiviz package`. Se si usano script di compilazione personalizzati, specificare un comando di compilazione `npm run package` personalizzato.

### <a name="source-code-requirements"></a>Requisiti del codice sorgente

Verificare di attenersi all'elenco dei criteri per la [certificazione aggiuntiva degli oggetti visivi di Power BI](https://docs.microsoft.com/legal/marketplace/certification-policies#1200-power-bi-visuals-additional-certification). Se l'invio non rispetta queste linee guida, il Centro per i partner invierà un messaggio di posta elettronica di rifiuto includendo i numeri dei criteri elencati in questo collegamento.

Seguire i requisiti di codice elencati di seguito per assicurarsi che il codice sia in linea con i criteri di certificazione di Power BI.  

**Obbligatorio**
* Usare solo componenti OSS pubblicabili, ad esempio librerie JavaScript o TypeScript pubbliche.
* Il codice deve supportare l'[API per gli eventi di rendering](event-service.md).
* Assicurarsi che il modello DOM venga modificato in modo sicuro. Usare la purificazione per i dati o l'input dell'utente, prima di aggiungerli al modello DOM.
* Usare il [report di esempio](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix) come set di dati di test.

**Non consentito**
* Accesso a servizi o risorse esterni. Nessuna richiesta HTTP/S o WebSocket, ad esempio, può uscire da Power BI verso alcun servizio.
* Uso di `innerHTML` o `D3.html(user data or user input)`.
* Errori o eccezioni JavaScript nella console del browser per i dati di input.
* Codice arbitrario o dinamico, ad esempio `eval()`, uso non sicuro di `settimeout()`, `requestAnimationFrame()`, `setinterval(user input function)` e dati o input dell'utente.
* File o progetti JavaScript minimizzati.

## <a name="submitting-a-power-bi-visual-for-certification"></a>Invio di un oggetto visivo di Power BI per la certificazione

È possibile richiedere la certificazione dell'oggetto visivo di Power BI da parte del team di Power BI tramite il Centro per i partner.

>[!TIP]
>Il processo di certificazione di Power BI può richiedere tempo. Se si sta creando un nuovo oggetto visivo di Power BI, è consigliabile pubblicarlo attraverso il Centro per i partner prima di richiedere la certificazione di Power BI. In questo modo si garantisce che la pubblicazione dell'oggetto visivo non subisca ritardi.

Per richiedere la certificazione di Power BI:

1. Accedere al Centro per i partner.
2. Nella **pagina Panoramica** scegliere l'oggetto visivo di Power BI e passare alla pagina **Configurazione prodotto**.
3. Selezionare la casella di controllo **Richiedere la certificazione di Power BI**.
4. Nella casella di testo **Note per la certificazione** della pagina **Rivedi e pubblica** indicare un collegamento al codice sorgente e le credenziali necessarie per accedervi.

### <a name="private-repository-submission-process"></a>Processo di invio di un repository privato

Se si usa un repository privato, ad esempio GitHub, per inviare l'oggetto visivo di Power BI per la certificazione, seguire le istruzioni riportate in questa sezione.
1. Creare un nuovo account per il team di convalida.
2. Configurare l'[autenticazione a due fattori](https://help.github.com/github/authenticating-to-github/securing-your-account-with-two-factor-authentication-2fa) per l'account.
3. [Generare un nuovo set di codici di recupero](https://help.github.com/github/authenticating-to-github/configuring-two-factor-authentication-recovery-methods#generating-a-new-set-of-recovery-codes).
4. Quando si invia l'oggetto visivo di Power BI, specificare quanto segue:
    * Collegamento al repository
    * Credenziali di accesso (inclusa una password)
    * Codici di recupero
    * Autorizzazioni di sola lettura per l'account ([pbicvsupport](https://github.com/pbicvsupport))

## <a name="certified-power-bi-visual-badges"></a>Badge degli oggetti visivi di Power BI certificati

Quando un oggetto visivo di Power BI viene certificato, riceve un badge designato che ne indica la certificazione.

### <a name="certified-power-bi-visuals-in-appsource"></a>Oggetti visivi di Power BI certificati in AppSource

* Quando si esegue la ricerca online di [oggetti visivi di Power BI in AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals), un piccolo badge giallo sulla scheda dell'oggetto visivo indica che si tratta di un oggetto visivo di Power BI certificato.

    ![Oggetto visivo di Power BI certificato in AppSource](media/power-bi-custom-visuals-certified/certified-visual-yellow-small.png)

* Dopo aver fatto clic sulla scheda dell'oggetto visivo di Power BI in AppSource, un badge giallo denominato *PBI Certified* indica che l'oggetto visivo di Power BI è certificato.

    ![Oggetto visivo di Power BI certificato nella pagina dell'app](media/power-bi-custom-visuals-certified/certified-visual-yellow-big.png)

### <a name="certified-power-bi-visuals-in-the-power-bi-interface"></a>Oggetti visivi di Power BI certificati nell'interfaccia di Power BI

* Quando si importa un oggetto visivo di Power BI dall'interno di Power BI (Desktop o servizio), un badge blu indica che l'oggetto visivo di Power BI è certificato.

    ![Oggetto visivo di Power BI certificato nell'interfaccia di Power BI](media/power-bi-custom-visuals-certified/certified-visual-blue.png)

* È possibile visualizzare solo gli oggetti visivi di Power BI certificati selezionando l'opzione di filtro *Certificati da Power BI*.

## <a name="publication-timeline"></a>Tempistiche per la pubblicazione

La distribuzione in AppSource è un processo che può richiedere del tempo. Al termine del processo, l'oggetto visivo di Power BI sarà disponibile per il download da AppSource.

### <a name="when-will-users-be-able-to-download-my-visual"></a>Quando potranno scaricare l'oggetto visivo gli utenti?

* Se è il primo invio di un oggetto visivo di Power BI, gli utenti potranno scaricarlo poche ore dopo la ricezione di un messaggio di posta elettronica da AppSource.

* Nel caso dell'invio di un aggiornamento per un oggetto visivo di Power BI esistente, gli utenti potranno scaricarlo entro un mese dall'invio.

    >[!NOTE]
    > Il campo della *versione* in AppSource verrà aggiornato con il giorno di approvazione dell'oggetto visivo di Power BI da AppSource, circa una settimana dopo l'invio. Gli utenti potranno scaricare l'oggetto visivo aggiornato, ma le funzionalità aggiornate non verranno applicate. Le nuove funzionalità dell'oggetto visivo verranno applicate ai report dell'utente dopo circa un mese. 

### <a name="when-will-my-power-bi-visual-display-a-certification-badge"></a>Quando verrà visualizzato un badge di certificazione per l'oggetto visivo di Power BI inviato?

* Nel caso del primo invio di un oggetto visivo di Power BI, il badge di certificazione verrà visualizzato entro un giorno dalla ricezione del messaggio di posta elettronica di approvazione da AppSource.

* Se si richiede la certificazione per un oggetto visivo di Power BI esistente, il badge di certificazione sarà visibile entro un mese dall'invio.

## <a name="next-steps"></a>Passaggi successivi

* Gli sviluppatori Web interessati a creare oggetti visivi Power BI personalizzati e ad aggiungerli a  [Microsoft AppSource](https://appsource.microsoft.com) possono iniziare con l'esercitazione  [Sviluppo di un oggetto visivo di Power BI](custom-visual-develop-tutorial.md).

* Per altre informazioni sugli oggetti visivi, vedere le [domande frequenti sugli oggetti visivi certificati](power-bi-custom-visuals-faq.md#certified-power-bi-visuals).

* [Sviluppo di un oggetto visivo di Power BI](custom-visual-develop-tutorial.md)

* [Playlist degli oggetti visivi di Power BI di Microsoft su YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)

* [Oggetti visivi in Power BI](power-bi-custom-visuals.md)

* [Pubblicare oggetti visivi di Power BI in Microsoft AppSource](office-store.md)

* Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)