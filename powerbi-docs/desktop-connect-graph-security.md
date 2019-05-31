---
title: Connettersi all'API Microsoft Graph Security in Power BI Desktop
description: Connettersi facilmente all'API Microsoft Graph Security in Power BI Desktop
author: preetikr
manager: kfile
ms.reviewer: ''
ms.custom: seojan19
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/29/2019
ms.author: preetikr
LocalizationGroup: Connect to data
ms.openlocfilehash: 9c265a5d8ad1a08396e0bb4fb553a87a134472fd
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61317987"
---
# <a name="connect-to-the-microsoft-graph-security-api-in-power-bi-desktop"></a>Connettersi all'API Microsoft Graph Security in Power BI Desktop

Il connettore Microsoft Graph Security di Power BI Desktop può essere usato per connettersi all'[API Microsoft Graph Security](https://aka.ms/graphsecuritydocs). In seguito sarà possibile creare dashboard e report e ottenere informazioni dettagliate sugli [avvisi](https://docs.microsoft.com/graph/api/resources/alert?view=graph-rest-1.0) correlati alla sicurezza e sul [punteggio di sicurezza](https://docs.microsoft.com/graph/api/resources/securescores?view=graph-rest-beta).

L'API Microsoft Graph Security collega [diverse soluzioni di sicurezza](https://aka.ms/graphsecurityalerts) realizzate da Microsoft e dai relativi partner di ecosistema per semplificare la correlazione degli avvisi. Questa combinazione offre accesso a una quantità notevole di informazioni contestuali e semplifica l'automazione. Consente alle organizzazioni di ottenere informazioni dettagliate e agire rapidamente in più prodotti di sicurezza, riducendo complessità e costi.

## <a name="prerequisites-to-use-the-microsoft-graph-security-connector"></a>Prerequisiti per usare il connettore Microsoft Graph Security

