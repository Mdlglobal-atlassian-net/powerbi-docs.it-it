---
title: Come acquistare Power BI Premium
description: Informazioni su come acquistare Power BI Premium e abilitare l'accesso ai contenuti per tutta l'organizzazione.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 10/20/2018
ms.author: mblythe
LocalizationGroup: Premium
ms.openlocfilehash: e2d2f0bd73d17d8d987dab9f3b3396bf7845d16e
ms.sourcegitcommit: a764e4b9d06b50d9b6173d0fbb7555e3babe6351
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2018
ms.locfileid: "49641414"
---
# <a name="how-to-purchase-power-bi-premium"></a>Come acquistare Power BI Premium

Questo articolo descrive le modalità di acquisto della capacità Premium di Power BI per l'organizzazione. È possibile acquistare la capacità Premium di Power BI nell'interfaccia di amministrazione di Office 365 e [gestire le capacità](service-admin-premium-manage.md) nell'interfaccia di amministrazione di Power BI.

<iframe width="640" height="360" src="https://www.youtube.com/embed/NkvYs5Qp4iA?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

Per altre informazioni su Power BI Premium, vedere [Che cos'è Power BI Premium?](service-premium.md) Per informazioni sui prezzi e la pianificazione correnti, vedere la [pagina dei prezzi di Power BI](https://powerbi.microsoft.com/pricing/) e il [calcolatore Power BI Premium](https://powerbi.microsoft.com/calculator/).

> [!IMPORTANT]
> Per gli autori del contenuto è ancora necessaria una licenza di Power BI Pro, anche se l'organizzazione usa Power BI Premium. Acquistare almeno una licenza di Power BI Pro per l'organizzazione.
>
>Quando una sottoscrizione Premium scade, l'accesso completo alla capacità è garantito per altri 30 giorni. Allo scadere di questo periodo, il contenuto torna ad avere una capacità condivisa. I modelli superiori a 1 GB non sono supportati nella capacità condivisa.

## <a name="create-a-new-tenant-with-power-bi-premium-p1"></a>Creare un nuovo tenant con Power BI Premium P1

Se non si ha un tenant esistente e si vuole crearne uno, è possibile acquistare contemporaneamente Power BI Premium. Il collegamento seguente guida attraverso il processo di creazione di un nuovo tenant e consente di acquistare Power BI Premium: [Power BI Premium P1](https://signup.microsoft.com/Signup?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1).

![Power BI Premium P1](media/service-admin-premium-purchase/premium-purchase-with-tenant.png)

Quando si crea il tenant, si viene automaticamente assegnati al ruolo di amministratore globale di Office 365 per il tenant.

## <a name="purchase-a-power-bi-premium-capacity-for-an-existing-organization"></a>Acquistare capacità di Power BI Premium per l'organizzazione

Se si ha un'organizzazione esistente, è necessario avere il ruolo di amministratore globale di Office 365 o di amministratore fatturazione per l'acquisto di sottoscrizioni e licenze. Per altre informazioni, vedere [Informazioni sui ruoli di amministratore di Office 365](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d).

Per acquistare una capacità Premium, seguire questa procedura.

1. Dal servizio Power BI scegliere Office 365 dalla selezione app e quindi **Amministratore**.

    ![Selezione app di Office 365](media/service-admin-premium-purchase/o365-app-picker.png)

    In alternativa, è possibile passare al centro di amministrazione di Office 365, passando a https://portal.office.com e selezionando **Amministratore**.

1. Selezionare **Fatturazione** > **Acquisto di servizi**.

1. In **Other plans** (Altri piani) cercare le offerte di Power BI Premium. Verranno elencate le offerte da P1 a P3, EM3 e P1 (mensile).

1. Passare il mouse sui puntini di sospensione (**. . .**) e selezionare **Buy now** (Acquista).

    ![Acquista ora](media/service-admin-premium-purchase/premium-purchase.png)

1. Per completare l'acquisto, seguire la procedura.

È anche possibile selezionare i collegamenti seguenti per passare direttamente alla pagina di acquisto per questo SKU. Per altre informazioni su questi SKU, vedere [Che cos'è Power BI Premium?](service-premium.md#premiumskus)

> [!IMPORTANT]
> Se si seleziona uno dei collegamenti seguenti viene generato un errore se non si ha il ruolo di amministratore globale di Office 365 o di amministratore fatturazione.

| Collegamenti diretti agli acquisti |
| --- |
| [SKU EM3 (mensile)](https://portal.office.com/commerce/completeorder.aspx?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |
| [P1 SKU](https://portal.office.com/commerce/completeorder.aspx?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1&adminportal=1) |
| [SKU P1 (mensile)](https://portal.office.com/commerce/completeorder.aspx?OfferId=E4C8EDD3-74A1-4D42-A738-C647972FBE81&adminportal=1) |
| [P2 SKU](https://portal.office.com/commerce/completeorder.aspx?OfferId=062F2AA7-B4BC-4B0E-980F-2072102D8605&adminportal=1) |
| [P3 SKU](https://portal.office.com/commerce/completeorder.aspx?OfferId=40c7d673-375c-42a1-84ca-f993a524fed0&adminportal=1) |

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

![Annulla sottoscrizione](media/service-admin-premium-purchase/premium-cancel-subscription.png)

1. Passare all'interfaccia di amministrazione di Office 365.

1. Selezionare **Fatturazione** > **Sottoscrizioni**.

1. Selezionare la sottoscrizione di Power BI Premium dall'elenco.

1. Nell'elenco a discesa **Altre azioni** selezionare **Annulla sottoscrizione**.

    ![Altre azioni](media/service-admin-premium-purchase/o365-more-actions.png)

1. La pagina **Annulla sottoscrizione** indicherà se si è responsabili o no di una [penale per risoluzione anticipata](https://support.office.com/article/early-termination-fees-6487d4de-401a-466f-8bc3-c0beb5cc40d3). Questa pagina indica anche quando verranno eliminati i dati per la sottoscrizione.

1. Leggere attentamente le informazioni e, se si vuole continuare, selezionare **Annulla sottoscrizione**.

## <a name="next-steps"></a>Passaggi successivi

[Pagina dei prezzi](https://powerbi.microsoft.com/pricing/)
[Calcolatore Power BI Premium](https://powerbi.microsoft.com/calculator/)
[Che cos'è Power BI Premium?](service-premium.md)
[Domande frequenti su Power BI Premium](service-premium-faq.md)
[Microsoft Power BI Premium whitepaper (White paper di Microsoft Power BI Premium)](https://aka.ms/pbipremiumwhitepaper)
[Planning a Power BI Enterprise Deployment whitepaper (Pianificazione di una distribuzione aziendale di Power BI - White paper)](https://aka.ms/pbienterprisedeploy)

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)