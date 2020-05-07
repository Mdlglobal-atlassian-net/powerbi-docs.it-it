---
title: Analisi approfondita del gateway dati locale
description: Questo articolo offre un'analisi approfondita del gateway dati locale. Illustra come funziona il servizio con Azure Active Directory e Active Directory locale quando si lavora con Analysis Services
author: arthiriyer
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: arthii
LocalizationGroup: Gateways
ms.openlocfilehash: c277c21ffd3546307f9c38dfc06364324702986f
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "74699384"
---
# <a name="on-premises-data-gateway-in-depth"></a>Analisi approfondita del gateway dati locale

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Le informazioni riportate in questo articolo sono state spostate in diversi articoli della documentazione generale e di Power BI. Per trovare il contenuto pertinente, seguire i collegamenti sotto ogni intestazione.

## <a name="how-the-gateway-works"></a>Funzionamento del gateway

Vedere [Architettura gateway dati locale](/data-integration/gateway/service-gateway-onprem-indepth).

## <a name="list-of-available-data-source-types"></a>Elenco di tipi di origini dati disponibili

Vedere [Gestire le origini dati](service-gateway-data-sources.md).

## <a name="authentication-to-on-premises-data-sources"></a>Autenticazione a origini dati locali

Vedere [Autenticazione a origini dati locali](/data-integration/gateway/service-gateway-onprem-indepth#authentication-to-on-premises-data-sources).

## <a name="authentication-to-a-live-analysis-services-data-source"></a>Autenticazione a un'origine dati Analysis Services live

Vedere [Autenticazione a un'origine dati Analysis Services live](service-gateway-enterprise-manage-ssas.md#authentication-to-a-live-analysis-services-data-source).

## <a name="role-based-security"></a>Sicurezza basata sui ruoli

Vedere [Sicurezza basata sui ruoli](service-gateway-enterprise-manage-ssas.md#role-based-security).

## <a name="row-level-security"></a>Sicurezza a livello di riga

Vedere [Sicurezza a livello di riga](service-gateway-enterprise-manage-ssas.md#row-level-security).

## <a name="what-about-azure-active-directory"></a>Ruolo di Azure Active Directory

Vedere [Azure Active Directory](/data-integration/gateway/service-gateway-onprem-indepth#azure-active-directory).

## <a name="how-do-i-tell-what-my-upn-is"></a>Come si identifica l'UPN?

Vedere [Come si identifica l'UPN?](/data-integration/gateway/service-gateway-onprem-indepth#how-do-i-tell-what-my-upn-is).

## <a name="map-user-names-for-analysis-services-data-sources"></a>Eseguire il mapping dei nomi utente per le origini dati di Analysis Services

Vedere [Eseguire il mapping dei nomi utente per le origini dati di Analysis Services](service-gateway-enterprise-manage-ssas.md#map-user-names-for-analysis-services-data-sources).

## <a name="synchronize-an-on-premises-active-directory-with-azure-active-directory"></a>Sincronizzare un server di Active Directory locale con Azure Active Directory

Vedere [Sincronizzare un server di Active Directory locale con Azure Active Directory](/data-integration/gateway/service-gateway-onprem-indepth#synchronize-an-on-premises-active-directory-with-azure-active-directory).

## <a name="what-to-do-next"></a>Azioni successive

Vedere gli articoli sulle origini dati:

[Gestire le origini dati](service-gateway-data-sources.md)
[Gestire l'origine dati - Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[Gestire l'origine dati - SAP HANA](service-gateway-enterprise-manage-sap.md)  
[Gestire l'origine dati - SQL Server](service-gateway-enterprise-manage-sql.md)  
[Gestire l'origine dati - Oracle](service-gateway-onprem-manage-oracle.md)  
[Gestire l'origine dati - Importazione/aggiornamento pianificato](service-gateway-enterprise-manage-scheduled-refresh.md)  

## <a name="where-things-can-go-wrong"></a>Possibili esiti negativi

Vedere [Risolvere i problemi del gateway dati locale](/data-integration/gateway/service-gateway-tshoot) e [Risolvere i problemi relativi ai gateway - Power BI](service-gateway-onprem-tshoot.md).

## <a name="sign-in-account"></a>Account di accesso

Vedere [Account di accesso](/data-integration/gateway/service-gateway-onprem-indepth#sign-in-account).

## <a name="windows-service-account"></a>Account del servizio Windows

Vedere [Modificare l'account del servizio Gateway dati locale](/data-integration/gateway/service-gateway-service-account).

## <a name="ports"></a>Porte

Vedere [Porte](/data-integration/gateway/service-gateway-communication#ports).

## <a name="forcing-https-communication-with-azure-service-bus"></a>Forzare la comunicazione HTTPS con il bus di servizio di Azure

Vedere [Forzare la comunicazione HTTPS con il bus di servizio di Azure](/data-integration/gateway/service-gateway-communication#force-https-communication-with-azure-service-bus).

## <a name="support-for-tls-12"></a>Supporto per TLS 1.2

Vedere [TLS 1.2 per il traffico del gateway](/data-integration/gateway/service-gateway-communication#tls-12-for-gateway-traffic).

## <a name="how-to-restart-the-gateway"></a>Come riavviare il gateway

Vedere [Riavviare un gateway](/data-integration/gateway/service-gateway-restart).

## <a name="next-steps"></a>Passaggi successivi

[Informazioni sul gateway dati locale](service-gateway-onprem.md)

Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)