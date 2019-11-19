---
title: Amministrazione di Power BI - Domande frequenti
description: Risposte alle domande frequenti sull'iscrizione a Power BI, sulla gestione del tenant e su altre attività amministrative.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 6cc29bd1d06e948facf1058411759c15841a8352
ms.sourcegitcommit: 2b7beec5237a597bab2da8eb6ffe69122a5d2ed9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/02/2019
ms.locfileid: "73442930"
---
# <a name="administering-power-bi---frequently-asked-questions-faq"></a>Amministrazione di Power BI - Domande frequenti

Questo articolo contiene le risposte alle domande frequenti sull'amministrazione di Power BI. Per una panoramica dell'amministrazione di Power BI, vedere [Che cos'è l'amministrazione di Power BI?](service-admin-administering-power-bi-in-your-organization.md).

## <a name="whats-in-this-article"></a>Contenuto dell'articolo

### <a name="sign-up-for-power-bi-section"></a>Sezione relativa all'iscrizione a Power BI

* [Uso di PowerShell](#using-powershell)
* [In che modo gli utenti si iscrivono a Power BI?](#how-do-users-sign-up-for-power-bi)
* [In che modo si iscrivono i singoli utenti dell'organizzazione?](#how-do-individual-users-in-my-organization-sign-up)
* [Come si può impedire agli utenti di aggiungersi all'attuale tenant di Office 365?](#how-can-i-prevent-users-from-joining-my-existing-microsoft-365-tenant)
* [Come si può consentire agli utenti di aggiungersi al tenant esistente di Office 365?](#how-can-i-allow-users-to-join-my-existing-microsoft-365-tenant)
* [Come si verifica se è attivato il blocco nel tenant?](#how-do-i-check-if-i-have-the-block-on-in-the-tenant)
* [Come è possibile impedire agli utenti di iniziare a usare Power BI?](#how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi)
* [Come si può consentire agli utenti esistenti di iscriversi a Power BI?](#how-can-i-allow-my-existing-users-to-sign-up-for-power-bi)

### <a name="administration-of-power-bi-section"></a>Sezione relativa all'amministrazione di Power BI

* [Come cambierà la gestione delle identità per gli attuali utenti dell'organizzazione?](#how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today)
* [Come si gestisce Power BI?](#how-do-we-manage-power-bi)
* [Qual è la procedura per gestire un tenant creato da Microsoft per gli utenti?](#what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users)
* [Se si hanno più domini, è possibile controllare il tenant di Microsoft 365 in cui vengono aggiunti gli utenti?](#if-i-have-multiple-domains-can-i-control-the-microsoft-365-tenant-that-users-get-added-to)
* [Come si rimuove Power BI per gli utenti che hanno già effettuato l'iscrizione?](#how-do-i-remove-power-bi-for-users-that-already-signed-up)
* [Come si può sapere se nuovi utenti si aggiungono al tenant?](#how-do-i-know-when-new-users-have-joined-my-tenant)
* [È necessario prepararsi per altro?](#are-there-any-additional-things-i-should-prepare-for)
* [Dove si trova il tenant di Power BI?](#where-is-my-power-bi-tenant-located)
* [Che cos'è il Contratto di servizio di Power BI?](#what-is-the-power-bi-sla)
* [In che modo Power BI gestisce la disponibilità elevata e il failover?](#how-does-power-bi-handle-high-availability-and-failover)

### <a name="security-in-power-bi-section"></a>Sezione relativa alla sicurezza in Power BI

* [Power BI soddisfa i requisiti di conformità nazionali, regionali e specifici del settore?](#does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements)
* [Come funziona la sicurezza in Power BI?](#how-does-security-work-in-power-bi)

## <a name="sign-up-for-power-bi"></a>Iscriversi a Power BI

### <a name="using-powershell"></a>Uso di PowerShell

Alcune delle procedure di questa sezione richiedono gli script di Windows PowerShell. Se no si ha familiarità con PowerShell, vedere [Guida introduttiva a Windows PowerShell](http://go.microsoft.com/fwlink/p/?LinkID=286814). Per eseguire gli script, installare la versione a 64 bit più recente di [Azure Active Directory PowerShell per Graph](/powershell/azure/active-directory/).

### <a name="how-do-users-sign-up-for-power-bi"></a>In che modo gli utenti si iscrivono a Power BI?

Un amministratore di Microsoft 365 può iscriversi a Power BI tramite il [sito Web Power BI](https://powerbi.microsoft.com) o la pagina [Acquisto di servizi](https://admin.microsoft.com/AdminPortal/Home#/catalog) nell'interfaccia di amministrazione di Microsoft 365. Quando un amministratore di Microsoft 365 si iscrive a Power BI, può poi assegnare le licenze utente agli utenti che devono avere accesso al servizio.

Anche i singoli utenti dell'organizzazione potrebbero essere in grado di iscriversi a Power BI tramite il [sito web di Power BI](https://powerbi.microsoft.com). Quando un utente dell'organizzazione si iscrive a Power BI, il servizio gli assegna automaticamente una licenza di Power BI. Per altre informazioni, vedere [Iscriversi a Power BI come utente singolo](service-self-service-signup-for-power-bi.md) e [Gestione delle licenze di Power BI nell'organizzazione](service-admin-licensing-organization.md).

### <a name="how-do-individual-users-in-my-organization-sign-up"></a>In che modo si iscrivono i singoli utenti dell'organizzazione?

Esistono tre possibili scenari:

* **Scenario 1**: l'organizzazione ha già un ambiente Microsoft 365 e l'utente che effettua l'iscrizione a Power BI ha già un account di Microsoft 365.
    In questo scenario, se un utente ha già un account aziendale o dell'istituto di istruzione nel tenant (ad esempio contoso.com) ma non ha ancora Power BI, Microsoft attiva semplicemente il piano Power BI (gratuito) per tale account. L'utente riceve automaticamente una notifica relativa a come usare il servizio Power BI.

* **Scenario 2**: l'organizzazione ha già un ambiente Microsoft 365, ma l'utente che effettua l'iscrizione a Power BI non ha un account di Microsoft 365.
    In questo scenario l'utente ha un indirizzo di posta elettronica nel dominio dell'organizzazione (ad esempio, contoso.com) ma non ha ancora un account di Microsoft 365. In questo caso, l'utente può iscriversi a Power BI e gli viene assegnato automaticamente un account. Ciò consente all'utente di accedere al servizio Power BI. Se, ad esempio, una dipendente di nome Nancy esegue l'iscrizione usando il suo indirizzo di posta elettronica aziendale, come nancy@contoso.com, Microsoft aggiunge automaticamente Nancy come utente nell'ambiente Microsoft 365 di Contoso e attiva Power BI per tale account.

* **Scenario 3**: l'organizzazione non ha un ambiente Microsoft 365 connesso al proprio dominio di posta elettronica.
    Non sono necessarie azioni amministrative da parte dell'organizzazione per poter usufruire di Power BI. Il servizio aggiunge gli utenti a una nuova directory utente solo cloud. È anche possibile scegliere di acquisire la proprietà come amministratore globale di Microsoft 365 per il tenant e provvedere alla gestione.

> [!IMPORTANT]
> Se l'organizzazione ha più domini di posta elettronica e si preferisce che tutte le estensioni degli indirizzi di posta elettronica siano incluse nello stesso tenant, aggiungere tutti i domini di indirizzi di posta elettronica a un tenant di Azure Active Directory prima dell'iscrizione di qualsiasi utente. Una volta creati gli utenti, non c'è alcun meccanismo automatico per spostarli tra tenant. Per altre informazioni su questo processo, vedere [Se si hanno più domini, è possibile controllare il tenant di Microsoft 365 in cui vengono aggiunti gli utenti?](#if-i-have-multiple-domains-can-i-control-the-microsoft-365-tenant-that-users-get-added-to) più avanti in questo articolo e [Aggiungere un dominio a Microsoft 365](/office365/admin/setup/add-domain/).

### <a name="how-can-i-prevent-users-from-joining-my-existing-microsoft-365-tenant"></a>Come si può impedire agli utenti di aggiungersi all'attuale tenant di Microsoft 365?

Questa è la procedura che un amministratore globale di Microsoft 365 può eseguire per impedire agli utenti di aggiungersi al tenant di Microsoft 365 esistente. Se si blocca l'accesso, i tentativi di iscrizione degli utenti hanno esito negativo e viene visualizzato un messaggio che invita gli utenti a contattare l'amministratore dell'organizzazione. Non è necessario ripetere questa procedura se è già stata disabilitata la distribuzione automatica delle licenze (ad esempio tramite Office 365 Education per studenti, istituti di istruzione e docenti).

Usare lo script di PowerShell seguente per impedire ai nuovi utenti di aggiungersi a un tenant gestito. [Altre informazioni su PowerShell][1].

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $false
```

> [!NOTE]
> Bloccando l'accesso si impedisce ai nuovi utenti dell'organizzazione di iscriversi a Power BI. Gli utenti che si iscrivono a Power BI prima della disabilitazione delle nuove iscrizioni per l'organizzazione mantengono le proprie licenze. Per rimuovere un utente, vedere [Come si rimuove Power BI per gli utenti che hanno già effettuato l'iscrizione?](#how-do-i-remove-power-bi-for-users-that-already-signed-up), più avanti in questo articolo.

### <a name="how-can-i-allow-users-to-join-my-existing-microsoft-365-tenant"></a>Come si può consentire agli utenti di aggiungersi al tenant esistente di Microsoft 365?

Usare lo script di PowerShell seguente per consentire ai nuovi utenti di aggiungersi a un tenant gestito. [Altre informazioni su PowerShell][1].

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $true
```

### <a name="how-do-i-check-if-i-have-the-block-on-in-the-tenant"></a>Come si controlla se è attivato il blocco nel tenant?

Usare lo script di PowerShell seguente per controllare le impostazioni. *AllowEmailVerifiedUsers* deve essere false. [Altre informazioni su PowerShell][1].

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Get-MsolCompanyInformation | fl allow*
```

### <a name="how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi"></a>Come è possibile impedire agli utenti di iniziare a usare Power BI?

L'impostazione di Azure AD che controlla questa operazione è **AllowAdHocSubscriptions**. Per la maggior parte dei tenant questa opzione è *true*, ovvero abilitata. Se Power BI è stato acquistato attraverso un partner, l'impostazione potrebbe essere *false*, ovvero disabilitata.

Usare lo script di PowerShell seguente per disabilitare le sottoscrizioni ad hoc. ([Altre informazioni su PowerShell][1].)

1. Accedere ad Azure Active Directory usando le credenziali di Microsoft 365. La prima riga dello script PowerShell seguente richiede le credenziali. La seconda riga si connette ad Azure Active Directory.

    ```powershell
     $msolcred = get-credential
     connect-msolservice -credential $msolcred
    ```

   ![Screenshot dell'accesso ad Azure Active Directory tramite PowerShell](media/service-admin-licensing-organization/azure-ad-sign-in.png)

1. Dopo aver effettuato l'accesso, eseguire il comando seguente per vedere come è configurato il tenant.

    ```powershell
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
    ```

1. Eseguire il comando seguente per abilitare (`$true`) o disabilitare (`$false`) **AllowAdHocSubscriptions**.

    ```powershell
     Set-MsolCompanySettings -AllowAdHocSubscriptions $false
    ```

> [!NOTE]
> Usare il flag **AllowAdHocSubscriptions** per controllare diverse funzionalità utente nell'organizzazione, tra cui la possibilità per gli utenti di iscriversi al servizio Azure Rights Management. La modifica di questo flag ha effetto su tutte queste funzionalità. Con l'impostazione *false* gli utenti possono comunque iscriversi per una singola versione di valutazione di Power BI Pro.

### <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>Come si può consentire agli utenti esistenti di iscriversi a Power BI?

Per consentire agli utenti esistenti di iscriversi a Power BI, eseguire il comando indicato per la domanda precedente, ma passare `$true` invece di `$false` nell'ultimo passaggio.

## <a name="administration-of-power-bi"></a>Amministrazione di Power BI

### <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>Come cambierà la gestione delle identità per gli attuali utenti dell'organizzazione?

Esistono tre possibili scenari:

* **Scenario 1**: se l'organizzazione ha già un ambiente Microsoft 365 e tutti gli utenti dell'organizzazione hanno account di Microsoft 365, il processo di gestione delle identità rimane invariato.

* **Scenario 2**: se l'organizzazione ha già un ambiente Microsoft 365 ma non tutti gli utenti dell'organizzazione hanno account di Microsoft 365, viene creato un utente nel tenant e le licenze vengono assegnate in base all'indirizzo di posta elettronica aziendale o dell'istituto di istruzione dell'utente.

    Di conseguenza, il numero di utenti da gestire in un determinato momento aumenta man mano che nuovi utenti nell'organizzazione si iscrivono al servizio.

* **Scenario 3**: se l'organizzazione non ha un ambiente Microsoft 365 connesso al dominio di posta elettronica, la gestione delle identità rimane invariata.

    Il servizio aggiunge gli utenti a una nuova directory utente solo cloud. È anche possibile scegliere di acquisire la proprietà come amministratore globale di Microsoft 365 e provvedere alla gestione.

### <a name="how-do-we-manage-power-bi"></a>Come si gestisce Power BI?

Power BI offre un portale di amministrazione di Power BI per gli utenti del ruolo Amministratore globale di Microsoft 365 e per gli utenti del ruolo di amministratore del servizio Power BI. Per usare il portale di amministrazione di Power BI, l'account deve essere contrassegnato come **Amministratore globale** in Microsoft 365 o in Azure Active Directory o avere ricevuto il ruolo di amministratore del servizio Power BI. Per altre informazioni, vedere [Informazioni sul ruolo di amministratore di Power BI](service-admin-role.md) e [Portale di amministrazione di Power BI](service-admin-portal.md). Il portale offre la possibilità di controllare le impostazioni a livello di tenant e di visualizzare le statistiche di utilizzo di Power BI, oltre a un collegamento all'interfaccia di amministrazione di Microsoft 365 per gestire utenti e gruppi.

### <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>Qual è la procedura per gestire un tenant creato da Microsoft per gli utenti?

Quando un utente self-service si iscrive a un servizio cloud che usa Azure AD, viene aggiunto a una directory di Azure AD non gestita in base al dominio di posta elettronica. È possibile richiedere e gestire un tenant creato da un altro utente con un processo noto come *acquisizione della proprietà come amministratore*. Per altre informazioni, vedere [Acquisire la proprietà di una directory non gestita come amministratore in Azure Active Directory](/azure/active-directory/users-groups-roles/domains-admin-takeover). Il tipo di acquisizione della proprietà dipende dalla presenza o meno di un tenant gestito esistente associato al dominio:

* Power BI supporta l'acquisizione interna della proprietà come amministratore. Quando si esegue un' acquisizione _interna_ della proprietà come amministratore di una directory di Azure non gestita, si viene aggiunti come amministratore globale della directory non gestita. Non viene eseguita la migrazione di utenti, domini o piani di servizio a nessun'altra directory amministrata dall'utente.

* Power BI non supporta più l'acquisizione esterna della proprietà come amministratore. Quando si esegue un'acquisizione _esterna_ della proprietà come amministratore di una directory di Azure non gestita, si aggiunge il nome di dominio DNS della directory non gestita alla directory di Azure gestita. L'acquisizione esterna della proprietà comporterà la perdita dell'accesso all'intero contenuto di Power BI nel tenant non gestito originale. I report di Power BI dovranno essere ripubblicati nel nuovo tenant e i dashboard e le app di Power BI dovranno essere ricreati nel nuovo tenant.

### <a name="if-i-have-multiple-domains-can-i-control-the-microsoft-365-tenant-that-users-get-added-to"></a>Se si hanno più domini, è possibile controllare il tenant di Microsoft 365 in cui vengono aggiunti gli utenti?

Se non si interviene in alcun modo, il servizio crea un tenant per ogni domino e sottodominio di posta elettronica degli utenti. Se si vuole che gli utenti stiano nello stesso tenant indipendentemente dalle estensioni dei loro indirizzi di posta elettronica: Creare un tenant di destinazione anticipatamente o usare un tenant esistente. Aggiungere quindi tutti i domini e i sottodomini esistenti da consolidare all'interno del tenant. Tutti gli utenti con indirizzi di posta elettronica che terminano con tali domini e sottodomini vengono automaticamente aggiunti al tenant di destinazione quando effettuano l'iscrizione.

> [!IMPORTANT]
> Una volta creati gli utenti, non c'è alcun meccanismo automatico supportato per spostarli tra tenant. Per informazioni sull'aggiunta di domini a un singolo tenant di Microsoft 365, vedere [Aggiungere utenti e dominio in Office 365](/office365/admin/setup/add-domain/).

### <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>Come si rimuove Power BI per gli utenti che hanno già effettuato l'iscrizione?

Se un utente ha effettuato l'iscrizione a Power BI ma non si vuole più consentirgli di accedere al servizio, è possibile rimuovere la licenza di Power BI di tale utente.

1. Passare all'[interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. Nella barra di spostamento a sinistra selezionare **Utenti** > **Utenti attivi**.

1. Trovare l'utente di cui si vuole rimuovere la licenza e selezionare il relativo nome.

    È anche possibile eseguire in blocco la gestione delle licenze per gli utenti. A tale scopo, selezionare più utenti e quindi **Modifica licenze di prodotto**.

1. Nella pagina dei dettagli dell'utente, vicino a **Licenze di prodotto** selezionare **Modifica**.

1. A seconda della licenza applicata all'account, impostare **Power BI (gratuito)** o **Power BI Pro** su **Disattivato**.

1. Selezionare **Salva**.

### <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>Come si può sapere se nuovi utenti si aggiungono al tenant?

Ai nuovi utenti che si aggiungono al tenant tramite l'iscrizione in modalità self-service viene assegnata una licenza univoca che è possibile filtrare nel riquadro degli utenti attivi del dashboard di amministrazione. Per creare questa nuova visualizzazione, seguire questi passaggi.

1. Passare all'[interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. Nella barra di spostamento a sinistra selezionare **Utenti** > **Utenti attivi**.

1. Dal menu **Visualizzazioni** scegliere **Aggiungi visualizzazione personalizzata**.

1. Assegnare un nome alla nuova visualizzazione e in **Licenza di prodotto assegnata** selezionare **Power BI (gratuito)** o **Power BI Pro**.

    È possibile selezionare una sola licenza per ogni visualizzazione. Se nell'organizzazione sono disponibili sia licenze di **Power BI (gratuito)** che di **Power BI Pro**, è possibile creare due visualizzazioni.

1. Immettere eventuali altre condizioni desiderate e quindi selezionare **Aggiungi**.

1. Dopo essere stata creata, la nuova visualizzazione è disponibile nel menu **Visualizzazioni**.

### <a name="are-there-any-additional-things-i-should-prepare-for"></a>È necessario prepararsi per altro?

Si potrebbe riscontrare un aumento di richieste di reimpostazione delle password. Per informazioni su questo processo, vedere [Reimpostare la password di un utente](/office365/admin/add-users/reset-passwords).

È possibile rimuovere un utente dal tenant tramite il processo standard nell'interfaccia di amministrazione di Microsoft 365. Se tuttavia l'utente ha ancora un indirizzo di posta elettronica attivo dell'organizzazione, può aggiungersi di nuovo, a meno che non si impedisca a tutti gli utenti di aggiungersi.

### <a name="where-is-my-power-bi-tenant-located"></a>Dove si trova il tenant di Power BI?

Per informazioni sull'area dati in cui si trova il tenant di Power BI, vedere [Dove si trova il tenant di Power BI?](service-admin-where-is-my-tenant-located.md).

### <a name="what-is-the-power-bi-sla"></a>Che cos'è il Contratto di servizio di Power BI?

Per informazioni sul contratto di servizio di Power BI, vedere l'articolo [Condizioni e documentazione per le licenze](http://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37) nella sezione **Licenze** del sito Web Microsoft Licensing.

### <a name="how-does-power-bi-handle-high-availability-and-failover"></a>In che modo Power BI gestisce la disponibilità elevata e il failover?

Per informazioni sulla disponibilità elevata e sul failover, vedere [Domande frequenti su disponibilità elevata, failover e ripristino di emergenza in Power BI](service-admin-failover.md).

## <a name="security-in-power-bi"></a>Sicurezza in Power BI

### <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>Power BI soddisfa i requisiti di conformità nazionali, regionali e specifici del settore?

Per altre informazioni sulla conformità di Power BI, vedere [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/default.aspx).

### <a name="how-does-security-work-in-power-bi"></a>Come funziona la sicurezza in Power BI?

Power BI è basato su Microsoft 365, che a sua volta è basato su servizi di Azure come Azure Active Directory. Per una panoramica dell'architettura di Power BI, vedere [Sicurezza di Power BI](service-admin-power-bi-security.md).

## <a name="next-steps"></a>Passaggi successivi

[Portale di amministrazione di Power BI](service-admin-portal.md)  
[Informazioni sul ruolo di amministratore di Power BI](service-admin-role.md)  
[Iscrizione a Power BI in modalità self-service](service-self-service-signup-for-power-bi.md)  
[Acquisto di Power BI Pro](service-admin-purchasing-power-bi-pro.md)  
[Che cos'è Power BI Premium?](service-premium-what-is.md)  
[Come acquistare Power BI Premium](service-admin-premium-purchase.md)  
[White paper su Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  
[Gestire il gruppo in Power BI e Office 365](service-manage-app-workspace-in-power-bi-and-office-365.md)  
[Gestione degli account utente in Office 365](/office365/servicedescriptions/office-365-platform-service-description/user-account-management/)  
[Gestione dei gruppi in Office 365](/office365/admin/email/create-edit-or-delete-a-security-group/)  

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

[1]: https://docs.microsoft.com/powershell/scripting/overview
