---
title: Analisi approfondita del gateway dati locale
description: Questo articolo offre un'analisi approfondita del gateway dati locale. Illustra come funziona il servizio con Azure Active Directory e Active Directory locale quando si lavora con Analysis Services
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-gateways
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 8b0121dbfe633eca9c438dfd272d3aeb56fd59a4
ms.sourcegitcommit: 001ea0ef95fdd4382602bfdae74c686de7dc3bd8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38921508"
---
# <a name="on-premises-data-gateway-in-depth"></a>Analisi approfondita del gateway dati locale
Gli utenti dell'organizzazione possono accedere ai dati locali (per i quali hanno già l'autorizzazione di accesso), ma prima che possano connettersi all'origine dati locale, è necessario installare e configurare un gateway dati locale. Il gateway facilita consente una comunicazione "dietro le quinte" rapida e sicura tra un utente nel cloud e l'origine dati locale e viceversa.

L'installazione e la configurazione di un gateway viene in genere eseguita da un amministratore. Può richiedere conoscenze specializzate dei server locali e in alcuni casi le autorizzazioni di amministratore del server.

Questo articolo non contiene istruzioni dettagliate su come installare e configurare il gateway. A tale scopo, vedere [Gateway dati locale](service-gateway-onprem.md). Questo articolo mira a fornire una conoscenza approfondita del funzionamento del gateway. Verranno anche fornite alcune informazioni dettagliate sui nomi utente e la sicurezza sia in Azure Active Directory sia in Analysis Services, nonché sul modo in cui il servizio cloud usa l'indirizzo di posta elettronica con cui un utente esegue l'accesso, il gateway e Active Directory per connettersi in modo sicuro ai dati locali ed eseguire query su di essi.

<!-- Shared Requirements Include -->
[!INCLUDE [gateway-onprem-requirements-include](./includes/gateway-onprem-how-it-works-include.md)]

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-datasources-include](./includes/gateway-onprem-datasources-include.md)]

## <a name="sign-in-account"></a>Account di accesso
Gli utenti eseguiranno l'accesso con un account aziendale o dell'istituto di istruzione. Questo è l'account aziendale. Se è stata effettuata l'iscrizione per un'offerta di Office 365 senza specificare l'indirizzo di posta elettronica dell'ufficio, questo può apparire come nancy@contoso.onmicrosoft.com. All'interno di un servizio cloud, l'account viene archiviato in un tenant di Azure Active Directory (AAD). Nella maggior parte dei casi, l'UPN dell'account AAD corrisponderà all'indirizzo di posta elettronica.

## <a name="authentication-to-on-premises-data-sources"></a>Autenticazione a origini dati locali
Una credenziale archiviata verrà usata per connettersi a origini dati locali dal gateway ad eccezione di Analysis Services. Indipendentemente dal singolo utente, il gateway usa credenziali archiviate per connettersi.

## <a name="authentication-to-a-live-analysis-services-data-source"></a>Autenticazione a un'origine dati Analysis Services live
Ogni volta che un utente interagisce con Analysis Services, il nome utente effettivo viene passato al gateway e quindi al server di Analysis Services locale. Il nome dell'entità utente (UPN), che in genere corrisponde all'indirizzo di posta elettronica con cui si accede al cloud, è l'informazione che viene passata ad Analysis Services come utente effettivo. L'UPN viene passato nella proprietà di connessione EffectiveUserName. Questo indirizzo di posta elettronica deve corrispondere a un UPN definito all'interno del dominio di Active Directory locale. L'UPN è una proprietà di un account di Active Directory. Questo account di Windows deve quindi essere presente in un ruolo di Analysis Services per avere accesso al server. Se non viene trovata alcuna corrispondenza in Active Directory, l'accesso non riesce.

Analysis Services può anche fornire filtri basati su questo account. I filtri possono usare la sicurezza basata sui ruoli o la sicurezza a livello di riga.

## <a name="role-based-security"></a>Sicurezza basata sui ruoli
I modelli assicurano la sicurezza basata sui ruoli utente. I ruoli vengono definiti per un particolare progetto di modello durante la creazione in SQL Server Data Tools – Business Intelligence (SSDT-BI) oppure dopo la distribuzione di un modello, usando SQL Server Management Studio (SSMS). I ruoli contengono membri in base al nome utente o gruppo di Windows. I ruoli definiscono le autorizzazioni di un utente per eseguire una query o azioni sul modello. La maggior parte degli utenti appartiene a un ruolo con autorizzazioni di lettura. Altri ruoli sono destinati agli amministratori con autorizzazioni di elaborazione degli elementi, gestione delle funzioni di database e di altri ruoli.

