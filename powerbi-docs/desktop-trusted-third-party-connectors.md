---
title: Attendibili i connettori di terze parti in Power BI
description: Come rendere attendibile un connettore di terze parti firmato in Power BI
author: cpopell
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/3/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: 30b7457c6149320c43f24b967a842382821b01b1
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65607787"
---
# <a name="trusting-third-party-connectors"></a>Concessione dell'attendibilità i connettori di terze parti

## <a name="why-do-you-need-trusted-third-party-connectors"></a>Il motivo per cui occorre connettori di terze parti attendibili?

In Power BI, è generalmente consigliabile mantenere a livello di 'sicurezza estensione dati' a un livello superiore, che impedisce il caricamento di codice non certificate da Microsoft. Tuttavia, potrebbero esserci molti i casi in cui si desidera caricare connettori specifici: quelli che già scritto o quelli forniti da un consulente o un fornitore all'esterno del percorso di certificazione Microsoft.

Lo sviluppatore di un determinato oggetto connector possibile firmarla con un certificato e fornire le informazioni necessarie per caricarlo in modo sicuro senza riduzione delle impostazioni di sicurezza.

Se si desidera ottenere maggiori informazioni sulle impostazioni di sicurezza, è possibile leggere riguardo [qui](https://docs.microsoft.com/power-bi/desktop-connector-extensibility).

## <a name="using-the-registry-to-trust-third-party-connectors"></a>Usando il Registro di sistema di considerare attendibili i connettori di terze parti

Concessione dell'attendibilità connettori di terze parti in Power BI avviene elencando l'identificazione personale del certificato che si desidera considerare attendibile un valore del Registro di sistema. Se questa identificazione personale corrisponda all'identificazione personale del certificato da caricare nel connettore, sarà in grado di caricarla nel livello di protezione 'Consigliati' di Power BI. 

Il percorso del Registro di sistema è HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Power BI Desktop. Assicurarsi che il percorso esista o crearla. Abbiamo scelto questo percorso a causa del principalmente controllati da criteri IT, nonché che richiedono accesso di amministrazione di computer locale da modificare. 

![Registro di sistema di Power BI Desktop senza chiavi di terze parti attendibili impostare](media/desktop-trusted-third-party-connectors/desktoptrustedthird1.png)

Aggiungere un nuovo valore nel percorso specificato in precedenza. Il tipo deve essere "Valore multistringa" (REG_MULTI_SZ) e deve essere chiamato "TrustedCertificateThumbprints" 

![Registro di sistema di Power BI Desktop con una voce per i connettori di terze parti attendibili ma non contiene chiavi](media/desktop-trusted-third-party-connectors/desktoptrustedthird2.png)

Aggiungere le identificazioni personali dei certificati di cui che si vuole considerare attendibili. È possibile aggiungere più certificati usando "\0" come un delimitatore o nell'editor del Registro di sistema, a destra fare clic su -> modificare e inserire ogni identificazione personale in una nuova riga. Identificazione personale di esempio viene eseguita da un certificato autofirmato. 

 ![Registro di sistema di Power BI Desktop con un set di chiavi di terze parti attendibile](media/desktop-trusted-third-party-connectors/desktoptrustedthird3.png)

Se è stata seguita correttamente le istruzioni e viene fornito l'identificazione personale corretta per lo sviluppatore, dovrebbe ora essere in grado di attendibilità in modo sicuro i connettori firmati con il certificato associato.

## <a name="how-to-sign-connectors"></a>Come firmare i connettori

Se si dispone di un connettore è o uno sviluppatore devi accedere, è possibile leggere informazioni nella documentazione di Power Query [qui](https://docs.microsoft.com/power-query/handlingconnectorsigning).
