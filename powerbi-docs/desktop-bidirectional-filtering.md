---
title: Filtro incrociato bidirezionale in Power BI Desktop
description: Abilitare il filtro incrociato con DirectQuery in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 141dabdce7816d21c49d8c7f98d1438c2fc20e8d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "76709843"
---
# <a name="enable-bidirectional-cross-filtering-for-directquery-in-power-bi-desktop"></a>Abilitare il filtro incrociato bidirezionale con DirectQuery in Power BI Desktop

Quando le tabelle vengono filtrate per creare la visualizzazione appropriata dei dati, per gli autori di report e di modelli di dati non è semplice determinare la corretta modalità di applicazione dei filtri a un report. In precedenza, il contesto di filtro della tabella era mantenuto su un lato della relazione, ma non sull'altro. In questo modo, era spesso necessario applicare una formula DAX complessa per ottenere i risultati desiderati.

Con il filtro incrociato bidirezionale, gli autori di report e modelli di dati hanno ora un maggiore controllo sulla modalità di applicazione dei filtri durante l'uso di tabelle correlate. Il filtro incrociato bidirezionale consente loro di applicare filtri su *entrambi* i lati di una relazione tra tabelle. Per ottenere questo risultato, il contesto di filtro viene propagato a una seconda tabella correlata sull'altro lato della relazione.

## <a name="enable-bidirectional-cross-filtering-for-directquery"></a>Abilitare il filtro incrociato bidirezionale per DirectQuery

È possibile abilitare il filtro incrociato nella finestra di dialogo **Modifica relazione**. Per abilitare il filtro incrociato per una relazione, è necessario configurare le opzioni seguenti:

* Impostare **Direzione filtro incrociato** su **Entrambi**.
* Selezionare **Applica filtro di sicurezza in entrambe le direzioni**.

  ![Configurare il filtro incrociato bidirezionale in Power BI Desktop.](media/desktop-bidirectional-filtering/bidirectional-filtering_2.png)

> [!NOTE]
> Quando si creano formule DAX per il filtro incrociato in Power BI Desktop, usare il campo *UserPrincipalName*, che spesso corrisponde all'account di accesso di un utente, ad esempio <em>joe@contoso.com</em>, invece di *UserName*. Può quindi essere necessario creare una tabella correlata per il mapping di *UserName* o*EmployeeID* a *UserPrincipalName*.

Per altre informazioni e per esempi sul funzionamento del filtro incrociato bidirezionale, vedere il [white paper sul filtro incrociato bidirezionale per Power BI Desktop](https://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx).