Per usare il connettore Microsoft Graph Security, è necessario ottenere l'autorizzazione *esplicita* dall'amministratore di tenant di Azure Active Directory (Azure AD). Vedere [Microsoft Graph Security authentication requirements](https://aka.ms/graphsecurityauth) (Requisiti di autenticazione di Microsoft Graph Security).
Il consenso richiede l'ID e il nome applicazione del connettore che vengono citati qui e sono disponibili nel [portale di Azure](https://portal.azure.com):

| Property | Valore |
|----------|-------|
| **Nome applicazione** | `MicrosoftGraphSecurityPowerBIConnector` |
| **ID applicazione** | `cab163b7-247d-4cb9-be32-39b6056d4189` |
|||

Per concedere il consenso per il connettore, l'amministratore del tenant di Azure AD può seguire uno di questi metodi:

* [Concedere il consenso per le applicazioni di Azure AD](https://docs.microsoft.com/azure/active-directory/develop/v2-permissions-and-consent)

* Rispondere a una richiesta inoltrata dall'app per la logica durante la prima esecuzione nell'[esperienza di consenso per l'applicazione](https://docs.microsoft.com/azure/active-directory/develop/application-consent-experience)
   
L'account utente usato per l'accesso al connettore Microsoft Graph Security deve essere un membro del ruolo di amministratore con limitazioni con autorizzazioni di lettura per la sicurezza in Azure AD, in quanto *ruolo con autorizzazioni di lettura per la sicurezza* o *amministratore della protezione*. Vedere [Assign Azure AD roles to users](https://docs.microsoft.com/graph/security-authorization#assign-azure-ad-roles-to-users) (Assegnare ruoli di Azure AD agli utenti).

## <a name="using-the-microsoft-graph-security-connector"></a>Uso del connettore Microsoft Graph Security

Per usare il connettore, seguire la procedura qui sotto:

1. Selezionare **Recupera dati** > **Altro** nella scheda **Home** della barra multifunzione in Power BI Desktop.
2. Selezionare **Servizi online** dall'elenco di categorie riportato a sinistra.
3. Selezionare **Microsoft Graph Security (Beta)** .

    ![Finestra di dialogo Recupera dati](media/desktop-connect-graph-security/GetData.PNG)
    
4. Nella finestra **Microsoft Graph Security** selezionare la versione dell'API Microsoft Graph su cui eseguire la query: **v1.0** o **beta**.

    ![Finestra di dialogo di selezione della versione](media/desktop-connect-graph-security/selectVersion.PNG)
    
5. Quando viene richiesto, accedere all'account Azure Active Directory. Questo account deve avere il *ruolo con autorizzazioni di lettura per la sicurezza* oppure il ruolo *amministratore della protezione*, come indicato nella sezione precedente.

    ![Accedi](media/desktop-connect-graph-security/SignIn.PNG) 
    
6. Se si è l'amministratore del tenant *e* non è ancora stato dato il consenso al connettore Microsoft Graph Security di Power BI (applicazione), viene visualizzata la finestra di dialogo seguente. Selezionare **Acconsenti per conto dell'organizzazione**.

    ![Finestra di dialogo di consenso dell'amministratore](media/desktop-connect-graph-security/AdminConsent.PNG)
    
7. Dopo l'accesso, viene visualizzata la finestra di dialogo seguente che indica che è stata eseguita l'autenticazione. Selezionare **Connetti**.

    ![Finestra di dialogo "L'utente ha eseguito l'accesso"](media/desktop-connect-graph-security/SignedIn.PNG)
    
8. Dopo la connessione, nella finestra **Strumento di navigazione** vengono visualizzati gli avvisi, i punteggi di sicurezza e altre entità che sono disponibili nell'[API Microsoft Graph Security](https://aka.ms/graphsecuritydocs) per la versione selezionata nel passaggio 4. Selezionare una o più entità da importare e usare in Power BI Desktop. Quindi, selezionare **Carica** per ottenere la visualizzazione di risultati illustrata dopo il passaggio 9.

    ![Finestra di dialogo Strumento di navigazione](media/desktop-connect-graph-security/NavTable.PNG)
    
9. Se si vuole eseguire una query avanzata con l'API Microsoft Graph Security, selezionare **Specify custom Microsoft Graph Security URL to filter results** (Specifica URL Microsoft Graph Security personalizzato per filtrare i risultati). Usare questa funzione per generare una query [OData.Feed](https://docs.microsoft.com/power-bi/desktop-connect-odata) sull'API Microsoft Graph Security con le autorizzazioni necessarie.

   L'esempio seguente usa l'oggetto *serviceUri* `https://graph.microsoft.com/v1.0/security/alerts?$filter=Severity eq 'High'`. Per informazioni su come compilare query per filtrare, ordinare o recuperare i risultati più recenti, fare riferimento a [OData system query options](https://docs.microsoft.com/graph/query-parameters) (Opzioni query di sistema OData).

   ![Esempio di OdataFeed](media/desktop-connect-graph-security/ODataFeed.PNG)
    
   Quando si seleziona **Richiama**, la funzione **OData.Feed** esegue una chiamata all'API, che apre l'Editor di Query. Filtrare e affinare il set di dati che si vuole usare. In seguito caricare i dati in Power BI Desktop.

Di seguito viene riportata la finestra dei risultati per le entità di Microsoft Graph Security su cui è stata eseguita la query:

   ![Esempio di finestra di risultati](media/desktop-connect-graph-security/Result.PNG)
    

È ora possibile usare i dati importati dal connettore di Microsoft Graph Security in Power BI Desktop. È possibile creare grafici o report oppure interagire con altri dati importati da cartelle di lavoro di Excel, database o altre origini dati.

## <a name="next-steps"></a>Passaggi successivi
* Vedere gli esempi e i modelli di Power BI che usano questo connettore negli [esempi di Microsoft Graph Security di Power BI in GitHub](https://aka.ms/graphsecuritypowerbiconnectorsamples).

* Per scenari utente e altre informazioni vedere il [post di blog del connettore Microsoft Graph Security di Power BI](https://aka.ms/graphsecuritypowerbiconnectorblogpost).

* È possibile connettersi a molti tipi di dati usando Power BI Desktop. Per altre informazioni, vedere le risorse seguenti:

    * [Che cos'è Power BI Desktop?](desktop-what-is-desktop.md)
    * [Origini dati in Power BI Desktop](desktop-data-sources.md)
    * [Effettuare il data shaping e combinare i dati con Power BI Desktop](desktop-shape-and-combine-data.md)
    * [Connettersi a cartelle di lavoro di Excel in Power BI Desktop](desktop-connect-excel.md)
    * [Immettere dati direttamente in Power BI Desktop](desktop-enter-data-directly-into-desktop.md)
