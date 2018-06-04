---
title: Connettersi a Zuora con Power BI
description: Zuora per Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: f283a8ed273dcb609e9d5160adbeb714e8935ab9
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34251934"
---
# <a name="connect-to-zuora-with-power-bi"></a>Connettersi a Zuora con Power BI
Zuora per Power BI consente di visualizzare dati importanti relativi a ricavi, fatturazione e sottoscrizioni. È possibile usare il dashboard e i report predefiniti per analizzare le tendenze di utilizzo, tenere traccia di fatture e pagamenti e monitorare i ricavi ricorrenti oppure personalizzare dashboard e report in base alle esigenze specifiche.

Connettersi a [Zuora](https://app.powerbi.com/getdata/services/Zuora) per Power BI.

## <a name="how-to-connect"></a>Come connettersi
1. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro.

   ![](media/service-connect-to-zuora/getdata.png)
2. Nella casella **Servizi** selezionare **Recupera**.

   ![](media/service-connect-to-zuora/services.png)
3. Selezionare **Zuora** \> **Recupera**.

   ![](media/service-connect-to-zuora/zuora.png)
4. Specificare l'URL di Zuora. Il percorso è solitamente "https://www.zuora.com". Per informazioni dettagliate sulla [ricerca dei parametri](#FindingParams), vedere più avanti.

   ![](media/service-connect-to-zuora/params.png)
5. In **Metodo di autenticazione**selezionare **Di base** e fornire il nome utente e la password (distinzione tra maiuscole e minuscole), quindi selezionare **Accedi**.

    ![](media/service-connect-to-zuora/creds.png)
6. Dopo l'approvazione, il processo di importazione inizierà automaticamente. Al termine nel riquadro di spostamento verranno visualizzati un nuovo dashboard, un nuovo report e un nuovo set di dati. Selezionare il dashboard per visualizzare i dati importati.

     ![](media/service-connect-to-zuora/dashboard.png)

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](power-bi-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](service-dashboard-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificare la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="whats-included"></a>Cosa è incluso
Il pacchetto di contenuto usa l'API di Zuora AQUA per recuperare le tabelle seguenti:

| Tabelle |  |  |
| --- | --- | --- |
| Account |InvoiceItemAdjustment |Refund |
| AccountingCode |Payment |RevenueSchedule |
| AccountingPeriod |PaymentMethod |RevenueScheduleItem |
| BillTo |Product |Subscription |
| DateDim |ProductRatePlan |TaxationItem |
| Invoice |ProductRatePlanCharge |Usage |
| InvoiceAdjustment |RatePlan | |
| InvoiceItem |RatePlanCharge | |

It also includes these calculated measures:

| Misura | Descrizione | Pseudo-calcolo |
| --- | --- | --- |
| Account: Payments |Importo totale dei pagamenti in un periodo di tempo, in base alla data effettiva del pagamento. |SUM (Payment.Amount) <br>WHERE<br>Payment.EffectiveDate =< TimePeriod.EndDate<br>AND    Payment.EffectiveDate >= TimePeriod.StartDate |
| Account: Refunds |Importo totale dei rimborsi in un periodo di tempo, in base alla data del rimborso. L'importo viene riportato come numero negativo. |-1*SUM(Refund.Amount)<br>WHERE<br>Refund.RefundDate =< TimePeriod.EndDate<br>AND    Refund.RefundDate >= TimePeriod.StartDate |
| Account: Net Payments |Somma dei pagamenti e dei rimborsi degli account in periodo di tempo. |Account.Payments + Account.Refunds |
| Account: Active Accounts |Numero di account attivi in un periodo di tempo. Le sottoscrizioni devono essere iniziate prima (o in corrispondenza) della data iniziale del periodo di tempo. |COUNT (Account.AccountNumber)<br>WHERE<br>    Subscription.Status != "Expired"<br>AND    Subscription.Status != "Draft"<br>AND    Subscription.SubscriptionStartDate <= TimePeriod.StartDate<br>AND    (Subscription.SubscriptionEndDate > TimePeriod.StartDate<br>OR<br>Subscription.SubscriptionEndDate = null) –evergreen subscription |
| Account: Average Recurring Revenue |MRR lordo per account attivo in un periodo di tempo. |Gross MRR / Account.ActiveAccounts |
| Account: Cancelled Subscriptions |Numero di account che hanno annullato una sottoscrizione in un periodo di tempo. |COUNT (Account.AccountNumber)<br>WHERE<br>Subscription.Status = "Cancelled"<br>AND    Subscription.SubscriptionStartDate <= TimePeriod.StartDate<br>AND    Subscription.CancelledDate >= TimePeriod.StartDate |
| Account: Payment Errors |Valore totale degli errori di pagamento. |SUM (Payment.Amount)<br>WHERE<br>Payment.Status = "Error" |
| Revenue Schedule Item: Recognized Revenue |Fatturato riconosciuto totale in un periodo contabile. |SUM (RevenueScheduleItem.Amount)<br>WHERE<br>AccountingPeriod.StartDate = TimePeriod.StartDate |
| Subscription: New Subscriptions |Numero di nuove sottoscrizioni in un periodo di tempo. |COUNT (Subscription.ID)<br>WHERE<br>Subscription.Version = "1"<br>AND    Subscription.CreatedDate <= TimePeriod.EndDate<br>AND    Subscription.CreatedDate >= TimePeriod.StartDate |
| Invoice: Invoice Items |Importi totali addebiti per voci fattura in un periodo di tempo. |SUM (InvoiceItem.ChargeAmount)<br>WHERE<br>    Invoice.Status = "Posted"<br>AND    Invoice.InvoiceDate <= TimePeriod.EndDate<br>AND    Invoice.InvoiceDate >= TimePeriod.StartDate |
| Invoice: Taxation Items |Importi totali imposte per voci di imposta in un periodo di tempo. |SUM (TaxationItem.TaxAmount)<br>WHERE<br>Invoice.Status = "Posted"<br>AND    Invoice.InvoiceDate <= TimePeriod.EndDate<br>AND    Invoice.InvoiceDate >= TimePeriod.StartDate |
| Invoice: Invoice Item Adjustments |Importi totali rettifiche di voci fattura in un periodo di tempo. |SUM (InvoiceItemAdjustment.Amount) <br>WHERE<br>    Invoice.Status = "Posted"<br>AND    InvoiceItemAdjustment.AdjustmentDate <= TimePeriod.EndDate<br>AND    InvoiceItemAdjustment.AdjustmentDate >= TimePeriod.StartDate |
| Invoice: Invoice Adjustments |Importi totali rettifiche di fatture in un periodo di tempo. |SUM (InvoiceAdjustment.Amount) <br>WHERE<br>    Invoice.Status = "Posted"<br>AND    InvoiceAdjustment.AdjustmentDate <= TimePeriod.EndDate<br>AND    InvoiceAdjustment.AdjustmentDate >= TimePeriod.StartDate |
| Invoice: Net Billings |Somma di voci fattura, voci di imposta, rettifiche di voci fattura e rettifiche di fatture in un periodo di tempo. |Invoice.InvoiceItems + Invoice.TaxationItems + Invoice.InvoiceItemAdjustments + Invoice.InvoiceAdjustments |
| Invoice: Invoice Aging Balance |Somma dei saldi delle fatture registrate. |SUM (Invoice.Balance) <br>WHERE<br>    Invoice.Status = "Posted" |
| Invoice: Gross Billings |Somma degli importi di addebito per le voci delle fatture registrate in un periodo di tempo. |SUM (InvoiceItem.ChargeAmount) <br>WHERE<br>    Invoice.Status = "Posted"<br>AND    Invoice.InvoiceDate <= TimePeriod.EndDate<br>AND    Invoice.InvoiceDate >= TimePeriod.StartDate |
| Invoice: Total Adjustments |Somma delle rettifiche di fatture e delle rettifiche di voci di fattura elaborate associate alle fatture registrate. |SUM (InvoiceAdjustment.Amount) <br>WHERE<br>    Invoice.Status = "Posted"<br>AND    InvoiceAdjustment.Status = "Processed"<br>+<br>SUM (InvoiceItemAdjustment.Amount) <br>WHERE<br>    Invoice.Status = "Posted"<br>AND    invoiceItemAdjustment.Status = "Processed" |
| Rate Plan Charge: Gross MRR |Somma dei ricavi periodici mensili da sottoscrizioni in un periodo di tempo. |SUM (RatePlanCharge.MRR) <br>WHERE<br>    Subscription.Status != "Expired"<br>AND    Subscription.Status != "Draft"<br>AND    RatePlanCharge.EffectiveStartDate <= TimePeriod.StartDate<br>AND        RatePlanCharge.EffectiveEndDate > TimePeriod.StartDate<br>    OR    RatePlanCharge.EffectiveEndDate = null --evergreen subscription |

## <a name="system-requirements"></a>Requisiti di sistema
È necessario l'accesso all'API Zuora.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Individuazione dei parametri
Fornire l'URL usato in genere per accedere ai dati di Zuora. Le opzioni valide sono:  

* https://www.zuora.com  
* https://www.apisandbox.zuora.com  
* URL corrispondente all'istanza del servizio  

## <a name="troubleshooting"></a>Risoluzione dei problemi
Il pacchetto di contenuto Zuora effettua il pull di numerosi elementi dell'account Zuora. Se non si usano determinate funzionalità, i riquadri o i report corrispondenti potrebbero apparire vuoti. Se si verificano problemi di caricamento, contattare il supporto di Power BI.

## <a name="next-steps"></a>Passaggi successivi
[Introduzione a Power BI](service-get-started.md)

[Recuperare dati in Power BI](service-get-data.md)
