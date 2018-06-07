## <a name="update-to-the-latest-version"></a>Aggiornare alla versione più recente
Quando la versione del gateway non è aggiornata, possono verificarsi molti problemi.  In generale, è consigliabile assicurarsi di usare sempre la versione più recente.  Se il gateway non è stato aggiornato da un mese o più, potrebbe essere utile provare a installare la versione più recente del gateway e provare a riprodurre il problema.

## <a name="common-issues"></a>Problemi comuni
Ecco alcuni problemi comuni e risoluzioni risultati utili per diversi clienti in ambienti che limitano l'accesso a Internet.

<iframe width="560" height="315" src="https://www.youtube.com/embed/-t7RO6mHATI?showinfo=0" frameborder="0" allowfullscreen></iframe>

### <a name="authentication-to-proxy-server"></a>Autenticazione al server proxy
Il proxy può richiedere l'autenticazione da un account utente di dominio. Per impostazione predefinita, il gateway usa un SID del servizio per l'utente di accesso al servizio di Windows. La modifica dell'utente di accesso in utente di dominio può risultare utile a questo scopo. Per altre informazioni, vedere [Modifica dell'account del servizio gateway in un account utente di dominio](../service-gateway-proxy.md#changing-the-gateway-service-account-to-a-domain-user).

### <a name="your-proxy-only-allows-ports-80-and-443-traffic"></a>Il proxy consente il traffico solo sulle porte 80 e 443
Alcuni proxy limitano il traffico solo alle porte 80 e 443. Per impostazione predefinita, la comunicazione con il bus di servizio avviene su porte diverse dalla 443.

È possibile forzare il gateway per comunicare con il bus di servizio di Azure usando HTTPS anziché il TCP diretto. È necessario modificare il file *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*. Modificare il valore da `AutoDetect` a `Https`. Per impostazione predefinita, questo file si trova in *C:\Programmi\Gateway dati locale*.

```
<setting name="ServiceBusSystemConnectivityModeString" serializeAs="String">
    <value>Https</value>
</setting>
```

## <a name="installation"></a>Installazione
### <a name="error-failed-to-add-user-to-group---2147463168---pbiegwservice---performance-log-users---"></a>Errore: Non è stato possibile aggiungere l'utente al gruppo.  (-2147463168   PBIEgwService   Performance Log Users   )
Questo errore può verificarsi se si sta provando a installare il gateway in un controller di dominio. La distribuzione in un controller di dominio non è supportata. Il gateway deve essere distribuito in un computer che non sia un controller di dominio.

### <a name="installation-fails"></a>Installazione non riuscita
È possibile riscontrare errori di installazione se il software antivirus del computer in cui si esegue installazione non è aggiornato. È possibile aggiornare l'installazione del software antivirus oppure disabilitare l'antivirus solo fino al completamento dell'installazione del gateway, quindi riabilitare l'antivirus.

