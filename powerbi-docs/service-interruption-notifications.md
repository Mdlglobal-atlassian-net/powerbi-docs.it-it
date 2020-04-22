---
title: Notifiche di interruzione del servizio
description: Informazioni su come ricevere notifiche tramite posta elettronica quando si verifica un'interruzione o una riduzione del servizio Power BI.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/17/2020
ms.author: kfollis
ms.openlocfilehash: 85b26b68c4943e0bc100be7a298730cec34cfc78
ms.sourcegitcommit: d43761104f7daf4b2f297648855bb573b53e6d8c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2020
ms.locfileid: "81637761"
---
# <a name="service-interruption-notifications"></a>Notifiche di interruzione del servizio

Avere informazioni dettagliate sulla disponibilità delle applicazioni aziendali critiche è fondamentale. Power BI offre notifiche per gli eventi imprevisti, in modo che sia possibile ricevere messaggi di posta elettronica in caso di interruzione o riduzione del servizio. Nonostante il fatto che nel 99,9% dei casi il contratto di servizio (SLA) di Power BI riduca al minimo l'incidenza di questi eventi, è necessario assicurarsi di essere sempre informati. Lo screenshot seguente illustra il tipo di messaggio di posta elettronica che verrà visualizzato se si abilitano le notifiche:

![Messaggio di posta elettronica di notifica per aggiornamento](media/service-interruption-notifications/refresh-notification-email.png)

Attualmente i messaggi di posta elettronica vengono inviati per gli _scenari di affidabilità_ seguenti:

- Affidabilità apertura report
- Affidabilità aggiornamento modello
- Affidabilità aggiornamento query

Vengono inviate notifiche quando si verifica un _ritardo prolungato_ per operazioni come l'apertura di report, l'aggiornamento di set di dati o l'esecuzione di query. Dopo la risoluzione di un evento imprevisto, si riceve un messaggio di posta elettronica di completamento.

> [!NOTE]
> Questa funzionalità attualmente è disponibile solo per capacità dedicate in Power BI Premium. Non è disponibile per la capacità condivisa o incorporata.





## <a name="enable-notifications"></a>Abilitare le notifiche

Un amministratore di tenant di Power BI abilita le notifiche nel portale di amministrazione:

1. Identificare o creare un gruppo di sicurezza abilitato per la posta elettronica che deve ricevere le notifiche.

1. Nel portale di amministrazione selezionare **Impostazioni tenant**. In **Impostazioni per Guida e supporto tecnico** espandere **Ricevi notifiche di posta elettronica per interruzioni del servizio o eventi imprevisti**.

1. Abilitare le notifiche, immettere un gruppo di sicurezza e selezionare **Applica**.

    ![Abilitare le notifiche del servizio](media/service-interruption-notifications/enable-notifications.png)

> [!NOTE]
> Power BI invia notifiche dall'account no-reply-powerbi@microsoft.com. Assicurarsi che l'account sia presente nell'elenco di elementi consentiti in modo che le notifiche non finiscano in una cartella di posta indesiderata.

## <a name="next-steps"></a>Passaggi successivi

[Opzioni di supporto per Power BI Pro e Power BI Premium](service-support-options.md)

Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)
