---
title: Esperienze dei pacchetti di contenuto modello in Power BI
description: Esperienze dei pacchetti di contenuto modello
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/09/2017
ms.author: maggies
ms.openlocfilehash: f1010557bdd781fac9542c2636424e7e2bef2c26
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54288268"
---
# <a name="template-content-pack-experiences-in-power-bi"></a>Esperienze dei pacchetti di contenuto modello in Power BI
Questa sezione descrive l'esperienza tipica di un utente che effettua la connessione a un [pacchetto di contenuto](service-connect-to-services.md) ISV.

Provare l'esperienza di connessione effettuando la connessione a un pacchetto di contenuto rilasciato in https://app.powerbi.com/getdata/services (ad esempio il [pacchetto di contenuto GitHub](https://app.powerbi.com/getdata/services/github) descritto di seguito).

## <a name="connect"></a>Connetti
Per iniziare, l'utente cerca il pacchetto di contenuto a cui connettersi nella raccolta di pacchetti di contenuto. La voce del pacchetto di contenuto fornisce un nome, un'icona e un testo descrittivo con maggiori informazioni per l'utente.

![connessione](media/template-content-pack-experience/github_data.png)

![connessione](media/template-content-pack-experience/github_connect.png)

## <a name="parameters"></a>Parametri
Dopo aver effettuato la selezione, all'utente verrà richiesto di specificare i parametri (se necessari). La finestra di dialogo Parametri viene fornita in modo dichiarativo dall'autore durante la creazione del pacchetto di contenuto.

Attualmente l'interfaccia utente dei parametri è molto semplice: non è possibile enumerare gli elenchi a discesa e la convalida dell'input di dati è vincolata alle espressioni regolari.

![parametri](media/template-content-pack-experience/github_params.png)

## <a name="credentials"></a>Credenziali
Dopo l'immissione dei parametri, all'utente verrà richiesto di accedere.  Se l'origine supporta più tipi di autenticazione, l'utente sceglierà l'opzione appropriata. Se l'origine richiede OAuth, l'interfaccia utente di accesso del servizio viene visualizzata quando l'utente preme Accedi.  In caso contrario, l'utente può immettere le proprie credenziali nella finestra di dialogo.

![Credenziali](media/template-content-pack-experience/github_login.png)

![connessione](media/template-content-pack-experience/github_creds2.png)

## <a name="instantiation"></a>Creazione di istanze
Dopo la corretta esecuzione dell'accesso, gli elementi inclusi nel pacchetto di contenuto, cioè modello, report e dashboard, vengono visualizzati nella barra di navigazione.  Questi elementi vengono aggiunti all'account di ciascun utente.  I dati vengono caricati in modo asincrono per popolare il set di dati (modello).  L'utente riuscirà quindi a utilizzare il dashboard, il report e il modello.

Per impostazione predefinita, viene configurata una pianificazione giornaliera dell'aggiornamento per l'utente, che rivaluterà le query nel modello.  Le credenziali fornite all'utente devono consentire l'aggiornamento dei dati senza che l'utente sia presente.

![Creazione di istanze](media/template-content-pack-experience/github_dashboard.png)

## <a name="exploration-and-monitoring"></a>Esplorazione e monitoraggio
Quando il pacchetto di contenuto viene nell'account dell'utente, è possibile esplorare e monitorare i dati o le informazioni,

che in genere includono:

* Visualizzazione e personalizzazione del dashboard.
* Visualizzazione e personalizzazione del report.
* Uso del linguaggio naturale per porre domande sui dati
* Uso dell'area di disegno per esplorare i dati nel modello di dati

È necessario valutare la possibilità di fornire strumenti di modellazione del linguaggio naturale (sinonimi) e uno schema di modello comprensibile per migliorare le esperienze di esplorazione.

