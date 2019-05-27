---
title: Distribuire il contenuto di Power BI agli utenti guest esterni usando Azure Active Directory B2B
description: White paper che descrive come usare B2B di Azure Active Directory per la distribuzione di Power BI agli utenti guest esterni
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/07/2019
ms.author: davidi
LocalizationGroup: Conceptual
ms.openlocfilehash: 79b8ae80413cc54b065d12bf36ccb1651a670812
ms.sourcegitcommit: ec5b6a9f87bc098a85c0f4607ca7f6e2287df1f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66051583"
---
# <a name="distribute-power-bi-content-to-external-guest-users-using-azure-active-directory-b2b"></a>Distribuire il contenuto di Power BI agli utenti guest esterni usando Azure Active Directory B2B

**Riepilogo:** Si tratta di un white paper tecnico su come distribuire il contenuto a utenti esterni all'organizzazione usando l'integrazione di Azure Active Directory Business-to-business (B2B di Azure AD).

**Writer:** Lukasz Pawlowski, Kasper de Jonge

**Revisori tecnici:** ADAM Wilson, Sheng Liu, Qian Liang, Sergei Gundorov, Jacob Grimm, Adam Saxton, Shenhav Maya, Nimrod Shalit, Elisabeth Olson

> [!NOTE]
> È possibile salvare o stampare questo white paper selezionando **Stampa** dal browser, quindi selezionando **Salva come PDF**.

## <a name="introduction"></a>Introduzione

Power BI offre alle organizzazioni una visualizzazione a 360 gradi della propria azienda e promuove tutti gli utenti in queste aziende a prendere decisioni intelligenti usando i dati. Molte di queste organizzazioni hanno relazioni attendibile e sicure con partner esterni, i client e terzisti. Queste organizzazioni necessario fornire accesso sicuro ai dashboard di Power BI e report per gli utenti in questi partner esterni.

