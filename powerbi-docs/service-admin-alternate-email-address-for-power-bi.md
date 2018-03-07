---
title: Uso di un indirizzo di posta elettronica alternativo
description: Uso di un indirizzo di posta elettronica alternativo
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 08/09/2017
ms.author: maghan
LocalizationGroup: Troubleshooting
ms.openlocfilehash: c97f60e39d68060c8eb3396bac4eb7725dab9c86
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/24/2018
---
# <a name="using-an-alternate-email-address"></a>Uso di un indirizzo di posta elettronica alternativo
Per impostazione predefinita, l'indirizzo di posta elettronica con cui è stata effettuata l'iscrizione a Power BI viene usato per inviare aggiornamenti sulle attività in Power BI,  ad esempio per inviare gli inviti di condivisione.

In alcuni casi si preferisce che questi messaggi vengano inviati a un indirizzo di posta elettronica alternativo, diverso da quello usato per l'iscrizione a Power BI.

## <a name="updating-through-office-365-personal-info-page"></a>Aggiornamento tramite la pagina delle informazioni personali di Office 365
1. Passare alla [pagina delle informazioni personali di Office 365](https://portal.office.com/account/#personalinfo).  Se richiesto, accedere con l'indirizzo di posta elettronica e la password usati per Power BI.
2. Fare clic sul collegamento Modifica nella sezione Dettagli contatto.  
   
   > [!NOTE]
   > Se il collegamento Modifica non è presente, l'indirizzo di posta elettronica viene gestito dall'amministratore di Office 365 ed è necessario contattare questa figura per aggiornare l'indirizzo.
   > 
   > 
   
   ![](media/service-admin-alternate-email-address-for-power-bi/contact-details.png)
3. Nel campo Indirizzo di posta elettronica alternativo immettere l'indirizzo di posta cui verranno inviati gli aggiornamenti di Power BI.

> [!NOTE]
> La modifica di questa impostazione non influisce sull'indirizzo di posta elettronica usato per inviare aggiornamenti del servizio, newsletter e altre comunicazioni di carattere promozionale.  Questi messaggi verranno sempre inviati all'indirizzo usato in origine durante la registrazione a Power BI.
> 
> 

## <a name="updating-with-powershell"></a>Aggiornamento con PowerShell
È possibile aggiornare l'indirizzo di posta elettronica alternativo tramite PowerShell per Azure Active Directory. Per questa operazione, eseguire il comando [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser).

```
Set-AzureADUser -ObjectId john@contoso.com -OtherMails "otheremail@somedomain.com"
```

Per altre informazioni, vedere [Azure Active Directory PowerShell Version 2](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2) (Azure Active Directory PowerShell versione 2).

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

