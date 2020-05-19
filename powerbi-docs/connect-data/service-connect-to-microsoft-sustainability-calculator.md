---
title: Connettere Microsoft Sustainability Calculator
description: Microsoft Sustainability Calculator per Power BI
author: joshthor3222
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 01/06/2020
ms.author: v-tikid
LocalizationGroup: Connect to services
ms.openlocfilehash: 8ab3dbb500faf072b87ba398b16b820c164cdefa
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83337605"
---
# <a name="connect-the-microsoft-sustainability-calculator"></a>Connettere Microsoft Sustainability Calculator
È possibile ottenere dati analitici sulle emissioni di CO2 dell'infrastruttura IT per prendere decisioni più sostenibili riguardo all'elaborazione dei dati

Microsoft Sustainability Calculator offre nuove informazioni dettagliate sui dati relativi alle emissioni di CO2 associati ai servizi di Azure. I responsabili della creazione di report e della pianificazione della sostenibilità all'interno delle proprie organizzazioni possono ora quantificare l'impatto del carbonio di ogni sottoscrizione di Azure, nonché stimare l'entità della riduzione delle emissioni che si ottiene eseguendo tali carichi di lavoro in Azure piuttosto che nei data center locali. Questi dati possono essere usati per la segnalazione delle emissioni Scope 3 dei gas a effetto serra. L'accesso a Microsoft Sustainability Calculator richiede l'ID tenant e la chiave di accesso dell'utente, in genere messi a disposizione dall'amministratore di Azure dell'organizzazione.

Per usare questa app, sono necessarie informazioni reperibili in Azure Enterprise Portal. È possibile rivolgersi agli amministratori di sistema dell'organizzazione per ottenere tali informazioni. Prima di installare l'app, leggere queste istruzioni e ottenere le informazioni necessarie. 

Questa versione del connettore supporta solo le registrazioni Enterprise da [https://ea.azure.com](https://ea.azure.com/). Le registrazioni per la Cina non sono attualmente supportate.

## <a name="how-to-connect"></a>Come connettersi
[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]

1. Selezionare **Microsoft Sustainability Calculator** \> **Scarica adesso**.
1. In **Installare questa app di Power BI?** selezionare **Installa**.
1. Nel riquadro **App** selezionare **Microsoft Sustainability Calculator**.
1. In **Operazioni iniziali con la nuova app** selezionare **Connetti**.

    ![Operazioni iniziali con la nuova app](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

1. Immettere **nome della società, numero di registrazione utente** e **numero di mesi \> eseguire l'accesso.** Per informazioni dettagliate su [come trovare questi parametri](#finding-parameters), vedere più avanti.

    ![Registrazione della società](media/service-connect-to-microsoft-sustainability-calculator/company-enrollment.png)

1. Selezionare **Chiave** come **metodo di autenticazione** e **organizzazione** come livello di **privacy**.
1. Per **Chiave** immettere la propria **chiave di accesso \> e accedere**.

    ![Immissione della chiave di accesso](media/service-connect-to-microsoft-sustainability-calculator/access-key-entry.png)

1. Il processo di importazione inizia automaticamente. Al termine nel **riquadro di spostamento** vengono visualizzati un nuovo dashboard, un nuovo report e un nuovo modello. Selezionare il report per visualizzare i dati importati.

## <a name="finding-parameters"></a>Individuazione dei parametri

Per trovare l'**ID di registrazione** e la **chiave di accesso** della società, rivolgersi all'amministratore di Azure per ottenere le informazioni necessarie. L'amministratore

1. accede ad [Azure Enterprise Portal](https://ea.azure.com), fa clic su **Gestisci** sulla barra multifunzione a sinistra e ottiene il **numero di registrazione** come illustrato di seguito
2. da [Azure Enterprise Portal](https://ea.azure.com) fa clic su **Report** e quindi sulla chiave di accesso API, come illustrato di seguito per ottenere la chiave primaria dell'account di registrazione

## <a name="using-the-app"></a>Uso dell'app

Per aggiornare i parametri in qualsiasi momento, passare alle impostazioni del **set di dati**, accedere all'area di lavoro associata all'app e aggiornare ID tenant, nome della società o mesi di dati. Dopo aver applicato i parametri, fare clic su **Aggiorna** per ricaricare i dati con i nuovi parametri applicati.