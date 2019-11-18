---
title: Domande frequenti sugli oggetti visivi di Power BI
description: Esplorare un elenco di domande frequenti e risposte relative agli oggetti visivi di Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.custom: ''
ms.date: 12/17/2018
ms.openlocfilehash: 0b5677e7f3acab464f8d9e4c293ed1df9d0bdd0f
ms.sourcegitcommit: 08b73af260ded51daaa6749338cb85db2eab587f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2019
ms.locfileid: "74102158"
---
# <a name="frequently-asked-questions-about-power-bi-visuals"></a>Domande frequenti sugli oggetti visivi di Power BI

## <a name="organizational-visuals"></a>Oggetti visivi organizzazione

Il portale di amministrazione consente di gestire gli oggetti visivi di Power BI per l'organizzazione.

### <a name="how-can-the-admin-manage-the-organizational-power-bi-visuals"></a>In quale modo l'amministratore può gestire gli oggetti visivi di Power BI dell'organizzazione?

Nella scheda "Oggetti visivi dell'organizzazione" del portale di amministrazione l'amministratore può visualizzare e [gestire tutti gli oggetti visivi di Power BI dell'organizzazione](../service-admin-portal.md#organizational-visuals): aggiungere, disabilitare, abilitare ed eliminare.
Non è più necessario condividere questi oggetti visivi usando messaggi di posta elettronica o cartelle condivise. Dopo la distribuzione nel repository dell'organizzazione, gli utenti dell'organizzazione possono facilmente trovarli e importarli nei loro report direttamente da Power BI Desktop o dal servizio Power BI. Gli oggetti visivi dell'organizzazione sono disponibili dall'archivio predefinito (nella versione desktop e nel servizio) nella scheda *ORGANIZZAZIONE PERSONALE*. Quando l'amministratore carica una nuova versione di un oggetto visivo personalizzato dell'organizzazione, chiunque nell'organizzazione ottiene la stessa versione aggiornata. Gli autori di report non devono eliminare l'oggetto visivo nei report per ottenere la nuova versione di questi oggetti visivi, perché tutti i report che usano questi oggetti visivi vengono aggiornati automaticamente. Il meccanismo di aggiornamento è simile per gli oggetti visivi del marketplace.

### <a name="if-an-admin-uploads-a-custom-visual-from-the-public-marketplace-to-the-organization-store-is-it-automatically-updated-once-a-vendor-updates-the-visual-in-the-public-marketplace"></a>Se un amministratore carica un oggetto visivo personalizzato dal marketplace pubblico nell'archivio dell'organizzazione, viene aggiornato automaticamente quando un fornitore aggiorna l'oggetto visivo nel marketplace pubblico?

No, non è disponibile l'aggiornamento automatico dal marketplace pubblico.
È responsabilità dell'amministratore aggiornare la versione degli oggetti visivi dell'organizzazione.

### <a name="is-there-a-way-to-disable-the-organizational-store"></a>È possibile disabilitare l'archivio dell'organizzazione?

No, gli utenti vedono sempre la scheda "ORGANIZZAZIONE PERSONALE" in Power BI Desktop e nel servizio Power BI. L'amministratore può disabilitare o eliminare tutti gli oggetti visivi dell'organizzazione dal portale di amministrazione e l'archivio dell'organizzazione risulterà vuoto.
  
### <a name="if-the-administrator-disables-power-bi-visuals-from-the-admin-portal-tenant-settings-do-users-still-have-access-to-the-organizational-visuals"></a>Se l'amministratore disabilita gli oggetti visivi di Power BI dal portale di amministrazione (impostazioni del tenant), gli utenti avranno ancora accesso agli oggetti visivi dell'organizzazione?

Sì, se l'amministratore disabilita gli oggetti visivi di Power BI dal portale di amministrazione, tale operazione non influisce sull'archivio dell'organizzazione. Alcune organizzazioni disabilitano gli oggetti visivi di Power BI e abilitano solo quelli selezionati manualmente, importati e caricati dall'amministratore di Power BI nell'archivio dell'organizzazione. La disabilitazione degli oggetti visivi di Power BI dal portale di amministrazione non si riflette in Power BI Desktop. Gli utenti desktop possono comunque aggiungere e usare oggetti visivi di Power BI dal marketplace pubblico nei propri report. Tuttavia, tali oggetti visivi di Power BI pubblici non vengono più inclusi nel rendering dopo la pubblicazione nel servizio Power BI e generano un errore appropriato. Quando si usa il servizio Power BI, non è possibile importare gli oggetti visivi di Power BI dal marketplace pubblico. È possibile importare solo gli oggetti visivi dall'archivio dell'organizzazione perché l'impostazione per gli oggetti visivi di Power BI nel portale di amministrazione viene applicata nel servizio Power BI.

### <a name="why-does-the-organizational-store-and-organizational-visuals-make-a-great-enterprise-solution"></a>Per quale motivo l'archivio dell'organizzazione e gli oggetti visivi dell'organizzazione rappresentano un valida soluzione aziendale?

* Tutti gli utenti ottengono la stessa versione degli oggetti visivi, controllata dall'amministratore di Power BI. Quando l'amministratore aggiorna la versione dell'oggetto visivo nel portale di amministrazione, tutti gli utenti nell'organizzazione di ottengono automaticamente la versione aggiornata.

* Non è più necessario condividere i file degli oggetti visivi tramite posta elettronica o cartelle condivise. Un'unica posizione visibile per tutti i membri connessi.

* Sicurezza e facilità di supporto. Le nuove versioni degli oggetti visivi dell'organizzazione vengono aggiornate automaticamente in tutti i report, come per gli oggetti visivi del marketplace.

* Gli utenti dell'organizzazione che usano gli oggetti visivi dell'organizzazione devono essere connessi per poter visualizzare e usare gli oggetti visivi dell'organizzazione e ciò rappresenta una misura di sicurezza per l'organizzazione.

* Gli amministratori possono controllare quali oggetti visivi di Power BI sono disponibili nell'organizzazione.

* Gli amministratori possono abilitare o disabilitare gli oggetti visivi per attività di test dal portale di amministrazione. Maggiore sicurezza perché questi oggetti visivi saranno consentiti solo per i membri dell'organizzazione.

## <a name="certified-power-bi-visuals"></a>Oggetti visivi di Power BI certificati

### <a name="what-are-certified-power-bi-visuals"></a>Che cosa sono gli oggetti visivi di Power BI certificati?

Gli oggetti visivi di Power BI certificati sono gli oggetti visivi nel [marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) che soddisfano determinati requisiti del codice e di test [specificati](power-bi-custom-visuals-certified.md) dal team di Power BI.  I test eseguiti sono studiati per verificare che l'oggetto visivo non abbia accesso a risorse o servizi esterni. Microsoft non è tuttavia l'autore di oggetti visivi di Power BI di terze parti. È quindi consigliabile contattare l'autore direttamente per verificare la funzionalità degli oggetti.

### <a name="what-tests-are-done-during-the-certification-process"></a>Quali test vengono eseguiti durante il processo di certificazione?

I test del processo di certificazione includono ma non sono limitati a: revisioni del codice, analisi del codice statico, perdita di dati, test con dati casuali, test di penetrazione, test XSS di accesso, inserimento di dati dannosi, test di convalida dell'input e funzionali.
 
### <a name="do-you-certify-visuals-every-submission"></a>Gli oggetti visivi vengono certificati a ogni invio?

Sì. Ogni volta che una nuova versione dell'oggetto visivo certificato viene inviata al Marketplace, l'aggiornamento della versione dell'oggetto visivo viene sottoposto agli stessi controlli di certificazione.

Nota per gli sviluppatori: se si invia un aggiornamento della versione di un oggetto visivo certificato, non è necessario inviare un messaggio di posta elettronica separato come [prima richiesta di certificazione.](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified#process-for-submitting-a-custom-visual-for-certification) La certificazione dell'aggiornamento della versione avviene automaticamente e in caso di violazione che determina un rifiuto viene inviato un messaggio di posta elettronica per spiegare gli elementi da correggere. 

### <a name="is-it-possible-that-a-certified-visual-stops-being-certified-with-a-new-update"></a>È possibile che un oggetto visivo certificato non sia più certificato con un nuovo aggiornamento?

No, non è possibile. Un oggetto visivo certificato non può essere non certificato con un nuovo aggiornamento. L'aggiornamento viene rifiutato.
 
### <a name="do-i-need-to-share-my-code-in-public-repository-if-i-am-submitting-to-the-certification-process"></a>È necessario condividere il codice nel repository pubblico nel corso del processo di certificazione?

No, non è necessario condividere pubblicamente il codice. È tuttavia necessario concedere autorizzazioni di lettura per controllare il codice degli oggetti visivi. Ad esempio repository privato in GitHub.
 
### <a name="do-we-have-to-publishhttpsdocsmicrosoftcompower-bideveloperoffice-store-the-visual-in-the-marketplacehttpsappsourcemicrosoftcommarketplaceappspage1productpower-bi-visuals-to-certify-it"></a>È necessario [pubblicare](https://docs.microsoft.com/power-bi/developer/office-store) l'oggetto visivo nel [Marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) per certificarlo?

Sì. La pubblicazione dell'oggetto visivo nel Marketplace come prima operazione è un requisito obbligatorio per la certificazione.
Per certificare un oggetto visivo personalizzato, deve essere presente nei nostri server. Non è possibile certificare oggetti visivi privati.
 
### <a name="how-long-does-it-take-to-certify-my-visual"></a>Quanto tempo è necessario per certificare l'oggetto visivo?

Per la versione aggiornata potrebbero essere richieste fino a 3 settimane. Per una nuova sottoscrizione (prima certificazione) possono essere necessarie fino a 4 settimane. 

### <a name="does-the-certification-process-ensure-that-no-data-leakage-occurs"></a>Il processo di certificazione assicura che non si verifichi alcuna perdita di dati?

I test eseguiti sono studiati per verificare che l'oggetto visivo non abbia accesso a risorse o servizi esterni. Microsoft non è tuttavia l'autore di oggetti visivi di Power BI di terze parti. È quindi consigliabile contattare l'autore direttamente per verificare la funzionalità degli oggetti.
 
### <a name="are-uncertified-power-bi-visuals-safe-to-use"></a>Gli oggetti visivi di Power BI non certificati possono essere usati in modo sicuro?

Gli oggetti visivi di Power BI non certificati non sono necessariamente oggetti visivi non sicuri.
Alcuni oggetti visivi non vengono certificati perché non sono conformi a uno o più [requisiti di certificazione](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements), accedono ad esempio a un servizio esterno, come oggetti visivi mappa oppure oggetti visivi che usano librerie commerciali.
 
## <a name="visuals-with-additional-purchases"></a>Oggetti visivi con acquisti aggiuntivi

### <a name="what-is-a-visual-with-additional-purchases"></a>Che cos'è un oggetto visivo con acquisti aggiuntivi?

Un oggetto visivo con acquisti aggiuntivi è simile ai componenti aggiuntivi con acquisto in-app nel marketplace che hanno il tag **Potrebbe essere necessario un acquisto aggiuntivo**.

Gli oggetti visivi di Power BI con acquisti in-app sono gratuiti e gli utenti possono scaricarli senza pagare nulla dal marketplace. Gli oggetti visivi con acquisto in-app offrono acquisti in-app facoltativi per le funzionalità avanzate.  

### <a name="whats-the-benefit-to-developers"></a>Qual è il vantaggio per gli sviluppatori?

Gli oggetti visivi di Power BI con acquisti in-app di AppSource sono a disposizione dei numerosi visitatori giornalieri, incrementando notevolmente il traffico e il riconoscimento degli oggetti visivi di Power BI con acquisti in-app e dell'utente come sviluppatore.

Se fino a poco tempo fa questi oggetti visivi venivano gestiti sul sito Web, ora è possibile inviarli ad AppSource. In questo modo aumenterà il livello di individuabilità e visibilità degli oggetti visivi con acquisto in-app all'interno della community di Power BI.

Gli oggetti visivi di AppSource usufruiscono di un canale di feedback diretto da parte dei clienti che usano gli oggetti visivi personalizzato con acquisto in-app attraverso le revisioni e il sistema di valutazione nello store.  

Dopo che un oggetto visivo con acquisto in-app viene approvato dal team di convalida di AppSource, è possibile inviarlo per la certificazione. È un processo facoltativo.  

Dopo essere stati certificati, gli oggetti visivi di Power BI con acquisti in-app possono essere esportati in PowerPoint e visualizzati nei messaggi di posta elettronica ricevuti quando un utente effettua la sottoscrizione per le pagine del report. Quindi, se si inviano oggetti visivi con acquisti in-app al marketplace, attualmente gli oggetti visivi di Power BI con acquisti in-app possono anche essere certificati e supportano set di funzionalità aggiuntive.  

### <a name="do-iap-visuals-need-to-be-certified"></a>Gli oggetti visivi con acquisto in-app devono essere certificati?

Il processo di certificazione è facoltativo. Spetta allo sviluppatore decidere se certificare o meno i propri oggetti visivi di Power BI con acquisti in-app e lo stesso vale per gli oggetti visivi gratuiti.

### <a name="what-is-changing-in-the-submission-process"></a>Cosa cambia nel processo di invio?

Il processo di invio al marketplace degli oggetti visivi di Power BI con acquisti in-app è lo stesso processo usato per gli oggetti visivi gratuiti. Si effettua attraverso il dashboard venditori.  L'unica modifica al processo di invio è che gli sviluppatori devono indicare quanto segue nelle note per gli sviluppatori nel dashboard venditori: "Oggetto visivo con acquisto in-app". È anche necessario specificare una chiave o un token di licenza, se si devono convalidare le funzionalità a pagamento o avanzate.  

Non sarà disponibile alcuna nuova opzione nel dashboard venditori: *gratuito con acquisti in-app*, si dovranno inviare gli oggetti visivi con acquisto in-app come *gratuiti*.

Inoltre, per far sapere agli utenti cosa aspettarsi, indicare nella descrizione lunga nello store quali funzionalità sono gratuite e quali richiedono acquisti aggiuntivi per funzionare.  

### <a name="what-should-i-do-beforesubmittingmy-iap-custom-visual"></a>Cosa si deve fare prima di inviare l'oggetto visivo personalizzato con acquisto in-app?

Se si sta lavorando a un oggetto visivo personalizzato con acquisto in-app o l'oggetto è già presente, verificare che sia conforme alle linee guida.  

Se l'oggetto visivo personalizzato contiene un logo, verificare che sia conforme alle linee guida per i logo (colore, posizione, dimensione e attivazione di azioni).

Nelle linee guida è anche possibile trovare indicazioni per le procedure consigliate.  
> [!Note]
> Tutti gli oggetti visivi gratuiti dovrebbero avere le stesse funzionalità gratuite offerte in precedenza. È possibile aggiungere funzionalità avanzate facoltative a pagamento, in aggiunta alle funzionalità gratuite precedenti. È consigliabile inviare gli oggetti visivi in-app con funzionalità avanzate come nuovi oggetti visivi anziché aggiornare gli oggetti gratuiti precedenti.

### <a name="can-i-get-my-iap-custom-visual-certified"></a>È possibile ottenere la certificazione dell'oggetto visivo personalizzato con acquisto in-app?

Sì, come per gli oggetti visivi gratuiti.  Dopo che l'oggetto visivo personalizzato con acquisto in-app viene approvato dal team di AppSource, è possibile inviarlo al processo di certificazione.

Per essere certificato, l'oggetto visivo deve essere conforme ai requisiti di certificazione, ad esempio non può accedere ai servizi esterni per la convalida delle licenze.

La certificazione dei richiami è un processo facoltativo, spetta all'utente decidere se l'oggetto visivo con acquisto in-app deve essere certificato.

## <a name="additional-questions"></a>Altre domande

### <a name="how-to-get-support"></a>Come si ottiene il supporto?

È possibile contattare il team di supporto per gli oggetti visivi di Power BI: *pbicvsupport@microsoft.com*  per eventuali domande, commenti o problemi.  

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni, vedere [Risoluzione dei problemi relativi agli oggetti visivi di Power BI](power-bi-custom-visuals-troubleshoot.md).
