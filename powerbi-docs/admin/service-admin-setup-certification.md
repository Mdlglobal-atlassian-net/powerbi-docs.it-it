---
title: Configurare la certificazione di set di dati e flussi di dati (anteprima)
description: Informazioni su come configurare il processo di certificazione di set di dati e flussi di dati nell'organizzazione.
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/22/2020
ms.author: painbar
LocalizationGroup: Share your work
ms.openlocfilehash: 1fc33b48613335f4fba97921e3d528175eb2a47f
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "81267846"
---
# <a name="set-up-dataset-and-dataflow-certification-preview"></a>Configurare la certificazione di set di dati e flussi di dati (anteprima)

L'organizzazione può certificare set di dati e flussi di dati con origini autorevoli per informazioni di importanza critica.

L'amministratore del tenant di Power BI è responsabile della configurazione del processo di certificazione per l'organizzazione. Ciò significa:
* Abilitare la certificazione nel tenant.
* Definire un elenco di gruppi e utenti autorizzati a certificare i set di dati e i flussi di dati.
* Per i set di dati, specificare l'URL dei criteri di certificazione dei set di dati dell'organizzazione, se esistenti.

La certificazione dei set di dati e dei flussi di dati fa parte dell'*approvazione* dei set di dati e dei flussi di dati. Per altre informazioni, vedere [Approvazione dei set di dati](../service-datasets-promote.md) e [Approvazione dei flussi di dati](../transform-model/service-dataflows-promote-certify.md).


## <a name="set-up-certification"></a>Configurare la certificazione

1. Nel portale di amministrazione passare a Impostazioni tenant.
1. Nella sezione Impostazioni di esportazione e condivisione espandere la sezione Certificazione.

   ![Configurare la certificazione di set di dati e flussi di dati](media/service-admin-setup-certification/service-admin-certification-setup-dialog.png)

1. Impostare l'interruttore su **Abilitato**.
1. Per la certificazione dei set di dati, se l'organizzazione ha pubblicato un criterio di certificazione, è possibile specificarne qui l'URL, che diventerà il collegamento **Altre informazioni** nella sezione Certificazione della [finestra di dialogo delle impostazioni di approvazione dei flussi di dati](../service-datasets-promote.md#request-dataset-certification) 
1. Specificare gli utenti o i gruppi autorizzati a certificare i set di dati e i flussi di dati. Questi certificatori autorizzati potranno usare il pulsante Certificazione nella sezione Certificazione della finestra di dialogo delle impostazioni di approvazione dei [set di dati](../service-datasets-promote.md#request-dataset-certification) o dei [flussi di dati](../transform-model/service-dataflows-promote-certify.md#certify-a-dataflow).
1. Fare clic su **Applica**.

## <a name="next-steps"></a>Passaggi successivi
* [Alzare di livello i set di dati](../service-datasets-promote.md)
* [Certificare i set di dati](../service-datasets-certify.md)
* [Alzare di livello i flussi di dati](../transform-model/service-dataflows-promote-certify.md#promote-a-dataflow)
* [Certificare i flussi di dati](../transform-model/service-dataflows-promote-certify.md#certify-a-dataflow)
* Domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
