---
title: Gestire l'origine dati - Analysis Services
description: Come gestire il gateway dati locale e le origini dati che vi appartengono. Questo argomento è per Analysis Services in modalità tabulare e multidimensionale.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 93475f6476f8baad73229473bd3ce60db68a320b
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271634"
---
# <a name="manage-your-data-source---analysis-services"></a>Gestire l'origine dati - Analysis Services

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Dopo aver [installato il gateway dati locale](/data-integration/gateway/service-gateway-install), sarà necessario [aggiungere le origini dati](service-gateway-data-sources.md#add-a-data-source) che possono essere usate con il gateway. Questo articolo descrive l'uso di gateway e origini dati di Analysis Services per l'aggiornamento pianificato o le connessioni in tempo reale.

Per altre informazioni sulla configurazione di una connessione dinamica ad Analysis Services, [guardare questo video](https://www.youtube.com/watch?v=GPf0YS-Xbyo&feature=youtu.be).

> [!NOTE]
> Se si dispone di un'origine dati di Analysis Services, è necessario installare il gateway in un computer appartenente allo stesso insieme di strutture o dominio del server Analysis Services.

## <a name="add-a-data-source"></a>Aggiungere un'origine dati

Per informazioni sull'aggiunta di un'origine dati, vedere [Aggiungere un'origine dati](service-gateway-data-sources.md#add-a-data-source). Selezionare Analysis Services per il **tipo di origine dati** se ci si connette a un server tabulare o multidimensionale.

![Aggiungere l'origine dati di Analysis Services](media/service-gateway-enterprise-manage-ssas/datasourcesettings2-ssas.png)

Inserire le informazioni per l'origine dati, tra cui il **Server** e il **Database**. Il **Nome utente** e la **Password** immessi verranno usati dal gateway per connettersi all'istanza di Analysis Services.

> [!NOTE]
> L'account di Windows immesso deve avere le autorizzazioni di amministratore del server per l'istanza a cui ci si connette. Se la password dell'account è impostata in modo da scadere, gli utenti potrebbero visualizzare un errore di connessione se la password non viene aggiornata per l'origine dati. Per altre informazioni su come vengono archiviate le credenziali, vedere [Archiviazione di credenziali crittografate nel cloud](service-gateway-data-sources.md#storing-encrypted-credentials-in-the-cloud).

![Compilazione delle impostazioni origine dati](media/service-gateway-enterprise-manage-ssas/datasourcesettings3-ssas.png)

Selezionare **Aggiungi** dopo aver compilato tutti i campi. È ora possibile usare questa origine dati per l'aggiornamento pianificato, o per le connessioni in tempo reale, su un'istanza di Analysis Services locale. Verrà visualizzato *Connessione riuscita* se la connessione ha avuto esito positivo.

![Visualizzazione dello stato della connessione](media/service-gateway-enterprise-manage-ssas/datasourcesettings4.png)

### <a name="advanced-settings"></a>Impostazioni avanzate

È possibile configurare il livello di privacy per l'origine dati, se necessario. Questa impostazione controlla il modo in cui vengono combinati i dati. L'impostazione viene usata solo per l'aggiornamento pianificato e non per le connessioni in tempo reale. Per altre informazioni sui livelli di privacy per l'origine dati, vedere [Livelli di privacy (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540).

![Impostazione del livello di privacy](media/service-gateway-enterprise-manage-ssas/datasourcesettings9.png)

## <a name="usernames-with-analysis-services"></a>Nomi utente con Analysis Services

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qb5EEjkHoLg" frameborder="0" allowfullscreen></iframe>

Ogni volta che un utente interagisce con un report connesso ad Analysis Services, il nome utente effettivo viene passato al gateway e quindi al server Analysis Services locale. L'indirizzo di posta elettronica con cui si accede a Power BI è l'informazione che viene passata ad Analysis Services come utente effettivo. Tale informazione viene passata nella proprietà di connessione [EffectiveUserName](https://msdn.microsoft.com/library/dn140245.aspx#bkmk_auth). Questo indirizzo di posta elettronica deve corrispondere a un nome di entità utente (UPN) definito all'interno del dominio di Active Directory locale. L'UPN è una proprietà di un account di Active Directory. Questo account di Windows deve quindi essere presente in un ruolo di Analysis Services. Se non viene rilevata alcuna corrispondenza in Active Directory, l'accesso non riesce. Per altre informazioni su Active Directory e sulla denominazione degli utenti, consultare gli [attributi di denominazione degli utenti](https://msdn.microsoft.com/library/ms677605.aspx).

È anche possibile eseguire il [mapping del nome di accesso a Power BI con un UPN della directory locale](service-gateway-enterprise-manage-ssas.md#mapping-usernames-for-analysis-services-data-sources).

## <a name="mapping-usernames-for-analysis-services-data-sources"></a>Mapping di nomi utente per le origini dati di Analysis Services

<iframe width="560" height="315" src="https://www.youtube.com/embed/eATPS-c7YRU" frameborder="0" allowfullscreen></iframe>

Power BI consente di eseguire il mapping di nomi utente per le origini dati di Analysis Services. È possibile configurare regole per eseguire il mapping di un nome utente che ha eseguito l'accesso a Power BI a un nome che viene passato per EffectiveUserName usando la connessione di Analysis Services. La funzionalità di mapping dei nomi utente rappresenta un'ottima soluzione alternativa quando il nome utente in AAD non corrisponde a un UPN in Active Directory locale. Ad esempio, se l'indirizzo di posta elettronica è nancy@contoso.onmicrsoft.com, è possibile eseguirne il mapping a nancy@contoso.com e tale valore viene passato al gateway.

È possibile eseguire il mapping dei nomi utente per Analysis Services in due modi diversi:

* Nuovo mapping manuale dell'utente
* Ricerca proprietà in Active Directory locale per ripetere il mapping gli UPN di AAD agli utenti di Active Directory (mapping con ricerca tramite AD)

Sebbene sia possibile eseguire il mapping manuale usando il secondo approccio, questa operazione richiederebbe molto tempo ed è difficile da gestire. È particolarmente difficile quando i criteri di ricerca non sono sufficienti, ad esempio quando i nomi di dominio sono diversi tra AAD e AD locale oppure quando i nomi degli account utente sono diversi tra AAD e AD. Di conseguenza, il mapping manuale con il secondo approccio è sconsigliato.

Questi due approcci vengono descritti nelle due sezioni seguenti.

### <a name="manual-user-name-re-mapping"></a>Nuovo mapping manuale dei nomi utente

Per le origini dati di Analysis Services, è possibile configurare regole personalizzate del nome dell'entità utente (UPN). Ciò sarà utile se i nomi di accesso al servizio Power BI non corrispondono all’UPN della directory locale. Ad esempio, se si accede a Power BI con john@contoso.com, ma l'UPN della directory locale è john@contoso.local, è possibile configurare una regola di mapping in modo che john@contoso.local sia passato ad Analysis Services.

Per visualizzare la schermata di mapping dell’UPN, eseguire le operazioni seguenti.

1. Passare all’**icona dell’ingranaggio** e selezionare **Gestisci gateway**.
2. Espandere il gateway che contiene l'origine dati di Analysis Services. In alternativa, se non è stata creata l'origine dati di Analysis Services, è possibile farlo ora.
3. Selezionare l'origine dati, quindi la scheda **Utenti**.
4. Selezionare **Mapping nome utente**.

    ![Schermata del mapping UPN](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names_02.png)

Verranno quindi visualizzate le opzioni per aggiungere regole, nonché testarle per un determinato utente.

> [!NOTE]
> Si potrebbe modificare inavvertitamente un utente che non si intendeva modificare. Ad esempio, se il **Sostituisci (valore originale)** è <em>@contoso.com</em> e **Con (nuovo nome)** è <em>@contoso.local</em>, tutti gli utenti con un nome di accesso contenente <em>@contoso.com</em> verranno sostituiti con <em>@contoso.local</em>. Inoltre, se il **Sostituisci (nome originale)** è <em>dave@contoso.com</em> e **Con (nuovo nome)** è <em>dave@contoso.local</em>, un utente con il nome di accesso v-dave@contoso.com sarà inviato come v-dave<em>@contoso.local</em>.

### <a name="ad-lookup-mapping"></a>Mapping con ricerca tramite AD

Per eseguire la ricerca proprietà in Active Directory locale in modo da ripetere il mapping degli UPN di AAD agli utenti di Active Directory, seguire i passaggi descritti in questa sezione. Per iniziare, esaminarne il funzionamento.

Nel **servizio Power BI** si verifica quanto segue:

* Per ogni query da un utente di AAD di Power BI a un server SSAS locale, viene passata una stringa UPN, ad esempio:      firstName.lastName@contoso.com

> [!NOTE]
> Tutti i mapping utente UPN manuali definiti nella configurazione di origine dati di Power BI vengono comunque applicati *prima* di inviare la stringa del nome utente al gateway dati locale.

Nel gateway dati locale con mapping personalizzato configurabile dall'utente, eseguire questa procedura:

1. Trovare Active Directory per la ricerca (automatica o configurabile).
2. Cercare l'attributo dell'utente di Active Directory (ad esempio *Email*) basato sulla stringa UPN in ingresso ("firstName.lastName@contoso.com") dal **servizio Power BI**.
3. Se la ricerca tramite AD non riesce, proverà a usare l'UPN passato come EffectiveUser a SSAS.
4. Se la ricerca tramite AD riesce, viene recuperato il *UserPrincipalName* di tale utente di Active Directory.
5. Viene anche passato l'indirizzo di posta elettronica *UserPrincipalName* come *EffectiveUser* a SSAS, ad esempio <em>Alias@corp.on-prem.contoso</em>.

Per configurare il gateway per eseguire la ricerca con AD:

1. [Scaricare e installare il gateway più recente](/data-integration/gateway/service-gateway-install).

2. Nel gateway, è necessario modificare il **servizio Gateway dati locale** in modo che venga eseguito con un account di dominio (anziché un account del servizio locale, in caso contrario la ricerca tramite AD non funzionerà correttamente in fase di esecuzione). Passare all'[app del gateway dati locale](/data-integration/gateway/service-gateway-app) nel computer, quindi passare a **Impostazioni servizio > Modifica account di servizio**. Assicurarsi di avere la chiave di ripristino per il gateway, poiché sarà necessario ripristinarlo nello stesso computer, a meno che non si voglia creare invece un nuovo gateway. Sarà necessario riavviare il servizio gateway per rendere effettiva la modifica.

3. Passare alla cartella di installazione del gateway, *C:\Programmi\Gateway dati locale* come amministratore per assicurarsi di avere le autorizzazioni di scrittura e aprire il file *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*.

4. Modificare i due valori di configurazione seguenti in base alla *propria* configurazione di attributi di Active Directory per gli utenti di Active Directory. I valori di configurazione illustrati di seguito sono riportati esempi soli: è necessario specificarli in base alla configurazione di Active Directory. Queste configurazioni fanno distinzione tra maiuscole e minuscole, quindi assicurarsi che corrispondano ai valori in Active Directory.

    ![Impostazioni di Azure Active Directory](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names_03.png)

    Se non viene specificato alcun valore per la configurazione di ADServerPath, il gateway usa il Catalogo globale predefinito. Per ADServerPath è anche possibile specificare più valori. I valori devono essere separati da un punto e virgola, come nell'esempio seguente.

    ```xml
    <setting name="ADServerPath" serializeAs="String">
        <value> >GC://serverpath1; GC://serverpath2;GC://serverpath3</value>
    </setting>
    ```

    Il gateway analizza i valori di ADServerPath da sinistra a destra fino a quando non trova una corrispondenza. Se non viene trovata alcuna corrispondenza, viene usato il nome UPN originale. Assicurarsi che l'account che esegue il servizio gateway (PBIEgwService) disponga delle autorizzazioni per eseguire query in tutti i server AD specificati in ADServerPath.

    Il gateway supporta due tipi di ADServerPath, come negli esempi seguenti.

    **WinNT**

    ```xml
    <value="WinNT://usa.domain.corp.contoso.com,computer"/>
    ```

    **GC**

    ```xml
    <value> GC://USA.domain.com </value>
    ```

5. Riavviare il **gateway dati locale** per rendere effettiva la modifica della configurazione.

### <a name="working-with-mapping-rules"></a>Uso delle regole di mapping

Per creare una regola di mapping, immettere un valore per il **nome originale** e il **nuovo nome** e quindi selezionare **Aggiungi**.

| Campo | Descrizione |
| --- | --- |
| Sostituisci (nome originale) |Indirizzo di posta elettronica con cui è stato effettuato l'accesso a Power BI. |
| Con (nuovo nome) |Valore con cui si vuole sostituirlo. Il risultato della sostituzione è ciò che verrà passato alla proprietà *EffectiveUserName* proprietà per la connessione di Analysis Services. |

![Creare una regola di mapping](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names-effective-user-names.png)

Quando si seleziona un elemento nell'elenco, è possibile modificarne l'ordine tramite le **icone delle frecce** o **eliminare** la voce.

![Riordinamento di un elemento nell'elenco](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names-entry-selected.png)

### <a name="using-wildcard-"></a>Uso del carattere jolly (\*)

È possibile usare un carattere jolly per la stringa **Sostituisci (nome originale)** . Il carattere jolly può essere usato da solo, ma non con nessun'altra parte della stringa. In questo modo sarà possibile accettare tutti gli utenti e passare un singolo valore all'origine dati. Ciò è utile quando si vuole che tutti gli utenti nell'organizzazione usino lo stesso nome utente nell'ambiente locale.

### <a name="test-a-mapping-rule"></a>Testare una regola di mapping

È possibile convalidare come verrà sostituito un nome originale immettendo un valore per il **nome originale** e selezionando **Testa regola**.

![Test di una regola di mapping](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-test-mapping-rule.png)

> [!NOTE]
> Quando le regole vengono salvate, sono necessari alcuni minuti prima che il servizio inizi a usarle. All'interno del browser, la regola funzionerà immediatamente.

### <a name="limitations-for-mapping-rules"></a>Limitazioni per le regole di mapping

Il mapping è destinato all’origine dati specifica che si sta configurando. Non si tratta di un'impostazione globale. Se si hanno più origini dati di Analysis Services, è necessario eseguire il mapping degli utenti per ogni origine dati.

## <a name="authentication-to-a-live-analysis-services-data-source"></a>Autenticazione a un'origine dati Analysis Services live

Ogni volta che un utente interagisce con Analysis Services, il nome utente effettivo viene passato al gateway e quindi al server di Analysis Services locale. Il nome dell'entità utente (UPN), che in genere corrisponde all'indirizzo di posta elettronica con cui si accede al cloud, è l'informazione che viene passata ad Analysis Services come utente effettivo. L'UPN viene passato nella proprietà di connessione EffectiveUserName. Questo indirizzo di posta elettronica deve corrispondere a un UPN definito all'interno del dominio di Active Directory locale. L'UPN è una proprietà di un account di Active Directory. Questo account di Windows deve quindi essere presente in un ruolo di Analysis Services per avere accesso al server. Se non viene trovata alcuna corrispondenza in Active Directory, l'accesso non riesce.

Analysis Services può anche fornire filtri basati su questo account. I filtri possono usare la sicurezza basata sui ruoli o la sicurezza a livello di riga.

## <a name="role-based-security"></a>Sicurezza basata sui ruoli

I modelli assicurano la sicurezza basata sui ruoli utente. I ruoli vengono definiti per un particolare progetto di modello durante la creazione in SQL Server Data Tools – Business Intelligence (SSDT-BI) oppure dopo la distribuzione di un modello, usando SQL Server Management Studio (SSMS). I ruoli contengono membri in base al nome utente o gruppo di Windows. I ruoli definiscono le autorizzazioni di un utente per eseguire una query o azioni sul modello. La maggior parte degli utenti appartiene a un ruolo con autorizzazioni di lettura. Altri ruoli sono destinati agli amministratori con autorizzazioni di elaborazione degli elementi, gestione delle funzioni di database e di altri ruoli.

## <a name="row-level-security"></a>Sicurezza a livello di riga

La sicurezza a livello di riga è specifica per la sicurezza a livello di Analysis Services. I modelli possono fornire sicurezza dinamica a livello di riga. Invece di avere almeno un ruolo a cui appartengono gli utenti, la sicurezza dinamica non è richiesta per alcun modello tabulare. A un livello elevato, la sicurezza dinamica definisce l'accesso in lettura di un utente ai dati fino a una specifica riga di una determinata tabella. Analogamente ai ruoli, la sicurezza dinamica a livello di riga si basa su un nome utente Windows.

La possibilità di un utente di eseguire query e visualizzare i dati del modello è prima di tutto determinata dai ruoli di cui è membro il rispettivo account utente di Windows e, in secondo luogo, dalla sicurezza dinamica a livello di riga, se configurata.

L'implementazione della sicurezza basata sui ruoli e della sicurezza dinamica a livello di riga nei modelli esula dall'ambito di questo articolo. Per altre informazioni, vedere [Ruoli (SSAS tabulare)](https://msdn.microsoft.com/library/hh213165.aspx) e [Ruoli di sicurezza (Analysis Services - Dati multidimensionali)](https://msdn.microsoft.com/library/ms174840.aspx) in MSDN. Inoltre, per una conoscenza più approfondita della sicurezza del modello tabulare, scaricare e leggere il white paper [Protezione del modello semantico BI tabulare](https://msdn.microsoft.com/library/jj127437.aspx).

## <a name="what-about-azure-active-directory"></a>Ruolo di Azure Active Directory

I servizi cloud Microsoft usano [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) per eseguire l'autenticazione degli utenti. Azure Active Directory è il tenant che contiene i nomi utente e i gruppi di sicurezza. In genere, un utente accede con lo stesso indirizzo di posta elettronica dell'UPN dell'account.

Qual è il ruolo di Active Directory locale?

Affinché il server di Analysis Services possa determinare se un utente a esso connesso appartiene a un ruolo con autorizzazioni di lettura dei dati, deve convertire il nome utente effettivo passato da AAD al gateway e quindi al server di Analysis Services. Il server di Analysis Services passa il nome utente effettivo a un controller di dominio di Windows Active Directory. Il controller di dominio di Active Directory verifica quindi che il nome utente effettivo sia un UPN valido, su un account locale, e restituisce un nome utente di Windows al server Analysis Services.

EffectiveUserName non può essere usato in un server di Analysis Services non appartenente al dominio. Per evitare errori di accesso, il server di Analysis Services locale deve appartenere a un dominio.

### <a name="how-do-i-tell-what-my-upn-is"></a>Come si identifica l'UPN?

È possibile che l'utente non conosca l'UPN e non sia un amministratore di dominio. È possibile usare il comando seguente dalla workstation per identificare l'UPN dell'account.

    whoami /upn

Il risultato sarà simile a un indirizzo di posta elettronica, ma si tratta dell'UPN dell'account di dominio. Se si usa un'origine dati di Analysis Services per le connessioni dinamiche e il valore non corrisponde all'indirizzo di posta elettronica con cui si accede a Power BI, è consigliabile verificare come [si esegue il mapping dei nomi utente](#mapping-usernames-for-analysis-services-data-sources).

## <a name="synchronize-an-on-premises-active-directory-with-azure-active-directory"></a>Sincronizzare un server di Active Directory locale con Azure Active Directory

È opportuno che gli account di Active Directory locali corrispondano ad Azure Active Directory se si intende usare connessioni dinamiche ad Analysis Services, analogamente al modo in cui l'UPN deve corrispondere tra gli account.

I servizi cloud rilevano solo gli account in Azure Active Directory. Anche se è stato aggiunto un account in Active Directory locale, se non esiste in AAD, non può essere usato. Esistono diversi modi in cui è possibile associare gli account Active Directory locali con Azure Active Directory.

1. È possibile aggiungere manualmente account in Azure Active Directory.

   È possibile creare un account nel portale di Azure o nell'interfaccia di amministrazione di Microsoft 365. Il nome dell'account corrisponde all'UPN dell'account Active Directory locale.

2. È possibile usare lo strumento [Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-sync-whatis) per sincronizzare gli account locali al tenant di Azure Active Directory.

   Lo strumento Azure AD Connect offre opzioni per sincronizzare le directory e configurare l'autenticazione, incluse la sincronizzazione degli hash delle password, l'autenticazione pass-through e la federazione. Se non si è un amministratore tenant o un amministratore di dominio locale, è necessario contattare l'amministratore IT per ottenere questa configurazione.

L'uso di Azure AD Connect garantisce la corrispondenza tra l'UPN e AAD e Active Directory locale.

> [!NOTE]
> La sincronizzazione degli account con lo strumento Azure AD Connect creerà nuovi account nel tenant di AAD.

## <a name="using-the-data-source"></a>Uso dell'origine dati

Dopo aver creato l'origine dati, sarà possibile usarla con le connessioni dinamiche o con l'aggiornamento pianificato.

> [!NOTE]
> I nomi del server e del database devono corrispondere tra Power BI Desktop e l'origine dati all'interno del gateway dati locale.

Il collegamento tra il set di dati e l'origine dati all'interno del gateway si basa sul nome del server e sul nome del database. Questi nomi devono corrispondere. Ad esempio, se si indica un indirizzo IP per il nome del server, all'interno di Power BI Desktop è necessario usare l'indirizzo IP per l'origine dati all'interno della configurazione del gateway. Se si usa *SERVER\ISTANZA*, in Power BI Desktop è necessario usarlo anche all'interno dell'origine dati configurata per il gateway.

Questo vale sia per le connessioni dinamiche che per l'aggiornamento pianificato.

### <a name="using-the-data-source-with-live-connections"></a>Uso dell'origine dati con le connessioni dinamiche

È necessario assicurarsi che i nomi del server e del database corrispondano tra Power BI Desktop e l'origine dati configurata per il gateway. È inoltre necessario assicurarsi che l'utente sia elencato nella scheda **Utenti** dell'origine dati per pubblicare i set di dati delle connessioni dinamiche. Per le connessioni diamiche, la selezione avviene all'interno di Power BI Desktop alla prima importazione dei dati.

Dopo la pubblicazione, da Power BI Desktop o **Recupera dati**, i report dovrebbero iniziare a funzionare. Dopo la creazione dell'origine dati all'interno del gateway potrebbero essere necessari alcuni minuti prima di poter usare la connessione.

### <a name="using-the-data-source-with-scheduled-refresh"></a>Uso dell’origine dati con l'aggiornamento pianificato

Se si è presenti nella scheda **Utenti** dell'origine dati configurata all'interno del gateway e i nomi del server e del database corrispondono, il gateway viene visualizzato come un'opzione per l'uso con l'aggiornamento pianificato.

![Visualizzazione degli utenti](media/service-gateway-enterprise-manage-ssas/powerbi-gateway-enterprise-schedule-refresh.png)

### <a name="limitations-of-analysis-services-live-connections"></a>Limitazioni di connessioni dinamiche ad Analysis Services

È possibile usare una connessione dinamica su istanze tabulari o multidimensionali.

| **Versione del server** | **SKU necessario** |
| --- | --- |
| 2012 SP1 CU4 o versione successiva |Business Intelligence e SKU Enterprise |
| 2014 |Business Intelligence e SKU Enterprise |
| 2016 |SKU standard o versione successiva |

* La formattazione a livello di cella e le funzionalità di conversione non sono supportate.
* Azioni e set denominati non sono esposti in Power BI. È comunque possibile connettersi a cubi multidimensionali che contengono anche azioni o set denominati e creare oggetti visivi e report.

## <a name="next-steps"></a>Passaggi successivi

* [Risoluzione dei problemi del gateway dati locale](/data-integration/gateway/service-gateway-tshoot)
* [Risolvere i problemi relativi ai gateway - Power BI](service-gateway-onprem-tshoot.md)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

