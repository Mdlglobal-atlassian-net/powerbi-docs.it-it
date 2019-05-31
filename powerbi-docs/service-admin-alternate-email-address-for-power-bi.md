---
title: Usare un indirizzo e-mail alternativo
description: Usare un indirizzo e-mail alternativo
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/23/2019
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 88432f55fc8cfeefa07b66ea68437bbb23f12531
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "64906631"
---
# <a name="use-an-alternate-email-address"></a>Usare un indirizzo e-mail alternativo

Quando si effettua l'iscrizione per Power BI, si specifica un indirizzo di posta elettronica. Per impostazione predefinita, Power BI usa questo indirizzo per inviare aggiornamenti sull'attività nel servizio, ad esempio per inviare gli inviti di condivisione.

In alcuni casi, potrebbe essere necessario recapitare questi messaggi a un indirizzo di posta elettronica diverso da quello con cui è stata effettuata l'iscrizione. Questo articolo illustra come specificare un indirizzo alternativo in Office 365 e in PowerShell. L'articolo spiega anche come Azure Active Directory (Azure AD) si risolve un indirizzo di posta elettronica.

> [!NOTE]
> Specificare un indirizzo alternativo, non influisce sull'indirizzo di posta elettronica usato da Power BI per aggiornamenti del servizio, newsletter e altre comunicazioni promozionali. Le comunicazioni vengono inviate sempre all'indirizzo di posta elettronica usato durante l'iscrizione a Power BI.

## <a name="use-office-365"></a>Usare Office 365

Per specificare un indirizzo alternativo in Office 365, seguire questa procedura.

1. Aprire la [pagina delle informazioni personali di Office 365](https://portal.office.com/account/#personalinfo). Se l'app viene richiesto, accedere con l'indirizzo di posta elettronica e la password usati per Power BI.

1. Nel menu di sinistra selezionare **Info personali**.

1. Nella sezione **Dettagli contatto** selezionare **Modifica**.

    Se non è possibile modificare i dettagli, ciò significa che l'amministratore di Office 365 gestisce l'indirizzo di posta elettronica. Contattare l'amministratore per aggiornare l'indirizzo di posta elettronica.

    ![Dettagli contatto](media/service-admin-alternate-email-address-for-power-bi/contact-details.png)

1. Nel **indirizzo email alternativo** immettere l'indirizzo di posta elettronica si potrebbe, ad esempio Office 365 per gli aggiornamenti di Power BI.

## <a name="use-powershell"></a>Usare PowerShell

Per specificare un indirizzo alternativo in PowerShell, usare il comando [Set-AzureADUser](/powershell/module/azuread/set-azureaduser/).

```powershell
Set-AzureADUser -ObjectId john@contoso.com -OtherMails "otheremail@somedomain.com"
```

## <a name="email-address-resolution-in-azure-ad"></a>Risoluzione degli indirizzi di posta elettronica in Azure AD

Per acquisire un'istanza di Azure AD token di incorporamento per Power BI, è possibile usare uno dei tre tipi diversi di indirizzi di posta elettronica:

* L'indirizzo di posta elettronica principale associato con account Azure AD dell'utente

* L'indirizzo di posta elettronica UPN (UserPrincipalName)

* L'attributo della matrice dell'*altro indirizzo di posta*

Power BI seleziona l'indirizzo di posta elettronica da usare in base alla sequenza seguente:

1. Se l'attributo relativo alla posta elettronica è presente nell'oggetto utente di Azure AD, Power BI usa questo attributo per l'indirizzo di posta elettronica.

1. Se l'indirizzo di posta elettronica UPN *non* è un indirizzo di posta elettronica di un dominio **\*.onmicrosoft.com** (l'informazione dopo il simbolo "\@"), Power BI usa questo attributo per l'indirizzo di posta elettronica.

1. Se il *altro indirizzo di posta elettronica* attributo della matrice nell'oggetto utente di Azure AD è presente, in Power BI Usa il primo messaggio di posta elettronica in tale elenco (poiché può esserci un elenco di messaggi di posta elettronica in questo attributo).

1. Se nessuna delle condizioni precedenti sono presente, Power BI Usa l'indirizzo UPN.

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)