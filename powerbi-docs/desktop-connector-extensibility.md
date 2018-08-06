---
title: Estendibilità dei connettori in Power BI
description: Funzionalità di estendibilità dei connettori, funzioni, impostazioni di sicurezza e connettori certificati
author: cpopell
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 07/25/2018
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: c63357df043ff6a646562d398a07d8042dd5a0ee
ms.sourcegitcommit: 7fb0b68203877ff01f29724f0d1761d023075445
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/26/2018
ms.locfileid: "39256570"
---
# <a name="connector-extensibility-in-power-bi"></a>Estendibilità dei connettori in Power BI

In Power BI i clienti e gli sviluppatori possono estendere le origini dati a cui è possibile connettersi in modi diversi, ad esempio usando i connettori esistenti e le origini dati generiche (ODBC, OData, Oledb, Web, CSV, XML, JSON). In aggiunta a queste origini dati, gli sviluppatori possono creare estensioni dati chiamate **connettori personalizzati** e certificare un connettore per renderle **connettori certificati**.

Nelle versioni precedenti di Power BI l'uso dei **connettori personalizzati** veniva abilitato tramite un interruttore. È ora disponibile un menu che consente di controllare in modo sicuro il livello del codice personalizzato di cui si vuole autorizzare l'esecuzione nel sistema: tutti i connettori personalizzati oppure solo i connettori certificati e distribuiti da Microsoft nella finestra di dialogo **Dati**.

## <a name="custom-connectors"></a>Connettori personalizzati

I **connettori personalizzati** possono includere un'ampia gamma di possibilità: dalle API di piccole dimensioni fondamentali per l'attività aziendale ai servizi specifici del settore di grandi dimensioni non implementati da Microsoft. La maggior parte dei connettori di questo tipo viene distribuita dai fornitori stessi. Se è necessario un connettore dati specifico, contattare il fornitore.

Per usare un **connettore personalizzato**, inserirlo nella cartella *\[Documenti]\\Power BI Desktop\\Connettori personalizzati* e modificare le impostazioni di sicurezza come descritto nella sezione seguente.

Non è necessario modificare le impostazioni di sicurezza per usare i **connettori certificati**.

## <a name="data-extension-security"></a>Sicurezza dell'estensione per i dati

Per modificare le impostazioni di sicurezza dell'estensione per i dati, in **Power BI Desktop** selezionare **File > Opzioni e impostazioni > Opzioni > Sicurezza**.

![Controllare il caricamento dei connettori personalizzati con le opzioni di sicurezza delle estensioni per i dati](media/desktop-connector-extensibility/data-extension-security-1.png)

In **Estensioni dati** è possibile selezionare uno dei due livelli di sicurezza:

* (Consigliato) per consentire solo il caricamento delle estensioni certificate
* (Non consigliato) per consentire il caricamento di tutte le estensioni senza avviso

Se si prevede di usare **connettori personalizzati** o connettori sviluppati o distribuiti personalmente o da terze parti, è necessario selezionare **(Non consigliato)** per consentire il caricamento di tutte le estensioni senza avviso. Questa impostazione di sicurezza non è consigliabile a meno che non si preveda di eseguire **connettori personalizzati**.

Se sono presenti connettori personalizzati nel sistema, nell'impostazione di sicurezza **(Consigliato)** viene visualizzato un errore che descrive i connettori che non possono essere caricati a causa delle impostazioni di sicurezza.

![Una finestra di dialogo descrive i connettori personalizzati che non possono essere caricati a causa delle impostazioni di sicurezza, in questo caso TripPin](media/desktop-connector-extensibility/data-extension-security-2.png)

Per risolvere l'errore e usare i connettori, è necessario modificare le impostazioni di sicurezza impostandole su **(Non consigliato)** come descritto in precedenza e quindi riavviare **Power BI Desktop**.

## <a name="certified-connectors"></a>Connettori certificati

Sebbene un subset limitato di estensioni per i dati sia **Certificato** e questi connettori certificati siano disponibili nella finestra di dialogo **Dati**, la parte responsabile della manutenzione e del supporto rimane lo sviluppatore di terze parti che ha creato il connettore. Sebbene distribuisca questi connettori, Microsoft non è responsabile delle loro prestazioni o della loro continuità di funzionamento.

Per certificare un connettore personalizzato, è necessario che il fornitore contatti Microsoft.
