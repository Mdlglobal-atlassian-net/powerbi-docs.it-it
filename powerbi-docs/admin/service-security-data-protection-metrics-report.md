---
title: Report sulle metriche di protezione dei dati
description: Informazioni sul report sulle metriche di protezione dei dati
author: paulinbar
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: d2bd3308de21aa6064765b820745201efd8b23ab
ms.sourcegitcommit: 480bba9c745cb9af2005637e693c5714b3c64a8a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/11/2020
ms.locfileid: "79112489"
---
# <a name="data-protection-metrics-report-preview"></a>Report sulle metriche di protezione dei dati (anteprima)

## <a name="what-is-the-data-protection-metrics-report"></a>Che cos'è il report sulle metriche di protezione dei dati?
Il report sulle metriche di protezione dei dati è un report dedicato che gli [amministratori di Power BI](../service-admin-role.md) possono usare per monitorare e tenere traccia dell'utilizzo e dell'adozione delle etichette di riservatezza dei dati nel tenant.

![Report sulle metriche di protezione dei dati](./media/service-security-data-protection-metrics-report/protection-metrics-seven-days-1.png)
 
Caratteristiche del report:
* Istogramma a colonne in pila 100% che mostra l'utilizzo quotidiano delle etichette di riservatezza nel tenant per gli ultimi 7, 30 o 90 giorni. Questo grafico consente di tenere traccia più facilmente dell'utilizzo relativo dei diversi tipi di etichette nel tempo.
* Grafici ad anello che mostrano lo stato corrente dell'utilizzo delle etichette di riservatezza nel tenant per dashboard, report, set di dati e flussi di dati.
* Un collegamento al portale di Cloud App Security in cui sono disponibili gli avvisi di Power BI, gli utenti a rischio, i log attività e altre informazioni. Per altre informazioni, vedere [Uso dei controlli di Microsoft Cloud App Security in Power BI (anteprima)](./service-security-using-microsoft-cloud-app-security-controls.md).

Il report viene aggiornato ogni 24 ore.

## <a name="viewing-the-data-protection-metrics-report"></a>Visualizzazione del report sulle metriche di protezione dei dati

Per aprire e visualizzare il report, è necessario avere un [ruolo di amministratore di Power BI](../service-admin-role.md).
Per visualizzare il report, passare a **Impostazioni > Portale di amministrazione** e scegliere **Metriche di protezione (anteprima)** .

![portale di amministrazione - metriche di protezione](./media/service-security-data-protection-metrics-report/protection-metrics-admin-portal.png)
 
 
La prima volta che si apre il report sulle metriche di protezione dei dati, il caricamento potrebbe richiedere alcuni secondi. Un report e un set di dati con titolo **Data protection metrics (automatically generated)** (Metriche di protezione dei dati - generato automaticamente) verranno creati nell'ambiente privato dell'utente in "Area di lavoro personale". Non è consigliabile visualizzarlo qui. Questo non è il report con funzionalità complete. Visualizzare invece il report nel portale di amministrazione come descritto in precedenza.

> [!CAUTION]
> Non modificare il report o il set di dati in alcun modo, dato che vengono distribuite regolarmente nuove versioni del report e tutte le modifiche apportate al report originale verranno sovrascritte se si esegue l'aggiornamento alla nuova versione.

## <a name="report-updates"></a>Aggiornamenti del report

Vengono rilasciate periodicamente versioni migliorate del report sulle metriche di protezione dei dati. All'apertura del report, se è disponibile una nuova versione verrà richiesto se si vuole aprire la nuova versione. Se si conferma, verrà caricata la nuova versione del report che sovrascriverà la versione precedente. Eventuali modifiche apportate al report precedente e/o al set di dati andranno perse. È possibile scegliere di non aprire la nuova versione, ma in questo caso non sarà possibile usufruire dei miglioramenti di tale versione. 
## <a name="notes-and-considerations"></a>Note e considerazioni
* Per consentire la generazione corretta del report sulle metriche di protezione dei dati, è necessario abilitare [Information Protection](./service-security-enable-data-sensitivity-labels.md) nel tenant e [applicare le etichette di riservatezza](../designer/service-security-apply-data-sensitivity-labels.md). 
* Per accedere alle informazioni di Cloud App Security, è necessario che l'organizzazione disponga della [licenza di Cloud App Security](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls#microsoft-cloud-app-security-licensing) appropriata.
* Se si decide di condividere le informazioni dal report sulle metriche di protezione dei dati con un utente che non è un amministratore di Power BI, tenere presente che il report contiene informazioni sensibili sull'organizzazione.
* Il report sulle metriche di protezione dei dati è un tipo di report speciale e non viene visualizzato negli elenchi "Condivisi con l'utente corrente", "Recenti" e "Preferiti".
* Il report sulle metriche di protezione dei dati non è disponibile per gli [utenti esterni (utenti guest di Azure Active Directory B2B)](../service-admin-azure-ad-b2b.md).
## <a name="next-steps"></a>Passaggi successivi
* [Protezione dei dati in Power BI (anteprima)](./service-security-data-protection-overview.md)
* [Uso dei controlli di Microsoft Cloud App Security in Power BI (anteprima)](./service-security-using-microsoft-cloud-app-security-controls.md)
* [Informazioni sul ruolo di amministratore del servizio Power BI](../service-admin-role.md)
* [Abilitare le etichette di riservatezza dei dati in Power BI](./service-security-enable-data-sensitivity-labels.md)