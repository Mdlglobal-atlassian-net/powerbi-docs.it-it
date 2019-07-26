---
title: Gateway dati locale
description: Questa è una panoramica del gateway dati locale per Power BI. È possibile usare questo gateway per usare le origini dati DirectQuery. È anche possibile usare questo gateway per aggiornare i set di dati cloud con dati locali.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Gateways
ms.date: 07/15/2019
ms.openlocfilehash: 57c4292913a2056ab285716de1e1b83e2313f723
ms.sourcegitcommit: 9d13ef7a257b5006fca5f92acf5b611f5cd143a2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/18/2019
ms.locfileid: "68307090"
---
# <a name="what-is-an-on-premises-data-gateway"></a>Informazioni sul gateway dati locale

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Il gateway dati locale funziona come un ponte, poiché offre un trasferimento di dati rapido e sicuro tra i dati locali, ovvero i dati non sul cloud, e diversi servizi cloud Microsoft, tra cui Power BI, PowerApps, Microsoft Flow, Azure Analysis Services e App per la logica. L'uso di un gateway consente alle organizzazioni di mantenere i database e altre origini dati all'interno delle reti locali e allo stesso tempo di usare in sicurezza i dati locali nei servizi cloud.

## <a name="how-the-gateway-works"></a>Come funziona il gateway

![Panoramica del gateway](media/service-gateway-onprem/on-premises-data-gateway.png)

Per informazioni dettagliate sul funzionamento del gateway, vedere [Architettura del gateway dati locale](/data-integration/gateway/service-gateway-onprem-indepth).

## <a name="types-of-gateways"></a>Tipi di gateway

Esistono due tipi di gateway diversi, ognuno per uno scenario diverso:

* **Gateway dati locale** - Consente a più utenti di connettersi a più origini dati locali. È possibile usare un gateway dati locale con tutti i servizi supportati, con un'unica installazione del gateway. Questo gateway è ideale per scenari complessi, in cui più utenti accedono a più origini dati.

* **Gateway dati locale (modalità personale)** – Consente a un utente di connettersi alle origini e non può essere condiviso con altri utenti. Un gateway dati locale (modalità personale) può essere usato solo con Power BI. Questo gateway è ideale per gli scenari in cui si è l'unica persona che crea report e non è necessario condividere le origini dati con altri utenti.

## <a name="using-a-gateway"></a>Uso di un gateway

I passaggi principali per usare un gateway sono quattro:

1. [Scaricare e installare il gateway](/data-integration/gateway/service-gateway-install) in un computer locale.
2. [Configurare](/data-integration/gateway/service-gateway-app) il gateway in base al firewall e ad altri requisiti di rete.
3. [Aggiungere gli amministratori del gateway](/data-integration/gateway/service-gateway-manage) che possono anche gestire e amministrare altri requisiti di rete.
4. [Risolvere i problemi](service-gateway-onprem-tshoot.md) del gateway in caso di errori.

## <a name="next-steps"></a>Passaggi successivi

* [Installare il gateway dati locale](/data-integration/gateway/service-gateway-install)


Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)
