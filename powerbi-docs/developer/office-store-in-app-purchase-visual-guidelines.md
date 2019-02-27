---
title: Potrebbe essere necessario un acquisto aggiuntivo - Linee guida per gli oggetti visivi di Power BI
description: Informazioni su come pubblicare l'oggetto visivo personalizzato in AppSource in modo che altri utenti possano individuarlo e usarlo tramite acquisto.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 11/26/2018
ms.openlocfilehash: 92d4320026164e523297cbe48ee87ce33d9ab2f7
ms.sourcegitcommit: 796bf513bf8669676e2a44627b56221b1629a6a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2019
ms.locfileid: "56826584"
---
# <a name="guidelines-for-power-bi-visuals-with-additional-purchases"></a>Linee guida per gli oggetti visivi di Power BI con acquisti aggiuntivi

Fino a poco tempo fa, il Marketplace (AppSource) accettava solo oggetti visivi di Power BI gratuiti. Questa regola è stata modificata ed è possibile inviare in AppSource anche oggetti visivi con il tag di prezzo "Potrebbe essere necessario un acquisto aggiuntivo". 

Gli oggetti visivi con il tag "Potrebbe essere necessario un acquisto aggiuntivo" sono analoghi ai componenti aggiuntivi con acquisto in-app disponibili in Office Store. Gli sviluppatori possono anche inviare questi oggetti visivi per richiedere la certificazione dopo aver ricevuto l'approvazione del team di AppSource e averne verificato la conformità con i requisiti. Per altre informazioni sui requisiti, vedere [Oggetti visivi personalizzati certificati](../power-bi-custom-visuals-certified.md).

> [!NOTE]
> * Perché l'oggetto visivo sia certificato, non deve avere accesso a servizi o risorse esterni.
> * Tutti gli oggetti visivi gratuiti devono mantenere le stesse funzionalità gratuite offerte in precedenza. È possibile aggiungere funzionalità a pagamento avanzate facoltative oltre alle funzionalità gratuite esistenti. È consigliabile inviare gli oggetti visivi con acquisto in-app con funzionalità avanzate come nuovi oggetti visivi anziché aggiornare gli oggetti gratuiti esistenti.


## <a name="what-changed-in-the-submission-process"></a>Che cosa è cambiato nel processo di invio?

Gli sviluppatori caricano gli oggetti visivi con acquisto in-app in AppSource usando il Dashboard venditori, come erano soliti fare per gli oggetti visivi gratuiti. Per indicare che l'oggetto visivo inviato contiene funzionalità con acquisto in-app, gli sviluppatori devono indicare nelle note del dashboard venditori: "Oggetto visivo con acquisto in-app". Gli sviluppatori devono anche specificare anche un codice di licenza o un token in modo che il team di convalida possa convalidare le funzionalità con acquisto in-app. Dopo aver convalidato e approvato l'oggetto visivo, nell'elenco AppSource degli oggetti visivi con acquisto in-app viene visualizzato "Potrebbe essere necessario un acquisto aggiuntivo" tra le opzioni di prezzo.

## <a name="what-is-a-power-bi-visual-with-iap-features"></a>Che cos'è un oggetto visivo di Power BI con funzionalità con acquisto in-app?

Un oggetto visivo con acquisto in-app è un oggetto visivo gratuito che offre funzionalità gratuite. Include anche alcune funzionalità avanzate per l'uso delle quali potrebbe essere previsto un costo aggiuntivo. Nella descrizione dell'oggetto visivo gli sviluppatori devono segnalare agli utenti la presenza di funzionalità che richiedono un acquisto aggiuntivo per poter essere usate. Attualmente, Microsoft non fornisce API native per supportare l'acquisto di app e componenti aggiuntivi.

Per questo tipo di acquisti, gli sviluppatori possono usare un sistema di pagamento di terze parti. Per altre informazioni, vedere l'[informativa per lo store](https://docs.microsoft.com/office/dev/store/validation-policies#2-apps-or-add-ins-can-display-certain-ads).

> [!NOTE]
> Le filigrane non sono consentite per le funzionalità gratuite. Gli sviluppatori potrebbero visualizzare una finestra popup o una filigrana se le funzionalità avanzate a pagamento vengono usate senza una licenza valida.  

## <a name="logo-guidelines"></a>Linee guida per il logo

In questa sezione vengono descritte le specifiche per l'aggiunta dei logo negli oggetti visivi.

> [!NOTE]
> I logo sono consentiti solo in modalità di modifica. I logo non possono essere visualizzati in modalità di visualizzazione.

![Definizioni](media/office-store-in-app-purchase-visual-guidelines/definitions.png)

![Aspetti da tenere a mente](media/office-store-in-app-purchase-visual-guidelines/things-to-keep-in-mind.png)

![Cose da evitare](media/office-store-in-app-purchase-visual-guidelines/things-to-avoid.png)

![Dimensioni e formato](media/office-store-in-app-purchase-visual-guidelines/size-and-format.png)

![Margini e dimensioni](media/office-store-in-app-purchase-visual-guidelines/margins-and-sizes.png)

![Modalità di modifica](media/office-store-in-app-purchase-visual-guidelines/logos-in-edit-mode.png)

## <a name="best-practices"></a>Procedure consigliate

### <a name="visual-landing-page"></a>Pagina di destinazione dell'oggetto visivo

Usare la pagina di destinazione per spiegare come usare l'oggetto visivo e dove acquistare la licenza. Non includere video che si attivano automaticamente. Aggiungere solo materiale che ottimizza l'esperienza dell'utente, ad esempio informazioni o collegamenti su dettagli di acquisto delle licenze o sull'uso delle funzionalità con acquisto in-app.

### <a name="license-key-and-token"></a>Codice di licenza e token

Per comodità dell'utente, aggiungere i campi correlati a codice di licenza o token nella parte superiore del riquadro formato.

## <a name="faq"></a>DOMANDE FREQUENTI

Per altre informazioni sugli oggetti visivi, vedere le [domande frequenti sugli oggetti visivi con acquisti aggiuntivi](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-faq#visuals-with-additional-purchases).

## <a name="next-steps"></a>Passaggi successivi

Informazioni su come pubblicare l'oggetto visivo personalizzato in [AppSource](office-store.md) in modo che altri utenti possano individuarlo e usarlo.
