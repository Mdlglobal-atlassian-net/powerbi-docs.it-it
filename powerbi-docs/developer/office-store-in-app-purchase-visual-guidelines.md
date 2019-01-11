---
title: Potrebbe essere necessario un acquisto aggiuntivo - Linee guida per gli oggetti visivi di Power BI
description: Informazioni su come pubblicare l'oggetto visivo personalizzato in AppSource in modo che altri utenti possano individuarlo e usarlo tramite acquisto.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 11/26/2018
ms.openlocfilehash: 2b7a71baafd8ec2ef839aaca95529221c642357f
ms.sourcegitcommit: c09241803664643e1b2ba0c150e525e1262ca466
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54072176"
---
# <a name="guidelines-for-power-bi-visuals-with-additional-purchases"></a>Linee guida per gli oggetti visivi di Power BI con acquisti aggiuntivi

Fino a poco tempo fa, il **Marketplace (AppSource)** accettava solo oggetti visivi di Power BI gratuiti. Questo criterio è in fase di modifica tant'è che è anche possibile inviare ad **AppSource** oggetti visivi che hanno l'etichetta di prezzo "Potrebbe essere necessario un acquisto aggiuntivo". Gli oggetti visivi con l'etichetta "Potrebbe essere necessario un acquisto aggiuntivo" sono analoghi ai componenti aggiuntivi con acquisto in-app disponibili in Office Store. Gli sviluppatori possono anche inviare questi oggetti visivi per richiedere la certificazione dopo aver ricevuto l'approvazione del team di **AppSource** e averne verificato la conformità con i requisiti, come descritto nell'[articolo Oggetti visivi personalizzati certificati](../power-bi-custom-visuals-certified.md).

> [!Note]
> Perché l'oggetto visivo sia certificato, non deve avere accesso a servizi o risorse esterni.

## <a name="whats-changing-in-the-submission-process"></a>Cosa cambia nel processo di invio?

Gli sviluppatori caricano gli oggetti visivi con acquisto in-app in AppSource usando il Dashboard venditori, come erano soliti fare per gli oggetti visivi gratuiti. Per indicare che l'oggetto visivo inviato contiene funzionalità con acquisto in-app, gli sviluppatori devono indicare nelle note del dashboard venditori: "Oggetto visivo con acquisto in-app." Gli sviluppatori devono anche specificare anche un codice di licenza o un token in modo che il team di convalida possa convalidare le funzionalità con acquisto in-app. Dopo aver convalidato e approvato l'oggetto visivo, nell'elenco AppSource degli oggetti visivi con acquisto in-app viene visualizzato "Potrebbe essere necessario un acquisto aggiuntivo" tra le opzioni di prezzo.

## <a name="what-is-a-power-bi-visual-with-iap-features"></a>Che cos'è un oggetto visivo di Power BI con funzionalità con acquisto in-app?

Un oggetto visivo con acquisto in-app è un oggetto visivo gratuito con funzionalità gratuite, che offre tuttavia anche funzionalità aggiuntive per il cui utilizzo viene applicato un costo aggiuntivo. Nella descrizione dell'oggetto visivo gli sviluppatori devono specificare quali sono le funzionalità che richiedono un acquisto aggiuntivo per essere usate. Attualmente, Microsoft non offre Application Programming Interface (API) native per supportare l'acquisto di app e componenti aggiuntivi. Per questo tipo di acquisti, gli sviluppatori possono usare un sistema di pagamento di terze parti. Fare riferimento ai [criteri](https://docs.microsoft.com/office/dev/store/validation-policies#2-apps-or-add-ins-can-display-certain-ads) di Microsoft Store.

## <a name="logo-guidelines"></a>Linee guida per il logo

In questa sezione vengono descritte le specifiche per l'aggiunta dei logo negli oggetti visivi.

> [!NOTE]
> I logo sono consentiti solo in modalità di modifica. I logo non possono essere visualizzati in modalità di visualizzazione.

![definitions](media/office-store-in-app-purchase-visual-guidelines/definitions.png)

![things-to-keep](media/office-store-in-app-purchase-visual-guidelines/things-to-keep-in-mind.png)

![things-to](media/office-store-in-app-purchase-visual-guidelines/things-to-avoid.png)

![size-and-format ](media/office-store-in-app-purchase-visual-guidelines/size-and-format.png)

![margins-and](media/office-store-in-app-purchase-visual-guidelines/margins-and-sizes.png)

![edit-mode](media/office-store-in-app-purchase-visual-guidelines/logos-in-edit-mode.png)

## <a name="best-practices"></a>Procedure consigliate

### <a name="visual-landing-page"></a>Pagina di destinazione dell'oggetto visivo

Usare la pagina di destinazione per spiegare come usare l'oggetto visivo e dove acquistare la licenza. Non includere video che si attivano automaticamente. Aggiungere solo materiale che ottimizza l'esperienza dell'utente, ad esempio informazioni o collegamenti su dettagli di acquisto delle licenze o sull'uso delle funzionalità con acquisto in-app.

### <a name="license-key-and-token"></a>Codice di licenza e token

Per motivi di praticità dell'utente, aggiungere i campi relativi al codice di licenza o al token nella parte superiore del riquadro del formato, in modo che l'utente possa individuarli facilmente.

## <a name="faq"></a>DOMANDE FREQUENTI

Per altre informazioni e risposte, vedere le [domande frequenti sugli oggetti visivi con acquisti aggiuntivi](https://docs.microsoft.com/en-us/power-bi/power-bi-custom-visuals-faq#visuals-with-additional-purchases).

## <a name="next-steps"></a>Passaggi successivi

Informazioni su come pubblicare l'oggetto visivo personalizzato in [AppSource](office-store.md) in modo che altri utenti possano individuarlo e usarlo.