## <a name="row-level-security"></a>Sicurezza a livello di riga
La sicurezza a livello di riga è specifica per la sicurezza a livello di Analysis Services. I modelli possono fornire sicurezza dinamica a livello di riga. Invece di avere almeno un ruolo a cui appartengono gli utenti, la sicurezza dinamica non è richiesta per alcun modello tabulare. A un livello elevato, la sicurezza dinamica definisce l'accesso in lettura di un utente ai dati fino a una specifica riga di una determinata tabella. Analogamente ai ruoli, la sicurezza dinamica a livello di riga si basa su un nome utente Windows.

La possibilità di un utente di eseguire query e visualizzare i dati del modello è prima di tutto determinata dai ruoli di cui è membro il rispettivo account utente di Windows e, in secondo luogo, dalla sicurezza dinamica a livello di riga, se configurata.

L'implementazione della sicurezza basata sui ruoli e della sicurezza dinamica a livello di riga nei modelli esula dall'ambito di questo articolo.  Per altre informazioni, vedere [Ruoli (SSAS tabulare)](https://msdn.microsoft.com/library/hh213165.aspx) e [Ruoli di sicurezza (Analysis Services - Dati multidimensionali)](https://msdn.microsoft.com/library/ms174840.aspx) in MSDN. Inoltre, per una conoscenza più approfondita della sicurezza del modello tabulare, scaricare e leggere il white paper [Protezione del modello semantico BI tabulare](https://msdn.microsoft.com/library/jj127437.aspx).

## <a name="what-about-azure-active-directory"></a>Ruolo di Azure Active Directory
I servizi cloud Microsoft usano [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/) per eseguire l'autenticazione degli utenti. Azure Active Directory è il tenant che contiene i nomi utente e i gruppi di sicurezza. In genere, un utente accede con lo stesso indirizzo di posta elettronica dell'UPN dell'account.

Qual è il ruolo di Active Directory locale?

Affinché il server di Analysis Services possa determinare se un utente a esso connesso appartiene a un ruolo con autorizzazioni di lettura dei dati, deve convertire il nome utente effettivo passato da AAD al gateway e quindi al server di Analysis Services. Il server di Analysis Services passa il nome utente effettivo a un controller di dominio di Windows Active Directory. Il controller di dominio di Active Directory verifica quindi che il nome utente effettivo sia un UPN valido, su un account locale, e restituisce un nome utente di Windows al server Analysis Services.

EffectiveUserName non può essere usato in un server di Analysis Services non appartenente al dominio. Per evitare errori di accesso, il server di Analysis Services locale deve appartenere a un dominio.

## <a name="how-do-i-tell-what-my-upn-is"></a>Come si identifica l'UPN?
È possibile che l'utente non conosca l'UPN e non sia un amministratore di dominio. È possibile usare il comando seguente dalla workstation per identificare l'UPN dell'account.

    whoami /upn

Il risultato sarà simile a un indirizzo di posta elettronica, ma si tratta dell'UPN dell'account di dominio locale. Se si usa un'origine dati di Analysis Services per connessioni dinamiche, questa deve corrispondere a ciò che è stato passato a EffectiveUserName dal gateway.

## <a name="mapping-usernames-for-analysis-services-data-sources"></a>Mapping di nomi utente per le origini dati di Analysis Services
Power BI consente di eseguire il mapping di nomi utente per le origini dati di Analysis Services. È possibile configurare regole per eseguire il mapping di un nome utente che ha eseguito l'accesso a Power BI a un nome che viene passato per EffectiveUserName usando la connessione di Analysis Services. La funzionalità di mapping dei nomi utente rappresenta un'ottima soluzione alternativa quando il nome utente in AAD non corrisponde a un UPN in Active Directory locale. Ad esempio, se l'indirizzo di posta elettronica è nancy@contoso.onmicrsoft.com, è possibile eseguirne il mapping a nancy@contoso.com e tale valore viene passato al gateway. Sono disponibili altre informazioni su come [eseguire il mapping dei nomi utente](service-gateway-enterprise-manage-ssas.md#map-user-names).

## <a name="synchronize-an-on-premises-active-directory-with-azure-active-directory"></a>Sincronizzare un server di Active Directory locale con Azure Active Directory
È opportuno che gli account Active Directory locali corrispondano ad Azure Active Directory se si intende usare connessioni Analysis Services dinamiche, analogamente al modo in cui l'UPN deve corrispondere tra gli account.

I servizi cloud rilevano solo gli account in Azure Active Directory. Anche se è stato aggiunto un account in Active Directory locale, se non esiste in AAD, non può essere usato. Esistono diversi modi in cui è possibile associare gli account Active Directory locali con Azure Active Directory.

1. È possibile aggiungere manualmente account in Azure Active Directory.
   
   È possibile creare un account nel portale di Azure o nel portale di amministrazione di Office 365 e il nome dell'account corrisponde l'UPN dell'account Active Directory locale.
2. È possibile usare lo strumento [Azure AD Connect](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) per sincronizzare gli account locali al tenant di Azure Active Directory.
   
   Lo strumento Azure AD Connect offre opzioni per sincronizzare le directory e configurare l'autenticazione, incluse la sincronizzazione degli hash delle password, l'autenticazione pass-through e la federazione. Se non si è un amministratore tenant o un amministratore di dominio locale, è necessario contattare l'amministratore IT per ottenere questa configurazione.

L'uso di Azure AD Connect garantisce la corrispondenza tra l'UPN e AAD e Active Directory locale.

> [!NOTE]
> La sincronizzazione degli account con lo strumento Azure AD Connect creerà nuovi account nel tenant di AAD.
> 
> 

## <a name="now-this-is-where-the-gateway-comes-in"></a>A questo punto, è possibile usare il gateway
Il gateway funge da ponte tra il cloud e il server locale. Il trasferimento dei dati tra il cloud e il gateway viene protetto con il [bus di servizio di Azure](https://azure.microsoft.com/documentation/services/service-bus/). Il bus di servizio crea un canale sicuro tra il cloud e il server locale attraverso una connessione in uscita sul gateway.  Non sono presenti connessioni in ingresso che è necessario aprire nel firewall locale.

Se si dispone di un'origine dati di Analysis Services, è necessario installare il gateway in un computer appartenente allo stesso insieme di strutture o dominio del server Analysis Services.

Quanto più il gateway è vicino al server, tanto più veloce sarà la connessione. È preferibile che il gateway si trovi nello stesso server dell’origine dati, per evitare la latenza di rete tra il gateway e il server.

## <a name="what-to-do-next"></a>Azioni successive
Dopo averlo installato, è consigliabile creare origini dati per il gateway. È possibile aggiungere origini dati all'interno della schermata **Gestisci gateway**. Per altre informazioni vedere gli articoli sulla gestione delle origini dati.

[Gestire l'origine dati - Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[Gestire l'origine dati - SAP HANA](service-gateway-enterprise-manage-sap.md)  
[Gestire l'origine dati - SQL Server](service-gateway-enterprise-manage-sql.md)  
[Gestire l'origine dati - Oracle](service-gateway-onprem-manage-oracle.md)  
[Gestire l'origine dati - Importazione/aggiornamento pianificato](service-gateway-enterprise-manage-scheduled-refresh.md)  

## <a name="where-things-can-go-wrong"></a>Possibili esiti negativi
In alcuni casi l'installazione del gateway non riesce. In altri casi, il gateway sembra essere installato correttamente, ma il servizio non riesce comunque a usarlo. In molti casi, si tratta di un problema semplice, ad esempio la password per le credenziali che il gateway usa per accedere all'origine dati.

In altri casi, potrebbero esserci problemi con il tipo di indirizzo di posta elettronica con cui gli utenti eseguono l'accesso oppure con l'impossibilità di risolvere un nome utente effettivo in Analysis Services. Se si hanno più domini con trust reciproci e il gateway si trova in uno di essi e Analysis Services nell'altro, in alcuni casi potrebbero verificarsi dei problemi.

Invece di analizzare la risoluzione dei problemi del gateway in questo articolo, è stata raccolta una serie di passaggi di risoluzione dei problemi in un altro articolo, [Risoluzione dei problemi del gateway dati locale](service-gateway-onprem-tshoot.md). Probabilmente non si verificherà alcun problema, ma in tal caso, la conoscenza del funzionamento generale e l'articolo sulla risoluzione dei problemi dovrebbero essere d'aiuto.

<!-- Account and Port information -->
[!INCLUDE [gateway-onprem-accounts-ports-more](./includes/gateway-onprem-accounts-ports-more.md)]

## <a name="next-steps"></a>Passaggi successivi
[Risoluzione dei problemi del gateway dati locale](service-gateway-onprem-tshoot.md)  
[Bus di servizio di Azure](https://azure.microsoft.com/documentation/services/service-bus/)  
[Azure AD Connect](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/)  
Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

