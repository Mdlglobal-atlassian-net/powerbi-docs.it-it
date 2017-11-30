## <a name="firewall-or-proxy"></a>Firewall o proxy
Per informazioni su come specificare le informazioni del proxy per il gateway, vedere [Configurazione delle impostazioni del proxy per Power BI Gateway](../service-gateway-proxy.md).

È possibile verificare se il firewall o il proxy blocca le connessioni eseguendo [Test-NetConnection](https://technet.microsoft.com/library/dn372891.aspx) da un prompt dei comandi di PowerShell. Verrà così testata la connettività al bus di servizio di Azure. Viene testata solo la connettività di rete e non vengono eseguite operazioni relative al servizio del server cloud o al gateway. Questa operazione è utile per determinare se il computer riesce effettivamente a connettersi a Internet.

    Test-NetConnection -ComputerName watchdog.servicebus.windows.net -Port 9350

> [!NOTE]
> Test-NetConnection è disponibile solo in Windows Server 2012 R2 e versioni successive. È anche disponibile in Windows 8.1 e versioni successive. Nelle versioni precedenti del sistema operativo, è possibile usare Telnet per testare la connettività di porta.
> 
> 

I risultati dovrebbero essere simile ai seguenti. La differenza riguarderà TcpTestSucceeded. Se **TcpTestSucceeded** non è *true*, è possibile che le connessioni vengano bloccate da un firewall.

    ComputerName           : watchdog.servicebus.windows.net
    RemoteAddress          : 70.37.104.240
    RemotePort             : 5672
    InterfaceAlias         : vEthernet (Broadcom NetXtreme Gigabit Ethernet - Virtual Switch)
    SourceAddress          : 10.120.60.105
    PingSucceeded          : False
    PingReplyDetails (RTT) : 0 ms
    TcpTestSucceeded       : True

Per completezza, sostituire i valori di **ComputerName** e **Port** valori con quelli elencati per le [porte](../service-gateway-onprem.md#ports).

È anche possibile che il firewall blocchi le connessioni effettuate dal bus di servizio di Azure ai data center di Azure. In questo caso, è consigliabile aggiungere all'elenco elementi consentiti (sbloccare) gli indirizzi IP per l'area di questi data center. Per un elenco di indirizzi IP di Azure, vedere [qui](https://www.microsoft.com/download/details.aspx?id=41653).

