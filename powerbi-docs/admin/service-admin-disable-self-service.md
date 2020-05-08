---
title: Abilitare o disabilitare l'iscrizione e l'acquisto in modalità self-service
description: Informazioni per gli amministratori per disattivare la possibilità per gli utenti di iscriversi a Power BI e acquistare una licenza.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/08/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 561d8b6cd0e17e885ced984315a04376400a2a58
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "81447511"
---
# <a name="enable-or-disable-self-service-sign-up-and-purchasing"></a>Abilitare o disabilitare l'iscrizione e l'acquisto in modalità self-service

Nella maggior parte delle organizzazioni l'iscrizione in modalità self-service è abilitata per impostazione predefinita. I singoli utenti dell'organizzazione possono iscriversi per Power BI usando il proprio account aziendale o dell'istituto di istruzione. È anche possibile offrire agli utenti la possibilità di acquistare direttamente una licenza di Power BI Pro se tentano di usare una funzionalità che richiede la versione Pro. L'amministratore ha la facoltà di decidere se abilitare o disabilitare l'iscrizione in modalità self-service. Può anche controllare se gli utenti dell'organizzazione possono effettuare acquisti in modalità self-service per ottenere la propria licenza.

> [!NOTE]
>Se Power BI è stato acquistato tramite un provider di soluzioni cloud (CSP) Microsoft, l'impostazione potrebbe essere disabilitata per impedire agli utenti di iscriversi singolarmente. Il CSP può anche fungere da amministratore globale dell'organizzazione e in questo caso sarà necessario contattarlo per modificare questa impostazione.
>
>

Per modificare le impostazioni che controllano l'iscrizione e l'acquisto in modalità self-service si usano comandi di PowerShell. Sono disponibili due impostazioni che controllano se gli utenti dell'organizzazione possono eseguire l'iscrizione in modalità self-service o effettuare acquisti in modalità self-service.