Power BI si integra con [Azure Active Directory Business-to-business (B2B di Azure AD)](https://docs.microsoft.com/azure/active-directory/b2b/what-is-b2b) per consentire la distribuzione sicura di Power BI contenuti agli utenti guest all'esterno dell'organizzazione, mentre comunque mantenere il controllo e che controllano l'accesso a dati interni.

Questo white paper illustra i tutti i dettagli che necessari per comprendere l'integrazione di Power BI con Azure Active Directory B2B. Vengono illustrati il caso d'uso più comune, il programma di installazione, licenza e sicurezza a livello di riga.

> [!NOTE]
> In questo white paper, facciamo riferimento ai Azure Active Directory come Azure AD e Azure Active Directory Business-to-Business come Azure AD B2B.

## <a name="scenarios"></a>Scenari

Contoso è un produttore di settore automobilistico e funziona con molti fornitori diversi che forniscono tutti i materiali, i componenti e i servizi necessari per eseguire le operazioni di produzione. Contoso desidera semplificare relativo la logistica della catena di fornitura e prevede di usare Power BI per monitorare le metriche di prestazioni chiave della catena di alimentazione. Contoso desidera condividere con analitica di partner esterni supply chain in modo sicuro e gestibile.

Contoso può abilitare le esperienze seguenti per gli utenti esterni con Power BI e Azure AD B2B.

### <a name="ad-hoc-per-item-sharing"></a>Ad hoc per la condivisione degli elementi

Contoso è compatibile con un fornitore che compila radiatori per automobili di Contoso. Spesso è necessario ottimizzare l'affidabilità dei radiatori usando i dati di tutti di automobili di Contoso. Un analista di Contoso USA Power BI per condividere un report di affidabilità radiatore con un Engineer presso il fornitore. Il tecnico riceve un messaggio di posta elettronica con un collegamento per visualizzare il report.

Come descritto in precedenza, questa condivisione ad hoc viene eseguita dagli utenti aziendali in base alle diverse esigenze. Il collegamento inviato da Power BI per l'utente esterno è un collegamento di invito B2B di Azure AD. Quando l'utente esterno selezioni il collegamento, gli viene chiesto join organizzazione di Azure AD di Contoso come utente Guest. Una volta accettato l'invito, il collegamento apre il report specifico o il dashboard. L'amministratore di Azure Active Directory delega autorizzati a invitare utenti esterni all'organizzazione e sceglie li operazioni eseguibili dagli utenti una volta accettata l'invito come descritto nella sezione Governance di questo documento. L'analista di Contoso può invitare l'utente Guest solo perché tale azione e Power BI è consentita l'amministratore di Azure AD Amministratore utenti consentiti per invitare utenti guest a visualizzare il contenuto nelle impostazioni del tenant di Power BI.

![Invitare utenti guest a Power BI tramite Azure Active Directory](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_01.png)

1. Il processo inizia con un utente interno di Contoso condividere un dashboard o un report con un utente esterno. Se l'utente esterno non è già un utente guest in Azure di Contoso AD, ne determina l'invito. Un messaggio di posta elettronica viene inviato al relativo indirizzo di posta elettronica che include un invito ad Azure di Contoso AD
2. Il destinatario accetta l'invito a Contoso di Azure AD e viene aggiunto come utente Guest in Azure di Contoso AD.
3. Il destinatario quindi viene reindirizzato al dashboard, report o app, che sono di sola lettura per l'utente di Power BI.

Il processo è considerato ad-hoc poiché gli utenti aziendali in Contoso eseguono l'azione di invito in base alle necessità per gli scopi aziendali. Ogni elemento condiviso è un singolo collegamento può accedere l'utente esterno per visualizzare il contenuto.

Una volta che l'utente esterno è stato invitato per accedere alle risorse di Contoso, un account shadow potrebbe essere creato in Azure AD di Contoso e non dovranno essere nuovamente invitati.  La prima volta che tentano di accedere a una risorsa di Contoso Analogamente a un dashboard di Power BI, passano attraverso il processo di consenso che Riscatta l'invito.  Se non completano il consenso, non possono accedere a uno dei contenuti di Contoso.  Se l'utente ha riscattare l'invito tramite il collegamento originale fornito, un amministratore di Azure AD può inviare nuovamente un collegamento di invito specifico per poter riscattare.

### <a name="planned-per-item-sharing"></a>Pianificato per la condivisione degli elementi

Contoso Usa un terzista per eseguire l'analisi di affidabilità di radiatori. Quest ' ultimo ha un team di 10 persone che devono accedere ai dati nell'ambiente di Power BI di Contoso. L'amministratore di Azure AD di Contoso è coinvolto per invitare tutti gli utenti e per gestire le aggiunte/modifiche come il personale la modifica dei subappaltatori. L'amministratore di Azure AD crea un gruppo di sicurezza per tutti i dipendenti di quest ' ultimo. Tramite il gruppo di sicurezza, i dipendenti di Contoso possono facilmente gestire l'accesso ai report e verificare che tutto il personale necessari terzista hanno accesso a tutti i report necessari, dashboard e le app di Power BI. L'amministratore di Azure AD può essere evitato anche essere coinvolti nel processo di invito completamente scegliendo di delegare i diritti di invito a un dipendente di Contoso o a quest ' ultimo per garantire al personale tempestivo management.

Alcune organizzazioni richiedono maggiore controllo sulla quando vengono aggiunti gli utenti esterni, vuole invitare più utenti in un'organizzazione esterna o molte organizzazioni esterne. In questi casi, la condivisione pianificato è utilizzabile per gestire la scala della condivisione, per applicare i criteri dell'organizzazione e anche per delegare autorizzazioni agli utenti attendibili consente di invitare e gestire gli utenti esterni. Azure Active Directory B2B supporta inviti pianificati per essere inviato direttamente [dal portale di Azure da un amministratore IT](https://docs.microsoft.com/azure/active-directory/b2b/add-users-administrator), o tramite [PowerShell usando l'API di gestione di invito](https://docs.microsoft.com/azure/active-directory/b2b/customize-invitation-api) in cui un set di utenti può essere invitato in una azione. Usando il pianificato invites approccio, l'organizzazione possa controllare chi può invitare gli utenti e implementare processi di approvazione. Avanzate funzionalità di Azure AD, ad esempio i gruppi dinamici possono renderlo facili da gestire automaticamente l'appartenenza al gruppo di sicurezza.


![Controllo che gli utenti guest possono visualizzare contenuto](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_02.png)



1. Le stelle di processo con l'amministratore IT vuole invitare l'utente guest manualmente o tramite l'API fornita da Azure Active Directory
2. L'utente accetta l'invito all'organizzazione.
3. Una volta che l'utente ha accettato l'invito, un utente in Power BI può condividere un report o un dashboard con l'utente esterno o un gruppo di sicurezza in che si trovano. Proprio come con regolari condivisione in Power BI l'utente esterno riceve un messaggio di posta elettronica con il collegamento all'elemento.
4. Quando gli accessi utente esterno il collegamento, l'autenticazione nella propria directory viene passato a Contoso di Azure AD e usato per ottenere l'accesso al contenuto di Power BI.

### <a name="ad-hoc-or-planned-sharing-of-power-bi-apps"></a>Ad hoc o pianificato la condivisione di App di Power BI

Contoso ha un set di report e dashboard che devono condividere con uno o più fornitori. Per assicurarsi che tutti gli utenti esterni necessari hanno accesso al contenuto, si viene assemblato come un'app Power BI. Gli utenti esterni che vengono aggiunti direttamente all'elenco di accesso app o tramite gruppi di sicurezza. Un utente di Contoso invia quindi l'URL dell'app per tutti gli utenti esterni, ad esempio in un messaggio di posta elettronica. Quando gli utenti esterni aprono il collegamento, viene visualizzato tutto il contenuto in un unico semplice, esperienza.

Utilizzo di un'app Power BI semplifica per Contoso creare un portale BI per i suoi fornitori. Un elenco di accesso singolo controlla l'accesso a tutto il contenuto necessario riducendo il controllo delle perdite di tempo e impostando le autorizzazioni a livello di elemento. Azure AD B2B gestisce l'accesso di sicurezza usando identità nativi del fornitore in modo che gli utenti non debbano le credenziali di accesso aggiuntivi. Se uso pianificato invita con gruppi di sicurezza, gestione dell'accesso all'app come il personale ruotare all'interno o all'esterno del progetto viene semplificata. Appartenenza al gruppo di sicurezza gruppi manualmente o utilizzando [i gruppi dinamici](https://docs.microsoft.com/azure/active-directory/b2b/use-dynamic-groups), in modo che tutti gli utenti esterni da un fornitore vengono aggiunti automaticamente al gruppo di sicurezza appropriato.


![Controllo del contenuto con AAD](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_03.png)

1. Il processo viene avviato dall'utente invitato all'organizzazione di Azure AD di Contoso tramite il portale di Azure o PowerShell
2. L'utente può essere aggiunto a un gruppo di utenti in Azure AD. Può essere utilizzato un gruppo di utenti statici o dinamici, ma i gruppi dinamici consentono a ridurre il lavoro manuale.
3. Gli utenti esterni vengono concesso l'accesso all'App Power BI tramite il gruppo di utenti. L'app URL deve essere inviato direttamente all'utente esterno o inserito in un sito di cui hanno accesso. Power BI tenta di inviare un messaggio di posta elettronica con il collegamento all'app a utenti esterni, ma quando si usa l'appartenenza al quale è possibile modificare i gruppi di utenti, Power BI non è in grado di inviare a tutti gli utenti esterni gestiti tramite i gruppi di utenti.
4. Quando l'utente esterno accede l'URL dell'app Power BI, vengono autenticati da Azure di Contoso AD, l'app viene installata per l'utente e l'utente può visualizzare tutti i report contenuti e i dashboard all'interno dell'app.

Le app hanno anche una funzionalità univoca che consente agli autori di app installare l'applicazione automaticamente per l'utente, pertanto è disponibile quando l'utente effettua l'accesso. Questa funzionalità solo viene installato automaticamente per gli utenti esterni che fanno già parte dell'organizzazione di Contoso al momento l'applicazione viene pubblicata o aggiornata. Di conseguenza, è particolarmente utile con l'approccio di inviti pianificati e dipende l'app viene pubblicato o aggiornato dopo che gli utenti vengono aggiunti ad Azure di Contoso AD. Gli utenti esterni è sempre possono installare l'app usando il collegamento all'app.

### <a name="commenting-and-subscribing-to-content-across-organizations"></a>Aggiunta di commenti e la sottoscrizione di contenuto nelle organizzazioni

Come Contoso continua a funzionare con i relativi subappaltatori di Microsoft o fornitori, i tecnici esterni necessario lavorare a stretto contatto con gli analisti di Contoso. Power BI fornisce diverse funzionalità di collaborazione che consentono agli utenti di comunicare sul contenuto che può utilizzare. Aggiunta di commenti dashboard (e presto segnalare commenti) consente agli utenti di discutere i punti dati sono vedere e comunicare con gli autori di report per porre domande.

Attualmente, gli utenti guest esterni possono partecipare commenti lasciando commenti e leggendo le risposte. Tuttavia, a differenza degli utenti interni, gli utenti guest non possono essere @mentioned e non si ricevono notifiche che abbia ricevuto un commento. Gli utenti guest non è possibile usare la funzionalità di sottoscrizioni all'interno di Power BI al momento della scrittura. In una versione futura, verranno rimossa tali restrizioni e l'utente Guest riceverà un messaggio di posta elettronica quando un commento @mentions , o quando una sottoscrizione viene recapitata alla posta elettronica contenente un collegamento al contenuto in Power BI.

### <a name="access-content-in-the-power-bi-mobile-apps"></a>Accedere al contenuto nelle App per dispositivi mobili di Power BI

In una versione futura, quando gli utenti di Contoso condividono i dashboard o report con le controparti Guest esterne, Power BI invierà un messaggio di posta elettronica che informa l'utente Guest. Quando l'utente guest viene aperto il collegamento al report o dashboard nel proprio dispositivo mobile, verrà aperto il contenuto nelle App native per dispositivi mobili Power BI nel dispositivo, se sono installati. Sarà in grado di spostarsi tra i contenuti condivisi con loro nel tenant esterni, ripristinando il proprio contenuto dal tenant home dell'utente guest.

> [!NOTE]
> L'utente guest non è possibile aprire l'app per dispositivi mobili di Power BI e immediatamente passare al tenant di esterni, devono iniziare con un collegamento a un elemento nel tenant esterni. Le soluzioni alternative comuni descritte nel [distribuzione collegamenti a contenuto in Power BI dell'organizzazione padre](#distributing-links-to-content-in-the-parent-organizations-power-bi) sezione più avanti in questo documento.

### <a name="cross-organization-editing-and-management-of-power-bi-content"></a>Modifica tra organizzazioni e gestione del contenuto di Power BI

Contoso fornitori e i relativi subappaltatori interagiscono sempre più da vicino. Un analista di quest ' ultimo deve spesso visualizzazioni di dati o le metriche aggiuntive da aggiungere a un report di che Contoso ha condiviso con loro. I dati devono risiedere nel tenant di Power BI di Contoso, ma gli utenti esterni devono essere in grado di modificarlo, creare nuovo contenuto e anche distribuirlo agli individui appropriati.

Power BI offre un'opzione che consenta **utenti guest esterni possono modificare e gestire il contenuto** nell'organizzazione. Per impostazione predefinita, gli utenti esterni avere un'esperienza di sola lettura orientato ai consumi. Tuttavia, questa nuova impostazione consente all'amministratore di Power BI di scegliere quali utenti esterni possono modificare e gestire contenuto della propria organizzazione. Una volta consentito, l'utente esterno può modificare i report, dashboard, pubblicare o aggiornare le app, lavorare nelle aree di lavoro e connettersi ai dati che sono autorizzati a usare.

Questo scenario è descritto dettagliatamente gli utenti esterni di abilitazione di sezione per modificare e gestire il contenuto all'interno di Power BI più avanti in questo documento.

## <a name="organizational-relationships-using-power-bi-and-azure-ad-b2b"></a>Relazioni dell'organizzazione usando Power BI e Azure AD B2B

Quando tutti gli utenti di Power BI sono interni all'organizzazione, non è necessario usare Azure AD B2B. Tuttavia, quando due o più organizzazioni vogliono collaborare su dati e informazioni dettagliate, il supporto di Power BI per Azure AD B2B rende semplice e conveniente per eseguire questa operazione.

Di seguito sono in genere rilevate strutture organizzative che sono particolarmente adatte per la collaborazione tra organizzazioni di Azure AD B2B stile di visualizzazione in Power BI. Azure AD B2B funziona bene nella maggior parte dei casi, ma in alcune situazioni comuni approcci alternativi illustrati alla fine di questo documento sono opportuno considerare.

### <a name="case-1-direct-collaboration-between-organizations"></a>Caso 1: Collaborazione diretta tra le organizzazioni

Relazione di Contoso con il fornitore radiatore è riportato un esempio di collaborazione diretta tra le organizzazioni. Poiché sono presenti relativamente pochi utenti presso la società Contoso e il fornitore che devono accedere alle informazioni di affidabilità radiatore, usando Azure AD B2B basato su condivisione esterna è ideale. È facile da utilizzare e semplice da amministrare. Questo è un modello comune in servizi di consulenza in cui potrebbe essere necessario un consulente creare contenuto per un'organizzazione.

![Condividere tra organizzazioni](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_04.png)


In genere, questa condivisione vengono eseguite utilizzando inizialmente Ad hoc per la condivisione degli elementi. Tuttavia, i team di espansione o ad approfondire le relazioni, la pianificato per la condivisione degli elementi approccio diventa il metodo preferito per ridurre il sovraccarico di gestione. Inoltre, Ad hoc o pianificato la condivisione di App di Power BI, commenti e la sottoscrizione per il contenuto tra organizzazioni diverse, l'accesso al contenuto nelle App per dispositivi mobili possa entrare in play, nonché tra organizzazioni la modifica e gestione del contenuto di Power BI. Importante, se utenti entrambe le organizzazioni hanno licenze di Power BI Pro nelle rispettive organizzazioni, è possibile usare le licenze Pro in ognuno degli altri ambienti di Power BI. In questo modo vantaggioso licenze poiché l'organizzazione che emette l'invito non potrebbe essere necessario pagare per una licenza Power BI Pro per gli utenti esterni. Questo argomento viene discusso più dettagliatamente nella sezione licenze più avanti in questo documento.

### <a name="case-2-parent-and-its-subsidiaries-or-affiliates"></a>Caso 2: Elemento padre e sue società controllate o consociate

Alcune strutture dell'organizzazione sono più complesse, tra cui parzialmente o interamente controllate, delle aziende affiliate o relazioni di provider del servizio gestito. Queste organizzazioni dispongono di un'elemento organizzazione padre, ad esempio una società finanziaria, ma le organizzazioni sottostante operano punto e virgola in modo autonomo, a volte con diversi requisiti a livello di area. Di conseguenza ogni organizzazione che abbia il proprio ambiente di Azure AD e separare i tenant di Power BI.

![Utilizzo di filiali](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_05.png)


In questa struttura, l'elemento organizzazione padre deve in genere distribuire informazioni standardizzati alle sue società controllate. In genere, questa condivisione vengono eseguite utilizzando la condivisione Ad hoc o pianificato dell'approccio di App di Power BI, come illustrato nell'immagine seguente, che consente di distribuzione di contenuto autorevole standardizzato ampie tipologie di pubblico. In pratica viene utilizzata una combinazione di tutti gli scenari menzionati in precedenza in questo documento.

![La combinazione di scenari](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_06.png)


Viene seguito il processo seguente:

1. Gli utenti da ogni filiale sono invitati a Azure di Contoso AD
2. Quindi viene pubblicata l'app Power BI per assegnare questi utenti l'accesso ai dati necessari
3. Infine, gli utenti di aprono l'app tramite un collegamento che sono stati concessi per visualizzare i report

Le organizzazioni in questa struttura sono devono affrontare alcune sfide decisive diversi:

- Come distribuire i collegamenti al contenuto in Power BI dell'organizzazione principale
- Come consentire agli utenti sussidiari per accedere a origine dei dati ospitata da elemento organizzazione padre

#### <a name="distributing-links-to-content-in-the-parent-organizations-power-bi"></a>Distribuire i collegamenti al contenuto in Power BI dell'organizzazione principale

Tre approcci vengono comunemente utilizzati per distribuire i collegamenti al contenuto. Il primo e basic la maggior parte delle consiste nell'inviare il collegamento all'app per gli utenti richiesti o inserirlo in un sito di SharePoint Online da cui può essere aperto. Gli utenti possono quindi aggiungere un segnalibro il collegamento nel browser per un accesso più rapido per i dati che necessari.

Il secondo approccio si basa sulla modifica tra organizzazioni e gestione delle funzionalità di contenuto di Power BI. Elemento organizzazione padre consente agli utenti presso le filiali di accedere ai relativi Power BI e consente di controllare quali elementi sono accessibili tramite l'autorizzazione. Ciò consente di accedere a Power BI Home in cui l'utente dalla società affiliata Visualizza un elenco completo di contenuto condiviso con loro nel tenant dell'organizzazione padre. Quindi l'URL all'ambiente di Power BI le organizzazioni padre viene assegnato agli utenti nelle filiali.

L'approccio finale viene usata un'app di Power BI creata all'interno del tenant di Power BI per ogni filiale. L'app Power BI include un dashboard con [riquadri configurati con l'opzione di collegamento esterno](https://docs.microsoft.com/power-bi/service-dashboard-edit-tile#hyperlink). Quando l'utente preme il riquadro, vengono rilevati per i report appropriato, dashboard o app in Power BI dell'organizzazione padre. Questo approccio offre il vantaggio che l'app può essere installato automaticamente per tutti gli utenti nella società affiliata ed è disponibile ogni volta che accedono al proprio ambiente di Power BI. Un altro vantaggio di questo approccio è che funziona bene con le App per dispositivi mobili di Power BI che è possono aprire il collegamento in modo nativo. È anche possibile combinare questa con il secondo approccio abilitare più semplice il passaggio tra gli ambienti di Power BI.

#### <a name="allowing-subsidiary-users-to-access-data-sources-hosted-by-the-parent-organization"></a>Consentendo sussidiario agli utenti di accedere alle origini dati ospitate da elemento organizzazione padre

Spesso gli analisti di una filiale necessario per creare i propri analitica usando i dati forniti dall'elemento organizzazione padre. In questo caso, origini dati cloud vengono comunemente usate per risolvere il problema.

Il primo approccio sfrutta [Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-overview) per compilare un data warehouse di livello aziendale che soddisfi le esigenze di analisti tra l'elemento padre e le sue filiali, come illustrato nell'immagine seguente. Contoso può ospitare i dati e usare funzionalità come la sicurezza a livello di riga che consente agli utenti in ogni filiale può accedere solo ai dati. Gli analisti di ogni organizzazione possono accedere al data warehouse con Power BI Desktop e pubblicare analitica risultante per i rispettivi tenant di Power BI.

![La condivisione come avviene con i tenant di Power BI](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_07.png)


Il secondo approccio sfrutta [Database SQL di Azure](https://azure.microsoft.com/services/sql-database/) per compilare un data warehouse relazionale per fornire l'accesso ai dati. Questa opzione funziona in modo analogo all'approccio di Azure Analysis Services, tuttavia alcune funzionalità, ad esempio la sicurezza a livello di riga potrebbe essere più difficili da distribuire e gestire tra filiali.

Approcci più sofisticati sono anche possibili, ma quello precedente è di gran lunga il più comuni.

### <a name="case-3-shared-environment-across-partners"></a>Caso 3: Ambiente condiviso tra i partner

Contoso potrebbe instaurare una collaborazione con un concorrente congiuntamente creazione di un'automobile in una catena di montaggio condivisa, ma per la distribuzione del veicolo in marchi diversi o in aree diverse. Ciò richiede comproprietà di dati, intelligence e analitica e collaborazione completa tra organizzazioni diverse. Questa struttura è anche comune nel settore dei servizi di consulenza in cui un team di consulenti clientè analitica basato sul progetto per un client.

![Ambiente condiviso tra i partner](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_08.png)



In pratica, queste strutture sono complesse, come illustrato nell'immagine seguente e richiedono personale per mantenere. Per essere efficace questa struttura si basa su di modifica tra organizzazioni e la gestione delle funzionalità di contenuto di Power BI che consente alle organizzazioni di riutilizzare le licenze di Power BI Pro acquistate per i rispettivi tenant di Power BI.

![Licenze e contenuto condiviso organizzazione](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_09.png)



Per stabilire un tenant di Power BI condiviso, è necessario creare un Azure Active Directory e almeno un account utente di Power BI Pro deve essere acquistato per un utente in active directory. Questo utente invita gli utenti richiesti per l'organizzazione condiviso. È importante in questo scenario, gli utenti di Contoso vengono considerati gli utenti esterni quando operano all'interno Power BI dell'organizzazione condivisi.

Il processo è come segue:

1. L'organizzazione condiviso viene definito come un nuovo Azure Active Directory e almeno un account utente viene creato nella nuova organizzazione. Tale utente deve avere assegnata una licenza Power BI Pro.
2. Questo utente quindi stabilisce un tenant di Power BI e invita gli utenti richiesti da Contoso e organizzazione del Partner. L'utente definisce anche qualsiasi asset di dati condiviso, come Azure Analysis Services. Contoso e gli utenti Partner possono accedere Power BI dell'organizzazione condivisi come utenti guest. Se è consentito modificare e gestire contenuto in Power BI gli utenti esterni possono usare home di Power BI, usare le aree di lavoro, caricamento o la modifica del contenuto e condividere i report. In genere, tutte le risorse condivise sono archiviate e accessibili dall'organizzazione condiviso.
3. A seconda del modo in cui le parti riconoscono la collaborazione, è possibile per ogni organizzazione sviluppare i propri dati proprietari e uso degli asset di dati condiviso warehouse analitica. È possibile distribuire ai rispettivi utenti interni con i tenant di Power BI interni.

### <a name="case-4-distribution-to-hundreds-or-thousands-of-external-partners"></a>Caso 4: Distribuzione a centinaia o migliaia di partner esterni

Anche se sono stati creati un report di affidabilità radiatore per un particolare fornitore, ora Contoso desidera creare un set di report standardizzati per centinaia di fornitori. Ciò consente a Contoso per assicurarsi che tutti i fornitori hanno l'analitica che hanno bisogno di apportare miglioramenti o per correggere difetti di produzione.

![Distribuzione di molti partner](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_10.png)


Quando un'organizzazione deve distribuire dati standardizzati e informazioni dettagliate a molte organizzazioni/gli utenti esterne, è possibile usare la condivisione Ad hoc o pianificato dello scenario di App di Power BI per creare un portale BI rapidamente e senza i costi di sviluppo estesa necessaria. Il processo per creare questo tipo un portale usando un'app di Power BI è illustrato nel caso di Studio: Creazione di un portale BI usando Power BI + Azure AD B2B – dettagliate le istruzioni più avanti in questo documento.

Una variante di questo caso comune è quando un'organizzazione sta tentando di condividerle con i consumer, in particolare durante la ricerca per l'uso di B2C di Azure con Power BI. Power BI non supporta in modo nativo Azure B2C. Se si sta valutando le opzioni per questo caso, è consigliabile usare Alternative Option 2 gli approcci alternativi comuni la sezione più avanti in questo documento.

## <a name="case-study-building-a-bi-portal-using-power-bi--azure-ad-b2b--step-by-step-instructions"></a>Case Study: Creazione di un portale BI usando Power BI e Azure AD B2B: istruzioni dettagliate

Integrazione di Power BI con Azure AD B2B consente un modo semplice e pratico per fornire agli utenti guest accesso sicuro per il portale di BI di Contoso. Contoso può configurare questa con tre passaggi:

![Creazione di un portale](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_11.png)


1. Creare un portale BI in Power BI

    La prima attività di Contoso consiste nel creare proprio portale BI in Power BI. Portale di BI di Contoso sarà costituito da una raccolta di dashboard progettati su misura e report che verrà resa disponibile a molti utenti interni e guest. È consigliabile per eseguire questa operazione in Power BI per creare un'app di Power BI. Altre informazioni sulle [App in Power BI](https://powerbi.microsoft.com/blog/distribute-to-large-audiences-with-power-bi-apps/).

- Il team di BI di Contoso consente di creare un'area di lavoro in Power BI

    ![Area di lavoro per le app](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_12.png)
    

- Altri autori vengono aggiunti all'area di lavoro

    ![Aggiungere gli autori](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_13.png)


- Il contenuto viene creato all'interno di area di lavoro

    ![Creare il contenuto all'interno dell'area di lavoro](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_14.png)


    Ora che il contenuto viene creato in un'area di lavoro, Contoso è pronto per invitare utenti guest di organizzazioni partner per utilizzare questo contenuto.

2. Invitare gli utenti guest

    Esistono due modi per Contoso invitare utenti guest per il portale di BI in Power BI:

    * Inviti pianificati
    * Inviti ad hoc

    **Inviti pianificati**

    Questo approccio, Contoso invita gli utenti guest di Azure Active Directory anticipo e quindi distribuisce il contenuto di Power BI a essi. Contoso può invitare utenti guest dal portale di Azure o tramite PowerShell. Ecco i passaggi per invitare utenti guest dal portale di Azure:

    - Amministratore di Azure AD di Contoso passa a **portale di Azure > Azure Active Directory > utenti e gruppi > tutti gli utenti > Nuovo utente guest**

    ![Utente Guest](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_15.png)


    - Aggiungere un messaggio di invito per gli utenti guest e fare clic su invito

    ![Aggiungere l'invito](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_16.png)


    > [!NOTE]
    > Per invitare utenti guest dal portale di Azure, è necessario un amministratore di Azure Active Directory del tenant.

    Se Contoso desidera invitare molti utenti guest, è possibile farlo usando PowerShell. Amministratore di Azure AD di Contoso archivia gli indirizzi di posta elettronica di tutti gli utenti guest in un file CSV. Ecco [Azure Active Directory B2B collaboration codici ed esempi di PowerShell](https://docs.microsoft.com/azure/active-directory/b2b/code-samples) e istruzioni.

    Dopo l'invito, gli utenti guest ricevono un messaggio di posta elettronica con il collegamento di invito.

    ![Collegamento di invito](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_17.png)


    Una volta che gli utenti guest di fare clic sul collegamento, possono accedere contenuti nel tenant di Azure AD di Contoso.

    > [!NOTE]
    > È possibile modificare il layout di invito tramite posta elettronica usando la funzionalità di branding di Azure AD, come descritto [qui](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-invitation-email).


    **Inviti ad hoc**

    Cosa accade se Contoso non conosce tutti gli utenti guest che vuole invitare anticipo? Oppure, se l'analista che ha creato il portale di BI in Contoso vuole distribuire il contenuto per gli utenti guest di se stesso? Questo scenario è anche supportato in Power BI con inviti ad hoc.

    L'analista può solo aggiungere gli utenti esterni all'elenco di accesso dell'app quando si pubblica. Gli utenti guest Ottiene un invito e una volta viene accettata, viene automaticamente reindirizzato al contenuto di Power BI.

    ![Aggiungere utenti esterni](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_18.png)


    > [!NOTE]
    > Gli inviti sono necessari solo la prima volta che un utente esterno viene invitato nell'organizzazione.


3. Distribuire contenuto

    Ora che il team di BI di Contoso ha creato il portale di BI e invitato utenti guest, è possibile distribuire proprio portale per gli utenti finali fornendo agli utenti guest l'accesso all'app e pubblicandola. Power BI e completa automaticamente i nomi degli utenti guest che sono stati aggiunti in precedenza per il tenant Contoso. Inoltre è possibile aggiungere a questo punto gli inviti ad hoc agli altri utenti guest.

    > [!NOTE]
    > Se si usa i gruppi di sicurezza per gestire l'accesso all'app per gli utenti esterni, usare l'approccio inviti pianificati e condividere il collegamento all'app direttamente con ogni utente esterno deve accedervi. In caso contrario, l'utente esterno potrebbe non essere in grado di installare o visualizzare il contenuto all'interno dell'app. _

    Gli utenti guest ricevono un messaggio di posta elettronica con un collegamento all'app.

    ![Collegamento di posta elettronica di invito](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_19.png)


    Facendo clic su questo collegamento, gli utenti guest vengono richiesto di eseguire l'autenticazione con l'identità dell'organizzazione.

    ![Nella pagina di accesso](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_20.png)


    Una volta vengono autenticati correttamente, vengono reindirizzati all'app di BI di Contoso.

    ![Vedere il contenuto condiviso](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_21.png)

    Gli utenti guest possono successivamente accedere all'app di Contoso o facendo clic sul collegamento nel messaggio di posta elettronica il collegamento di segnalibri. Contoso può anche semplificare per gli utenti guest tramite l'aggiunta di questo collegamento per qualsiasi portale extranet esistente che già usano gli utenti guest.

4. Passaggi successivi

    Usa un'app di Power BI e Azure AD B2B, Contoso è stata in grado di creare rapidamente un portale BI per i suoi fornitori in modo senza codice. Ciò notevolmente semplificata la distribuzione di analitica standardizzato per tutti i fornitori che hanno bisogno.

    Mentre l'esempio illustra come un singolo report comune potrebbe essere distribuito tra fornitori, Power BI possono andare molto più complessa. Per assicurare che ogni partner veda solo i dati pertinenti a se stessi, sicurezza a livello di riga possono essere aggiunti facilmente al modello di report e i dati. La sicurezza dei dati per la sezione partner esterni più avanti in questo documento descrive questo processo nei dettagli.

    Dashboard e report spesso singoli devono essere incorporati in un portale esistente. Questa impostazione può essere eseguita anche riutilizzare molte delle tecniche illustrate nell'esempio. Tuttavia, in tali situazioni può risultare più semplice incorporare report o dashboard direttamente da un'area di lavoro. Il processo per l'invito e l'assegnazione dell'autorizzazione di sicurezza per il richiedono gli utenti restano invariati.

## <a name="under-the-hood-how-is-lucy-from-supplier1-able-to-access-power-bi-content-from-contosos-tenant"></a>Dietro le quinte: Quali sono le Lucy da Supplier1 in grado di accedere al contenuto di Power BI dal tenant di Contoso?

Ora che abbiamo visto come Contoso è in grado di distribuire facilmente il contenuto di Power BI agli utenti guest di organizzazioni partner, esaminiamo il funzionamento dietro le quinte.

Quando Contoso invitati [ lucy@supplier1.com ](mailto:lucy@supplier1.com) alla directory di Azure AD crea un collegamento tra [ Lucy@supplier1.com ](mailto:Lucy@supplier1.com) e il tenant di Azure AD di Contoso. Questo collegamento consente ad Azure AD sa che Lucy@supplier1.com possa accedere al contenuto nel tenant Contoso.

Quando si tenta di accedere alle app di Power BI di Contoso Lucy, Azure AD verifica che Lucy possono accedere al tenant di Contoso e quindi fornisce un token che indica che è stata autenticata Lucy accesso contenuto nel tenant Contoso Power BI. Power BI Usa questo token per autorizzare e assicurarsi che Lucy abbia accesso all'app di Power BI di Contoso.

![Verifica e autorizzazione](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_22.png)

Integrazione di Power BI con Azure AD B2B funziona con tutti gli indirizzi di posta elettronica aziendale. Se l'utente non ha un'identità Azure AD, questi potrebbe essere richiesto di crearne una. L'immagine seguente mostra il flusso dettagliato:

![Diagramma di flusso di integrazione](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_23.png)


È importante riconoscere che l'account Azure AD verrà utilizzata o creato nella parte esterna di Azure AD, questo verrà assicurarsi ogni volta che è possibile che Lucy può utilizzare il proprio nome utente e la password e le proprie credenziali automaticamente smetterà di funzionare in altri tenant Anna lascia l'azienda quando l'organizzazione Usa Azure AD.

## <a name="licensing"></a>Gestione delle licenze

Contoso può scegliere uno dei tre approcci di utenti guest di licenza dai propri fornitori e le organizzazioni partner ad accedere a contenuto di Power BI.

> [!NOTE]
> _Livello gratuito di B2B di Azure AD è sufficiente usare Power BI con Azure AD B2B. Alcune funzionalità di Azure AD B2B avanzate, ad esempio i gruppi dinamici richiedere licenze aggiuntive. Consultare la documentazione di Azure AD B2B per informazioni aggiuntive:_ [_https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance_](https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance)

### <a name="approach-1-contoso-uses-power-bi-premium"></a>Approccio 1: Contoso USA Power BI Premium

Con questo approccio, Contoso acquista capacità di Power BI Premium e assegna il contenuto del portale di BI a questa capacità. Ciò consente agli utenti guest di organizzazioni partner di accedere alle app di Power BI di Contoso senza alcuna licenza di Power BI.

Gli utenti esterni sono inoltre soggetti al consumo di esperienze sole offerto agli utenti "Gratuiti" in Power BI durante l'utilizzo di contenuto all'interno di Power BI Premium.

Contoso può anche sfruttare altre funzionalità di Power BI premium per le app come maggiori frequenze di aggiornamento, capacità dedicata e modelli di grandi dimensioni.

![Funzionalità aggiuntive](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_24.png)


### <a name="approach-2-contoso-assigns-power-bi-pro-licenses-to-guest-users"></a>Approccio 2: Contoso assegna licenze di Power BI Pro agli utenti guest

Con questo approccio, Contoso assegna le licenze pro per gli utenti guest da partner alle organizzazioni, questa operazione può essere eseguita dall'interfaccia di amministrazione di Microsoft 365 di Contoso. Ciò consente agli utenti guest di organizzazioni partner di accedere alle app di Power BI di Contoso senza dover acquistare una licenza a se stessi. Ciò risulta appropriato per la condivisione con utenti esterni, la cui organizzazione non ha adottato ancora Power BI.

> [!NOTE]
> _Licenza pro di Contoso si applica agli utenti guest solo quando accedono al contenuto nel tenant Contoso. Le licenze Pro attivare l'accesso al contenuto che non si trova in una capacità di Power BI Premium. Tuttavia, gli utenti esterni con una licenza Pro sono limitati per impostazione predefinita per un'esperienza unica di consumo. Può trattarsi di modifica utilizzando l'approccio descritto nel_ _consentendo agli utenti esterni di modificare e gestire il contenuto all'interno di Power BI_ _sezione più avanti in questo documento._

![Informazioni sulle licenze](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_25.png)


### <a name="approach-3-guest-users-bring-their-own-power-bi-pro-license"></a>Approccio 3: Gli utenti guest di spostare le licenze di Power BI Pro

Con questo approccio, Supplier 1 assegna una licenza Power BI Pro per Lucy. Anna può quindi accedere app di Power BI di Contoso con questa licenza. Dal momento Lucy è possibile utilizzare la sua licenza Pro dalla propria organizzazione quando si accede a un ambiente esterno di Power BI, questo approccio viene talvolta detta _bring your own license per_ (BYOL). Se entrambe le organizzazioni usano Power BI, questo offre licenze vantaggiose per la soluzione complessiva di analitica e riduce al minimo il sovraccarico dell'assegnazione delle licenze agli utenti esterni.

> [!NOTE]
> _La licenza pro a Lucy indicata dal fornitore 1 si applica a qualsiasi tenant di Power BI in questo momento Lucy sia un utente guest. Le licenze Pro attivare l'accesso al contenuto che non si trova in una capacità di Power BI Premium. Tuttavia, gli utenti esterni con una licenza Pro sono limitati per impostazione predefinita per un'esperienza unica di consumo. Può trattarsi di modifica utilizzando l'approccio descritto nel_ _consentendo agli utenti esterni di modificare e gestire il contenuto all'interno di Power BI_ _sezione più avanti in questo documento._

![Requisiti di licenza Pro](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_26.png)

## <a name="data-security-for-external-partners"></a>Protezione dei dati per i partner esterni

In genere quando si usano più fornitori esterni, Contoso deve assicurarsi che ogni fornitore veda i dati solo sui propri prodotti. Sicurezza basata sull'utente e la sicurezza a livello di riga dinamica semplificano notevolmente il facile con Power BI.

### <a name="user-based-security"></a>Sicurezza basata sull'utente

Una delle funzionalità più potenti di Power BI è sicurezza a livello di riga. Questa funzionalità consente a Contoso di creare un singolo report e set di dati, ma comunque applicare le regole di sicurezza diverse per ogni utente. Per una spiegazione dettagliata, vedere [sicurezza a livello di riga (RLS)](https://powerbi.microsoft.com/documentation/powerbi-admin-rls/).

Integrazione di Power BI con Azure AD B2B consente a Contoso assegnare le regole di sicurezza a livello di riga per gli utenti guest non appena vengono invitati a tenant Contoso. Come abbiamo visto prima, Contoso può aggiungere utenti guest tramite pianificati o inviti ad hoc. Se Contoso desidera implementare la sicurezza a livello di riga, è consigliabile usare inviti pianificati per aggiungere gli utenti guest in anticipo rispetto alla volta e assegnando loro i ruoli di protezione prima di condividere il contenuto. Se Contoso utilizza invece inviti ad hoc, potrebbe esserci un breve periodo di tempo in cui gli utenti guest non saranno in grado di visualizzare tutti i dati.

> [!NOTE]
> Per supportare le richieste al team IT, perché gli utenti vedranno sia vuota o interrotta alla ricerca di report/dashboard durante l'apertura di una condivisione di un collegamento nel messaggio di posta elettronica ricevono può causare questo ritardo nell'accesso ai dati protetti da a livello di riga quando l'utilizzo ad hoc invita. Pertanto, è consigliabile usare inviti pianificati in questo scenario.* *

Di seguito viene illustrato ciò con un esempio.

Come accennato in precedenza, Contoso dispone di fornitori in tutto il mondo, e che si desidera assicurarsi che gli utenti di organizzazioni i fornitori ottengano informazioni dettagliate dai dati dal proprio territorio.  Ma gli utenti da Contoso possono accedere tutti i dati. Anziché creare numerosi report diversi, Contoso crea un singolo report e i filtri dei dati in base all'utente di visualizzarlo.

![Contenuto condiviso](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_27.png)

Per assicurarsi che Contoso è possibile filtrare i dati in base a chi si connette, due ruoli vengono creati in Power BI desktop. Uno per filtrare tutti i dati da SalesTerritory "Europe" e un'altra per "North America".

![Gestione dei ruoli](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_28.png)

Ogni volta che i ruoli vengono definiti nel report, un utente deve essere assegnato a un ruolo specifico per poter ottenere l'accesso a tutti i dati. L'assegnazione dei ruoli si verifica all'interno del servizio Power BI ( **set di dati > sicurezza** )

![Impostazione della sicurezza](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_29.png)

Verrà visualizzata una pagina in cui il team di BI di Contoso può visualizzare i due ruoli vengono creati.  Team di BI di Contoso ora possibile assegnare utenti ai ruoli.

![Sicurezza a livello di riga](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_30.png)

Nell'esempio di Contoso viene aggiunta di un utente in un'organizzazione partner con indirizzo di posta elettronica "[adam@themeasuredproduct.com](mailto:adam@themeasuredproduct.com)" al ruolo Europe:

![Impostazioni di sicurezza a livello di riga](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_31.png)

Quando questo viene risolto da Azure AD, Contoso possibile visualizzare il nome visualizzato nella finestra pronto per essere aggiunto:

![Mostra i ruoli](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_32.png)

A questo punto quando l'utente apre l'app a cui è stata condivisa con lui, vede solo un report con i dati dall'Europa:

![Visualizzare il contenuto](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_33.png)

### <a name="dynamic-row-level-security"></a>Sicurezza a livello di riga dinamica

Un altro argomento interessante consiste nel verificare il lavoro a livello di sicurezza (RLS) con Azure AD B2B di riga dinamica.

In breve, la sicurezza a livello di riga dinamica funziona filtrando i dati nel modello basato su nome utente della persona che ci si connette a Power BI. Anziché aggiungere più ruoli per i gruppi di utenti, si definiscono gli utenti nel modello. Non descriveremo in dettaglio di seguito il modello. Kasper de Jong offre un'operazione di scrittura dettagliati su tutte le versioni di sicurezza a livello di riga in [foglio informativo di sicurezza dinamici di Power BI Desktop](https://www.kasperonbi.com/power-bi-desktop-dynamic-security-cheat-sheet/)e nella [questo white paper](https://msdn.microsoft.com/library/jj127437.aspx) .

Verrà ora esaminato un piccolo esempio, Contoso dispone di un semplice report sulle vendite dai gruppi:

![Contenuto di esempio](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_34.png)

A questo punto il report deve essere condivisa con due utenti guest e un utente interno: l'utente interno può visualizzare tutto, ma gli utenti guest possono visualizzare solo i gruppi di cui hanno accesso. Ciò significa che è necessario filtrare i dati solo per gli utenti guest. Per filtrare i dati in modo appropriato, Contoso Usa il modello a livello di riga dinamica come descritto nel post di blog e white paper. Ciò significa, Contoso aggiunge i nomi utente ai dati stessi:

![Visualizzare gli utenti a livello di riga ai dati stessi](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_35.png)

Quindi, Contoso crea il modello di dati appropriato che filtra i dati in modo appropriato con le relazioni a destra:

![Vengono visualizzati i dati appropriati](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_36.png)

Per filtrare i dati automaticamente in base a chi è collegato, Contoso deve creare un ruolo che passa l'utente che effettua la connessione. In questo caso, Contoso crea due ruoli: il primo è "securityrole" che consente di filtrare la tabella degli utenti con il nome utente corrente dell'utente connesso a Power BI (Ciò funziona anche per gli utenti guest B2B di Azure AD).

![Gestisci ruoli](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_37.png)

Contoso crea anche un altro "AllRole" per gli utenti interni che possono vedere tutti gli elementi: questo ruolo non dispone di qualsiasi predicato di sicurezza.

Dopo aver caricato il file di Power BI desktop al servizio, Contoso può assegnare gli utenti guest a "SecurityRole" e "AllRole" gli utenti interni

A questo punto, quando gli utenti guest aprono il report, si vede solo le vendite da gruppo a:

![Solo da un gruppo](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_38.png)

Nella matrice a destra è possibile visualizzare il risultato della funzione UserName () e userPrincipalName () restituiscono entrambi che indirizzo di posta elettronica gli utenti guest.

L'utente interno ottiene ora visualizzare tutti i dati:

![Tutti i dati visualizzati](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_39.png)

Come può notare, a livello di riga dinamica funziona con gli utenti sia interni o guest.

> [!NOTE]
> Questo scenario funziona anche quando si usa un modello in Azure Analysis Services. In genere il servizio di analisi di Azure è connessa ad Azure AD come Power BI stesso, in tal caso, Azure Analysis Services conosca anche gli utenti guest invitati tramite Azure AD B2B.

## <a name="connecting-to-on-premises-data-sources"></a>La connessione a origini dati locali

Power BI offre la funzionalità per consentire a sfruttare le caratteristiche delle origini dati locali, ad esempio Contoso [SQL Server Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/) oppure [SQL Server](https://powerbi.microsoft.com/documentation/powerbi-gateway-kerberos-for-sso-pbi-to-on-premises-data/) direttamente grazie alla [gateway dati locale](https://powerbi.microsoft.com/documentation/powerbi-gateway-onprem/). È anche possibile accedere alle origini dei dati con le stesse credenziali utilizzate con Power BI.

> [!NOTE]
> Quando si installa un gateway per connettersi al tenant di Power BI, è necessario usare un utente creato all'interno del tenant. Gli utenti esterni non è possibile installare un gateway e connetterlo al tenant. _

Per gli utenti esterni, questo potrebbe essere più complesso, poiché gli utenti esterni non sono in genere noti da locale AD. Power BI offre una soluzione alternativa per questo, consentendo agli amministratori di Contoso di eseguire il mapping di nomi utente esterni per i nomi utente interni come descritto in [gestire l'origine dati - Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/). Ad esempio, [ lucy@supplier1.com ](mailto:lucy@supplier1.com) possono essere mappati ai [lucy\_supplier1\_com #EXT@contoso.com](mailto:lucy_supplier1_com).

![Mapping dei nomi utente](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_40.png)

Questo metodo è bene se Contoso ha solo un numero limitato di utenti o se Contoso può eseguire il mapping di tutti gli utenti esterni a un singolo account interni. Per scenari più complessi in cui ogni utente deve avere le proprie credenziali, è disponibile un approccio più avanzato che utilizza [attributi Active Directory personalizzati](https://technet.microsoft.com/library/cc961737.aspx) per eseguire il mapping come descritto in [gestire l'origine dati - Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/). Ciò consente all'amministratore di Contoso di definire un mapping per ogni utente in Azure AD (anche utenti B2B esterni).  Questi attributi possono essere impostati tramite il modello a oggetti Active Directory usando script o codice in modo che Contoso può automatizzare completamente il mapping su invito o su una frequenza pianificata.

## <a name="enabling-external-users-to-edit-and-manage-content-within-power-bi"></a>Consentire a utenti esterni modificare e gestire il contenuto all'interno di Power BI

Contoso può consentire agli utenti esterni di contribuire al contenuto all'interno dell'organizzazione come descritto in precedenza la tra organizzazioni la modifica e la gestione della sezione di contenuto di Power BI.

> [!NOTE]
> Per modificare e gestire il contenuto all'interno di Power BI dell'organizzazione, l'utente deve avere una licenza Power BI Pro in un'area di lavoro diverso da area di lavoro personale. Gli utenti possono ottenere licenze Pro come illustrato nelle the_ _Licensing__section di questo documento._

Il portale di amministrazione di Power BI fornisce il **consentire agli utenti guest esterni di modificare e gestire contenuto all'interno dell'organizzazione** impostazione nelle impostazioni del Tenant. Per impostazione predefinita, l'impostazione è impostata su disabled, vale a dire gli utenti esterni ottengono un'esperienza di sola lettura vincolata per impostazione predefinita. L'impostazione si applica agli utenti con UserType impostato su Guest di Azure AD. Nella tabella seguente vengono descritti i comportamenti gli utenti riscontrano a seconda del suo UserType e le impostazioni di configurazione.

| **Tipo di utente in Azure AD** | **Consentire agli utenti guest esterni modificare e gestire le impostazioni del contenuto** | **Comportamento** |
| --- | --- | --- |
| Guest | Disabilitato per l'utente (impostazione predefinita) | Per ogni visualizzazione solo degli elementi del consumo. Consente l'accesso di sola lettura ai report, dashboard e le app quando viene visualizzato tramite un URL inviato per l'utente Guest. Le app di Power BI per dispositivi mobili forniscono una visualizzazione di sola lettura per l'utente guest. |
| Guest | Per l'utente abilitata | L'utente esterno ottiene accesso all'esperienza di Power BI completo, anche se alcune funzionalità non sono disponibili ad essi. L'utente esterno deve accedere a Power BI con l'URL del servizio Power BI con le informazioni del tenant incluse. Ottiene l'utente può esaminare l'esperienza iniziale, un'area di lavoro personale e in base alle autorizzazioni, visualizzare e creare il contenuto. </br></br> Le app di Power BI per dispositivi mobili forniscono una visualizzazione di sola lettura per l'utente guest. |

> [!NOTE]
> Gli utenti esterni in Azure AD possono essere impostati anche membro di UserType. Non si è attualmente supportato in Power BI.

Nel portale di amministrazione di Power BI, l'impostazione è illustrata nell'immagine seguente.

![Impostazioni dell'amministratore](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_41.png)

Gli utenti guest di ottengono l'utilizzo predefinito di sola lettura e che possono modificare e gestire il contenuto. Il valore predefinito è Disabled, vale a dire che tutti gli utenti Guest hanno l'esperienza di sola lettura. L'amministratore di Power BI possono abilitare l'impostazione per tutti gli utenti Guest nell'organizzazione o per gruppi di sicurezza specifici definiti in Azure AD. Nell'immagine seguente, l'amministratore di Contoso Power BI creato un gruppo di sicurezza in Azure AD per gestire quali utenti esterni possono modificare e gestire il contenuto nel tenant Contoso.

Per aiutare questi utenti per accedere a Power BI, fornire l'URL del Tenant. Per trovare l'URL del tenant, seguire questa procedura.

1. Nel servizio Power BI, nel menu in alto, selezionare la Guida ( **?** ) quindi **informazioni su Power BI**.
2. Cercare il valore accanto a **URL Tenant**. Questo è l'URL del tenant è possibile condividere con gli utenti guest.

    ![URL tenant](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_42.png)

Quando si usa Consenti agli utenti guest esterni per modificare e gestire il contenuto all'interno dell'organizzazione, gli utenti guest specificato ottenere l'accesso a Power BI dell'organizzazione e notano contenuti a cui hanno l'autorizzazione. Si può accedere alle Home, esplorare e contribuire al contenuto per le aree di lavoro, installare le App in cui sono presenti nell'elenco di accesso e includere un'area di lavoro personale. Possono creare aree di lavoro che fanno uso dell'esperienza delle nuove aree di lavoro o esserne amministratori.

> [!NOTE]
> Quando si usa questa opzione assicurarsi di consultare la sezione di governance di questo documento, poiché le impostazioni di Azure AD predefinito impediscono agli utenti Guest per usare determinate funzionalità come selezione di utenti che possono comportare una riduzione experience.* *

Per gli utenti guest abilitati tramite gli utenti guest esterni Consenti per modificare e gestire il contenuto nell'impostazione del tenant dell'organizzazione, alcune esperienze non sono a loro disposizione. Per aggiornare o pubblicare i report, gli utenti guest è necessario usare il web del servizio Power BI dell'interfaccia utente, tra cui recupera dati per caricare i file di Power BI Desktop. Le esperienze seguenti non sono supportate:

- Pubblicazione diretta da Power BI Desktop al servizio Power BI
- Gli utenti guest non possono usare Power BI desktop per connettersi ai set di dati del servizio nel servizio Power BI
- Aree di lavoro classiche associate a gruppi di Office 365: Gli utenti guest non possono creare queste aree di lavoro o esserne amministratori; possono essere membri.
- L'invio di inviti ad hoc non è supportato per gli elenchi di accesso all'area di lavoro
- Power BI Publisher per Excel non è supportato per gli utenti guest
- Gli utenti guest non possono installare un Power BI Gateway e connetterlo all'organizzazione
- Gli utenti guest non possono installare app di pubblicazione per l'intera organizzazione
- Gli utenti guest non possono usare, creare, aggiornare o installare pacchetti di contenuto dell'organizzazione
- Gli utenti guest non possono usare Analizza in Excel
- Gli utenti guest non possono essere @mentioned in commenti (questa funzionalità verrà aggiunta in una versione futura)
- Gli utenti guest non è possibile utilizzare le sottoscrizioni (questa funzionalità verrà aggiunta in una versione futura)
- Gli utenti guest che usano questa funzionalità dovrebbero avere un account aziendale o dell'istituto di istruzione. Gli utenti guest usando sia account personali sperimentare altre limitazioni a causa delle restrizioni di accesso.



## <a name="governance"></a>Governance

### <a name="additional-azure-ad-settings-that-affect-experiences-in-power-bi-related-to-azure-ad-b2b"></a>Ulteriori impostazioni di Azure AD che influiscono sulle esperienze di Power BI correlato a Azure AD B2B

Quando si usa la condivisione di B2B di Azure AD, l'amministratore di Azure Active Directory consente di controllare aspetti dell'esperienza dell'utente esterno. Questi sono controllati nella pagina Impostazioni di collaborazione esterna all'interno delle impostazioni per il Tenant di Azure Active Directory.

Informazioni dettagliate sulle impostazioni sono disponibili qui:

[https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations](https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations)

> [!NOTE]
> Per impostazione predefinita, le autorizzazioni di utenti Guest sono limitate opzione è impostata su Sì, in modo che gli utenti Guest all'interno di Power BI non dispongono di esperienze in particolare, racchiudere la condivisione in selezione utenti di interfacce utente non funzionano per tali utenti. È importante rivolgersi all'amministratore di Azure AD per impostarlo su No, come illustrato di seguito per garantire una buona experience.* *

![Impostazioni di collaborazione esterna](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_43.png)


### <a name="control-guest-invites"></a>Inviti guest di controllo

Gli amministratori di Power BI è possono controllare la condivisione esterna per Power BI, visitare il portale di amministrazione di Power BI. Tuttavia, gli amministratori tenant possono inoltre controllare la condivisione esterna con vari criteri di Azure AD.  Questi criteri consentono tenant agli amministratori di

- Disattivare gli inviti per gli utenti finali
- Solo gli amministratori e gli utenti nel ruolo mittente dell'invito Guest possono invitare
- Gli amministratori, il ruolo mittente dell'invito Guest e i membri possono invitare
- Tutti gli utenti, inclusi gli utenti Guest, possono invitare

È possibile leggere altre informazioni su questi criteri nel [delegare gli inviti per collaborazione B2B di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-delegate-invitations).

Tutte le azioni di Power BI da utenti esterni sono inoltre [controllati nel nostro portale controllo](https://powerbi.microsoft.com/documentation/powerbi-admin-auditing/).

### <a name="conditional-access-policies-for-guest-users"></a>Criteri di accesso condizionale per gli utenti guest

Contoso può applicare i criteri di accesso condizionale per gli utenti guest che accedono al contenuto dal tenant Contoso. È possibile trovare istruzioni dettagliate in [accesso condizionale per gli utenti di collaborazione B2B](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-mfa-instructions).

## <a name="common-alternative-approaches"></a>Approcci alternativi comuni

Anche se Azure AD B2B rende più semplice condividere dati e report tra organizzazioni diverse, esistono diversi altri approcci che vengono comunemente utilizzati e potrebbero essere superiore in alcuni casi.

### <a name="alternative-option-1-create-duplicate-identities-for-partner-users"></a>Opzione alternativa 1: Creare le identità duplicate per partner di utenti

Con questa opzione, Contoso doveva creare manualmente le identità duplicate per ogni utente partner nel Contoso Tenant, come illustrato nell'immagine seguente. Quindi all'interno di Power BI, Contoso può condividere alle identità assegnata di report appropriate, dashboard o le app.

![Impostazione dei nomi e i mapping appropriati](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_44.png)

Motivi per scegliere questa alternativa:

- Dato che l'identità dell'utente è controllato dall'organizzazione, le relative servizio, ad esempio indirizzo di posta elettronica, SharePoint, e così via sono anche all'interno del controllo della propria organizzazione. Gli amministratori IT possono reimpostare le password, disabilitare l'accesso agli account o controllare le attività in questi servizi.
- Gli utenti che utilizzano gli account personali per la propria attività spesso sono limitate di accedere a determinati servizi, pertanto potrebbe essere necessario un account aziendale.
- Alcuni servizi funzionano solo gli utenti dell'organizzazione. Ad esempio, uso di Intune per gestire il contenuto nei dispositivi personali o per dispositivi mobili degli utenti esterni con B2B di Azure potrebbe non essere possibile.

Motivi per non sceglie questa alternativa:

- Gli utenti di organizzazioni partner devono ricordare due insiemi di credenziali: uno per accedere al contenuto dalla propria organizzazione e l'altro per accedere al contenuto da Contoso. Si tratta di una seccatura per questi utenti guest e molti utenti guest sono confusi da questa esperienza.
- Contoso deve acquistano e assegnano licenze per utente a questi utenti. Se un utente deve ricevere posta elettronica o usare le applicazioni di office, sono necessarie le licenze appropriate, tra cui Power BI Pro per modificare e condividere il contenuto di Power BI.
- Contoso potrebbe voler applicare criteri di governance per gli utenti esterni rispetto agli utenti interni e autorizzazione più rigorosi. A tale scopo, Contoso deve creare una nomenclatura interna per gli utenti esterni e tutti gli utenti di Contoso deve essere a conoscenza la nomenclatura.
- Quando l'utente lascia l'organizzazione, si continua ad avere accesso alle risorse di Contoso fino a quando l'amministratore di Contoso consente di eliminare manualmente il proprio account
- Gli amministratori di Contoso sono necessario gestire l'identità per l'utente guest, tra cui la creazione, la reimpostazione della password, e così via.

### <a name="alternative-option-2-create-a-custom-power-bi-embedded-application-using-custom-authentication"></a>Opzione alternativa 2: Creare un'applicazione di Power BI Embedded personalizzata usando l'autenticazione personalizzata

Un'altra opzione per Contoso consiste nel compilare la propria applicazione Power BI embedded personalizzata con l'autenticazione personalizzata (["App owns data"](https://docs.microsoft.com/power-bi/developer/embed-sample-for-customers)). Sebbene molte organizzazioni non si dispongano di tempo o risorse per creare un'applicazione personalizzata per la distribuzione di Power BI content ai propri partner esterni, per alcune organizzazioni è l'approccio migliore e merita valutando con attenzione.

Spesso, le organizzazioni hanno portali di partner esistente che centralizzare l'accesso a tutte le risorse dell'organizzazione per i partner, forniscono l'isolamento dalle risorse interne dell'organizzazione e offrono un'esperienza semplificata per i partner supportare molti partner di e i singoli utenti.

![Portali di molti partner](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_45.png)

Nell'esempio precedente, gli utenti dall'account di accesso ogni fornitore al portale di Partner di Contoso che utilizza AAD come provider di identità. Potrebbe usare AAD B2B, B2C di Azure, le identità native oppure attuare la federazione con un numero qualsiasi di altri provider di identità. L'utente potrebbe accedere e accedere a una build del portale di partner con App Web di Azure o un'infrastruttura simile.

All'interno dell'app web, report di Power BI sono incorporati da una distribuzione con Power BI Embedded. L'app web semplificherebbe l'accesso ai report e i servizi correlati in un'esperienza coerente mira a semplificare dei fornitori interagire con Contoso. Questo portale ambiente saranno così isolato da Azure Active Directory interna di Contoso e ambiente di Power BI per garantire suppliers interno di Contoso non è riuscito ad accedere a tali risorse. In genere, vengono archiviati dati in un data warehouse del Partner di separato per garantire l'isolamento dei dati nonché. Questo isolamento offre vantaggi poiché limita il numero di utenti esterni con accesso diretto ai dati dell'organizzazione, limitare i dati che potrebbe potenzialmente essere disponibili per l'utente esterno e limitando la condivisione accidentale con utenti esterni.

Usa Power BI Embedded, il portale è possibile sfruttare licenze vantaggioso, utilizzo token dell'applicazione o dell'utente master più capacità premium acquistata in un modello di Azure, che semplifica l'assegnazione delle licenze agli utenti finali rappresentano una preoccupazione e può aumentare/ridurre le prestazioni in base previsto on utilizzo. Il portale può offrire una qualità complessiva e l'esperienza coerente in quanto partner di accedere a un unico portale progettato tenendo conto delle esigenze del Partner. Infine, poiché Power BI Embedded basati su soluzioni sono in genere progettate per essere multi-tenant, rende più semplice garantire l'isolamento tra le organizzazioni partner.

Motivi per scegliere questa alternativa:

- Diventa più facile da gestire come il numero di organizzazioni partner. Poiché i partner vengono aggiunti a una directory distinta isolata dalla directory di AAD interni di Contoso, semplifica la governance compiti e consente di impedire la condivisione accidentale di dati interne per gli utenti esterni.
- Portali di Partner tipici sono altamente con marchio di esperienze con esperienze coerenti tra i partner e semplificati per soddisfare le esigenze dei partner tipico. Contoso può pertanto offrire un'esperienza complessiva migliore per i partner grazie all'integrazione di tutti i servizi necessari in un unico portale.
- Costi di licenza per scenari avanzati, ad esempio modifica il contenuto all'interno di Power BI Embedded è coperto da Azure acquistato Power BI Premium e non richiedono l'assegnazione delle licenze di Power BI Pro agli utenti.
- Offre un migliore isolamento tra i partner se progettati come una soluzione multi-tenant.
- Portale per i Partner spesso include altri strumenti per il partner di là delle App, dashboard e report Power BI.

Motivi per non sceglie questa alternativa:

- Notevole impegno è necessario per compilare, operare e gestire tali un portale rendendo un investimento significativo nel tempo e risorse.
- Possibile soluzione è molto più tempo rispetto all'uso di B2B di condivisione dopo un'attenta pianificazione ed esecuzione tra più flussi di lavoro è obbligatorio.
- In cui sono presenti un numero minore di partner è probabilmente troppo alta da giustificare l'impegno necessario per questa soluzione alternativa.
- Collaborazione con la condivisione ad hoc è lo scenario principale riscontrato dall'organizzazione.
- I report e dashboard sono diversi per ogni partner. Questa alternativa introduce gestione overhead oltre alla condivisione direttamente con i partner.



## <a name="faq"></a>DOMANDE FREQUENTI

**Il Contoso può inviare un invito che viene riscattato automaticamente, in modo che l'utente è semplicemente "pronto"? Oppure l'utente dispone sempre di fare clic per visualizzare l'URL di riscatto?**

L'utente finale deve sempre fare clic sull'esperienza di consenso prima di accedere a contenuto.

Se si invitando molti utenti guest, è consigliabile delegare questo dagli amministratori di core Azure AD dal [aggiunta di un utente al ruolo mittente dell'invito guest nell'organizzazione risorse](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-add-guest-to-role). L'utente può invitare altri utenti nell'organizzazione partner usando l'interfaccia utente di accesso, gli script di PowerShell, o le API. In questo modo si riduce il carico amministrativo negli amministratori di Azure AD per invitare o inviati di nuovo gli inviti agli utenti dell'organizzazione partner.

**Può Contoso imporre multi-factor authentication per gli utenti guest se il partner non dispongono dell'autenticazione a più fattori?**

Sì. Per altre informazioni, vedere [accesso condizionale per gli utenti di collaborazione B2B](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-mfa-instructions).

**Come la collaborazione B2B funziona quando il partner invitato Usa la federazione per aggiungere la propria autenticazione locale?**

Se il partner ha un tenant di Azure AD federato all'infrastruttura di autenticazione in locale, in locale single sign-on (SSO) viene automaticamente applicato. Se il partner non ha un tenant di Azure AD, un account Azure AD può essere creato per i nuovi utenti.

**È possibile invitare utenti guest con account di posta elettronica consumer?**

Invitare utenti guest con account di posta elettronica consumer è supportato in Power BI. Sono inclusi domini, ad esempio hotmail.com, outlook.com e gmail.com. Tuttavia, tali utenti potrebbero verificarsi limitazioni oltre gli elementi di lavoro gli utenti con o dell'istituto di istruzione verifica.
