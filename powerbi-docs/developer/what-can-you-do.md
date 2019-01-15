---
title: Quali operazioni possono eseguire gli sviluppatori con Power BI?
description: Power BI offre un'ampia gamma di opzioni per gli sviluppatori, che vanno dall'incorporamento agli oggetti visivi personalizzati fino ai set di dati in streaming.
author: markingmyname
ms.author: maghan
manager: kfile
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: mvc
ms.date: 09/17/2018
ms.openlocfilehash: a32bdceb317f2d6a2f5945dc3911f683a306605e
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54282472"
---
# <a name="what-can-developers-do-with-power-bi"></a>Quali operazioni possono eseguire gli sviluppatori con Power BI?

Gli sviluppatori hanno diverse opzioni per provare a includere contenuto di Power BI nelle applicazioni. Gli sviluppatori possono usare queste opzioni, tra cui**incorporamento con Power BI**, **oggetti visivi personalizzati** e **push dei dati in Power BI**.

## <a name="embedding-power-bi-content"></a>Incorporamento di contenuto di Power BI

Il servizio Power BI (SaaS) e il servizio Power BI Embedded in Azure (PaaS) offrono API per l'incorporamento di dashboard e report. Questa funzionalità consente di accedere alle funzionalità di Power BI più recenti, ad esempio dashboard, gateway e aree di lavoro per le app, quando si incorpora il contenuto.

È possibile usare lo [strumento di installazione dell'incorporamento](https://aka.ms/embedsetup) per iniziare rapidamente e scaricare un'applicazione di esempio.

Scegliere la soluzione adatta alle proprie esigenze:

* L'[incorporamento per i clienti](embedding.md#embedding-for-your-customers) offre la possibilità di incorporare dashboard e report per gli utenti che non hanno un account per Power BI. Eseguire la soluzione [Incorporare per i clienti](https://aka.ms/embedsetup/AppOwnsData).

* L'[incorporamento per l'organizzazione](embedding.md#embedding-for-your-organization) consente di estendere il servizio Power BI. Eseguire la soluzione [Incorporare per l'organizzazione](https://aka.ms/embedsetup/UserOwnsData).

![Esempio di Power BI Embedded](media/what-can-you-do/what-can-you-do-02.png)

Per altre informazioni sull'incorporamento con Power BI, vedere [Incorporamento con Power BI](embedding.md).

## <a name="developing-custom-visuals"></a>Sviluppo di oggetti visivi personalizzati

È possibile usare oggetti visivi personalizzati con Power BI per creare un tipo di oggetto visivo esclusivo in base alle esigenze dell'utente o della società. Spesso gli oggetti visivi personalizzati vengono creati dagli sviluppatori quando la pur grande varietà di oggetti visivi inclusi in Power BI non soddisfa le esigenze.

Gli oggetti visivi personalizzati consentono di creare oggetti visivi da usare all'interno di report di Power BI. Gli oggetti visivi personalizzati sono scritti in TypeScript, un soprainsieme di JavaScript. TypeScript supporta caratteristiche più avanzate e l'accesso anticipato alla funzionalità ES6/ES7. L'applicazione di stili visivi viene gestita tramite i fogli di stile CSS. Per praticità verrà usato il servizio di pre-compilazione Less, che supporta alcune funzionalità avanzate, ad esempio l'annidamento, le variabili e i cicli. Se non si vuole usare alcuna di queste funzionalità, è possibile scrivere fogli di stile CSS normali nel file di Less.

![Esempio di oggetti visivi](media/what-can-you-do/powerbi-custom-visual-store.png)

Per altre informazioni sullo sviluppo di oggetti visivi personalizzati, vedere [Developing a Power BI custom visual](custom-visual-develop-tutorial.md) (Sviluppo di un oggetto visivo personalizzato di Power BI).

## <a name="using-api-automation"></a>Uso dell'automazione API

Power BI visualizza dashboard interattivi, che possono essere creati e aggiornati da molte origini dati diverse in tempo reale. Usando un qualsiasi linguaggio di programmazione che supporti chiamate REST, è possibile creare un'app in grado di integrarsi con un dashboard di Power BI in tempo reale. È anche possibile integrare riquadri e report di Power BI nelle app.

Gli sviluppatori possono anche creare le proprie visualizzazioni dei dati che possono essere usate nei dashboard e nei report interattivi.

![Esempio di push dei dati](media/what-can-you-do/powerbi-push-data.png)

Per informazioni su alcune attività che è possibile eseguire con le API Power BI, vedere [Quali operazioni possono eseguire gli sviluppatori con le API Power BI](overview-of-power-bi-rest-api.md)?

## <a name="next-steps"></a>Passaggi successivi

[Incorporamento con Power BI](embedding.md)  

[Developing a Power BI custom visual](https://microsoft.github.io/PowerBI-visuals/docs/step-by-step-lab/developing-a-power-bi-custom-visual/) (Sviluppo di un oggetto visivo personalizzato di Power BI)

[Quali operazioni possono eseguire gli sviluppatori con le API Power BI?](overview-of-power-bi-rest-api.md)

[Centro per sviluppatori Power BI](https://powerbi.microsoft.com/developers/)