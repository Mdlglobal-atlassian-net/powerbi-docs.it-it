---
title: Configurazione delle impostazioni del proxy per il gateway dati locale
description: Informazioni sulla configurazione delle impostazioni del proxy per i gateway dati locali.
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: powerbi
ms.date: 11/21/2017
ms.author: davidi
ms.openlocfilehash: 77ae086d4b9c86f0d5ec4c0515ad96919160059d
ms.sourcegitcommit: 47ea78f58ad37a751171d01327c3381eca3a960e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2017
---
# <a name="configuring-proxy-settings-for-the-on-premises-data-gateway"></a>Configurazione delle impostazioni del proxy per il gateway dati locale
È possibile che l’ambiente di lavoro richieda il passaggio attraverso un proxy per accedere a Internet. Ciò potrebbe impedire la connessione al servizio del gateway dati locale.

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

Per altre informazioni sulla configurazione degli elementi del proxy per i file di configurazione .NET, vedere [Elemento defaultProxy (Impostazioni di rete)](https://msdn.microsoft.com/library/kd3cf2ex.aspx)

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
3. Avviare lo **strumento di configurazione del gateway dati locale**. È possibile selezionare il pulsante Start di Windows e cercare *Gateway dati locale*.
4. Accedere a Power BI.
5. Ripristinare il gateway usando la chiave di ripristino.
   
    In questo modo, il nuovo account di servizio potrà decrittografare le credenziali archiviate per le origini dati.

## <a name="next-steps"></a>Passaggi successivi
[Gateway dati locale (modalità personale)](service-gateway-personal-mode.md)
[Informazioni sul firewall](service-gateway-onprem-tshoot.md#firewall-or-proxy)  
Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

