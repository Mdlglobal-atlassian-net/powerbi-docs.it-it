---
title: Panoramica dell'accesso Single Sign-On (SSO) per i gateway in Power BI
description: Configurare il gateway per abilitare Single Sign-On (SSO) da Power BI alle origini dati locali.
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 10/10/2019
LocalizationGroup: Gateways
ms.openlocfilehash: b5ef7e99edbf862891811047ea5f1f961aaea348
ms.sourcegitcommit: b22a9a43f61ed7fc0ced1924eec71b2534ac63f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2020
ms.locfileid: "77527592"
---
# <a name="overview-of-single-sign-on-sso-for-gateways-in-power-bi"></a>Panoramica dell'accesso Single Sign-On (SSO) per i gateway in Power BI

Per usufruire di un'esperienza di connettività Single Sign-On ottimale che abilita l'aggiornamento di report e dashboard di Power BI in tempo reale dai dati locali, è possibile configurare il gateway dati locale. È possibile configurare il gateway scegliendo tra la delega vincolata [Kerberos](service-gateway-sso-kerberos.md) e Security Assertion Markup Language ([SAML](service-gateway-sso-saml.md)). Il gateway dati locale supporta l'accesso SSO tramite [DirectQuery](desktop-directquery-about.md) o per Aggiornamento, che consente la connessione alle origini dati locali. 

Power BI supporta le origini dati seguenti:

* SQL Server (Kerberos)
* SAP HANA (Kerberos e SAML)
* Server applicazioni SAP BW (Kerberos)
* Server messaggi SAP BW (Kerberos ) - Anteprima pubblica
* Oracle (Kerberos)- Anteprima pubblica
* Teradata (Kerberos)
* Spark (Kerberos)
* Impala (Kerberos)

L'accesso Single Sign-On non è attualmente supportato per le [estensioni M](https://github.com/microsoft/DataConnectors/blob/master/docs/m-extensions.md).

Quando un utente interagisce con un report DirectQuery nel servizio Power BI, ogni operazione di filtro incrociato, sezione, ordinamento e modifica di report può comportare l'esecuzione di query in tempo reale sull'origine dati locale sottostante. Quando si configura l'accesso Single Sign-On per l'origine dati, le query vengono eseguite in base all'identità dell'utente che interagisce con Power BI, ovvero tramite l'esperienza Web o le app Power BI per dispositivi mobili. Ogni utente, quindi, visualizza con precisione i dati a cui è autorizzato ad accedere nell'origine dati sottostante. 

È inoltre possibile configurare un report configurato per l'aggiornamento nel servizio Power BI per l'uso di SSO. Quando si configura SSO per questa origine dati, le query vengono eseguite con l'identità del proprietario del set di dati all'interno di Power BI. Pertanto, l'aggiornamento viene eseguito in base alle autorizzazioni del proprietario del set di dati per l'origine dati sottostante. L'aggiornamento tramite SSO è attualmente abilitato solo per le origini dati che usano la delega vincolata [Kerberos](service-gateway-sso-kerberos.md) 

## <a name="query-steps-when-running-sso"></a>Passi di query durante l'esecuzione di SSO

I passaggi per l'esecuzione di una query con accesso Single Sign-On sono tre, come illustrato nel diagramma seguente.

![Passi di query SSO](media/service-gateway-sso-overview/sso-query-steps.png)

Ecco alcuni dettagli aggiuntivi su ogni passaggio:

1. Per ogni query, il servizio Power BI include il *nome dell'entità utente (UPN, User Principal Name)* , ovvero il nome utente completo dell'utente connesso al servizio Power BI quando il servizio invia una richiesta di query al gateway configurato.

2. Il gateway deve eseguire il mapping del nome dell'entità utente di Azure Active Directory a un'identità di Active Directory locale:

   a. Se Azure AD DirSync (chiamato anche *Azure AD Connect*) è configurato, il mapping funziona automaticamente nel gateway.

   b.  In caso contrario, il gateway può cercare ed eseguire il mapping del nome dell'entità utente (UPN) di Azure AD a un utente di AD locale eseguendo una ricerca nel dominio di Active Directory locale.

3. Il processo del servizio gateway rappresenta l'utente locale di cui è stato eseguito il mapping, apre la connessione con il database sottostante e quindi invia la query. Non è necessario installare il gateway nello stesso computer del database.

## <a name="next-steps"></a>Passaggi successivi

Dopo aver appreso le nozioni di base per l'abilitazione dell'accesso Single Sign-On tramite il gateway, leggere informazioni più dettagliate su Kerberos e SAML:

* [Single Sign-On (SSO) - Kerberos](service-gateway-sso-kerberos.md)
* [Single Sign-On (SSO) - SAML](service-gateway-sso-saml.md)
