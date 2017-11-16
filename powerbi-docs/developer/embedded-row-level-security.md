---
title: Usare la sicurezza a livello di riga con il contenuto incorporato di Power BI
description: Informazioni sulla procedura da seguire per incorporare il contenuto di Power BI all'interno dell'applicazione.
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/09/2017
ms.author: asaxton
ms.openlocfilehash: 1f59bd4e0178b1fe1b67f57b085de69da1b06951
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2017
---
# <a name="use-row-level-security-with-power-bi-embedded-content"></a>Usare la sicurezza a livello di riga con il contenuto incorporato di Power BI
È possibile usare la sicurezza a livello di riga per limitare l'accesso utente ai dati in un report o in un set di dati e consentire a più utenti diversi di usare lo stesso report, visualizzando tutti dati differenti. La sicurezza a livello di riga è utile quando si incorporano i report da Power BI.

Se si incorporano dati per utenti non Power BI (i dati sono di proprietà dell'app), ovvero un tipico scenario ISV, leggere questo articolo. Sarà necessario configurare il token di incorporamento per l'utente e il ruolo. Ecco come eseguire questa operazione.

Se la condivisione viene effettuata con utenti di Power BI (i dati sono di proprietà dell'utente) all'interno dell'organizzazione, la sicurezza a livello di riga funziona esattamente come nel servizio Power BI. Non è necessario eseguire altre operazioni nell'applicazione. Per altre informazioni, vedere [Sicurezza a livello di riga con Power BI](../service-admin-rls.md).

![Elementi coinvolti con la sicurezza a livello di riga.](media/embedded-row-level-security/powerbi-embedded-rls-components.png)

Per sfruttare al meglio la sicurezza a livello di riga, è importante comprendere tre concetti fondamentali, ovvero utenti, ruoli e regole, che verranno ora analizzati più in dettaglio:

**Utenti**: si tratta degli utenti finali effettivi che visualizzano i report. In Power BI Embedded gli utenti vengono identificati tramite la proprietà username in un token di incorporamento.

**Ruoli**: gli utenti appartengono a ruoli. Un ruolo è un contenitore di regole e può essergli assegnato un nome simile a *Responsabile vendite* o *Rappresentante vendite*. I ruoli vengono creati in Power BI Desktop. Per altre informazioni, vedere [Sicurezza a livello di riga con Power BI Desktop](../desktop-rls.md).

**Regole**: i ruoli contengono regole e tali regole costituiscono i filtri effettivi che verranno applicati ai dati. Possono essere semplici, ad esempio "Paese = USA", oppure molto più dinamici.
La parte rimanente di questo articolo fornisce un esempio di creazione di sicurezza a livello di riga e il relativo utilizzo in un'applicazione incorporata. In questo esempio viene usato il file PBIX [Retail Analysis Sample](http://go.microsoft.com/fwlink/?LinkID=780547).

![Esempio di report](media/embedded-row-level-security/powerbi-embedded-report-example.png)

## <a name="adding-roles-with-power-bi-desktop"></a>Aggiunta di ruoli con Power BI Desktop
L'esempio di analisi delle vendite al dettaglio mostra le vendite per tutti i negozi di una catena specifica. Senza sicurezza a livello di riga, tutti i responsabili di area che accedono al report visualizzano gli stessi dati. I dirigenti hanno stabilito che ogni responsabile di area debba visualizzare solo le vendite dei negozi che gestisce e, per ottenere questo risultato, è possibile usare la sicurezza a livello di riga.

La sicurezza a livello di riga viene creata in Power BI Desktop. All'apertura del set di dati e del report, è possibile passare alla visualizzazione diagramma per visualizzare lo schema:

![Visualizzazione diagramma in Power BI Desktop](media/embedded-row-level-security/powerbi-embedded-schema.png)

Alcuni aspetti da notare in questo schema:

* Tutte le misure, ad esempio **Total Sales**, sono archiviate nella tabella dei fatti **Sales**.
* Sono presenti altre quattro tabelle delle dimensioni correlate: **Item**, **Time**, **Store** e **District**.
* Le frecce sulle linee delle relazioni indicano la direzione in cui i filtri possono essere applicati da una tabella all'altra. Ad esempio, se un filtro è posizionato su **Time[Date]**, nello schema corrente verrebbero filtrati solo i valori presenti nella tabella **Sales**. Questo filtro non influirebbe su altre tabelle, perché tutte le frecce sulle linee relative alle relazioni fanno riferimento alla tabella Sales, non ad altre tabelle.
* La tabella **District** indica il responsabile per ogni area:
  
    ![Righe all'interno della tabella District](media/embedded-row-level-security/powerbi-embedded-district-table.png)

In base a questo schema, se si applica un filtro alla colonna **District Manager** nella tabella **District** e se tale filtro corrisponde all'utente che visualizza il report, verranno filtrate anche le tabelle **Store** e **Sales** per visualizzare solo i dati relativi al responsabile di area specifico.

Ecco come:

1. Nella scheda **Creazione di modelli** selezionare **Gestisci ruoli**.
   
    ![Scheda Creazione di modelli in Power BI Desktop](media/embedded-row-level-security/powerbi-embedded-manage-roles.png)
2. Creare un nuovo ruolo denominato **Manager**.
   
    ![Crea nuovo ruolo](media/embedded-row-level-security/powerbi-embedded-new-role.png)
3. Nella tabella **District** immettere l'espressione DAX seguente: **[District Manager] = USERNAME()**.
   
    ![Istruzione DAX per la regola di sicurezza a livello di riga](media/embedded-row-level-security/powerbi-embedded-new-role-dax.png)
4. Per verificare che le regole funzionino correttamente, nella scheda **Creazione di modelli** selezionare **Visualizza come ruoli** e quindi il ruolo **Manager** appena creato, insieme ad **Altro utente**. Per l'utente, immettere **Andrew Ma**.
   
    ![Finestra di dialogo Visualizza come ruoli](media/embedded-row-level-security/powerbi-embedded-new-role-view.png)
   
    A questo punto, nei report verranno visualizzati i dati come se l'accesso fosse stato eseguito come **Andrew Ma**.

Applicando il filtro, come in questa procedura, vengono filtrati tutti i record nelle tabelle **District**, **Store** e **Sales**. Tuttavia, a causa della direzione del filtro sulle relazioni tra le tabelle **Sales** e **Time** e **Sales** e **Item**, le tabelle **Item** e **Time** non verranno filtrate. Per altre informazioni sui filtri incrociati bidirezionali, scaricare il white paper [Bidirectional cross-filtering in SQL Server Analysis Services 2016 and Power BI Desktop](http://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx) (Filtri incrociati bidirezionali in SQL Server Analysis Services 2016 e Power BI Desktop).

## <a name="applying-user-and-role-to-an-embed-token"></a>Applicazione di utente e ruolo a un token di incorporamento
A questo punto, dopo aver configurato i ruoli di Power BI Desktop, per usare i ruoli è necessario eseguire alcune operazioni nell'applicazione.

Gli utenti vengono autenticati e autorizzati dall'applicazione e i token di incorporamento vengono usati per concedere l'accesso utente a un report specifico di Power BI Embedded. Power BI Embedded non ha informazioni specifiche sull'identità dell'utente. Per il corretto funzionamento della sicurezza a livello di riga, sarà necessario passare altre informazioni del contesto come parte del token di incorporamento sotto forma di identità. Per questa operazione, si userà l'API [GenerateToken](https://msdn.microsoft.com/library/mt784614.aspx).

L'API [GenerateToken](https://msdn.microsoft.com/library/mt784614.aspx) accetta un elenco di identità con l'indicazione dei set di dati pertinenti. Attualmente, è possibile specificare una sola identità. In futuro verrà aggiunto il supporto per più set di dati, per l'incorporamento di dashboard. Per il corretto funzionamento della sicurezza a livello di riga, sarà necessario passare quanto segue come parte dell'identità.

* **username (obbligatoria)**: questa stringa può semplificare l'identificazione dell'utente quando si applicano le regole di sicurezza a livello di riga. È possibile specificare solo un utente.
* **roles (obbligatoria)**: stringa contenente i ruoli da selezionare quando si applicano le regole di sicurezza a livello di riga. Se si passa più di un ruolo, sarà necessario passarli come matrice di stringhe.
* **dataset (obbligatoria)**: set di dati applicabile per il report che verrà incorporato. Nell'elenco dei set di dati è possibile specificare un solo set di dati. In futuro verrà aggiunto il supporto per più set di dati, per l'incorporamento di dashboard.

Per creare il token di incorporamento, usare il metodo **GenerateTokenInGroup** su **PowerBIClient.Reports**. Attualmente, sono supportati solo i report.

È ad esempio possibile modificare l'esempio [PowerBIEmbedded_AppOwnsData](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/App%20Owns%20Data). Aggiornando le *righe 76 e 77 del file Home\HomeController.cs* da:

```
// Generate Embed Token.
var generateTokenRequestParameters = new GenerateTokenRequest(accessLevel: "view");

var tokenResponse = await client.Reports.GenerateTokenInGroupAsync(GroupId, report.Id, generateTokenRequestParameters);
```

a

```
var generateTokenRequestParameters = new GenerateTokenRequest("View", null, identities: new List<EffectiveIdentity> { new EffectiveIdentity(username: "username", roles: new List<string> { "roleA", "roleB" }, datasets: new List<string> { "datasetId" }) });

var tokenResponse = await client.Reports.GenerateTokenInGroupAsync("groupId", "reportId", generateTokenRequestParameters);
```

Se si chiama l'API REST, l'API aggiornata ora accetta una matrice JSON aggiuntiva, denominata **identities**, contenente un nome utente, un elenco dei ruoli stringa e un elenco di set di dati stringa, ad esempio:

```
{
    "accessLevel": "View",
    "identities": [
        {
            "username": "EffectiveIdentity",
            "roles": [ "Role1", "Role2" ],
            "datasets": [ "fe0a1aeb-f6a4-4b27-a2d3-b5df3bb28bdc" ]
        }
    ]
}
```

Ora, dopo aver eseguito tutti i passaggi, quando un utente effettua l'accesso all'applicazione per visualizzare questo report, potrà visualizzare solo i dati che è autorizzato a vedere, come definito dalla sicurezza a livello di riga.

## <a name="working-with-analysis-services-live-connections"></a>Uso di connessioni dinamiche ad Analysis Services
La sicurezza a livello di riga può essere usata solo con le connessioni in tempo reale di Analysis Services per i server locali. Esistono alcuni concetti specifici che è bene conoscere quando si usa questo tipo di connessione.

L'identità effettiva specificata per la proprietà username deve essere un utente di Windows con autorizzazioni per il server Analysis Services.

**Configurazione del gateway dati locale**

Un [gateway dati locale](../service-gateway-onprem.md) viene usato quando si lavora con connessioni dinamiche di Analysis Services. Quando si genera un token di incorporamento, con un'identità elencata, l'account principale deve essere elencato come amministratore del gateway. Se l'account principale non è elencato, la sicurezza a livello di riga non verrà applicata correttamente ai dati. Chi non è amministratore del gateway può fornire i ruoli, ma deve specificare il proprio nome utente per l'identità effettiva.

**Uso dei ruoli**

I ruoli possono essere forniti con l'identità in un token di incorporamento. Se non vengono forniti ruoli, il nome utente fornito verrà usato per risolvere i ruoli associati.

## <a name="considerations-and-limitations"></a>Considerazioni e limitazioni
* L'assegnazione di utenti ai ruoli, all'interno del servizio Power BI, non influisce sulla sicurezza a livello di riga quando si usa un token di incorporamento.
* Il servizio Power BI non applicherà l'impostazione di sicurezza a livello di riga agli amministratori o ai membri con autorizzazioni di modifica, ma quando si fornisce un'identità con un token di incorporamento, l'impostazione verrà applicata ai dati.
* Quando si chiama il metodo GenerateToken, il passaggio delle informazioni di identità è supportato solo per la lettura/scrittura dei report. Il supporto per altre risorse sarà disponibile in un secondo momento.
* Sono supportate le connessioni dinamiche ad Analysis Services per i server locali.
* Le connessioni in tempo reale ad Azure Analysis Services non sono supportate.
* Se il set di dati sottostante non richiede la sicurezza a livello di riga, la richiesta GenerateToken **non** deve contenere un'identità effettiva.
* Se il set di dati sottostante è un modello cloud (modello memorizzato nella cache o DirectQuery), l'identità effettiva deve includere almeno un ruolo. In caso contrario, l'assegnazione di ruolo non verrà eseguita.
* Nell'elenco di identità è possibile specificare una sola identità. Viene usato un elenco per consentire l'abilitazione di token con più identità per l'incorporamento di dashboard in futuro.

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)

