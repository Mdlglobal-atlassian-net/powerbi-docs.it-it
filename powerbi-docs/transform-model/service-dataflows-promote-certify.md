---
title: Alzare di livello o certificare i flussi di dati (anteprima)
description: Informazioni su come alzare di livello o certificare i flussi di dati.
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/17/2020
ms.author: painbar
LocalizationGroup: Share your work
ms.openlocfilehash: 7634711e8d26c4f265752427c5086e0901b210d5
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "81268881"
---
# <a name="promote-or-certify-dataflows-preview"></a>Alzare di livello o certificare i flussi di dati (anteprima)

In Power BI è possibile accrescere la visibilità dei flussi di dati più importanti e di qualità elevata in due modi: **promozione** e **certificazione**.

* **Promozione**: la promozione consente agli utenti di evidenziare i flussi di data ritenuti importanti e utili da usare per gli altri utenti. In questo modo, favorisce la diffusione collaborativa dei flussi di dati all'interno di un'organizzazione. Qualsiasi proprietario di un flusso di dati o qualsiasi membro con autorizzazioni di scrittura per l'area di lavoro in cui si trova un flusso di dati può semplicemente alzare di livello il flusso di dati quando ritiene che sia appropriato condividerlo.

* **Certificazione**: la certificazione indica che un flusso di dati è stato controllato da un revisore autorizzato ed è un'origine dati affidabile e autorevole pronta per essere usata in tutta l'organizzazione. Un gruppo di revisori selezionato definito dall'amministratore del tenant di Power BI determina quali flussi di dati certificare. Se un utente ritiene che un determinato flusso di dati debba essere certificato, ma non è autorizzato a farlo, deve contattare l'amministratore tenant.

  La certificazione di un flusso di dati è possibile solo se è stata [abilitata dall'amministratore del tenant di Power BI](../admin/service-admin-setup-certification.md).

La promozione o la certificazione di un flusso di dati è chiamata *approvazione*. Gli autori di report di Power BI spesso devono scegliere tra flussi di dati diversi e grazie all'approvazione possono individuare i flussi di dati affidabili, attendibili e autorevoli.

I flussi di dati approvati sono etichettati in modo chiaro in più posizioni di Power BI. In questo modo gli autori di report possono trovarli facilmente quando cercano dati affidabili e gli amministratori e gli autori di report possono tenere traccia di come vengono usati in tutta l'organizzazione.

L'immagine seguente illustra come i flussi di dati alzati di livello e certificati sono facilmente identificabili in Power Query.

![Flussi di dati approvati evidenziati in Power Query](media/service-dataflows-promote-certify/powerbi-dataflow-endorsement-power-query.png)

L'articolo illustra
* Promozione di un flusso di dati (proprietario del flusso di lavoro o qualsiasi utente con autorizzazioni per membri per l'area di lavoro in cui si trova il flusso di dati)
* Certificazione di un flusso di dati (certificatore di flussi di dati autorizzato, determinato dall'amministratore del tenant)

Per informazioni sulla configurazione della certificazione dei flussi di dati (amministratore del tenant), vedere [Configurare la certificazione di set di dati e flussi di dati](../admin/service-admin-setup-certification.md)


## <a name="promote-a-dataflow"></a>Alzare di livello un flusso di dati

Per alzare di livello un flusso di dati, è necessario avere le autorizzazioni di scrittura per l'area di lavoro in cui si trova il flusso di dati che si vuole alzare di livello.

1. Passare all'elenco dei flussi di dati nell'area di lavoro.
 
1. Selezionare **Altre opzioni** (...) nel flusso di dati che si vuole alzare di livello, quindi selezionare **Impostazioni**.

    ![Selezionare i puntini di sospensione nel flusso di dati](media/service-dataflows-promote-certify/power-bi-dataflow-settings.png)

1. Espandere la sezione Approvazione e selezionare **Alzato di livello**.

    ![Selezionare Innalzata e Applica](media/service-dataflows-promote-certify/power-bi-dataflow-promoted-endorsement.png)

1. Selezionare **Applica**.

## <a name="certify-a-dataflow"></a>Certificare un flusso di dati

Questa sezione è destinata agli utenti che sono stati autorizzati dall'amministratore del tenant a certificare i flussi di dati. La certificazione dei flussi di dati è una grande responsabilità. Questa sezione illustra il processo di certificazione.

1. Ottenere le autorizzazioni di scrittura per l'area di lavoro in cui si trova il flusso di dati che si vuole certificare. Le autorizzazioni possono essere concesse dal proprietario del flusso di dati o da chiunque abbia le autorizzazioni di amministratore per l'area di lavoro. 

1. Esaminare attentamente il flusso di dati e determinare se è idoneo per la certificazione.

1. Se si decide di certificare il flusso di dati, passare all'area di lavoro in cui si trova.
 
1. Trovare il flusso di dati che si sta cercando, fare clic su **Altre opzioni** (...), quindi selezionare **Impostazioni**.

    ![Selezionare i puntini di sospensione nel set di dati o nel flusso di dati](media/service-dataflows-promote-certify/power-bi-dataflow-settings.png)

1. Espandere la sezione Approvazione e fare clic su **Certificato**. 

    ![Fare clic sul collegamento Altre informazioni](media/service-dataflows-promote-certify/service-certify-datasets-dataflows.png)

2. Fare clic su **Applica**.

## <a name="next-steps"></a>Passaggi successivi

* [Configurare la certificazione di set di dati e flussi di dati](../admin/service-admin-setup-certification.md)
* Domande? [Contattare la community di Power BI](https://community.powerbi.com/)