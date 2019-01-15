---
title: Filtro incrociato bidirezionale in Power BI Desktop
description: Abilitare il filtro incrociato con DirectQuery in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: bb4ac81556541c40cfb2e96cb2139be4ea1cb820
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54285462"
---
# <a name="bidirectional-cross-filtering-using-directquery-in-power-bi-desktop"></a>Filtro incrociato bidirezionale con DirectQuery in Power BI Desktop

Quando si filtrano tabelle per creare la visualizzazione appropriata di dati, gli autori di report devono determinare in che modo i filtri vengono applicati a un report. Il contesto di filtro di una tabella viene ad esempio mantenuto su un lato della relazione ma non sull'altro e sono quindi spesso necessarie formule DAX complesse per ottenere i risultati richiesti.

Il filtro incrociato bidirezionale consente agli autori di report e ai responsabili della modellazione dei dati di avere un controllo maggiore sul modo in cui i filtri vengono applicati quando si utilizzano tabelle correlate, permettendo l'applicazione di questi filtri su *entrambi* i lati di una relazione tra tabelle. Per ottenere questo risultato, il contesto di filtro viene propagato a una seconda tabella correlata nell'altro lato della relazione tra tabelle.

## <a name="detailed-whitepaper-for-bidirectional-cross-filtering"></a>White paper dettagliato sul filtro incrociato bidirezionale
È disponibile un [white paper dettagliato](http://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx) che illustra il filtro incrociato bidirezionale in Power BI Desktop. Il white paper illustra anche SQL Server Analysis Services 2016, perché il comportamento è uguale in entrambi i casi.

* Scaricare il white paper[Bidirectional cross-filtering for Power BI Desktop](http://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx) (Filtro incrociato bidirezionale per Power BI Desktop).

## <a name="enabling-bidirectional-cross-filtering-for-directquery"></a>Abilitazione del filtro incrociato bidirezionale per DirectQuery

Per abilitare il filtro incrociato, nella finestra di dialogo **Modifica relazione** per una relazione è necessario selezionare le opzioni seguenti:

* L'opzione **Direzione filtro incrociato**deve essere impostata su **Entrambe**.
* È necessario selezionare anche l'opzione **Applica filtro di sicurezza in entrambe le direzioni**.

  ![](media/desktop-bidirectional-filtering/bidirectional-filtering_2.png)

> [!NOTE]
> Quando si creano formule DAX per il filtro incrociato in Power BI Desktop, usare *UserPrincipalName*, che spesso corrisponde all'accesso dell'utente; ad esempio <em>joe@contoso.com</em>, invece di *UserName*. Potrebbe essere quindi necessario creare una tabella correlata che esegue il mapping di *UserName* o EmployeeID, ad esempio, a *UserPrincipalName*.

Per altre informazioni e per esempi sul funzionamento del filtro incrociato bidirezionale, vedere il [white paper](http://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx) indicato in precedenza in questo articolo.

