---
title: Configurazione delle impostazioni del proxy per il gateway dati locale
description: Informazioni sulla configurazione delle impostazioni del proxy per il gateway dati locale.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-gateways
ms.topic: conceptual
ms.date: 11/21/2017
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: c0ad0c22d0787eaaa45cb36c74c01f6a1d1f85e3
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34722659"
---
# <a name="configuring-proxy-settings-for-the-on-premises-data-gateway"></a>Configurazione delle impostazioni del proxy per il gateway dati locale
È possibile che l’ambiente di lavoro richieda il passaggio attraverso un proxy per accedere a Internet. Ciò potrebbe impedire al gateway dati locale di connettersi al servizio.

## <a name="does-your-network-use-a-proxy"></a>La rete usa un proxy?
Il post seguente di superuser.com illustra come si può provare a determinare se si dispone di un proxy sulla rete.

[Come sapere qual è il server proxy in uso? (SuperUser.com)](https://superuser.com/questions/346372/how-do-i-know-what-proxy-server-im-using)

## <a name="configuration-file-location-and-default-configuration"></a>Posizione del file di configurazione e configurazione predefinita
Le informazioni sul proxy sono configurate all'interno di un file di configurazione .NET. La posizione e i nomi file sono diversi a seconda del gateway in uso.

### <a name="on-premises-data-gateway"></a>Gateway dati locale
I file di configurazione principali usati con il gateway dati locale sono due.

**Configurazione**

Il primo riguarda le schermate di configurazione che configurano effettivamente il gateway. Se si verificano problemi di configurazione del gateway, questo è il file da esaminare.

    C:\Program Files\On-premises data gateway\enterprisegatewayconfigurator.exe.config

**Servizio di Windows**

Il secondo riguarda il servizio di Windows che interagisce con il servizio Power BI e gestisce le richieste.

    C:\Program Files\On-premises data gateway\Microsoft.PowerBI.EnterpriseGateway.exe.config

## <a name="configuring-proxy-settings"></a>Configurazione delle impostazioni proxy
La configurazione proxy predefinita è la seguente.

    <system.net>
        <defaultProxy useDefaultCredentials="true" />
    </system.net>

La configurazione predefinita funziona con l'autenticazione di Windows. Se il proxy usa un altro tipo di autenticazione, è necessario modificare le impostazioni. In caso di dubbi, contattare l'amministratore di rete.

Oltre a usare le credenziali predefinite, è possibile aggiungere un elemento <proxy> per definire in maggior dettaglio le impostazioni del server proxy. Ad esempio è possibile impostare il parametro bypassonlocal su false per specificare che il gateway dati locale deve usare sempre il proxy anche per le risorse locali. Questa funzionalità può risultare utile in situazioni di risoluzione dei problemi, per tenere traccia di tutte le richieste HTTPS provenienti da un gateway dati locale nei file di log del proxy. La configurazione di esempio seguente specifica che tutte le richieste devono transitare attraverso un proxy specifico con l'indirizzo IP 192.168.1.10.

    <system.net>
        <defaultProxy useDefaultCredentials="true">
            <proxy  
                autoDetect="false"  
                proxyaddress="http://192.168.1.10:3128"  
                bypassonlocal="false"  
                usesystemdefault="true"
            />  
        </defaultProxy>
    </system.net>

Per altre informazioni sulla configurazione degli elementi del proxy per i file di configurazione .NET, vedere [Elemento defaultProxy (Impostazioni di rete)](https://msdn.microsoft.com/library/kd3cf2ex.aspx).

## <a name="changing-the-gateway-service-account-to-a-domain-user"></a>Modifica dell'account del servizio gateway in un account utente di dominio
Quando si configurano le impostazioni proxy per l'utilizzo delle credenziali predefinite come descritto in precedenza, possono verificarsi problemi di autenticazione con il proxy. Questi problemi dipendono dal fatto che l'account del servizio predefinito corrisponde al SID del servizio e a un utente di dominio autenticato. È possibile modificare l'account del servizio del gateway per consentire l'autenticazione corretta con il proxy.

> [!NOTE]
> È consigliabile usare un account del servizio gestito per evitare di reimpostare le password. Informazioni su come creare un [account del servizio gestito](https://technet.microsoft.com/library/dd548356.aspx) all'interno di Active Directory.
> 
> 

### <a name="change-the-on-premises-data-gateway-service-account"></a>Modificare l'account del servizio Gateway dati locale
1. Modificare l'account del servizio Windows per il **servizio Gateway dati locale**.
   
    L'account predefinito per questo servizio è *NT SERVICE\PBIEgwService*. È opportuno modificare questo account con un account utente di dominio all'interno del dominio di Active Directory. In alternativa, è possibile usare un account del servizio gestito per evitare di modificare la password.
   
    Modificare l'account nella scheda di **accesso** all'interno delle proprietà del servizio Windows.
2. Riavviare il **servizio Gateway dati locale**.
   
    Da un prompt dei comandi per amministratori, eseguire questi comandi.
   
        net stop PBIEgwService
   
        net start PBIEgwService
3. Avviare lo **strumento di configurazione del gateway dati locale**. È possibile selezionare il pulsante Start di Windows e cercare *gateway dati locale*.
4. Accedere a Power BI.
5. Ripristinare il gateway usando la chiave di ripristino.
   
    In questo modo, il nuovo account di servizio potrà decrittografare le credenziali archiviate per le origini dati.

## <a name="next-steps"></a>Passaggi successivi
[Gateway dati locale (modalità personale)](service-gateway-personal-mode.md)
[Informazioni sul firewall](service-gateway-onprem-tshoot.md#firewall-or-proxy)  
Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

