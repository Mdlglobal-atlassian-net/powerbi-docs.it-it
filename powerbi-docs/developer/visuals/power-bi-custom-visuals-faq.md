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
ms.openlocfilehash: d70d1357af3309ddd9584b11ccf79115cde095c8
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79383299"
---
# <a name="power-bi-visuals-faq"></a>Domande frequenti sugli oggetti visivi di Power BI

## <a name="organizational-power-bi-visuals"></a>Oggetti visivi di Power BI dell'organizzazione

Il portale di amministrazione consente di gestire gli oggetti visivi di Power BI per l'organizzazione.

### <a name="how-can-the-admin-manage-organizational-power-bi-visuals"></a>In quale modo l'amministratore può gestire gli oggetti visivi di Power BI dell'organizzazione?

Nella scheda *Oggetti visivi dell'organizzazione* del portale di amministrazione l'amministratore può vedere e [gestire tutti gli oggetti visivi di Power BI nell'azienda](../../service-admin-portal.md#organizational-visuals) ed eseguire le operazioni di aggiunta, disabilitazione, abilitazione ed eliminazione di oggetti visivi di Power BI.

Gli utenti dell'organizzazione possono trovare facilmente oggetti visivi di Power BI e importarli nei report direttamente da Power BI Desktop o dal servizio Power BI.

Quando l'amministratore carica una nuova versione di un oggetto visivo di Power BI dell'organizzazione, chiunque nell'organizzazione ottiene la stessa versione aggiornata. Tutti i report che usano oggetti visivi di Power BI aggiornati vengono aggiornati automaticamente.

Gli utenti possono trovare gli oggetti visivi di Power BI dell'organizzazione nell'archivio incorporato di Power BI Desktop e del servizio Power BI dell'organizzazione, nella scheda *ORGANIZZAZIONE PERSONALE*. 

### <a name="if-an-admin-uploads-a-power-bi-visual-from-the-public-marketplace-to-the-organization-store-is-it-automatically-updated-once-a-vendor-updates-the-visual-in-the-public-marketplace"></a>Se un amministratore carica un oggetto visivo di Power BI dal Marketplace pubblico nell'archivio dell'organizzazione e in seguito un fornitore aggiorna tale oggetto nel Marketplace pubblico, l'oggetto visivo viene aggiornato automaticamente?

No, non è disponibile l'aggiornamento automatico dal marketplace pubblico. È compito dell'amministratore aggiornare la versione degli oggetti visivi di Power BI dell'organizzazione.

### <a name="is-there-a-way-to-disable-the-organization-store"></a>È possibile disabilitare l'archivio dell'organizzazione?

No. Gli utenti visualizzano sempre la scheda *ORGANIZZAZIONE PERSONALE* in Power BI Desktop e nel servizio Power BI. Se un amministratore disabilita o elimina tutti gli oggetti visivi di Power BI dell'organizzazione dal portale di amministrazione, l'archivio dell'organizzazione rimane vuoto.
  
### <a name="if-the-admin-disables-power-bi-visuals-from-the-admin-portal-tenant-settings-do-users-still-have-access-to-the-organizational-power-bi-visuals"></a>Se l'amministratore disabilita gli oggetti visivi di Power BI dal portale di amministrazione (impostazioni del tenant), gli utenti hanno ancora accesso agli oggetti visivi di Power BI dell'organizzazione?

Sì, se l'amministratore disabilita gli oggetti visivi di Power BI dal portale di amministrazione, tale operazione non influisce sull'archivio dell'organizzazione.

Alcune organizzazioni disabilitano gli oggetti visivi di Power BI e abilitano solo quelli selezionati manualmente importati e caricati in precedenza dall'amministratore di Power BI nell'archivio dell'organizzazione.

La disabilitazione degli oggetti visivi di Power BI dal portale di amministrazione non si riflette in Power BI Desktop. Gli utenti desktop possono comunque aggiungere e usare oggetti visivi di Power BI dal marketplace pubblico nei propri report. Tuttavia, tali oggetti visivi di Power BI pubblici non vengono più inclusi nel rendering dopo la pubblicazione nel servizio Power BI e generano un errore appropriato. 

Se viene applicata l'impostazione degli oggetti visivi di Power BI nel portale di amministrazione, gli utenti del servizio Power BI non sono in grado di importare oggetti visivi di Power BI dal Marketplace pubblico ma solo oggetti visivi dall'archivio dell'organizzazione.

### <a name="what-are-the-advantages-of-power-bi-visuals-in-the-organizational-store"></a>Quali sono i vantaggi offerti dagli oggetti visivi di Power BI nell'archivio dell'organizzazione?

* Tutti gli utenti ottengono la stessa versione degli oggetti visivi, controllata dall'amministratore di Power BI. Quando l'amministratore aggiorna la versione dell'oggetto visivo nel portale di amministrazione, tutti gli utenti nell'organizzazione di ottengono automaticamente la versione aggiornata.

* Non è necessario condividere file di oggetti visivi tramite posta elettronica o cartelle condivise. Gli oggetti visivi presenti nell'archivio dell'organizzazione sono visibili a tutti i membri che hanno eseguito l'accesso.

* Gli oggetti visivi sono protetti e di facile supporto: le nuove versioni degli oggetti visivi di Power BI dell'organizzazione vengono aggiornate automaticamente in tutti i report.

* Gli amministratori sono in grado di stabilire quali oggetti visivi di Power BI devono essere disponibili in tutta l'organizzazione.

* Gli amministratori possono abilitare o disabilitare gli oggetti visivi per attività di test dal portale di amministrazione.

## <a name="certified-power-bi-visuals"></a>Oggetti visivi di Power BI certificati

### <a name="what-are-certified-power-bi-visuals"></a>Che cosa sono gli oggetti visivi di Power BI certificati?

Gli oggetti visivi di Power BI certificati sono oggetti visivi di Power BI che soddisfano [requisiti](power-bi-custom-visuals-certified.md) specifici e sono certificati da Microsoft.

Nel [Marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) gli oggetti visivi di Power BI certificati sono contrassegnati da una notifica gialla.

Microsoft non è l'autore di oggetti visivi di Power BI di terze parti. Per verificare la funzionalità degli oggetti visivi di terze parti, è quindi consigliabile contattare l'autore direttamente.

### <a name="what-tests-are-done-during-the-certification-process"></a>Quali test vengono eseguiti durante il processo di certificazione?

I test del processo di certificazione includono ma non sono limitati a: 
* Revisioni del codice
* Analisi del codice statico
* Perdita di dati
* Test con dati casuali
* Test di penetrazione
* Test di accesso XSS
* Inserimento di dati dannosi
* Convalida dell'input
* Test funzionale
 
### <a name="are-certified-power-bi-visual-checked-again-with-every-new-submission-upgrade"></a>Gli oggetti visivi di Power BI certificati vengono controllati nuovamente a ogni nuovo invio (aggiornamento)?

Sì. Ogni volta che una nuova versione dell'oggetto visivo certificato viene inviata al Marketplace, l'aggiornamento della versione dell'oggetto visivo viene sottoposto agli stessi controlli di certificazione.

La certificazione dell'aggiornamento della versione è automatica. Se viene rilevata una violazione che causa il rifiuto dell'aggiornamento, viene inviato un messaggio di posta elettronica allo sviluppatore che illustra i problemi che devono essere corretti.

### <a name="can-a-certified-power-bi-visual-stop-lose-its-certification-after-a-new-update"></a>È possibile che un oggetto visivo di Power BI certificato perda la certificazione dopo un nuovo aggiornamento?

No, non è possibile. Un oggetto visivo di Power BI certificato non può perdere la certificazione con un nuovo aggiornamento. L'aggiornamento viene rifiutato.
 
### <a name="do-i-need-to-share-my-code-in-a-public-repository-if-im-certifying-my-power-bi-visual"></a>Se si intende certificare un oggetto visivo di Power BI, è necessario condividerne il codice in un repository pubblico?

No, non è necessario condividere pubblicamente il codice.

Concedere le autorizzazioni di lettura per consentire il controllo del codice dell'oggetto visivo di Power BI, ad esempio, usando un repository privato in GitHub.
 
### <a name="does-a-certified-power-bi-visual-have-to-be-in-the-marketplace"></a>Un oggetto visivo di Power BI certificato deve trovarsi nel Marketplace?

Sì. Gli oggetti privati non vengono certificati.
 
### <a name="how-long-does-it-take-to-certify-my-visual"></a>Quanto tempo è necessario per certificare l'oggetto visivo?

La certificazione di un nuovo oggetto visivo di Power BI (prima certificazione) può richiedere fino a quattro settimane. 

La certificazione di una versione aggiornata di un oggetto visivo di Power BI può richiedere fino a tre settimane. 

### <a name="does-the-certification-process-ensure-that-there-is-no-data-leakage"></a>Il processo di certificazione assicura che non ci sia alcuna perdita di dati?

I test eseguiti sono studiati per verificare che l'oggetto visivo non abbia accesso a risorse o servizi esterni. 

Microsoft non è l'autore di oggetti visivi di Power BI di terze parti. Per verificare la funzionalità degli oggetti visivi di Power BI di terze parti, è quindi consigliabile contattare l'autore direttamente.
 
### <a name="are-uncertified-power-bi-visuals-safe-to-use"></a>Gli oggetti visivi di Power BI non certificati possono essere usati in modo sicuro?

Gli oggetti visivi di Power BI non certificati non sono necessariamente oggetti visivi non sicuri.

Alcuni oggetti visivi non vengono certificati perché non soddisfano uno o più [requisiti di certificazione](power-bi-custom-visuals-certified.md#certification-requirements), accedono ad esempio a un servizio esterno, come oggetti visivi mappa oppure oggetti visivi che usano librerie commerciali.
 
## <a name="visuals-with-additional-purchases"></a>Oggetti visivi con acquisti aggiuntivi

### <a name="what-is-a-visual-with-additional-purchases"></a>Che cos'è un oggetto visivo con acquisti aggiuntivi?

Un oggetto visivo con acquisti aggiuntivi è simile a un componente aggiuntivo di acquisto in-app (IAP, In-App Purchase). Questi componenti aggiuntivi riportano la dicitura **Potrebbe essere necessario un acquisto aggiuntivo**.

Gli oggetti visivi di Power BI IAP sono gratuiti e scaricabili. Gli utenti non pagano nulla per scaricare questi oggetti visivi di Power BI dal Marketplace.

Gli oggetti visivi con acquisto in-app offrono acquisti in-app facoltativi per le funzionalità avanzate.  

### <a name="what-is-changing-in-the-submission-process"></a>Cosa cambia nel processo di invio?

Il processo di invio al Marketplace degli oggetti visivi di Power BI IAP è lo stesso processo usato per gli oggetti visivi di Power BI gratuiti. È possibile inviare un oggetto visivo di Power BI per la certificazione tramite il [Centro per i partner](https://docs.microsoft.com/partner-center/).


Per la registrazione dell'oggetto visivo di Power BI, passare alla scheda *Configurazione prodotto* e selezionare la casella di controllo *Il prodotto richiede l'acquisto di un servizio*.

### <a name="what-should-i-do-beforesubmittingmy-iap-power-bi-visual"></a>Cosa si deve fare prima di inviare un oggetto visivo di Power BI IAP?

Se si sta lavorando a un oggetto visivo di Power BI IAP, assicurarsi che rispetti le [linee guida](guidelines-powerbi-visuals.md).  

> [!NOTE]
> Gli oggetti visivi di Power BI gratuiti con in più la funzionalità IAP devono contenere le stesse funzionalità gratuite disponibili in precedenza. È possibile aggiungere funzionalità avanzate facoltative a pagamento in aggiunta alle funzionalità gratuite precedenti. È consigliabile inviare l'oggetto visivo di Power BI IAP con le funzionalità avanzate come nuovo oggetto visivo di Power BI anziché aggiornare quello precedente gratuito.

### <a name="do-iap-power-bi-visuals-need-to-be-certified"></a>Gli oggetti visivi di Power BI IAP devono essere certificati?

Il processo di [certificazione](power-bi-custom-visuals-certified.md) è facoltativo. Spetta allo sviluppatore decidere se certificare o meno i propri oggetti visivi di Power BI IAP.

### <a name="can-i-get-my-iap-power-bi-visual-certified"></a>È possibile ottenere la certificazione dell'oggetto visivo di Power BI IAP?

Sì. Dopo l'approvazione da parte del team di AppSource, è possibile inviare l'oggetto visivo di Power BI IAP per la [certificazione](power-bi-custom-visuals-certified.md).

La certificazione è un processo facoltativo, spetta allo sviluppatore decidere se l'oggetto visivo IAP deve essere certificato.

## <a name="additional-questions"></a>Altre domande

### <a name="how-to-get-support"></a>Come si ottiene il supporto?

Per qualsiasi domanda, commento o problema, è possibile contattare il team di supporto degli oggetti visivi di Power BI all'indirizzo pbicvsupport@microsoft.com.  

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni, vedere [Risoluzione dei problemi relativi agli oggetti visivi di Power BI](power-bi-custom-visuals-troubleshoot.md).
