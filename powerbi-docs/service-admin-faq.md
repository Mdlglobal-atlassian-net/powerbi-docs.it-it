---
title: Amministrazione di Power BI - Domande frequenti
description: Risposte alle domande frequenti su Power BI di iscrizione, gestione del tenant e altre attività amministrative.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 2e51017333a940bd9d7838e6a903c1a66ce2e342
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65100761"
---
# <a name="administering-power-bi---frequently-asked-questions-faq"></a>Amministrazione di Power BI - Domande frequenti

Questo articolo contiene le risposte alle domande frequenti sull'amministrazione di Power BI. Per una panoramica dell'amministrazione di Power BI, vedere [Che cos'è l'amministrazione di Power BI?](service-admin-administering-power-bi-in-your-organization.md).

## <a name="whats-in-this-article"></a>Contenuto dell'articolo

### <a name="sign-up-for-power-bi-section"></a>Sezione relativa all'iscrizione a Power BI

* [Uso di PowerShell](#using-powershell)
* [In che modo gli utenti si iscrivono a Power BI?](#how-do-users-sign-up-for-power-bi)
* [In che modo si iscrivono i singoli utenti dell'organizzazione?](#how-do-individual-users-in-my-organization-sign-up)
* [Come si può impedire agli utenti di aggiungersi all'attuale tenant di Office 365?](#how-can-i-prevent-users-from-joining-my-existing-office-365-tenant)
* [Come si può consentire agli utenti di aggiungersi al tenant esistente di Office 365?](#how-can-i-allow-users-to-join-my-existing-office-365-tenant)
* [Come si controlla se è attivato il blocco nel tenant?](#how-do-i-check-if-i-have-the-block-on-in-the-tenant)
* [Come è possibile impedire agli utenti di iniziare a usare Power BI?](#how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi)
* [Come si può consentire agli utenti esistenti di iscriversi a Power BI?](#how-can-i-allow-my-existing-users-to-sign-up-for-power-bi)

### <a name="administration-of-power-bi-section"></a>Sezione relativa all'amministrazione di Power BI

* [Come cambierà la gestione delle identità per gli attuali utenti dell'organizzazione?](#how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today)
* [Come si gestisce Power BI?](#how-do-we-manage-power-bi)
* [Qual è la procedura per gestire un tenant creato da Microsoft per gli utenti?](#what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users)
* [Se si hanno più domini, è possibile controllare il tenant di Office 365 che gli utenti vengono aggiunti alla?](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-get-added-to)
* [Come si rimuove Power BI per gli utenti che hanno già effettuato l'iscrizione?](#how-do-i-remove-power-bi-for-users-that-already-signed-up)
* [Come si può sapere se nuovi utenti si aggiungono al tenant?](#how-do-i-know-when-new-users-have-joined-my-tenant)
* [Sono presenti altri elementi per che è necessario preparare?](#are-there-any-additional-things-i-should-prepare-for)
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

Come amministratore, è possibile iscriversi a Power BI tramite il [sito web di Power BI](https://powerbi.microsoft.com) o il [acquistare servizi](https://admin.microsoft.com/AdminPortal/Home#/catalog) pagina l'interfaccia di amministrazione di Microsoft 365. Quando un amministratore si iscrive a Power BI, possono assegnare le licenze utente per gli utenti devono disporre dell'accesso.

Anche i singoli utenti dell'organizzazione potrebbero essere in grado di iscriversi a Power BI tramite il [sito web di Power BI](https://powerbi.microsoft.com). Quando un utente nell'organizzazione si iscrive a Power BI, il servizio assegna automaticamente una licenza Power BI per l'utente. Per altre informazioni, vedi [iscriversi a Power BI come utente singolo](service-self-service-signup-for-power-bi.md) e [gestione delle licenze di Power BI nell'organizzazione](service-admin-licensing-organization.md).

### <a name="how-do-individual-users-in-my-organization-sign-up"></a>In che modo si iscrivono i singoli utenti dell'organizzazione?

Esistono tre possibili scenari:

* **Scenario 1**: l'organizzazione ha già un ambiente di Office 365 e l'utente che effettua l'iscrizione a Power BI ha già un account di Office 365.
    In questo scenario, se un utente ha già un account dell'istituto di istruzione nel tenant (ad esempio, contoso.com) ma non ha ancora Power BI, Microsoft attiva semplicemente il piano per tale account. L'utente viene automaticamente informato con informazioni su come usare il servizio Power BI.

* **Scenario 2**: l'organizzazione ha già un ambiente di Office 365, ma l'utente che effettua l'iscrizione a Power BI non ha un account di Office 365.
    In questo scenario, l'utente dispone di un indirizzo di posta elettronica nel dominio dell'organizzazione (ad esempio, contoso.com) ma non dispone ancora di un account Office 365. In questo caso, l'utente può iscriversi a Power BI e gli viene assegnato automaticamente un account. Questa azione consente all'utente l'accesso al servizio Power BI. Ad esempio, se un dipendente Nancy il suo lavoro indirizzo di posta elettronica (ad esempio nancy@contoso.com) per iscriversi, Microsoft aggiunge automaticamente Nancy come utente nell'ambiente di Office 365 di Contoso e attiva Power BI per quell'account.

* **Scenario 3**: L'organizzazione non dispone di un ambiente di Office 365 connesso al dominio di posta elettronica.
    Non sono presenti azioni amministrative necessarie per l'organizzazione possa sfruttare i vantaggi di Power BI. Il servizio consente di aggiungere utenti a una directory solo cloud, nuovo utente. È anche possibile scegliere assumere il ruolo di amministratore di tenant e gestirli.

> [!IMPORTANT]
> Se l'organizzazione ha più domini di posta elettronica e si preferisce che tutte le estensioni degli indirizzi di posta elettronica siano incluse nello stesso tenant, aggiungere tutti i domini di indirizzi di posta elettronica a un tenant di Azure Active Directory prima dell'iscrizione di qualsiasi utente. Dopo aver creato gli utenti, non vi è alcun meccanismo automatizzato per trasferire gli utenti tra tenant. Per altre informazioni su questo processo, vedere [se si hanno più domini, è possibile controllare il tenant di Office 365 che gli utenti vengono aggiunti alla?](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-get-added-to) più avanti in questo articolo e [aggiungere un dominio a Office 365](/office365/admin/setup/add-domain/).

### <a name="how-can-i-prevent-users-from-joining-my-existing-office-365-tenant"></a>Come si può impedire agli utenti di aggiungersi all'attuale tenant di Office 365?

Questa è la procedura che un amministratore può eseguire per impedire agli utenti di aggiungersi al tenant di Office 365 esistente. Se si blocca l'accesso, i tentativi degli utenti per l'iscrizione avranno esito negativo e viene visualizzato un messaggio che invita a contattare l'amministratore. dell'organizzazione Non è necessario ripetere questa procedura se già stata disabilitata la distribuzione automatica delle licenze (ad esempio, tramite Office 365 Education per studenti, docenti e personale).

Usare lo script di PowerShell seguente per impedire ai nuovi utenti di aggiungersi a un tenant gestito. [Altre informazioni su PowerShell][1].

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $false
```

> [!NOTE]
> Bloccando l'accesso si impedisce ai nuovi utenti dell'organizzazione di iscriversi a Power BI. Gli utenti che si iscrivono a Power BI prima della disabilitazione delle nuove iscrizioni per l'organizzazione mantengono le proprie licenze. Per rimuovere un utente, vedere [Come si rimuove Power BI per gli utenti che hanno già effettuato l'iscrizione?](#how-do-i-remove-power-bi-for-users-that-already-signed-up), più avanti in questo articolo.

### <a name="how-can-i-allow-users-to-join-my-existing-office-365-tenant"></a>Come si può consentire agli utenti di aggiungersi al tenant esistente di Office 365?

Usare lo script di PowerShell seguente per consentire ai nuovi utenti di partecipare a un tenant gestito. [Altre informazioni su PowerShell][1].

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

L'impostazione di Azure AD che controlla questa operazione è **AllowAdHocSubscriptions**. La maggior parte dei tenant hanno questa opzione impostata su true, il che significa che è abilitata. Se è stato acquistato Power BI tramite un partner, questo valore può essere impostato su false, il che significa che è disabilitata.

Usare lo script di PowerShell seguente per disabilitare le sottoscrizioni ad hoc. [Altre informazioni su PowerShell][1].

1. Accedere ad Azure Active Directory usando le credenziali di Office 365. La prima riga dello script PowerShell seguente richiede le credenziali. La seconda riga si connette ad Azure Active Directory.

    ```powershell
     $msolcred = get-credential
     connect-msolservice -credential $msolcred
    ```

   ![Accedi screenshot di Azure Active Directory tramite PowerShell](media/service-admin-licensing-organization/azure-ad-sign-in.png)

1. Una volta accedere, eseguire il comando seguente per vedere come il tenant è attualmente configurato.

    ```powershell
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
    ```

1. Eseguire il comando seguente per abilitare (`$true`) o disabilitare (`$false`) **AllowAdHocSubscriptions**.

    ```powershell
     Set-MsolCompanySettings -AllowAdHocSubscriptions $false
    ```

> [!NOTE]
> Usare la **AllowAdHocSubscriptions** flag per controllare diverse funzionalità utente nell'organizzazione, inclusa la possibilità per gli utenti per l'iscrizione per il servizio Azure Rights Management. La modifica di questo flag ha effetto su tutte queste funzionalità.

### <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>Come si può consentire agli utenti esistenti di iscriversi a Power BI?

Per consentire agli utenti esistenti di iscriversi a Power BI, eseguire il comando indicato per la domanda precedente, ma passare `$true` invece di `$false` nell'ultimo passaggio.

## <a name="administration-of-power-bi"></a>Amministrazione di Power BI

### <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>Come cambierà la gestione delle identità per gli attuali utenti dell'organizzazione?

Esistono tre possibili scenari:

* **Scenario 1**: Se l'organizzazione ha già un ambiente di Office 365 e tutti gli utenti dell'organizzazione hanno un account Office 365, non sussiste alcuna modifica nella modalità di gestione delle identità.

* **Scenario 2**: Se l'organizzazione ha già un ambiente di Office 365 ma non tutti gli utenti dell'organizzazione hanno un account Office 365, viene creato un utente nel tenant e assegnare le licenze basate su indirizzo di posta elettronica dell'istituto di istruzione o le attività dell'utente.

    Di conseguenza, il numero di utenti che è necessario gestire in un determinato momento aumenta man mano che gli utenti dell'organizzazione effettuare l'iscrizione per il servizio.

* **Scenario 3**: Se l'organizzazione non ha un ambiente di Office 365 connesso al dominio di posta elettronica, sussiste alcuna modifica nella modalità di gestione delle identità.

    Il servizio consente di aggiungere utenti a una directory solo cloud, nuovo utente. Inoltre, è possibile scegliere assumere il ruolo di amministratore di tenant e gestirli.

### <a name="how-do-we-manage-power-bi"></a>Come si gestisce Power BI?

Power BI offre un portale di amministrazione che consente di visualizzare le statistiche di utilizzo, viene fornito un collegamento all'interfaccia di amministrazione di Microsoft 365 per gestire utenti e gruppi e offre la possibilità di controllare le impostazioni a livello di tenant.

Per usare il portale di amministrazione di Power BI, è necessario contrassegnare l'account come un **amministratore globale** all'interno di Office 365 o Azure Active Directory o un utente deve assegnare il ruolo di amministratore del servizio Power BI al proprio account utente. Per altre informazioni, vedi [comprendere il ruolo di amministratore di Power BI](service-admin-role.md) e [portale di amministrazione di Power BI](service-admin-portal.md).

### <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>Qual è la procedura per gestire un tenant creato da Microsoft per gli utenti?

Quando un utente self-service si iscrive a un servizio cloud che usa Azure Active Directory, il servizio li aggiunge a un'istanza di Azure non gestita basata su Active directory nel dominio di posta elettronica. È possibile richiedere e gestire il tenant di cui è stato creato tramite un processo noto come un *un'acquisizione amministratore*. Il tipo di acquisizione della proprietà è eseguire dipende se è presente alcuna tenant associato al dominio gestito:

* Usare un'*acquisizione interna della proprietà* per creare un nuovo tenant gestito per il dominio.

* Usare un'*acquisizione esterna della proprietà* per spostare il dominio in un tenant gestito esistente.

Per altre informazioni, vedi [assumere una directory non gestita come amministratore in Azure Active Directory](/azure/active-directory/users-groups-roles/domains-admin-takeover).

Quando si esegue un'acquisizione esterna, questo servizio pone dei Power BI contenuto che è stato creato prima l'acquisizione della proprietà in un [area lavoro contenuto archiviato di Power BI](service-admin-power-bi-archived-workspace.md). È necessario eseguire manualmente la migrazione di qualsiasi contenuto che si vuole usare nel nuovo tenant.

### <a name="if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-get-added-to"></a>Se si hanno più domini, è possibile controllare il tenant di Office 365 che gli utenti vengono aggiunti alla?

Se si fa niente, il servizio crea un tenant per ogni dominio di posta elettronica utente e del sottodominio. Se si vuole che gli utenti stiano nello stesso tenant indipendentemente dalle estensioni dei loro indirizzi di posta elettronica: Creare un tenant di destinazione anticipatamente o usare un tenant esistente. Aggiungere quindi tutti i domini e sottodomini esistenti che si vuole consolidare all'interno del tenant. Tutti gli utenti con indirizzi di posta elettronica che termina con questi domini e sottodomini automaticamente aggiunti al tenant di destinazione quando si iscrivono.

> [!IMPORTANT]
> Dopo aver creato gli utenti, non vi è alcun meccanismo automatizzato per trasferire gli utenti tra tenant. Per informazioni sull'aggiunta di domini a un singolo tenant di Office 365, vedere [Aggiungere utenti e dominio in Office 365](/office365/admin/setup/add-domain/).

### <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>Come si rimuove Power BI per gli utenti che hanno già effettuato l'iscrizione?

Se un utente ha effettuato l'iscrizione a Power BI ma non si vuole più consentirgli di accedere al servizio, è possibile rimuovere la licenza di Power BI di tale utente.

1. Passare all'[interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. Nella barra di spostamento a sinistra selezionare **Utenti** > **Utenti attivi**.

1. Trovare l'utente di cui si vuole rimuovere la licenza e selezionare il relativo nome.

    È anche possibile eseguire in blocco la gestione delle licenze per gli utenti. A tale scopo, selezionare più utenti e quindi **Modifica licenze di prodotto**.

1. Nella pagina dei dettagli dell'utente, vicino a **Licenze di prodotto** selezionare **Modifica**.

1. A seconda che cos'è concedere in licenza applicata all'account, impostare **Power BI (gratuito)** oppure **Power BI Pro** al **Off**.

1. Selezionare **Salva**.

### <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>Come si può sapere se nuovi utenti si aggiungono al tenant?

Una licenza univoca che è possibile filtrare nel riquadro degli utenti attivi del dashboard di amministrazione vengono assegnati gli utenti che hanno avuto accesso al tenant come parte di questo programma. Per creare questa nuova visualizzazione, seguire questi passaggi.

1. Passare all'[interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. Nella barra di spostamento a sinistra selezionare **Utenti** > **Utenti attivi**.

1. Dal menu **Visualizzazioni** scegliere **Aggiungi visualizzazione personalizzata**.

1. Assegnare un nome alla nuova visualizzazione e in **Licenza di prodotto assegnata** selezionare **Power BI (gratuito)** o **Power BI Pro**.

    È possibile selezionare una sola licenza per ogni visualizzazione. Se nell'organizzazione sono disponibili sia licenze di **Power BI (gratuito)** che di **Power BI Pro**, è possibile creare due visualizzazioni.

1. Immettere eventuali altre condizioni desiderate e quindi selezionare **Aggiungi**.

1. Dopo aver creato la nuova vista, è disponibile il **viste** menu.

### <a name="are-there-any-additional-things-i-should-prepare-for"></a>Sono presenti altri elementi per che è necessario preparare?

Si potrebbe riscontrare un aumento di richieste di reimpostazione delle password. Per informazioni su questo processo, vedi [reimpostare una password utente](/office365/admin/add-users/reset-passwords).

È possibile rimuovere un utente dal tenant tramite il processo standard nell'interfaccia di amministrazione di Microsoft 365. Se tuttavia l'utente ha ancora un indirizzo di posta elettronica attivo dell'organizzazione, può aggiungersi di nuovo, a meno che non si impedisca a tutti gli utenti di aggiungersi.

### <a name="where-is-my-power-bi-tenant-located"></a>Dove si trova il tenant di Power BI?

Per informazioni su quale area dati è nel tenant di Power BI, vedere [dove si trova il tenant di Power BI?](service-admin-where-is-my-tenant-located.md).

### <a name="what-is-the-power-bi-sla"></a>Che cos'è il Contratto di servizio di Power BI?

Per informazioni su Power BI SLA (Service Level Agreement), vedere la [condizioni di licenza e documentazione](http://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37) articolo della **Licensing** sezione del sito Web Microsoft Licensing.

### <a name="how-does-power-bi-handle-high-availability-and-failover"></a>In che modo Power BI gestisce la disponibilità elevata e il failover?

Per informazioni sulla disponibilità elevata e failover, vedere [Power BI ad alto disponibilità, il failover e ripristino di emergenza domande frequenti su](service-admin-failover.md).

## <a name="security-in-power-bi"></a>Sicurezza in Power BI

### <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>Power BI soddisfa i requisiti di conformità nazionali, regionali e specifici del settore?

Per altre informazioni sulla conformità di Power BI, vedere [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/default.aspx).

### <a name="how-does-security-work-in-power-bi"></a>Come funziona la sicurezza in Power BI?

Microsoft Power BI ha creato sulla base di Office 365, che a sua volta si basa su servizi di Azure come Azure Active Directory. Per una panoramica dell'architettura di Power BI, vedere [Sicurezza di Power BI](service-admin-power-bi-security.md).

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