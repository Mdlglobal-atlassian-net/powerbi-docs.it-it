---
title: Estendibilità dei connettori in Power BI
description: Funzionalità di estendibilità dei connettori, funzioni, impostazioni di sicurezza e connettori certificati
author: cpopell
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/02/2020
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: b604ade56335e65b25501eb9fe3d3c2fd185a6f0
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "75761399"
---
# <a name="connector-extensibility-in-power-bi"></a>Estendibilità dei connettori in Power BI

Power BI può connettersi ai dati usando connettori esistenti e origini dati generiche, come ODBC, OData, OLE DB, Web, CSV, XML e JSON. In alternativa, gli sviluppatori possono abilitare nuove origini dati con estensioni per i dati personalizzate dette *connettori personalizzati*. Alcuni connettori personalizzati sono certificati e distribuiti da Microsoft come *connettori certificati*.

Per usare connettori personalizzati non certificati sviluppati autonomamente o da terze parti, è necessario modificare le impostazioni di sicurezza di Power BI Desktop per consentire il caricamento delle estensioni senza convalida o avviso. Poiché questo codice può gestire le credenziali, incluso l'invio su HTTP, e ignorare i livelli di privacy, usare questa impostazione di sicurezza solo se i connettori personalizzati sono completamente attendibili.

Un'altra opzione possibile è che lo sviluppatore firmi il connettore con un certificato e fornisca all'utente le informazioni necessarie per usarlo senza modificare le impostazioni di sicurezza. Per altre informazioni, vedere [Informazioni sui connettori di terze parti attendibili](desktop-trusted-third-party-connectors.md).

## <a name="custom-connectors"></a>Connettori personalizzati

I connettori personalizzati non certificati possono spaziare dalle API business-critical di piccole dimensioni ai grandi servizi specifici del settore per i quali Microsoft non ha rilasciato un connettore. Molti connettori vengono distribuiti dai fornitori. Se serve un connettore dati specifico, contattare il fornitore. 

Per usare un connettore personalizzato non certificato, inserire il file del connettore con estensione *pq*, *pqx*, *m* o *mez* nella cartella *\[Documenti]\\Power BI Desktop\\Custom Connectors*. Se la cartella non esiste, crearla.

Modificare le impostazioni di sicurezza dell'estensione per i dati come segue:

In Power BI Desktop selezionare **File** > **Opzioni e impostazioni** > **Opzioni** > **Sicurezza**.

In **Estensioni dati** selezionare **(Scelta non consigliata) Consenti il caricamento di qualsiasi estensione senza convalida o avviso**. Scegliere **OK** e riavviare Power BI Desktop. 

![Consentire i connettori personalizzati non certificati nelle opzioni di sicurezza delle estensioni per i dati](media/desktop-connector-extensibility/data-extension-security-1.png)

L'impostazione predefinita di sicurezza delle estensioni per i dati di Power BI Desktop è **(Scelta consigliata) Consenti il caricamento solo di estensioni certificate Microsoft e altre estensioni attendibili di terze parti**. Con questa impostazione, se nel sistema sono presenti connettori personalizzati non certificati, all'avvio di Power BI Desktop viene visualizzata la finestra di dialogo **Connettori non certificati**, che elenca i connettori che non possono essere caricati in modo sicuro.

![Finestra di dialogo Connettori non certificati](media/desktop-connector-extensibility/data-extension-security-2.png)

Per risolvere l'errore, è possibile modificare l'impostazione di sicurezza **Estensioni dati** oppure rimuovere i connettori non certificati dalla cartella *Custom Connectors*.

## <a name="certified-connectors"></a>Connettori certificati

Viene considerato *certificato* solo un sottoinsieme limitato di estensioni per i dati. Sebbene distribuisca questi connettori, Microsoft non è responsabile delle loro prestazioni o della loro continuità di funzionamento. La manutenzione e il supporto del connettore sono responsabilità dello sviluppatore di terze parti che lo ha creato. 

In Power BI Desktop i connettori certificati di terze parti sono visualizzati nell'elenco della finestra di dialogo **Recupera dati**, insieme ai connettori generici e comuni. Non è necessario modificare le impostazioni di sicurezza per usare i connettori certificati.

Per certificare un connettore personalizzato, chiedere al fornitore di contattare dataconnectors@microsoft.com.
