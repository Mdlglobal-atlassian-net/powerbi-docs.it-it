---
title: Connettori di terze parti attendibili in Power BI
description: Informazioni su come considerare attendibile un connettore di terze parti firmato in Power BI
author: cpopell
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/3/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: 05db20b2f83f10409339fad949874fc1076a6b98
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83285970"
---
# <a name="trusted-third-party-connectors"></a>Connettori di terze parti attendibili

## <a name="why-do-you-need-trusted-third-party-connectors"></a>Perché sono necessari connettori di terze parti attendibili?

In Power BI è in genere consigliabile mantenere l'opzione relativa alla sicurezza dell'estensione per i dati impostata su un livello più elevato per impedire il caricamento del codice non certificato da Microsoft. In alcuni casi, però, può essere necessario caricare connettori specifici, ovvero quelli scritti personalmente o forniti da un consulente o da un fornitore privo di certificazione Microsoft.

Lo sviluppatore di un determinato connettore può firmarlo con un certificato e fornire le informazioni necessarie per caricarlo in modo sicuro senza che sia necessario ridurre le impostazioni di sicurezza.

Per altre informazioni sulle impostazioni di sicurezza, vedere [questo articolo](https://docs.microsoft.com/power-bi/desktop-connector-extensibility).

## <a name="using-the-registry-to-trust-third-party-connectors"></a>Uso del Registro di sistema per considerare attendibili i connettori di terze parti

Per verificare l'attendibilità dei connettori di terze parti in Power BI, è possibile indicare l'identificazione personale del certificato da considerare attendibile in un valore specificato del Registro di sistema. Se questa identificazione personale corrisponde a quella del certificato nel connettore che si vuole caricare, sarà possibile caricarlo nel livello di sicurezza consigliato di Power BI. 

Il percorso del Registro di sistema è HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Power BI Desktop. Assicurarsi che il percorso esista oppure crearlo. È stato scelto questo percorso perché viene controllato principalmente da criteri IT e perché per modificarlo richiede l'accesso come amministratore del computer locale. 

![Registro di sistema di Power BI Desktop senza chiavi di terze parti attendibili impostate](media/desktop-trusted-third-party-connectors/desktoptrustedthird1.png)

Aggiungere un nuovo valore nel percorso specificato in precedenza. Il tipo deve essere "Valore multistringa" (REG_MULTI_SZ) e il nome deve essere "TrustedCertificateThumbprints". 

![Registro di sistema di Power BI Desktop con una voce per i connettori di terze parti attendibili ma senza chiavi](media/desktop-trusted-third-party-connectors/desktoptrustedthird2.png)

Aggiungere le identificazioni personali dei certificati che si vuole considerare attendibili. È possibile aggiungere più certificati specificando "\0" come delimitatore. In alternativa, nell'editor del Registro di sistema fare clic con il pulsante destro del mouse e quindi modificare e inserire ogni identificazione personale su una nuova riga. L'identificazione personale di esempio è ottenuta da un certificato autofirmato. 

 ![Registro di sistema di Power BI Desktop con una chiave di terze parti attendibile impostata](media/desktop-trusted-third-party-connectors/desktoptrustedthird3.png)

Se sono state seguite correttamente le istruzioni e l'identificazione personale corretta è stata fornita dallo sviluppatore, dovrebbe essere possibile proteggere in modo sicuro i connettori firmati con il certificato associato.

## <a name="how-to-sign-connectors"></a>Come firmare i connettori

Per informazioni su come firmare un connettore, vedere [questo articolo](https://docs.microsoft.com/power-query/handlingconnectorsigning) nella documentazione di Power Query.
