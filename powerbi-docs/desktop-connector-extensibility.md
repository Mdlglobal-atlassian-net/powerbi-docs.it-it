---
title: Estendibilità dei connettori in Power BI
description: Funzionalità di estendibilità dei connettori, funzioni, impostazioni di sicurezza e connettori certificati
author: cpopell
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/22/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: 16b96d91a9dd37fa8a502bbcca772438c703cb63
ms.sourcegitcommit: d88cc6a87d4ba82ad2c4d496a3634f927e4ac529
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/30/2019
ms.locfileid: "66412988"
---
# <a name="connector-extensibility-in-power-bi"></a>Estendibilità dei connettori in Power BI

In Power BI, i clienti e gli sviluppatori possono estendere le origini dati a cui si connettono in molti modi. Usano i connettori esistenti e origini dati generiche (ad esempio ODBC, OData, Oledb, Web, CSV, XML, JSON). In alternativa, gli sviluppatori di creano estensioni per i dati, dette **connettori personalizzati**e renderli **Certified connettori**.

Attualmente, si abilita **connettori personalizzati** tramite un menu che consente in modo sicuro controllare il livello di codice personalizzato che si desidera lasciare in esecuzione nel sistema. È possibile scegliere tutti i connettori personalizzati oppure solo i connettori certified e distribuiti da Microsoft nel **recupera dati** finestra di dialogo.

## <a name="custom-connectors"></a>Connettori personalizzati

**I connettori personalizzati** può includere un'ampia gamma di possibilità, che vanno dalle API di piccole dimensioni critiche per l'azienda, ai grandi servizi specifici del settore che Microsoft non ha rilasciato un connettore per. Molti connettori vengono distribuiti dal fornitore. Se si ha l'esigenza per un connettore dati specifici, è necessario contattare un fornitore.

Usare un **Custom Connector**, inserirlo nel  *\[documenti]\\Power BI Desktop\\i connettori personalizzati* cartella e modificare le impostazioni di sicurezza come descritto in la sezione seguente.

Non è necessario modificare le impostazioni di sicurezza per usare i **connettori certificati**.

## <a name="data-extension-security"></a>Sicurezza dell'estensione per i dati

Per modificare impostazioni di sicurezza di estensione dei dati, nella **Power BI Desktop** selezionate **File > Opzioni e impostazioni > Opzioni > sicurezza**.

![Controllare se si desidera caricare i connettori personalizzati con le opzioni di sicurezza di estensione dei dati](media/desktop-connector-extensibility/data-extension-security-1.png)

In **Estensioni dati** è possibile selezionare uno dei due livelli di sicurezza:

* (Consigliato) per consentire solo il caricamento delle estensioni certificate
* (Non consigliato) per consentire il caricamento di tutte le estensioni senza avviso

Se si prevede di usare **connettori personalizzati** o i connettori che è o terze parti hanno sviluppato, è necessario selezionare **"(Not Recommended) consentire qualsiasi estensione caricare senza alcun avviso"** . Questa impostazione di sicurezza non è consigliata a meno che non completamente attendibile i connettori personalizzati. Poiché il codice in questa posizione può gestire le credenziali, tra cui vengono inviati tramite HTTP e ignorare i livelli di privacy.

Nel **"(scelta consigliata)"** sicurezza impostazione, se sono presenti connettori personalizzati nel sistema, viene visualizzato un errore che descrive i connettori che non è possibile caricare a causa di sicurezza.

![Una finestra di dialogo vengono descritti i connettori personalizzati che non è possibile caricare a causa di impostazioni di sicurezza, in questo caso TripPin](media/desktop-connector-extensibility/data-extension-security-2.png)

Per risolvere l'errore e usare questi connettori, modificare le impostazioni di sicurezza per il **"(Not Recommended) consentire qualsiasi estensione caricare senza alcun avviso"** impostazione come descritto in precedenza. Quindi, riavviare **Power BI Desktop**.

## <a name="certified-connectors"></a>Connettori certificati

Un sottoinsieme limitato delle estensioni per i dati viene considerato **Certified**. Connettori di certificati di accesso di **recupera dati** finestra di dialogo. Tuttavia, lo sviluppatore di terze parti che ha creato il connettore è responsabile per la manutenzione e supporto. Mentre Microsoft distribuisce i connettori, non è responsabile per le prestazioni o una funzione costante.

Per certificare un connettore personalizzato, è necessario che il fornitore contatti dataconnectors@microsoft.com.
