---
title: Amministrazione di Power BI - Domande frequenti
description: Risposte alle domande frequenti sull'iscrizione a Power BI, la gestione del tenant e altre attività amministrative.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 11/28/2017
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 60ac0a944b1eb54ab998fbf25cb5fb79d6dddbe6
ms.sourcegitcommit: 833cf1252807721fb1b3000487bd032bfd6c8c98
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2018
ms.locfileid: "48271901"
---
# <a name="administering-power-bi---frequently-asked-questions-faq"></a>Amministrazione di Power BI - Domande frequenti

Questo articolo contiene le risposte alle domande frequenti sull'amministrazione di Power BI. Per una panoramica dell'amministrazione di Power BI, vedere [Che cos'è l'amministrazione di Power BI?](service-admin-administering-power-bi-in-your-organization.md).

## <a name="whats-in-this-article"></a>Contenuto dell'articolo
**Iscriversi a Power BI**

* [In che modo gli utenti si iscrivono a Power BI?](#how-do-users-sign-up-for-power-bi)
* [In che modo si iscrivono i singoli utenti dell'organizzazione?](#how-do-individual-users-in-my-organization-sign-up)
* [Come si può impedire agli utenti di aggiungersi all'attuale tenant di Office 365?](#how-can-i-prevent-users-from-joining-my-existing-office-365-tenant)
* [Come si può consentire agli utenti di aggiungersi al tenant esistente di Office 365?](#how-can-i-allow-users-to-join-my-existing-office-365-tenant)
* [Come si verifica se è attivato il blocco nel tenant?](#how-do-i-verify-if-i-have-the-block-on-in-the-tenant)
* [Come è possibile impedire agli utenti di iniziare a usare Power BI?](#how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi)
* [Come si può consentire agli utenti esistenti di iscriversi a Power BI?](#how-can-i-allow-my-existing-users-to-sign-up-for-power-bi)

**Amministrazione di Power BI**

* [Come cambierà la gestione delle identità per gli attuali utenti dell'organizzazione?](#how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today)
* [Come si gestisce Power BI?](#how-do-we-manage-power-bi)
* [Qual è la procedura per gestire un tenant creato da Microsoft per gli utenti?](#what-is-the-process-to-manage-a-tenant-created-by-Microsoft-for-my-users)
* [Se si hanno più domini, è possibile controllare il tenant di Office 365 in cui vengono aggiunti gli utenti?](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-are-added-to)
* [Come si rimuove Power BI per gli utenti che hanno già effettuato l'iscrizione?](#how-do-i-remove-power-bi-for-users-that-already-signed-up)
* [Come si può sapere se nuovi utenti si aggiungono al tenant?](#how-do-i-know-when-new-users-have-joined-my-tenant)
* [È necessario prepararsi per altro?](#are-there-any-additional-things-i-should-be-prepared-for)
* [Dove si trova il tenant di Power BI?](#where-is-my-power-bi-tenant-located)
* [Che cos'è il Contratto di servizio di Power BI?](#what-is-the-power-bi-sla)

**Sicurezza in Power BI**

* [Power BI soddisfa i requisiti di conformità nazionali, regionali e specifici del settore?](#does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements)
* [Come funziona la sicurezza in Power BI?](#how-does-security-work-in-power-bi)

## <a name="sign-up-for-power-bi"></a>Iscriversi a Power BI
### <a name="how-do-users-sign-up-for-power-bi"></a>In che modo gli utenti si iscrivono a Power BI?
È possibile iscriversi a Power BI tramite il [sito Web di Power BI](https://powerbi.microsoft.com). L'iscrizione è possibile anche tramite la pagina per l'acquisto dei servizi nell'interfaccia di amministrazione di Office 365. Quando un amministratore si iscrive a Power BI, può poi assegnare le licenze utente agli utenti che devono avere accesso al servizio.

Anche i singoli utenti dell'organizzazione potrebbero essere in grado di iscriversi a Power BI tramite il [sito web di Power BI](https://powerbi.microsoft.com). Agli utenti dell'organizzazione che si iscrivono Power BI viene assegnata automaticamente una licenza di Power BI. [Altre informazioni](service-self-service-signup-for-power-bi.md)

### <a name="how-do-individual-users-in-my-organization-sign-up"></a>In che modo si iscrivono i singoli utenti dell'organizzazione?
Esistono tre possibili scenari:

Scenario 1: l'organizzazione ha già un ambiente di Office 365 e l'utente che effettua l'iscrizione a Power BI ha già un account di Office 365.
In questo scenario, se un utente ha già un account aziendale o dell'istituto di istruzione nel tenant (ad esempio contoso.com) ma non ha ancora Power BI, Microsoft attiverà semplicemente il piano per tale account e l'utente riceverà automaticamente una notifica relativa all'uso del servizio Power BI.

Scenario 2: l'organizzazione ha un ambiente di Office 365 e l'utente che effettua l'iscrizione a Power BI non ha un account di Office 365.
In questo scenario, l'utente ha un indirizzo di posta elettronica nel dominio dell'organizzazione (ad esempio, contoso.com) ma non ha ancora un account Office 365. In questo caso, l'utente può iscriversi a Power BI e gli verrà assegnato automaticamente un account. Ciò consente all'utente di accedere al servizio Power BI. Ad esempio, se una dipendente di nome Nancy esegue l'iscrizione usando il suo indirizzo di posta elettronica di lavoro personale, ad esempio Nancy@contoso.com, Microsoft aggiungerà automaticamente Nancy come utente nell'ambiente Office 365 di Contoso e attiverà Power BI per quell'account.

Scenario 3: l'organizzazione non ha un ambiente di Office 365 connesso al proprio dominio di posta elettronica.
L'organizzazione non deve intraprendere alcuna azione amministrativa per poter usufruire di Power BI. Gli utenti verranno aggiunti a una nuova directory di utenti basata esclusivamente sul cloud e si avrà la possibilità di scegliere se assumere il ruolo di amministratore del tenant per gestirli.

> [!IMPORTANT]
> Se l'organizzazione ha più domini di posta elettronica e si preferisce che tutte le estensioni degli indirizzi di posta elettronica siano incluse nello stesso tenant, aggiungere tutti i domini di indirizzi di posta elettronica a un tenant di Azure Active Directory prima dell'iscrizione di qualsiasi utente. Non esiste alcun meccanismo automatizzato per trasferire gli utenti tra tenant dopo la creazione. Per altre informazioni su questo processo, vedere [Se si hanno più domini, è possibile controllare il tenant di Office 365 in cui vengono aggiunti gli utenti?](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-are-added-to) più avanti in questo articolo e [Aggiungere il dominio a Office 365](https://support.office.com/article/Add-your-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611) online.
> 
> 

### <a name="how-can-i-prevent-users-from-joining-my-existing-office-365-tenant"></a>Come si può impedire agli utenti di aggiungersi all'attuale tenant di Office 365?
Questa è la procedura che un amministratore può eseguire per impedire agli utenti di aggiungersi al tenant di Office 365 esistente. Se si blocca questa operazione, i tentativi di iscrizione degli utenti avranno esito negativo e gli utenti verranno invitati a contattare l'amministratore dell'organizzazione. Non è necessario ripetere questa procedura se è già stata disabilitata la distribuzione automatica delle licenze (ad esempio Office 365 Education per studenti e docenti).

Per questa procedura è richiesto l'uso di Windows PowerShell. Per informazioni introduttive su Windows PowerShell, vedere la [guida introduttiva di PowerShell](http://go.microsoft.com/fwlink/p/?LinkID=286814).

Per eseguire la procedura seguente, è necessario installare la versione a 64 bit più recente del [modulo di Azure Active Directory per Windows PowerShell](http://go.microsoft.com/fwlink/p/?LinkID=236297).

Dopo aver selezionato il collegamento, selezionare **Esegui** per eseguire il pacchetto del programma di installazione.

**Disabilitare l'aggiunta automatica al tenant**: usare questo comando di Windows PowerShell per impedire ai nuovi utenti di aggiungersi a un tenant gestito:

* Per disabilitare l'aggiunta automatica al tenant per i nuovi utenti:
  
    $msolcred = get-credential   connect-msolservice -credential $msolcred
  
    Set-MsolCompanySettings -AllowEmailVerifiedUsers $false
* Per abilitare l'aggiunta automatica al tenant per i nuovi utenti:
  
    $msolcred = get-credential   connect-msolservice -credential $msolcred
  
    Set-MsolCompanySettings -AllowEmailVerifiedUsers $true

> [!NOTE]
> Questo blocco impedisce ai nuovi utenti dell'organizzazione di iscriversi a Power BI. Gli utenti che si iscrivono a Power BI prima della disabilitazione delle nuove iscrizioni per l'organizzazione manterranno le proprie licenze. Vedere la selezione [Come si possono rimuovere le licenze?] per istruzioni su come è possibile rimuovere l'accesso a Power BI per gli utenti precedentemente iscritti al servizio.
> 
> 

### <a name="how-can-i-allow-users-to-join-my-existing-office-365-tenant"></a>Come si può consentire agli utenti di aggiungersi al tenant esistente di Office 365?
Per consentire agli utenti di aggiungersi al tenant, eseguire il comando opposto, come descritto nella domanda precedente.

Per eseguire la procedura seguente, è necessario installare la versione a 64 bit più recente del [modulo di Azure Active Directory per Windows PowerShell](http://go.microsoft.com/fwlink/p/?LinkID=236297).

    $msolcred = get-credential
    connect-msolservice -credential $msolcred

    Set-MsolCompanySettings -AllowEmailVerifiedUsers $true

### <a name="how-do-i-verify-if-i-have-the-block-on-in-the-tenant"></a>Come si verifica se è attivato il blocco nel tenant?
Usare lo script di PowerShell seguente.

Per eseguire la procedura seguente, è necessario installare la versione a 64 bit più recente del [modulo di Azure Active Directory per Windows PowerShell](http://go.microsoft.com/fwlink/p/?LinkID=236297).

    $msolcred = get-credential
    connect-msolservice -credential $msolcred

    Get-MsolCompanyInformation | fl allow*

### <a name="how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi"></a>Come è possibile impedire agli utenti di iniziare a usare Power BI?
Questa è la procedura che un amministratore può eseguire per impedire agli utenti di iscriversi a Power BI. Se si blocca questa operazione, i tentativi di iscrizione degli utenti avranno esito negativo e gli utenti verranno invitati a contattare l'amministratore dell'organizzazione. Non è necessario ripetere questa procedura se è già stata disabilitata la distribuzione automatica delle licenze (ad esempio Office 365 Education per studenti e docenti). [Altre informazioni](service-admin-licensing-organization.md#enable-or-disable-individual-user-sign-up-in-azure-active-directory)

L'impostazione di AAD che controlla questa operazione è **AllowAdHocSubscriptions**. La maggior parte dei tenant avrà questa opzione impostata su true, il che significa che è abilitata. Se Power Bi è stato acquistato tramite un partner, è possibile che questa opzione sia impostata su false, il che significa che è disabilitata.

Per eseguire la procedura seguente, è necessario installare la versione a 64 bit più recente del [modulo di Azure Active Directory per Windows PowerShell](http://go.microsoft.com/fwlink/p/?LinkID=236297).

1. È prima di tutto necessario accedere ad Azure Active Directory usando le credenziali di Office 365. La prima riga richiederà le credenziali. La seconda riga si connette ad Azure Active Directory.
   
     $msolcred = get-credential   connect-msolservice -credential $msolcred
2. Una volta effettuato l'accesso, è possibile eseguire il comando seguente per vedere come è configurato il tenant.
   
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
3. È possibile impostare questo comando per abilitare ($true) o disabilitare ($false) AllowAdHocSubscriptions.
   
     Set-MsolCompanySettings -AllowAdHocSubscriptions $true

> [!NOTE]
> Il flag AllowAdHocSubscriptions viene usato per controllare diverse funzionalità utente nell'organizzazione, inclusa la possibilità per gli utenti di iscriversi al servizio Azure Rights Management. La modifica di questo flag avrà effetto su tutte queste funzionalità.
> 
> 

### <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>Come si può consentire agli utenti esistenti di iscriversi a Power BI?
Per consentire agli utenti esistenti di iscriversi a Power BI, eseguire il comando indicato per la domanda precedente, ma passare true anziché false.

Per eseguire la procedura seguente, è necessario installare la versione a 64 bit più recente del [modulo di Azure Active Directory per Windows PowerShell](http://go.microsoft.com/fwlink/p/?LinkID=236297).

1. È prima di tutto necessario accedere ad Azure Active Directory usando le credenziali di Office 365. La prima riga richiederà le credenziali. La seconda riga si connette ad Azure Active Directory.
   
     $msolcred = get-credential   connect-msolservice -credential $msolcred
2. Una volta effettuato l'accesso, è possibile eseguire il comando seguente per vedere come è configurato il tenant.
   
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
3. È possibile impostare questo comando per abilitare ($true) o disabilitare ($false) AllowAdHocSubscriptions.
   
     Set-MsolCompanySettings -AllowAdHocSubscriptions $true

> [!NOTE]
> Il flag AllowAdHocSubscriptions viene usato per controllare diverse funzionalità utente nell'organizzazione, inclusa la possibilità per gli utenti di iscriversi al servizio Azure Rights Management. La modifica di questo flag avrà effetto su tutte queste funzionalità.
> 
> 

## <a name="administration-of-power-bi"></a>Amministrazione di Power BI
### <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>Come cambierà la gestione delle identità per gli attuali utenti dell'organizzazione?
Se l'organizzazione ha già un ambiente di Office 365 e tutti gli utenti dell'organizzazione hanno account di Office 365, il processo di gestione delle identità rimarrà invariato.

Se l'organizzazione ha già un ambiente di Office 365 ma non tutti gli utenti dell'organizzazione hanno account di Office 365, Microsoft creerà un utente nel tenant e assegnerà le licenze in base all'indirizzo di posta elettronica aziendale o dell'istituto di istruzione dell'utente. Questo significa che il numero di utenti da gestire in un determinato momento aumenterà man mano che nuovi utenti nell'organizzazione si iscrivono al servizio.

Se l'organizzazione non ha un ambiente di Office 365 connesso al proprio dominio di posta elettronica, non ci saranno cambiamenti nella modalità di gestione delle identità. Gli utenti verranno aggiunti a una nuova directory di utenti basata esclusivamente sul cloud e si avrà la possibilità di scegliere se assumere il ruolo di amministratore del tenant per gestirli.

### <a name="how-do-we-manage-power-bi"></a>Come si gestisce Power BI?
Power BI offre un portale di amministrazione che consente di visualizzare le statistiche di utilizzo, fornisce un collegamento all'interfaccia di amministrazione di Office 365 per gestire utenti e gruppi e offre la possibilità di controllare le impostazioni a livello di tenant. 

> [!NOTE]
> Per ottenere l'accesso al portale di amministrazione di Power BI, l'account deve essere contrassegnato come **Amministratore globale** in Office 365 o in Azure Active Directory o avere ricevuto il ruolo di amministratore del servizio Power BI. Per altre informazioni sul ruolo di amministratore del servizio Power BI, vedere [Informazioni sul ruolo di amministratore di Power BI](service-admin-role.md).
> 
> 

Per altre informazioni, vedere [Portale di amministrazione di Power BI](service-admin-portal.md).

### <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>Qual è la procedura per gestire un tenant creato da Microsoft per gli utenti?
Se Microsoft ha creato un tenant, è possibile chiedere di gestirlo eseguendo la procedura seguente:

1. Aggiungere il tenant, iscrivendosi a Power BI, con un dominio di posta elettronica corrispondente al dominio tenant che si vuole gestire. Se ad esempio Microsoft ha creato il tenant contoso.com, è necessario aggiungersi al tenant con un indirizzo di posta elettronica che termina con @contoso.com.
2. Richiedere il controllo di amministratore verificando di essere proprietari del dominio. Dopo l'aggiunta al tenant, è possibile alzarsi di livello al ruolo di *amministratore globale* verificando di essere proprietari del dominio. A tale scopo, seguire questa procedura:
   
   1. Passare a [https://portal.office.com](https://portal.office.com).
   2. Selezionare l'icona di avvio delle app in alto a sinistra e scegliere **Amministratore**.
   3. Leggere le istruzioni nella pagina **Diventare l'amministratore** e quindi scegliere **Sì, voglio essere l'amministratore**.
      
      > [!NOTE]
      > Se questa opzione non viene visualizzata, è già presente un amministratore di Office 365.
      > 
      > 

### <a name="if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-are-added-to"></a>Se si hanno più domini, è possibile controllare il tenant di Office 365 in cui vengono aggiunti gli utenti?
Se non si fa niente, verrà creato un tenant per ogni domino o sottodominio di posta elettronica degli utenti.

Se si vuole che gli utenti stiano nello stesso tenant indipendentemente dalle estensioni dei loro indirizzi di posta elettronica:

* Creare in anticipo un tenant di destinazione oppure usare un tenant esistente e aggiungere tutti i domini e sottodomini esistenti da consolidare al suo interno. Tutti gli utenti con un indirizzo di posta elettronica che termina con questi domini e sottodomini verranno quindi automaticamente aggiunti al tenant di destinazione quando si iscrivono.

> [!IMPORTANT]
> Non esiste alcun meccanismo automatizzato per spostare gli utenti tra i tenant dopo che sono stati creati. Per informazioni sull'aggiunta di domini a un singolo tenant di Office 365, vedere [Aggiungere utenti e dominio in Office 365](https://support.office.com/article/Add-your-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611).
> 
> 

### <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>Come si rimuove Power BI per gli utenti che hanno già effettuato l'iscrizione?
Se un utente ha effettuato l'iscrizione a Power BI ma non si vuole più consentirgli di accedere al servizio, è possibile rimuovere la licenza di Power BI di tale utente.

1. Accedere all'interfaccia di amministrazione di Office 365.
2. Nella barra di spostamento a sinistra selezionare **Utenti** > **Utenti attivi**.
3. Trovare l'utente di cui si vuole rimuovere la licenza, selezionarne il nome > **Modifica**.
4. Nella pagina dei dettagli dell'utente selezionare **Licenze** nella barra di spostamento sinistra.
5. Deselezionare **Power BI (gratuito)** o **Power BI Pro**, a seconda della licenza applicata all'account di tale utente.
6. Selezionare **Salva**.

> [!NOTE]
> È anche possibile eseguire in blocco la gestione delle licenze per gli utenti. A tale scopo, selezionare più utenti e selezionare **Modifica**.
> 
> 

### <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>Come si può sapere se nuovi utenti si aggiungono al tenant?
Ai nuovi utenti che si aggiungono al tenant nell'ambito di questo programma viene assegnata una licenza univoca che è possibile filtrare nel riquadro degli utenti attivi del dashboard di amministrazione.

Per creare la nuova visualizzazione, nell'interfaccia di amministrazione di Office 365, passare a **Utenti** > **Utenti attivi** e scegliere **Nuova visualizzazione** dal menu **Selezionare una visualizzazione**. Assegnare un nome alla nuova visualizzazione e in **Licenza assegnata** selezionare **Power BI (gratuito)** o **Power BI Pro**. È possibile selezionare una sola licenza per ogni visualizzazione. Se nell'organizzazione sono disponibili sia licenze di **Power BI (gratuito)** che di **Power BI Pro**, sarà necessario creare due visualizzazioni. Dopo la creazione della nuova visualizzazione, sarà possibile vedere tutti gli utenti nel tenant iscritti al programma.

### <a name="are-there-any-additional-things-i-should-be-prepared-for"></a>È necessario prepararsi per altro?
Si potrebbe riscontrare un aumento di richieste di reimpostazione delle password. Per informazioni su questo processo, vedere [Reimpostare la password di un utente](https://support.office.com/article/Reset-a-users-password-7a5d073b-7fae-4aa5-8f96-9ecd041aba9c).

È possibile rimuovere un utente dal tenant tramite il processo standard nell'interfaccia di amministrazione di Office 365. Se tuttavia l'utente ha ancora un indirizzo di posta elettronica attivo dell'organizzazione, potrà riaggiungersi a meno che non si impedisca a tutti gli utenti di aggiungersi.

### <a name="where-is-my-power-bi-tenant-located"></a>Dove si trova il tenant di Power BI?
Per informazioni su come trovare la località in cui risiede il tenant di Power BI, detta anche area dati, vedere [Dove si trova il tenant di Power BI?](service-admin-where-is-my-tenant-located.md)

### <a name="what-is-the-power-bi-sla"></a>Che cos'è il Contratto di servizio di Power BI?
Per informazioni sul Contratto di servizio di Power BI, vedere l'articolo [Licensing Terms and Documentation](http://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37) (Condizioni e documentazione per le licenze) nella sezione **Licensing** (Licenze) del sito Web Microsoft Licensing.

## <a name="security-in-power-bi"></a>Sicurezza in Power BI
### <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>Power BI soddisfa i requisiti di conformità nazionali, regionali e specifici del settore?
Per altre informazioni sulla conformità di Power BI, vedere [Microsoft Trust Center](http://go.microsoft.com/fwlink/?LinkId=785324).

### <a name="how-does-security-work-in-power-bi"></a>Come funziona la sicurezza in Power BI?
Power BI è basato su Office 365, che a sua volta è basato su servizi di Azure quali Azure Active Directory. Per una panoramica dell'architettura di Power BI, vedere [Sicurezza di Power BI](service-admin-power-bi-security.md). 

## <a name="next-steps"></a>Passaggi successivi
[Portale di amministrazione di Power BI](service-admin-portal.md)  
[Informazioni sul ruolo di amministratore di Power BI](service-admin-role.md)  
[Iscrizione a Power BI in modalità self-service](service-self-service-signup-for-power-bi.md)  
[Acquisto di Power BI Pro](service-admin-purchasing-power-bi-pro.md)  
[Power BI Premium: di cosa si tratta?](service-premium.md)  
[Come acquistare Power BI Premium](service-admin-premium-purchase.md)  
[Gestione degli account utente in Office 365](https://technet.microsoft.com/library/office-365-user-account-management.aspx)  
[Gestione dei gruppi in Office 365](https://support.office.com/Article/Find-help-about-Groups-in-Office-365-7a9b321f-b76a-4d53-b98b-a2b0b7946de1)  
[Gestire il gruppo in Power BI e Office 365](service-manage-app-workspace-in-power-bi-and-office-365.md)  
[White paper su Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)