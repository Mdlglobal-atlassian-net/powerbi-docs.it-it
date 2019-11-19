---
title: Gateway dati locale
description: Questo articolo descrive il gateway dati locale per Power BI. È possibile usare questo gateway per usare le origini dati DirectQuery. È anche possibile usare questo gateway per aggiornare i set di dati cloud con dati locali.
author: mgblythe
ms.author: mblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Gateways
ms.date: 07/15/2019
ms.openlocfilehash: b01a3ef5832541822aa9311df14289285f601b2b
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73872451"
---
# <a name="what-is-an-on-premises-data-gateway"></a>Informazioni sul gateway dati locale

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Il gateway dati locale funge da ponte per consentire il trasferimento rapido e protetto tra i dati locali (cioè non presenti nel cloud) e i numerosi servizi cloud di Microsoft. Questi servizi cloud includono Power BI, PowerApps, Microsoft Flow, Azure Analysis Services e App per la logica di Azure. L'uso di un gateway consente alle organizzazioni di mantenere i database e altre origini dati all'interno delle reti locali e allo stesso tempo di usare in sicurezza i dati locali nei servizi cloud.

## <a name="how-the-gateway-works"></a>Come funziona il gateway

![Panoramica del gateway](media/service-gateway-onprem/on-premises-data-gateway.png)

Per altre informazioni sul funzionamento del gateway, vedere [On-premises data gateway architecture](/data-integration/gateway/service-gateway-onprem-indepth) (Architettura del gateway dati locale).

## <a name="types-of-gateways"></a>Tipi di gateway

Esistono due tipi di gateway diversi, ognuno per uno scenario diverso:

* **Gateway dati locale** - Consente a più utenti di connettersi a più origini dati locali. È possibile usare un gateway dati locale con tutti i servizi supportati, con un'unica installazione del gateway. Questo gateway è ideale per scenari complessi, in cui più utenti accedono a più origini dati.

* **Gateway dati locale (modalità personale)** - Consente a un utente di connettersi alle origini e non può essere condiviso con altri utenti. Un gateway dati locale (modalità personale) può essere usato solo con Power BI. Questo gateway è ideale per gli scenari in cui si è l'unica persona che crea report e non è necessario condividere le origini dati con altri utenti.

## <a name="use-a-gateway"></a>Usare un gateway

I passaggi principali per usare un gateway sono quattro.

1. [Scaricare e installare il gateway](/data-integration/gateway/service-gateway-install) in un computer locale.
1. [Configurare](/data-integration/gateway/service-gateway-app) il gateway in base al firewall e ad altri requisiti di rete.
1. [Aggiungere gli amministratori del gateway](/data-integration/gateway/service-gateway-manage) che possono anche gestire e amministrare altri requisiti di rete.
1. [Usare il gateway](service-gateway-sql-tutorial.md) per aggiornare un'origine dati locale.
1. [Risolvere i problemi](service-gateway-onprem-tshoot.md) del gateway in caso di errori.

## <a name="next-steps"></a>Passaggi successivi

* [Installare il gateway dati locale](/data-integration/gateway/service-gateway-install)

Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)
