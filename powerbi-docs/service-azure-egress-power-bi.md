---
title: Dati in uscita di Power BI e Azure
description: Informazioni sui costi dei dati in uscita di Azure e Power BI in base alla posizione del tenant e Power BI Premium
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/18/2018
ms.author: davidi
LocalizationGroup: Data from databases
ms.openlocfilehash: 0150e4e62fffd116b144880ab4aecc81de0b2c49
ms.sourcegitcommit: 1a79e48ac820c28c5d0fd05399f49ed22fc74ed7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2018
ms.locfileid: "49435565"
---
# <a name="power-bi-and-azure-egress"></a>Dati in uscita di Power BI e Azure

Quando si usa Power BI con origini dati di Azure, è possibile evitare i costi dei dati in uscita di Azure verificando che il tenant di Power BI si trovi nella stessa area delle origini dati di Azure.

Quando il tenant di Power BI viene distribuito nella stessa area di Azure in cui si distribuiscono le origini dati, non vengono addebitati i costi per i dati in uscita per l'aggiornamento pianificato e le interazioni di DirectQuery. 

## <a name="determining-where-your-power-bi-tenant-is-located"></a>Determinazione della posizione del tenant di Power BI

Per scoprire dove si trova il tenant di Power BI, vedere l'articolo [Dove si trova il tenant di Power BI?](service-admin-where-is-my-tenant-located.md).

Per i clienti di Power BI Premium con il supporto di più aree geografiche, se il tenant di Power BI non si trova nella posizione ottimale per alcune delle origini dati basate su Azure, è possibile distribuire Power BI Premium con il supporto di più aree geografiche nell'area di Azure appropriata e beneficiare del posizionamento del tenant di Power BI e delle origini dati di Azure nella stessa area di Azure.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su Power BI Premium o sul supporto di più aree geografiche, esaminare le risorse seguenti:

* [Che cos'è Microsoft Power BI Premium?](service-premium.md)
* [How to purchase Power BI Premium](service-admin-premium-purchase.md) (Come acquistare Power BI Premium)
* [Supporto di più aree geografiche per Power BI Premium (anteprima)](service-admin-premium-multi-geo.md)
* [Dove si trova il tenant di Power BI?](service-admin-where-is-my-tenant-located.md)
* [Power BI Premium FAQ](service-premium-faq.md) (Domande frequenti su Power BI Premium)


