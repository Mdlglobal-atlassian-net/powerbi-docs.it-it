---
title: Come acquistare Power BI Premium
description: Informazioni su come acquistare Power BI Premium e abilitare l'accesso ai contenuti per tutta l'organizzazione.
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 03/12/2019
LocalizationGroup: Premium
ms.openlocfilehash: 312e010bfa3ea635ef014a0b2dd913fa9e3911b6
ms.sourcegitcommit: ac63b08a4085de35e1968fa90f2f49ea001b50c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2019
ms.locfileid: "57964848"
---
# <a name="how-to-purchase-power-bi-premium"></a>Come acquistare Power BI Premium

> [!NOTE]
> Questo articolo è in corso di aggiornamento per descrivere le nuove funzionalità, offrire più dettagli e migliorare la leggibilità. 

Questo articolo descrive le modalità di acquisto della capacità Power BI Premium (P1-P3) per l'organizzazione. È possibile acquistare la capacità Premium di Power BI nell'interfaccia di amministrazione di Office 365 e gestire le capacità nell'interfaccia di amministrazione di Power BI. Per informazioni sui prezzi e la pianificazione correnti, vedere la [pagina dei prezzi di Power BI](https://powerbi.microsoft.com/pricing/) e il [calcolatore Power BI Premium](https://powerbi.microsoft.com/calculator/).

Per gli autori del contenuto è ancora necessaria una licenza di Power BI Pro, anche se l'organizzazione usa Power BI Premium. Acquistare almeno una licenza di Power BI Pro per l'organizzazione.

Quando una sottoscrizione Premium scade, l'accesso completo alla capacità è garantito per altri 30 giorni. Allo scadere di questo periodo, il contenuto torna ad avere una capacità condivisa. I modelli di dimensioni superiori a 1 GB non sono supportati nella capacità condivisa.

## <a name="create-a-new-tenant-with-power-bi-premium-p1"></a>Creare un nuovo tenant con Power BI Premium P1

Se non si ha un tenant esistente e si vuole crearne uno, è possibile acquistare contemporaneamente Power BI Premium. Il collegamento seguente guida attraverso il processo di creazione di un nuovo tenant e consente di acquistare Power BI Premium: [Power BI Premium P1](https://signup.microsoft.com/Signup?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1). Quando si crea il tenant, si viene automaticamente assegnati al ruolo di amministratore globale di Office 365 per il tenant.

## <a name="purchase-a-power-bi-premium-capacity-for-an-existing-organization"></a>Acquistare capacità di Power BI Premium per l'organizzazione

Se si ha un'organizzazione esistente (tenant), è necessario avere il ruolo di amministratore globale di Office 365 o di amministratore fatturazione per l'acquisto di sottoscrizioni e licenze. Per altre informazioni, vedere [Informazioni sui ruoli di amministratore di Office 365](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d).

Per acquistare la capacità Premium, seguire questa procedura.

1. Dal servizio Power BI scegliere Office 365 dalla selezione app e quindi **Amministratore**.

    ![Selezione app di Office 365](media/service-admin-premium-purchase/o365-app-picker.png)

    In alternativa, è possibile passare al centro di amministrazione di Office 365, passando a https://portal.office.com e selezionando **Amministratore**.

1. Selezionare **Fatturazione** > **Acquisto di servizi**.

1. In **Other plans** (Altri piani) cercare le offerte di Power BI Premium. Verranno elencate le offerte da P1 a P3, EM3 e P1 (mensile).

1. Passare il mouse sui puntini di sospensione (**. . .**) e selezionare **Buy now** (Acquista).

    ![Acquista ora](media/service-admin-premium-purchase/premium-purchase.png)

1. Per completare l'acquisto, seguire la procedura.

Dopo aver completato l'acquisto, la pagina **Acquisto di servizi** indica che l'elemento è stato acquistato ed è attivo.

![Acquisto di Power BI Premium](media/service-admin-premium-purchase/premium-purchased.png)

## <a name="purchase-additional-capacities"></a>Acquistare capacità aggiuntive

Ora che si ha una capacità, è possibile aggiungerne altre in base alle esigenze. È possibile usare qualsiasi combinazione di SKU per la capacità Premium, da P1 a P3, all'interno dell'organizzazione. I vari SKU offrono diverse capacità delle risorse.

1. Nell'interfaccia di amministrazione di Office 365 selezionare **Fatturazione** > **Acquisto di servizi**.

1. Trovare l'elemento di Power BI Premium che si desidera acquistare in **Other plans** (Altri piani).

1. Passare il mouse sui **puntini di sospensione (...)**  e quindi selezionare **Change license quantity** (Modifica la quantità di licenze).

    ![Cambia la quantità di licenze](media/service-admin-premium-purchase/premium-purchase-more.png)

1. Modificare il numero di istanze che si desidera avere per questo elemento. Selezionare quindi **Invia** al termine.

   > [!IMPORTANT]
   > Se si seleziona **Invia** viene eseguito l'addebito sulla carta di credito inserita.

La pagina **Acquisto di servizi** indica il numero di istanze disponibili. All'interno del portale di amministrazione di Power BI, in **Impostazioni di capacità**, le memorie centrali virtuali disponibili riflettono la nuova capacità acquistata.

![Memorie centrali virtuali disponibili per la capacità di Power BI Premium](media/service-admin-premium-purchase/premium-capacities.png)

## <a name="cancel-your-subscription"></a>Annullare la sottoscrizione

È possibile annullare la sottoscrizione dall'interfaccia di amministrazione di Office 365. Per annullare la sottoscrizione Premium, eseguire le operazioni seguenti.

1. Passare all'interfaccia di amministrazione di Office 365.

1. Selezionare **Fatturazione** > **Sottoscrizioni**.

1. Selezionare la sottoscrizione di Power BI Premium dall'elenco.

1. Selezionare **Altre azioni** > **Annulla sottoscrizione**.

1. La pagina **Annulla sottoscrizione** indicherà se si è responsabili o no di una [penale per risoluzione anticipata](https://support.office.com/article/early-termination-fees-6487d4de-401a-466f-8bc3-c0beb5cc40d3). Questa pagina indica anche quando verranno eliminati i dati per la sottoscrizione.

1. Leggere attentamente le informazioni e, se si vuole continuare, selezionare **Annulla sottoscrizione**.

### <a name="when-canceling-or-your-license-expires"></a>Annullamento o scadenza della licenza

Quando si annulla la sottoscrizione Premium o la licenza per la capacità scade, è possibile continuare ad accedere alle capacità Premium per un periodo di 30 giorni dalla data dell'annullamento o della scadenza della licenza. Passati i 30 giorni non sarà più possibile accedere alle capacità Premium o alle relative aree di lavoro.

## <a name="next-steps"></a>Passaggi successivi

[Prezzi di Power BI](https://powerbi.microsoft.com/pricing/)   
[Calcolatore Power BI Premium](https://powerbi.microsoft.com/calculator/)   
[Domande frequenti su Power BI Premium](service-premium-faq.md)   
[Planning a Power BI Enterprise Deployment whitepaper](https://aka.ms/pbienterprisedeploy) (White paper sulla pianificazione della distribuzione aziendale di Power BI)

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)