---
ms.openlocfilehash: e24218e2a465619fdfbfc279d3cc45370202dd6e
ms.sourcegitcommit: aef57ff94a5d452d6b54a90598bd6a0dd1299a46
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/07/2019
ms.locfileid: "66814807"
---
## <a name="sign-in-account"></a>Account di accesso

Gli utenti eseguono l'accesso con un account aziendale o dell'istituto di istruzione. Questo account è l'**account dell'organizzazione**. Se è stata effettuata l'iscrizione per un'offerta di Office 365 senza specificare l'indirizzo di posta elettronica dell'ufficio, questo può apparire come nancy@contoso.onmicrosoft.com. L'account viene archiviato in un tenant di Azure Active Directory (AAD). Nella maggior parte dei casi, l'UPN dell'account AAD corrisponderà all'indirizzo di posta elettronica.

## <a name="windows-service-account"></a>Account del Servizio di Windows

Il Gateway dati locale è configurato per l'uso di *NT SERVICE\PBIEgwService* per le credenziali di accesso al servizio di Windows. Per impostazione predefinita, ha il diritto di accesso come servizio, nel contesto del computer in cui si installa il gateway. Questo account non è lo stesso usato per connettersi alle origini dati locali. Non si tratta neanche dell'account aziendale o dell'istituto di istruzione con cui si accede ai servizi cloud.

> [!NOTE]
> Se è stata selezionata la modalità personale, configurare separatamente l'account del servizio di Windows.

Se si verificano problemi di autenticazione con il server proxy, provare a sostituire l'account del servizio Windows con un account utente di dominio o un account di servizio gestito. Per altre informazioni, vedere [Configurazione delle impostazioni del proxy](../service-gateway-proxy.md#changing-the-gateway-service-account-to-a-domain-user).

## <a name="ports"></a>Porte

Il gateway crea una connessione in uscita al Bus di servizio di Azure. Esso comunica su porte in uscita: TCP 443 (predefinita), 5671, 5672, dalla 9350 alla 9354.  Il gateway non richiede porte in entrata.