- Per disabilitare tutte le iscrizioni in modalità self-service, modificare un'impostazione in Azure Active Directory denominata **AllowAdHocSubscriptions** usando i comandi di PowerShell per Azure AD. Eseguire la procedura descritta in questo articolo per [abilitare o disabilitare l'iscrizione in modalità self-service](#enable-or-disable-self-service-signup). Questa opzione disattiva l'iscrizione in modalità self-service per *tutti* i servizi e le app basati sul cloud Microsoft.

- Se si vuole impedire agli utenti di acquistare una propria licenza Pro, modificare l'impostazione **AllowSelfServicePurchase** usando i comandi di PowerShell per MSCommerce. Questa impostazione consente di disattivare l'acquisto in modalità self-service per prodotti specifici. Eseguire la procedura descritta in questo articolo per [abilitare o disabilitare l'acquisto in modalità self-service di licenze di Power BI Pro](#enable-or-disable-self-service-purchase).

## <a name="enable-or-disable-self-service-signup"></a>Abilitare o disabilitare l'iscrizione in modalità self-service

Se l'iscrizione in modalità self-service è abilitata, il valore di **AllowAdHocSubscriptions** è *true*. L'elenco seguente indica le conseguenze dell'impostazione di questo valore su *false*:

- Se si modifica l'impostazione da true a false, ai nuovi utenti dell'organizzazione viene impedito di eseguire l'iscrizione singolarmente. Tutti gli utenti che si sono iscritti a Power BI prima di modificare l'impostazione conservano le licenze.

- Se si imposta il valore su false, gli utenti che hanno già una licenza di Power BI (gratuito) possono comunque iscriversi per una singola versione di valutazione di Power BI Pro.

- Un amministratore deve assegnare tutte le licenze di Power BI ai nuovi utenti che ne hanno bisogno.

### <a name="before-you-begin"></a>Prima di iniziare

Questa procedura usa comandi di PowerShell per Azure Active Directory per modificare il valore dell'impostazione **AllowAdHocSubscriptions**. Questi comandi sono disponibili solo se è installato il modulo Azure AD di PowerShell. Per altre informazioni sull'uso di PowerShell, vedere [Introduzione a Windows PowerShell](https://docs.microsoft.com/powershell/scripting/getting-started/getting-started-with-windows-powershell?view=powershell-7).

Per installare il modulo Azure AD, avviare Windows PowerShell come amministratore. Assicurarsi che i criteri di esecuzione locale consentano di eseguire gli script. Se si verificano problemi, vedere [Criteri di esecuzione di PowerShell](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7#powershell-execution-policies) per informazioni su come modificare i criteri locali.

Eseguire il comando seguente per installare il modulo Azure AD:

```powershell
Install-Module MSOnline
```

### <a name="change-the-self-service-signup-policy"></a>Modificare i criteri di iscrizione in modalità self-service

In PowerShell eseguire il comando seguente per connettersi ad Azure AD:

```powershell
Connect-MsolService
```

Immettere le credenziali di amministratore nella finestra di dialogo di accesso, completando l'autenticazione a due fattori eventualmente richiesta. Dopo la verifica, viene visualizzata nuovamente la finestra di PowerShell.

Per visualizzare l'impostazione corrente, eseguire il comando seguente. L'output viene reindirizzato a un elenco formattato tramite l'opzione "fl".

```powershell
Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
```

Per modificare l'impostazione corrente, eseguire questo comando:

```powershell
Set-MsolCompanySettings -AllowAdHocSubscriptions $false
```

Dopo l'esecuzione di questo comando, l'iscrizione in modalità self-service è disabilitata per tutti gli utenti. Per riattivarla, eseguire di nuovo questo comando e impostare il valore su $true.

## <a name="enable-or-disable-self-service-purchase"></a>Abilitare o disabilitare l'acquisto in modalità self-service

Se l'acquisto in modalità self-service è abilitato, il valore di **AllowSelfServicePurchase** è *true*. L'elenco seguente indica le conseguenze dell'impostazione di questo valore su *false*:

- Se si modifica l'impostazione da true a false, agli utenti dell'organizzazione viene impedito di acquistare la propria licenza di Power BI Pro. Tutti gli utenti che hanno acquistato una licenza prima di modificare l'impostazione, la conservano.

- Se si imposta il valore su false, gli utenti che hanno una licenza di Power BI (gratuito) non possono ottenere una licenza di Power BI Pro individuale. 

- Un amministratore deve assegnare una licenza Pro a tutti gli utenti che ne hanno bisogno.

### <a name="before-you-begin"></a>Prima di iniziare

In questa procedura vengono usati i comandi di PowerShell per MSCommerce per modificare il valore dell'impostazione **AllowSelfServicePurchase**. Questi comandi sono disponibili solo se è installato il modulo MSCommerce di PowerShell. Per altre informazioni sull'uso di PowerShell, vedere [Introduzione a Windows PowerShell](https://docs.microsoft.com/powershell/scripting/getting-started/getting-started-with-windows-powershell?view=powershell-7).

Per installare il modulo MSCommerce, avviare Windows PowerShell come amministratore. Assicurarsi che i criteri di esecuzione locale consentano di eseguire gli script. Se si verificano problemi, vedere [Criteri di esecuzione di PowerShell](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7#powershell-execution-policies) per informazioni su come modificare i criteri locali.

Eseguire il comando seguente per installare il modulo MSCommerce:

```powershell
Install-Module -name MSCommerce
```

### <a name="change-the-self-service-signup-policy"></a>Modificare i criteri di iscrizione in modalità self-service

In PowerShell eseguire il comando seguente per connettersi:

```powershell
Connect-MSCommerce
```

Immettere le credenziali di amministratore nella finestra di dialogo di accesso, completando l'autenticazione a due fattori eventualmente richiesta. Dopo la verifica, la finestra di PowerShell mostra una connessione riuscita.

Per visualizzare l'impostazione corrente, eseguire il comando seguente. Per impedire il troncamento del testo, l'output viene reindirizzato a un elenco formattato tramite l'opzione "fl".

```powershell
Get-MSCommercePolicy -PolicyId AllowSelfServicePurchase | fl
```

È possibile disabilitare l'impostazione che consente l'acquisto in modalità self-service per un singolo prodotto specificando il relativo **ProductId**. Per modificare l'impostazione corrente per il servizio Power BI, eseguire questo comando:

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0L3PB -Enabled $False
```

Dopo aver eseguito questo comando, l'acquisto in modalità self-service per Power BI è disabilitato per tutti gli utenti. Per riattivarlo, eseguire di nuovo questo comando e impostare il valore su $true.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sull'acquisto in modalità self-service in Power BI e nel resto di Power Platform, vedere questi articoli:

- [Domande frequenti sugli acquisti in modalità self-service](https://docs.microsoft.com/microsoft-365/commerce/subscriptions/self-service-purchase-faq?view=o365-worldwide#admin-capabilities)
- [Usare AllowSelfServicePurchase per il modulo MSCommerce di PowerShell](https://docs.microsoft.com/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell?view=o365-worldwide)
