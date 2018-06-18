---
title: Come condividere i dashboard, i report e i riquadri di Power BI
description: Informazioni sulla procedura da seguire per incorporare il contenuto di Power BI all'interno dell'applicazione.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 05/25/2018
ms.author: maghan
ms.openlocfilehash: cb84cb2f4242cb120f187c27bb1b1675177c33a2
ms.sourcegitcommit: 8ee0ebd4d47a41108387d13a3bc3e7e2770cbeb8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2018
ms.locfileid: "34813044"
---
# <a name="embed-your-power-bi-dashboards-reports-and-tiles"></a>Incorporare i dashboard, i report e i riquadri di Power BI

Informazioni sulla procedura da seguire per incorporare il contenuto di Power BI all'interno dell'applicazione.

Microsoft ha [annunciato Power BI Premium](https://powerbi.microsoft.com/blog/microsoft-accelerates-modern-bi-adoption-with-power-bi-premium/), un nuovo modello di gestione delle licenze basato sulla capacità che aumenta la flessibilità di accesso, condivisione e distribuzione del contenuto per gli utenti. L'offerta aggiunge anche ulteriore scalabilità e rendimento al servizio Power BI. È stato annunciato anche Power BI Embedded, che consente la creazione di capacità in Microsoft Azure. Power BI Embedded è incentrato sull'applicazione e sui clienti dell'utente. 

Questo articolo esamina la procedura per incorporare il contenuto di Power BI per l'organizzazione e i clienti. I passaggi sono simili per entrambi gli scenari. Quando un passaggio è specifico della procedura di incorporamento per il cliente, questo viene chiaramente indicato.

A tale scopo, sono previsti alcuni passaggi che è necessario eseguire con l'applicazione. Vengono illustrati i passaggi necessari per creare e usare il contenuto incorporato all'interno dell'applicazione.

> [!NOTE]
> Le API di Power BI fanno ancora riferimento alle aree di lavoro per le app come gruppi. I riferimenti ai gruppi indicano che si stanno usando le aree di lavoro per le app.

## <a name="step-1-setup-your-embedded-analytics-development-environment"></a>Passaggio 1: Configurare l'ambiente di sviluppo di analisi incorporato

Prima di iniziare la procedura di incorporamento di dashboard e report in un'applicazione, è necessario assicurarsi che l'ambiente sia configurato per consentire l'incorporamento. La configurazione include le operazioni seguenti.

* [Verificare di avere un tenant di Azure Active Directory](embedding-content.md#azureadtenant)
* [Creare l'account di Power BI Pro](embedding-content.md#proaccount)

È possibile usare lo [strumento esperienza di onboarding](https://aka.ms/embedsetup) per iniziare rapidamente e scaricare un'applicazione di esempio.

Scegliere la soluzione adatta alle proprie esigenze:
* L'[incorporamento per i clienti](embedding.md#embedding-for-your-customers) offre la possibilità di incorporare dashboard e report per gli utenti che non hanno un account per Power BI. Eseguire la soluzione [Incorporare per i clienti](https://aka.ms/embedsetup/AppOwnsData).
* L'[incorporamento per l'organizzazione](embedding.md#embedding-for-your-organization) consente di estendere il servizio Power BI. Eseguire la soluzione [Incorporare per l'organizzazione](https://aka.ms/embedsetup/UserOwnsData).

Se tuttavia si sceglie di configurare l'ambiente manualmente, è possibile continuare con le istruzioni che seguono. 

> [!NOTE]
> La capacità dedicata non è necessaria per lo sviluppo dell'applicazione. Gli sviluppatori dell'applicazione devono avere una licenza di Power BI Pro.

### <a name="azureadtenant"></a>Tenant di Azure Active Directory

Per incorporare elementi da Power BI è necessario avere un tenant di Azure Active Directory (Azure AD). Questo tenant deve avere almeno un utente di Power BI Pro. È inoltre necessario definire un'app di Azure AD nel tenant. È possibile usare un tenant di Azure AD esistente o crearne uno nuovo specifico per eseguire l'incorporamento.

In caso di incorporamento per i clienti, è necessario stabilire la configurazione da usare per il tenant.

* Usare il tenant di Power BI aziendale esistente?
* Usare un tenant diverso per l'applicazione?
* Usare un tenant diverso per ogni cliente?

Se non si vuole usare un tenant esistente, è possibile decidere di creare un nuovo tenant per l'applicazione o di crearne uno per ogni cliente. Vedere [Creare un tenant di Azure Active Directory](create-an-azure-active-directory-tenant.md) o [Come ottenere un tenant di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-howto-tenant).

### <a name="proaccount"></a>Creare un account utente di Power BI Pro

Per incorporare il contenuto è necessario disporre di un solo account di Power BI Pro. Tuttavia, è consigliabile disporre di diversi utenti che hanno un accesso specifico agli elementi. Ecco gli utenti che è possibile prendere in considerazione all'interno del tenant.

È necessario che all'interno del tenant siano presenti gli account indicati di seguito e che sia stata loro assegnata una licenza di Power BI Pro. Per usare le aree di lavoro dell'app in Power BI, è necessaria una licenza per Power BI Pro.

#### <a name="an-organizationtenant-admin-user"></a>Un utente amministratore del tenant/dell'organizzazione

È consigliabile che l'utente amministratore globale del tenant o dell'organizzazione non sia usato come account dell'applicazione in caso di incorporamento per i clienti, allo scopo di ridurre l'accesso dell'account dell'applicazione all'interno del tenant. È consigliabile che l'utente amministratore sia un amministratore di tutte le aree di lavoro dell'app create per l'incorporamento.

#### <a name="accounts-for-analysts-that-create-content"></a>Account per gli analisti che creano il contenuto

Possono esserci più utenti che creano contenuto per Power BI. È necessario un account di Power BI Pro per ogni analista che crea e distribuisce il contenuto in Power BI.

#### <a name="an-application-master-user-account-for-embedding-for-your-customers"></a>Account utente *master* dell'applicazione per l'incorporamento per i clienti

L'account master è l'account usato dall'applicazione quando si incorpora contenuto per i clienti. Questo scenario è in genere relativo ad applicazioni ISV. L'account master è l'unico account obbligatorio che è necessario all'interno dell'organizzazione. Può anche essere usato come account di amministratore e analista, ma non è consigliato. Il back-end dell'applicazione memorizza le credenziali di questo account e lo usa per acquisire un token di autenticazione di Azure AD da usare con le API di Power BI. Questo account genera un token di incorporamento che l'applicazione usa per i clienti.

L'account master è semplicemente un utente normale con una licenza di Power BI Pro che viene usato con l'applicazione. Deve essere un account amministratore delle aree di lavoro per le app create per l'incorporamento.

### <a name="appreg"></a> Registrazione e autorizzazioni dell'app

Per effettuare chiamate all'API REST è necessario registrare l'applicazione in Azure AD. Per altre informazioni, vedere [Registrare un'app di Azure AD per incorporare il contenuto di Power BI](register-app.md).

### <a name="create-app-workspaces"></a>Creare aree di lavoro per le app

Se si intende incorporare dashboard e report per i clienti, questi elementi devono essere inseriti nell'area di lavoro di un'app. L'account *master* indicato in precedenza deve corrispondere a un amministratore dell'area di lavoro dell'app.

[!INCLUDE [powerbi-service-create-app-workspace](../includes/powerbi-service-create-app-workspace.md)]

> [!NOTE]
> Un utente senza privilegi di amministratore può creare solo fino a 250 aree di lavoro per le app. Per creare più aree di lavoro per le app, è necessario utilizzare un account di amministratore tenant.
>

### <a name="create-and-upload-your-reports"></a>Creare e caricare i report

È possibile creare report e set di dati usando Power BI Desktop e quindi pubblicando tali report in un'area di lavoro per le app. Per poter pubblicare in un'area di lavoro dell'app, l'utente finale che pubblica report deve avere una licenza di Power BI Pro.

## <a name="step-2-embed-your-content"></a>Passaggio 2: Incorporare il contenuto

All'interno dell'applicazione è necessario eseguire l'autenticazione con Power BI. Se si intende incorporare contenuto per i clienti, archiviare le credenziali per l'account *master* all'interno dell'applicazione. Per altre informazioni, vedere [Autenticare gli utenti e ottenere un token di accesso di Azure AD per l'app Power BI](get-azuread-access-token.md).

Dopo l'autenticazione, nell'applicazione usare le API REST di Power BI e le API JavaScript per incorporare dashboard e report nell'applicazione. 

Per l'**incorporamento per l'organizzazione**, vedere le procedure dettagliate seguenti:

* [Integrare un dashboard in un'app](integrate-dashboard.md)
* [Integrare un riquadro in un'app](integrate-tile.md)
* [Integrare un report in un'app](integrate-report.md)

Per l'**incorporamento per i clienti**, scenario tipico per ISV, vedere quanto segue:

* [Integrare un dashboard, un riquadro o un report nell'applicazione](embed-sample-for-customers.md)

Quando si esegue l'incorporamento per i clienti, è necessario un token di incorporamento. Per altre informazioni, vedere [Embed Token](https://docs.microsoft.com/rest/api/power-bi/embedtoken) (Token di incorporamento).

## <a name="step-3-promote-your-solution-to-production"></a>Passaggio 3: Alzare di livello della soluzione alla produzione

Lo spostamento in produzione richiede alcuni passaggi aggiuntivi.

### <a name="embedding-for-your-organization"></a>Incorporamento per l'organizzazione

Se si intende incorporare per l'organizzazione, è sufficiente informare gli utenti su come ottenere l'applicazione. 

Gli utenti del piano Gratuito possono usare i contenuti incorporati dall'area di lavoro di un'app (gruppo) se la capacità dedicata supporta l'area di lavoro. Indicare l'utente del piano Gratuito come membro dell'area di lavoro dell'app (gruppo). In caso contrario, verrà visualizzato un errore 401 di autorizzazione negata. La tabella seguente elenca gli SKU di Power BI Premium disponibili in Office 365.

| Nodo della capacità | Totale core<br/>*(Back-end + front-end)* | Core di back-end | Core di front-end | Limiti di connessione dinamica/DirectQuery | Rendering massimo della pagina all'ora di punta |
| --- | --- | --- | --- | --- | --- |
| EM3 |4 v-core |2 core, 10 GB di RAM |2 core | |601-1.200 |
| P1 |8 v-core |4 core, 25 GB di RAM |4 core |30 al secondo |1.201-2.400 |
| P2 |16 v-core |8 core, 50 GB di RAM |8 core |60 al secondo |2.401-4.800 |
| P3 |32 v-core |16 core, 100 GB di RAM |16 ore |120 al secondo |4.801-9600 |

> [!NOTE]
> Per acquistare Power BI Premium è necessario essere un amministratore globale o di fatturazione all'interno del tenant. Per informazioni su come acquistare Power BI Premium, vedere [How to purchase Power BI Premium](../service-admin-premium-purchase.md) (Come acquistare Power BI Premium).

>[!Note]
>[Configurare l'ambiente di analisi incorporato per l'organizzazione](#step-1-setup-your-embedded-analytics-development-environment).
>

### <a name="embedding-for-your-customers"></a>Incorporamento per i clienti

Per eseguire l'incorporamento per i clienti, procedere nel modo seguente.

* Se si usa un tenant diverso per lo sviluppo, è necessario assicurarsi che l'area di lavoro per le app, insieme ai dashboard e ai report, sia disponibile nell'ambiente di produzione. Assicurarsi di creare l'applicazione in Azure AD per il tenant di produzione e di assegnare le autorizzazioni di dell'app adeguate, come indicato nel Passaggio 1.
* Acquistare una capacità adatta alle proprie esigenze. È possibile usare la tabella seguente per individuare gli SKU per la capacità di Power BI Embedded necessari. Per altre informazioni, vedere [Embedded analytics capacity planning whitepaper](https://aka.ms/pbiewhitepaper) (White paper sulla pianificazione della capacità di analisi incorporata) Quando si è pronti, è possibile completare l'acquisto nel [portale di Microsoft Azure](https://portal.azure.com). Per informazioni dettagliate su come creare capacità per Power BI Embedded, vedere [Create Power BI Embedded capacity in the Azure portal](https://docs.microsoft.com/azure/power-bi-embedded/create-capacity) (Creare capacità per Power BI Embedded nel portale di Azure).

> [!IMPORTANT]
> Dato che i token di incorporamento sono destinati solo alle attività di test degli sviluppatori, il numero di token di incorporamento che un account master Power BI può generare è limitato. È necessario [acquistare una capacità](https://docs.microsoft.com/power-bi/developer/embedded-faq#technical) per gli scenari di incorporamento della produzione. Dopo l'acquisto di una capacità dedicata è possibile generare un numero illimitato di token di incorporamento. Vedere [Available Features](https://docs.microsoft.com/rest/api/power-bi/availablefeatures) (Funzionalità disponibili) per controllare il numero di token di incorporamento gratuiti usati.

| Nodo della capacità | Totale core<br/>*(Back-end + front-end)* | Core di back-end | Core di front-end | Limiti di connessione dinamica/DirectQuery | Rendering massimo della pagina all'ora di punta |
| --- | --- | --- | --- | --- | --- |
| A1 |1 v-core |0,5 core, 3 GB di RAM |0,5 core | 5 al secondo |1-300 |
| A2 |2 v-core |1 core, 5 GB di RAM |1 core | 10 al secondo |301-600 |
| A3 |4 v-core |2 core, 10 GB di RAM |2 core | 15 al secondo |601-1.200 |
| A4 |8 v-core |4 core, 25 GB di RAM |4 core |30 al secondo |1.201-2.400 |
| A5 |16 v-core |8 core, 50 GB di RAM |8 core |60 al secondo |2.401-4.800 |
| A6 |32 v-core |16 core, 100 GB di RAM |16 ore |120 al secondo |4.801-9600 |

* Modificare l'area di lavoro dell'app e assegnarla a una capacità dedicata in Avanzate.

    ![Assegnare un'area di lavoro a una capacità](media/embedding-content/powerbi-embedded-premium-capacity.png)

* Distribuire l'applicazione aggiornata nell'ambiente di produzione e iniziare a incorporare i dashboard e i report di Power BI.

>[!Note]
>[Configurare l'ambiente di analisi incorporato per i clienti](#step-1-setup-your-embedded-analytics-development-environment). 
>

## <a name="admin-settings"></a>Impostazioni di amministrazione

Gli amministratori globali o gli amministratori del servizio Power BI possono attivare o disattivare la possibilità di usare le API REST per un tenant. Gli amministratori di Power BI possono configurare questa impostazione per l'intera organizzazione o per singoli gruppi di sicurezza. L'opzione è abilitata per l'intera organizzazione per impostazione predefinita. Questa operazione viene eseguita tramite il [portale di amministrazione di Power BI](../service-admin-portal.md).

## <a name="next-steps"></a>Passaggi successivi

[Incorporamento con Power BI](embedding.md)  
[Come eseguire la migrazione del contenuto della raccolta di aree di lavoro di Power BI Embedded in Power BI](migrate-from-powerbi-embedded.md)  
[Power BI Premium - what is it?](../service-premium.md) (Power BI Premium: descrizione)  
[How to purchase Power BI Premium](../service-admin-premium-purchase.md) (Come acquistare Power BI Premium)  
[Archivio GIT API JavaScript](https://github.com/Microsoft/PowerBI-JavaScript)  
[Archivio GIT C# di Power BI](https://github.com/Microsoft/PowerBI-CSharp)  
[Esempio di incorporamento JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/)  
[Embedded analytics capacity planning whitepaper](https://aka.ms/pbiewhitepaper) (White paper sulla pianificazione della capacità di analisi incorporata)  
[White paper su Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)