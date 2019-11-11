---
title: Estendibilità dei connettori in Power BI
description: Funzionalità di estendibilità dei connettori, funzioni, impostazioni di sicurezza e connettori certificati
author: cpopell
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/22/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: e493e4a41e7b357a23677c1c50f654dbee51e0ca
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73878408"
---
# <a name="connector-extensibility-in-power-bi"></a>Estendibilità dei connettori in Power BI

In Power BI, i clienti e gli sviluppatori possono estendere le origini dati a cui si connettono in molti modi. Possono usare connettori esistenti e origini dati generiche (ad esempio ODBC, OData, OLEDB, Web, CSV, XML, JSON). In alternativa, gli sviluppatori possono creare estensioni per i dati, denominate **connettori personalizzati**, e trasformarle in **connettori certificati**.

È attualmente possibile attivare i **connettori personalizzati** usando un menu che consente di controllare in modo sicuro il livello di codice personalizzato che si vuole lasciar eseguire nel sistema. È possibile scegliere tutti i connettori personalizzati o solo quelli certificati e distribuiti da Microsoft nella finestra di dialogo **Recupera dati**.

## <a name="custom-connectors"></a>Connettori personalizzati

I **connettori personalizzati** possono includere un'ampia gamma di possibilità, che spazia dalle API di piccole dimensioni fondamentali per l'attività aziendale ai grandi servizi specifici del settore per i quali Microsoft non ha rilasciato un connettore. Molti connettori vengono distribuiti dal fornitore. Se è necessario un connettore di dati specifico, è necessario contattare il fornitore.

Per usare un **connettore personalizzato**, inserirlo nella cartella *\[Documenti]\\Power BI Desktop\\Connettori personalizzati* e modificare le impostazioni di sicurezza come descritto nella sezione seguente.

Non è necessario modificare le impostazioni di sicurezza per usare i **connettori certificati**.

## <a name="data-extension-security"></a>Sicurezza dell'estensione per i dati

Per modificare le impostazioni di sicurezza dell'estensione per i dati, in **Power BI Desktop** selezionare **File > Opzioni e impostazioni > Opzioni > Sicurezza**.

![Verificare se si desidera caricare i connettori personalizzati con le opzioni di sicurezza delle estensioni per i dati](media/desktop-connector-extensibility/data-extension-security-1.png)

In **Estensioni dati** è possibile selezionare uno dei due livelli di sicurezza:

* (Consigliato) per consentire solo il caricamento delle estensioni certificate
* (Non consigliato) per consentire il caricamento di tutte le estensioni senza avviso

Se si intende usare **connettori personalizzati** o connettori sviluppati personalmente o da terze parti, è necessario selezionare **"(Scelta non consigliata) Consenti in caricamento di qualsiasi estensione senza convalida o avviso"** . Questa impostazione di sicurezza non è consigliabile a meno che non si sia certi dell'assoluta attendibilità dei connettori personalizzati. Il codice in essi contenuto può infatti gestire le credenziali, ad esempio inviarle tramite HTTP, e ignorare i livelli di privacy.

Nell'impostazione di sicurezza **"(Scelta consigliata)"** , se nel sistema sono presenti connettori personalizzati, viene visualizzato l'errore "Il connettore seguente non è stato certificato e non è possibile verificarne la sicurezza d'uso" seguito da un elenco di connettori che non possono essere caricati in modo sicuro.

![Una finestra di dialogo descrive i connettori personalizzati che non possono essere caricati a causa delle impostazioni di sicurezza, in questo caso TripPin](media/desktop-connector-extensibility/data-extension-security-2.png)

Per risolvere il problema senza modificare le impostazioni di sicurezza, rimuovere i connettori non firmati dalla cartella "Connettori personalizzati".

Se invece li si vuole usare, modificare le impostazioni di sicurezza in **"(Scelta non consigliata) Consenti in caricamento di qualsiasi estensione senza convalida o avviso"** come descritto in precedenza. Riavviare **Power BI Desktop**.

## <a name="certified-connectors"></a>Connettori certificati

Un sottoinsieme limitato di estensioni per i dati viene considerato **Certificato**. Accedere ai connettori certificati nella finestra di dialogo **Recupera dati**. La manutenzione e il supporto del connettore sono responsabilità dello sviluppatore di terze parti che lo ha creato. Sebbene distribuisca questi connettori, Microsoft non è responsabile delle loro prestazioni o della loro continuità di funzionamento.

Per certificare un connettore personalizzato, è necessario che il fornitore contatti dataconnectors@microsoft.com.
