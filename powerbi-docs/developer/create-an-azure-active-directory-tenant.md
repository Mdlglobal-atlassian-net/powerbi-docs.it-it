---
title: Creare un tenant di Azure Active Directory da usare con Power BI
description: Informazioni su come creare un nuovo tenant di Azure Active Directory (Azure AD) da usare con l'applicazione personalizzata tramite le API REST di Power BI.
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
ms.date: 11/30/2017
ms.author: mihart
ms.openlocfilehash: 0e5df07ab3690b88c2fcf6673db44f8f79b1817d
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/30/2018
---
# <a name="create-an-azure-active-directory-tenant-to-use-with-power-bi"></a>Creare un tenant di Azure Active Directory da usare con Power BI
Informazioni su come creare un nuovo tenant di Azure Active Directory (Azure AD) da usare con l'applicazione personalizzata tramite le API REST di Power BI.

Un tenant rappresenta un'organizzazione in Azure Active Directory. È un'istanza dedicata del servizio Azure AD ricevuto e posseduto da un'organizzazione quando questa effettua l'iscrizione a un servizio cloud di Microsoft, ad esempio Azure, Microsoft Intune oppure Office 365. Ogni tenant di Azure AD è distinto e separato dagli altri tenant di Azure AD.

Dopo aver creato un tenant di Azure AD, è possibile definire un'applicazione e assegnare le autorizzazioni in modo che l'applicazione possa usare le API REST di Power BI.

È possibile che l'organizzazione disponga già di un tenant di Azure AD da usare per l'applicazione. È possibile usare tale tenant per le esigenze dell'applicazione oppure è possibile creare un nuovo tenant specifico per l'applicazione. In questo articolo viene descritto come creare un nuovo tenant.

## <a name="create-an-azure-active-directory-tenant"></a>Creare un tenant di Azure Active Directory
Per integrare Power BI nell'applicazione personalizzata, è necessario definire un'applicazione all'interno di Azure AD. A tale scopo, è necessario disporre di una directory all'interno di Azure AD, che sarà il tenant. Se l'organizzazione non dispone di un tenant, perché non usa Power BI oppure Office 365, [sarà necessario crearne uno](https://docs.microsoft.com/azure/active-directory/develop/active-directory-howto-tenant). È necessario crearne uno, se non si desidera che l'applicazione si combini con il tenant dell'organizzazione, per consentire all'utente di mantenere separato ciascun elemento.

In alternativa, è possibile creare un tenant a scopo di test.

Per creare un nuovo tenant di Azure AD, eseguire le operazioni seguenti.

1. Aprire il [portale di Azure](https://portal.azure.com) e accedere con un account che disponga di una sottoscrizione di Azure.
2. Selezionare l'**icona più (+)** e cercare *Azure Active Directory*.
   
    ![](media/create-an-azure-active-directory-tenant/new-directory.png)
3. Selezionare **Azure Active Directory** nei risultati della ricerca.
   
    ![](media/create-an-azure-active-directory-tenant/new-directory2.png)
4. Selezionare **Crea**.
5. Inserire un **nome per l'organizzazione** oltre al **nome di dominio iniziale**. Quindi selezionare **Crea** per creare la directory.
   
    ![](media/create-an-azure-active-directory-tenant/organization-and-domain.png)
   
   > [!NOTE]
   > Il dominio iniziale farà parte di onmicrosoft.com. È possibile aggiungere altri nomi di dominio in un secondo momento. È possibile che alla directory di un tenant siano stati assegnati più domini.
   > 
   > 
6. Dopo aver completato la creazione della directory, selezionare la casella di informazioni per gestire la nuova directory.

La directory è stata creata, ora è necessario aggiungere un utente al tenant.

## <a name="create-some-users-in-your-azure-active-directory-tenant"></a>Creare utenti nel tenant di Azure Active Directory
Ora che la directory è disponibile, è necessario creare almeno due utenti. Uno sarà amministratore globale del tenant e un altro sarà l'utente master per l'incorporamento. Basta immaginarlo come un account del servizio.

1. Nel portale di Azure assicurarsi di essere nel riquadro di Azure Active Directory.
   
    ![](media/create-an-azure-active-directory-tenant/aad-flyout.png)
   
    Altrimenti selezionare l'icona di Azure Active Directory nella barra dei servizi a sinistra.
   
    ![](media/create-an-azure-active-directory-tenant/aad-service.png)
2. In **Gestisci** selezionare **Utenti e gruppi**.
   
    ![](media/create-an-azure-active-directory-tenant/users-and-groups.png)
3. Selezionare **Tutti gli utenti** e quindi scegliere **+ Nuovo utente**.
4. Inserire un nome e il nome utente per questo utente. Questo sarà l'amministratore globale del tenant. È anche possibile modificare il **Ruolo della Directory** in *Amministratore globale*. È anche possibile visualizzare la password temporanea. Al termine, selezionare **Crea**.
   
    ![](media/create-an-azure-active-directory-tenant/global-admin.png)
5. È possibile eseguire nuovamente la stessa operazione per un utente normale nel tenant. Questa operazione può essere usata per l'account di incorporamento master . Questa volta, per **Ruolo della Directory** verrà lasciato *Utente*. Assicurarsi di annotare la password. Quindi selezionare **Crea**
   
    ![](media/create-an-azure-active-directory-tenant/pbiembed-user.png)
6. Iscriversi a Power BI con l'account utente creato nel passaggio 5. È possibile farlo aprendo la pagina [powerbi.com](https://powerbi.microsoft.com/get-started/) e selezionando **Provalo gratis** in *Power BI: Collaborazione e condivisione nel cloud*.
   
    ![](media/create-an-azure-active-directory-tenant/try-powerbi-free.png)
   
    Quando si effettua l'iscrizione, viene richiesto di provare Power BI Pro gratuitamente per 60 giorni. È possibile scegliere questa opzione per diventare un utente pro. Ora, se l'utente lo desidera, è anche possibile avviare lo sviluppo di una soluzione incorporata.
   
   > [!NOTE]
   > Verificare di effettuare l'accesso con il messaggio di posta elettronica indirizzo inserito per l'account utente.
   > 
   > 

## <a name="next-steps"></a>Passaggi successivi
Dopo aver creato un tenant di Azure AD, è possibile usarlo per testare gli elementi all'interno di Power BI e/o è possibile proseguire per incorporare report e dashboard di Power BI nell'applicazione. Per altre informazioni su come incorporare gli elementi, vedere [Come incorporare i dashboard, i report e i riquadri di Power BI](embedding-content.md).

[Che cos'è una directory di Azure AD?](https://docs.microsoft.com/azure/active-directory/active-directory-whatis)  
[Come ottenere un tenant di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-howto-tenant)  

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