È consigliabile aggiungere all'elenco degli indirizzi consentiti nel firewall gli indirizzi IP per l'area dati. È possibile scaricare l'[elenco degli indirizzi IP per i data center di Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653), che viene aggiornato con frequenza settimanale. In alternativa è possibile ottenere l'elenco delle porte necessarie eseguendo il [test della porta di rete](../service-gateway-onprem-tshoot.md#network-ports-test) nell'applicazione del gateway dati locale. Il gateway comunicherà con un Bus di servizio di Azure usando l'indirizzo IP insieme al nome di dominio completo (FQDN). Se si impone al gateway di comunicare tramite HTTPS, verrà usato esclusivamente il nome di dominio completo e non avrà luogo alcuna comunicazione usando gli indirizzi IP.


> [!NOTE]
> Gli indirizzi IP elencati nell'elenco di IP del data center di Azure sono in notazione CIDR. Ad esempio, 10.0.0.0/24 non significa da 10.0.0.0 a 10.0.0.24. Altre informazioni sulla [notazione CIDR](http://whatismyipaddress.com/cidr).

Di seguito è riportato un elenco dei nomi di dominio completi usati dal gateway.

| Nomi di dominio | Porte in uscita | Descrizione |  |
|-----------------------------|----------------|--------------------------------------------------------------------------------------------------------------------|---|
| *.download.microsoft.com | 80 | Usato per scaricare il programma di installazione. Viene usato anche dall'app del gateway dati per verificare la versione e l'area del gateway. |  |
| *.powerbi.com | 443 | Usato per identificare il cluster di Power BI rilevante. |  |
| *.analysis.windows.net | 443 | Usato per identificare il cluster di Power BI rilevante. |  |
| *.login.windows.net | 443 | Usato per autenticare l'app del gateway dati con Azure Active Directory / OAuth2. |  |
| *.servicebus.windows.net | 5671-5672 | Usato per il protocollo AMQP (Advanced Message Queuing Protocol). |  |
| *.servicebus.windows.net | 443, 9350-9354 | Usato dai listener in Inoltro del bus di servizio su TCP. È richiesta la porta 443 per l'acquisizione del token del controllo di accesso. |  |
| *.frontend.clouddatahub.net | 443 | Deprecato, non è più necessario. Sarà rimosso dalla prossima documentazione. |  |
| *.core.windows.net | 443 | Usato per flussi di dati in Power BI per scrivere dati in Azure Data Lake. |  |
| login.microsoftonline.com | 443 | Usato per autenticare l'app del gateway dati con Azure Active Directory / OAuth2. |  |
| *.msftncsi.com | 443 | Usato per testare la connettività Internet e verificare se il gateway non è raggiungibile dal servizio Power BI. |  |
| *.microsoftonline-p.com | 443 | Usato per autenticare l'app del gateway dati con Azure Active Directory / OAuth2. |  |
| | |

> [!NOTE]
> Dopo aver installato e registrato il gateway, sono necessari solo gli IP e le porte richiesti dal bus di servizio di Azure (servicebus.windows.net precedente). È possibile ottenere l'elenco delle porte necessarie eseguendo il [test della porta di rete](../service-gateway-onprem-tshoot.md#network-ports-test) nell'applicazione del gateway dati locale.

## <a name="forcing-https-communication-with-azure-service-bus"></a>Forzare la comunicazione HTTPS con il bus di servizio di Azure

È possibile forzare la comunicazione del gateway con il bus di servizio di Azure tramite HTTPS anziché TCP diretto.

> [!NOTE]
> A partire dalla versione di giugno 2019, nelle nuove installazioni, ma non negli aggiornamenti, HTTPS è l'opzione predefinita al posto di TCP, sulla base dei suggerimenti ricevuti dal bus di servizio di Azure.

Per forzare la comunicazione tramite HTTPS, modificare il file *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config* cambiando il valore da `AutoDetect` a `Https`, come illustrato nel frammento di codice riportato subito dopo questo paragrafo. Per impostazione predefinita, il file si trova in *C:\Programmi\Gateway dati locale*.

```xml
<setting name="ServiceBusSystemConnectivityModeString" serializeAs="String">
    <value>Https</value>
</setting>
```

Il valore del parametro *ServiceBusSystemConnectivityModeString* rispetta la distinzione tra maiuscole e minuscole. I valori validi sono *AutoDetect* e *Https*.

In alternativa, è possibile imporre al gateway di adottare questo comportamento usando l'interfaccia utente del gateway. Nell'interfaccia utente del gateway selezionare **Rete**, quindi impostare **Modalità di connettività del bus di servizio di Azure** su **Attiva**.

![](./media/gateway-onprem-accounts-ports-more/gw-onprem_01.png)

Una volta modificato, quando si seleziona **Applica** (un pulsante che viene visualizzato solo quando si apporta una modifica), il *gateway del servizio Windows* viene riavviato automaticamente, in modo che le modifiche abbiano effetto.

Per riferimento futuro, è possibile riavviare il *servizio Windows del gateway* nella finestra di dialogo dell'interfaccia utente, selezionando **Impostazioni servizio** e quindi *Riavvia adesso*.

![](./media/gateway-onprem-accounts-ports-more/gw-onprem_02.png)

## <a name="support-for-tls-12"></a>Supporto per TLS 1.2

Per impostazione predefinita, il gateway dati locale usa il protocollo TLS (Transport Layer Security) 1.2 per comunicare con il servizio Power BI. Per assicurare che tutto il traffico del gateway usi TLS 1.2 potrebbe essere necessario aggiungere o modificare le chiavi del Registro di sistema seguenti nel computer che esegue il servizio gateway:

```
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319]"SchUseStrongCrypto"=dword:00000001
[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319]"SchUseStrongCrypto"=dword:00000001
```

> [!NOTE]
> L'aggiunta o la modifica di queste chiavi del Registro di sistema viene applicata a tutte le applicazioni .NET. Per informazioni sulle modifiche del Registro di sistema che influiscono su TLS per altre applicazioni, vedere [Impostazioni del Registro di sistema per TLS (Transport Layer Security)](https://docs.microsoft.com/windows-server/security/tls/tls-registry-settings).

## <a name="how-to-restart-the-gateway"></a>Come riavviare il gateway

Il gateway viene eseguito come servizio di Windows. È possibile avviarlo e arrestarlo come qualsiasi servizio di Windows. Ecco come farlo dal prompt dei comandi.

1. Sul computer in cui è in esecuzione il gateway, avviare un prompt dei comandi come amministratore.
2. Usare il comando seguente per arrestare il servizio.
   
   net stop PBIEgwService
3. Usare il comando seguente per avviare il servizio.
   
   net start PBIEgwService

