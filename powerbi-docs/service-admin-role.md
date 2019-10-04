---
title: Informazioni sul ruolo di amministratore di Power BI
description: Questo articolo descrive il ruolo di amministratore del servizio Power BI e illustra come usarlo nell'organizzazione.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 8b4d2382f89c48f20767cf72bc0468589c366cfe
ms.sourcegitcommit: 02042995df12cc4e4b97eb8a369e62364eb5af36
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/25/2019
ms.locfileid: "71256427"
---
# <a name="understanding-the-power-bi-service-administrator-role"></a>Informazioni sul ruolo di amministratore del servizio Power BI

Informazioni su come usare il ruolo di amministratore del servizio Power BI nell'organizzazione. Gli utenti con questo ruolo hanno il controllo completo su un tenant di Power BI e sulle relative funzionalità di amministrazione, tranne che sulle licenze.

Il ruolo di amministratore del servizio Power BI può essere assegnato agli utenti che devono avere accesso al portale di amministrazione di Power BI, senza concedere a tali utenti l'accesso amministrativo completo per Office 365.

Gli amministratori della gestione utenti di Office 365 assegnano gli utenti al ruolo di amministratore del servizio Power BI nell'interfaccia di amministrazione di Microsoft 365 o tramite uno script di PowerShell. Gli utenti a cui viene assegnato questo ruolo possono accedere al [portale di amministrazione di Power BI](service-admin-portal.md). Lì hanno accesso alle metriche di utilizzo a livello di tenant e possono controllare l'utilizzo delle funzionalità di Power BI a livello di tenant.

## <a name="limitations-and-considerations"></a>Limitazioni e considerazioni

Il ruolo di amministratore del servizio Power BI non fornisce le funzionalità seguenti:

* Possibilità di modificare gli utenti e le licenze nell'interfaccia di amministrazione di Microsoft 365.

* Accesso ai log di controllo. Per altre informazioni, usare [Uso del controllo nell'organizzazione](service-admin-auditing.md).

## <a name="assign-users-to-the-admin-role-in-office-365"></a>Assegnare gli utenti al ruolo di amministratore in Office 365

Per assegnare utenti al ruolo di amministratore di Power BI nell'interfaccia di amministrazione di Microsoft 365, seguire questa procedura.

1. Nell'[interfaccia di amministrazione di Microsoft 365](https://portal.office.com/adminportal/home#/homepage) selezionare **Utenti** > **Utenti attivi**.

    ![Interfaccia di amministrazione di Microsoft 365](media/service-admin-role/powerbi-admin-users.png)

1. Selezionare l'utente a cui si vuole assegnare il ruolo.

1. In **Ruoli** selezionare **Modifica**.

    ![Modificare i ruoli](media/service-admin-role/powerbi-admin-edit-roles.png)

1. Selezionare **Amministratore personalizzato** > **Amministratore del servizio Power BI**.

    ![Amministratore del servizio Power BI](media/service-admin-role/powerbi-admin-role.png)

1. Selezionare **Salva**, quindi **Chiudi**.

Per il ruolo di quell'utente dovrebbe risultare **Amministratore del servizio Power BI**.

![Ruoli](media/service-admin-role/powerbi-admin-role-set.png)

## <a name="assign-users-to-the-admin-role-with-powershell"></a>Assegnare gli utenti al ruolo di amministratore con PowerShell

È anche possibile assegnare utenti ai ruoli usando PowerShell. Gli utenti vengono gestiti in Azure Active Directory (Azure AD). Se non si ha già il modulo Azure AD PowerShell, [scaricare e installare la versione più recente](https://www.powershellgallery.com/packages/AzureAD/).

1. In primo luogo connettersi ad Azure AD:
   ```
   PS C:\Windows\system32> Connect-AzureAD
   ```

1. Quindi ottenere il valore **ObjectId** per il ruolo **Amministratore del servizio Power BI**. È possibile eseguire [Get-AzureADDirectoryRole](/powershell/module/azuread/get-azureaddirectoryrole) per ottenere il valore **ObjectId**.

    ```
    PS C:\Windows\system32> Get-AzureADDirectoryRole

    ObjectId                             DisplayName                        Description
    --------                             -----------                        -----------
    00f79122-c45d-436d-8d4a-2c0c6ca246bf Power BI Service Administrator     Full access in the Power BI Service.
    250d1222-4bc0-4b4b-8466-5d5765d14af9 Helpdesk Administrator             Helpdesk Administrator has access to perform..
    3ddec257-efdc-423d-9d24-b7cf29e0c86b Directory Synchronization Accounts Directory Synchronization Accounts
    50daa576-896c-4bf3-a84e-1d9d1875c7a7 Company Administrator              Company Administrator role has full access t..
    6a452384-6eb9-4793-8782-f4e7313b4dfd Device Administrators              Device Administrators
    9900b7db-35d9-4e56-a8e3-c5026cac3a11 AdHoc License Administrator        Allows access manage AdHoc license.
    a3631cce-16ce-47a3-bbe1-79b9774a0570 Directory Readers                  Allows access to various read only tasks in ..
    f727e2f3-0829-41a7-8c5c-5af83c37f57b Email Verified User Creator        Allows creation of new email verified users.
    ```

    In questo caso, il valore **ObjectId** del ruolo è 00f79122-c45d-436d-8d4a-2c0c6ca246bf.

1. Ottenere quindi il valore **ObjectId** dell'utente. Per trovarlo, eseguire [Get-AzureADUser](/powershell/module/azuread/get-azureaduser).

    ```
    PS C:\Windows\system32> Get-AzureADUser -ObjectId 'tim@contoso.com'

    ObjectId                             DisplayName UserPrincipalName      UserType
    --------                             ----------- -----------------      --------
    6a2bfca2-98ba-413a-be61-6e4bbb8b8a4c Tim         tim@contoso.com        Member
    ```

1. Per aggiungere il membro al ruolo, eseguire [Add-AzureADDirectoryRoleMember](/powershell/module/azuread/add-azureaddirectoryrolemember).

    | Parametro | Descrizione |
    | --- | --- |
    | ObjectId |ID oggetto del ruolo. |
    | RefObjectId |ID oggetto dei membri. |

    ```powershell
    Add-AzureADDirectoryRoleMember -ObjectId 00f79122-c45d-436d-8d4a-2c0c6ca246bf -RefObjectId 6a2bfca2-98ba-413a-be61-6e4bbb8b8a4c
    ```

## <a name="next-steps"></a>Passaggi successivi

[Amministrazione di Power BI nell'organizzazione](service-admin-administering-power-bi-in-your-organization.md)  
[Portale di amministrazione di Power BI](service-admin-portal.md)  

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)