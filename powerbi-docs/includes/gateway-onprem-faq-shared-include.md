## <a name="general"></a>Generale
**Domanda:** Qual è il nome effettivo del servizio di Windows?  
**Risposta:** Il gateway viene chiamato servizio Gateway dati locale in Services

**Domanda:** Quali sono i requisiti per il gateway?  
**Risposta:** Vedere la sezione relativa ai requisiti nel principale [articolo sul gateway](../service-gateway-onprem.md).

**Domanda:** Quali origini dati sono supportate con il gateway?  
**Risposta:** Vedere la tabella relativa alle origini dati nel principale [articolo sul gateway](../service-gateway-onprem.md).

**Domanda:** È necessario un gateway per origini dati cloud come il database SQL di Azure?  
È**Risposta:** No. Il servizio riuscirà a connettersi all'origine dati senza un gateway.

**Domanda:** Sono presenti connessioni in ingresso verso il gateway dal cloud?  
**Risposta:** No. Il gateway usa una connessione in uscita al bus di servizio di Azure.

**Domanda:** Che succede se si bloccano le connessioni in uscita? Che cosa occorre aprire?  
**Risposta:** vedere l'[elenco di porte](../service-gateway-onprem.md#ports) e host usati dal gateway.

**Domanda:** Il gateway deve essere installato nello stesso computer dell'origine dati?  
**Risposta:** No. Il gateway si connetterà all'origine dati usando le informazioni di connessione fornite. In questo senso il gateway è simile a un'applicazione client. È solo necessario che riesca a connettersi allo stesso nome server specificato.

**Domanda:** Qual è la latenza per l'esecuzione di query in un'origine dati dal gateway? Qual è l'architettura migliore?  
**Risposta:** È consigliabile che il gateway si trovi il più vicino possibile all'origine dati, in modo da evitare la latenza di rete. Se è possibile installare il gateway nell'origine dati effettiva, si ridurrà al minimo la latenza introdotta. Prendere in considerazione anche i data center. Se, ad esempio, il servizio usa il data center Stati Uniti occidentali e SQL Server è ospitato in una macchina virtuale di Azure, è consigliabile posizionare anche la macchina virtuale di Azure negli Stati Uniti occidentali. In questo modo si minimizza la latenza e si evitano addebiti in uscita sulla macchina virtuale di Azure.

**Domanda:** Sono previsti requisiti per la larghezza di banda di rete?  
**Risposta:** È consigliabile mantenere una velocità effettiva ottimale per la connessione di rete. Ogni ambiente è diverso e questo valore dipende anche dalla quantità di dati inviati. L'uso di ExpressRoute può essere utile per assicurare un livello specifico di velocità effettiva tra l'ambiente locale e i data center di Azure.

È possibile usare l'[app Azure Speed Test](http://azurespeedtest.azurewebsites.net/) di terze parti per semplificare la valutazione della velocità effettiva.

**Domanda:** Il servizio di Windows Gateway può essere eseguito con un account Azure Active Directory?  
**Risposta:** No. Il servizio di Windows deve avere un account di Windows valido. Per impostazione predefinita, verrà eseguito con SID del servizio *NT SERVICE\PBIEgwService*.

**Domanda:** In che modo vengono restituiti al cloud i risultati?  
**Risposta:** Questa operazione viene eseguita usando il bus di servizio di Azure. Per altre informazioni, vedere la sezione relativa al [funzionamento](../service-gateway-onprem.md#how-the-gateway-works).

**Domanda:** Dove vengono archiviate le credenziali?  
**Risposta:** Le credenziali immesse per un'origine dati vengono archiviate crittografate nel servizio cloud gateway. Le credenziali vengono decrittografate nel gateway locale.

**Domanda:** è possibile inserire il gateway in una rete perimetrale?  
**Risposta:** Il gateway richiede una connessione all'origine dati. Se l'origine dati non è accessibile nella rete perimetrale, il gateway potrebbe non riuscire a connettersi. Ad esempio, se SQL Server non si trova nella rete perimetrale non sarà possibile connettersi a SQL Server dalla rete perimetrale. Se il gateway si trova nella rete perimetrale, non riuscirà a raggiungere SQL Server.

**Domanda:** È possibile forzare il gateway per usare il traffico HTTPS con il bus di servizio di Azure anziché con TCP?  
**Risposta:** Sì. Tuttavia, le prestazioni saranno notevolmente ridotte. È possibile modificare il file *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*. Si può anche modificare il valore da `AutoDetect` a `Https`. Per impostazione predefinita, questo file si trova in *C:\Programmi\Gateway dati locale*.

**Domanda:** è necessario aggiungere l'elenco di IP del data center di Azure agli elementi consentiti? Dove è possibile ottenere l'elenco?  
**Risposta:** se si blocca il traffico IP in uscita, potrebbe essere necessario aggiungere l'elenco di IP del data center di Azure all'elenco elementi consentiti. Attualmente, il gateway comunicherà con un Bus di servizio di Azure usando l'indirizzo IP insieme al nome di dominio completo (FQDN). L'elenco di IP del data center di Azure viene aggiornato con frequenza settimanale. È possibile scaricare l'[elenco di IP del data center di Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653).

```
<setting name="ServiceBusSystemConnectivityModeString" serializeAs="String">
    <value>Https</value>
</setting>
```

## <a name="high-availabilitydisaster-recovery"></a>Disponibilità elevata/Ripristino di emergenza
**Domanda:** Sono disponibili piani per l'abilitazione di scenari a disponibilità elevata con il gateway?  
**Risposta:** Sì, il team di Power BI si sta impegnando in modo significativo in questa area. Controllare il [blog di Power BI](https://powerbi.microsoft.com/blog/) per verificare se sono disponibili altri aggiornamenti su questa funzionalità.

**Domanda:** Quali opzioni sono disponibili per il ripristino di emergenza?  
**Risposta:** È possibile usare la chiave di ripristino per ripristinare o spostare un gateway. Quando si installa il gateway, fornire la chiave di ripristino.

**Domanda:** Qual è il vantaggio della chiave di ripristino?  
**Risposta:** Consente di eseguire la migrazione o di ripristinare le impostazioni del gateway. Viene usata anche per il ripristino di emergenza.

## <a name="troubleshooting"></a>Risoluzione dei problemi
**Domanda:** Dove si trovano i log del gateway?  
**Risposta:** Vedere la sezione relativa agli strumenti dell'[articolo sulla risoluzione dei problemi](../service-gateway-onprem-tshoot.md#tools-for-troubleshooting).

**Domanda:** In che modo è possibile visualizzare le query inviate all'origine dati locale?  
**Risposta:** È possibile abilitare la traccia della query.  La traccia includerà le query inviate. Occorre ricordare di ripristinare il valore originale al termine della risoluzione dei problemi. L'abilitazione della traccia della query comporterà la creazione di log di dimensioni maggiori.

È anche possibile verificare gli strumenti disponibili nell'origine dati per tenere traccia delle query. Per SQL Server e Analysis Services è ad esempio possibile usare Extended Events o SQL Profiler.

