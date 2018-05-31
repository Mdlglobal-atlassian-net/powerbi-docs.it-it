---
title: Incorporare contenuto di Power BI in un'applicazione per i clienti
description: Informazioni su come integrare o incorporare un report, un dashboard o un riquadro in un'app Web tramite le API di Power BI per i clienti.
services: powerbi
author: markingmyname
ms.author: maghan
ms.date: 05/07/2018
ms.topic: tutorial
ms.service: powerbi
ms.custom: mvc
manager: kfile
ms.openlocfilehash: 2d4fdee8d3e4cca60294acd0a9167da1f048afa5
ms.sourcegitcommit: 9fa954608e78dcdb8d8a503c3c9b01c43ca728ab
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/11/2018
ms.locfileid: "34051934"
---
# <a name="tutorial-embed-a-power-bi-report-dashboard-or-tile-into-an-application-for-your-customers"></a>Esercitazione: Incorporare un report, un dashboard o un riquadro di Power BI in un'applicazione per i clienti
Con **Power BI Embedded in Azure**, è possibile incorporare report, dashboard o riquadri in un'applicazione, in modo che i clienti possano condividere i dati. Questo scenario è in genere relativo a **sviluppatori ISV** che usano una struttura in cui i **dati sono di proprietà dell'app**. Il fatto che i **dati siano di proprietà dell'app** implica che il contenuto di Power BI per i propri clienti viene incorporato. Ad esempio, l'utente del contenuto di Power BI può visualizzare report, dashboard o riquadri senza dover accedere a **Power BI**. Questa esercitazione illustra come integrare o incorporare un report in un'applicazione tramite .NET SDK di **Power BI** insieme all'API JavaScript di **Power BI** quando si usa **Power BI Embedded in Azure**  per i clienti che usano **dati di proprietà dell'app**.

In questa esercitazione viene illustrato come:
>[!div class="checklist"]
>* Registrare un'applicazione in Azure.
>* Incorporare un report, un dashboard o un riquadro in un'applicazione usando Power BI Embedded in Azure.

## <a name="prerequisites"></a>Prerequisiti
Per iniziare, è necessario un account **Power BI Pro** e un account **Microsoft Azure**.

* Se non si è ancora iscritti a **Power BI Pro**, [iscriversi per ottenere una versione di prova gratuita](https://powerbi.microsoft.com/en-us/pricing/) prima di iniziare.
* Se non si ha una sottoscrizione di Azure, [creare un account gratuito](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) prima di iniziare.
* È necessario disporre del proprio [tenant di Azure Active Directory](create-an-azure-active-directory-tenant.md) configurato.
* È richiesta l'installazione di [Visual Studio](https://www.visualstudio.com/) (versione 2013 o successive).

## <a name="setup-your-embedded-analytics-development-environment"></a>Configurare l'ambiente di sviluppo di analisi incorporata

Prima di iniziare a incorporare report, dashboard o riquadri in un'applicazione, è necessario assicurarsi che l'ambiente sia configurato per consentire l'incorporamento. Come parte dell'installazione, sarà necessario eseguire le operazioni seguenti.

### <a name="register-an-application-in-azure-active-directory-azure-ad"></a>Registrare un'applicazione in Azure Active Directory (Azure AD)

La registrazione dell'applicazione in Azure Active Directory consente all'applicazione di accedere alle API REST di Power BI. Ciò permette di stabilire un'identità per l'applicazione e di specificare le autorizzazioni per accedere alle risorse REST di Power BI.

1. Accettare le [condizioni relative all'API di Microsoft Power BI](https://powerbi.microsoft.com/api-terms).

2. Accedere al [portale di Azure](https://portal.azure.com).
 
    ![Pagina principale del portale di Azure](media/embed-sample-for-customers/embed-sample-for-customers-002.png)

3. Nel riquadro di spostamento a sinistra scegliere **Tutti i servizi**, selezionare **Registrazioni per l'app** e quindi scegliere **Registrazione nuova applicazione**.
   
    ![Ricerca di Registrazioni per l'app](media/embed-sample-for-customers/embed-sample-for-customers-003.png)</br>
    ![Registrazione nuova applicazione](media/embed-sample-for-customers/embed-sample-for-customers-004.png)

4. Seguire le istruzioni e creare una nuova applicazione. Per i dati di proprietà delle app è necessario usare **Nativa** per il tipo di applicazione. È anche necessario specificare un **URI di reindirizzamento**, che verrà usato da **Azure AD** per restituire le risposte del token. Immettere un valore specifico per l'applicazione (ad esempio http://localhost:13526/redirect)).

    ![Creare l'app](media/embed-sample-for-customers/embed-sample-for-customers-005.png)

### <a name="apply-permissions-to-your-application-within-azure-active-directory"></a>Applicare le autorizzazioni all'applicazione in Azure Active Directory

È necessario abilitare autorizzazioni aggiuntive per l'applicazione oltre a quelle fornite nella pagina di registrazione dell'app. È necessario accedere con l'account *master*, usato per l'incorporamento, che deve essere un account di amministratore globale.

### <a name="use-the-azure-active-directory-portal"></a>Usare il portale di Azure Active Directory

1. Passare a [Registrazioni per l'app](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ApplicationsListBlade) nel portale di Azure e selezionare l'app che si usa per l'incorporamento.
   
    ![Scelta dell'app](media/embed-sample-for-customers/embed-sample-for-customers-006.png)

2. Selezionare **Impostazioni** e quindi in **Accesso all'API** selezionare **Autorizzazioni necessarie**.
   
    ![Autorizzazioni necessarie](media/embed-sample-for-customers/embed-sample-for-customers-008.png)

3. Selezionare **Microsoft Azure Active Directory** e quindi accertarsi che l'opzione **Accede alla directory come utente registrato** sia selezionata. Selezionare **Salva**.
   
    ![Autorizzazioni di Microsoft Azure AD](media/embed-sample-for-customers/embed-sample-for-customers-011.png)

4. Selezionare **Aggiungi**.

    ![Aggiungere autorizzazioni](media/embed-sample-for-customers/embed-sample-for-customers-012.png)

5. Fare clic su **Selezionare un'API**.

    ![Aggiungere l'accesso all'API](media/embed-sample-for-customers/embed-sample-for-customers-013.png)

6. Selezionare **Servizio Power BI** e quindi **Seleziona**.

    ![Selezionare i servizi PBI](media/embed-sample-for-customers/embed-sample-for-customers-014.png)

7. Selezionare tutte le autorizzazioni in **Autorizzazioni delegate**. Per salvare le selezioni è necessario selezionarle una alla volta. Al termine, selezionare **Salva**.
   
    ![Selezionare le autorizzazioni delegate](media/embed-sample-for-customers/embed-sample-for-customers-015.png)

8. In **Autorizzazioni necessarie** selezionare **Concedi autorizzazioni**.
   
    L'azione **Concedi autorizzazioni** è necessaria per l'*account master*, in modo da evitare che venga richiesto il consenso da Azure AD. Se l'account che esegue questa azione è un amministratore globale, si concederanno autorizzazioni a tutti gli utenti dell'organizzazione per questa applicazione. Se l'account che esegue questa azione è l'*account master* e non un amministratore globale, si concederanno autorizzazioni solo all'*account master* per questa applicazione.
   
    ![Concedere autorizzazioni nella finestra di dialogo Autorizzazioni necessarie](media/embed-sample-for-customers/embed-sample-for-customers-016.png)

### <a name="create-your-power-bi-embedded-dedicated-capacity-in-azure"></a>Creare la capacità dedicata di Power BI Embedded in Azure

1. Accedere al [portale di Azure](https://portal.azure.com).

    ![Pagina principale del portale di Azure](media/embed-sample-for-customers/embed-sample-for-customers-002.png)

2. Nel riquadro di spostamento a sinistra scegliere **Tutti i servizi** e selezionare **Power BI Embedded**.

    ![Ricerca di PBIE](media/embed-sample-for-customers/embed-sample-for-customers-017.png)

3. Seguire le istruzioni e specificare le informazioni appropriate richieste per creare una nuova capacità dedicata di **Power BI Embedded** e quindi selezionare **Crea**. Quando si sceglie il **Piano tariffario**, esaminare la tabella seguente per decidere quello più appropriato per le specifiche esigenze. Selezionare quindi **Crea** e attendere il completamento della risorsa.

    ![Configurazione di PBIE](media/embed-sample-for-customers/embed-sample-for-customers-018.png)

| Nodo della capacità | Totale core<br/>*(Back-end + front-end)* | Core di back-end | Core di front-end | Limiti di connessione dinamica/DirectQuery | Rendering massimo della pagina all'ora di punta |
| --- | --- | --- | --- | --- | --- |
| A1 |1 v-core |0,5 core, 3 GB di RAM |0,5 core | 5 al secondo |1-300 |
| A2 |2 v-core |1 core, 5 GB di RAM |1 core | 10 al secondo |301-600 |
| A3 |4 v-core |2 core, 10 GB di RAM |2 core | 15 al secondo |601-1.200 |
| A4 |8 v-core |4 core, 25 GB di RAM |4 core |30 al secondo |1.201-2.400 |
| A5 |16 v-core |8 core, 50 GB di RAM |8 core |60 al secondo |2.401-4.800 |
| A6 |32 v-core |16 core, 100 GB di RAM |16 ore |120 al secondo |4.801-9600 |

A questo punto è possibile visualizzare la nuova **capacità dedicata di Power BI Embedded**.

   ![Capacità dedicata di PBIE](media/embed-sample-for-customers/embed-sample-for-customers-019.png)

## <a name="setup-your-power-bi-environment"></a>Configurare l'ambiente di Power BI

### <a name="create-an-app-workspace"></a>Creare un'area di lavoro per le app

Se si incorporano report, dashboard o riquadri per i clienti, è necessario inserire il contenuto all'interno di un'area di lavoro per le app. L'account *master* deve essere un amministratore dell'area di lavoro per le app.

1. Iniziare creando l'area di lavoro. Selezionare **Aree di lavoro** > **Creare un'area di lavoro per le app**. Questa sarà la posizione in cui inserire il contenuto a cui l'applicazione deve accedere.

    ![Creare l'area di lavoro](media/embed-sample-for-customers/embed-sample-for-customers-020.png)

2. Assegnare un nome all'area di lavoro. Se il corrispondente **ID area di lavoro** non è disponibile, modificarlo in modo da ottenere un ID univoco. Questo sarà anche il nome dell'app.

    ![Assegnare un nome all'area di lavoro](media/embed-sample-for-customers/embed-sample-for-customers-021.png)

3. Ci sono alcune opzioni da impostare. Se si sceglie **Pubblica**, chiunque nell'organizzazione potrà visualizzare il contenuto dell'area di lavoro. **Privata**, d'altra parte, significa che solo i membri dell'area di lavoro potranno visualizzarne il contenuto.

    ![Pubblica/Privata](media/embed-sample-for-customers/embed-sample-for-customers-022.png)

    Dopo aver creato il gruppo, non è possibile modificare l'impostazione di gruppo pubblico o privato.

4. È anche possibile scegliere se i membri possono **modificare** o avere l'accesso di **sola visualizzazione**.

    ![Aggiunta di membri](media/embed-sample-for-customers/embed-sample-for-customers-023.png)

5. Aggiungere gli indirizzi di posta elettronica delle persone che avranno accesso all'area di lavoro e selezionare **Aggiungi**. Non è possibile aggiungere alias di gruppo, soli singoli utenti.

6. Decidere se ogni persona è un membro o un amministratore. Gli amministratori possono modificare l'area di lavoro stessa, inclusa l'aggiunta di altri membri. I membri possono modificare il contenuto nell'area di lavoro, a meno che non abbiano accesso in sola visualizzazione. Sia gli amministratori che i membri possono pubblicare l'app.

7. Espandere **Avanzate**, abilitare **Capacità dedicata** e quindi selezionare la **capacità dedicata di Power BI Embedded** creata. Selezionare quindi **Salva**.

    ![Aggiunta di membri](media/embed-sample-for-customers/embed-sample-for-customers-024.png)

È ora possibile visualizzare la nuova area di lavoro. Power BI crea l'area di lavoro, che verrà aperta e visualizzata nell'elenco delle aree di lavoro di cui si è membri. Gli amministratori potranno a questo punto selezionare i puntini di sospensione (…) per tornare indietro e apportare modifiche, aggiungere nuovi membri o modificarne le autorizzazioni.

   ![Nuova area di lavoro](media/embed-sample-for-customers/embed-sample-for-customers-025.png)

### <a name="create-and-publish-your-reports"></a>Creare e pubblicare i report

È possibile creare report e set di dati usando Power BI Desktop e quindi pubblicando tali report in un'area di lavoro per le app. Per pubblicare in un'area di lavoro per le app l'utente finale che pubblica i report deve avere una licenza di Power BI Pro.

1. Scaricare l'esempio [Blog Demo](https://github.com/Microsoft/powerbi-desktop-samples) da GitHub.

    ![Esempio di report](media/embed-sample-for-customers/embed-sample-for-customers-026-1.png)

2. Aprire il report di esempio con estensione pbix in **Power BI Desktop**.

   ![Report di PBI Desktop](media/embed-sample-for-customers/embed-sample-for-customers-027.png)

3. Eseguire la pubblicazione nell'**area di lavoro per le app**.

   ![Report di PBI Desktop](media/embed-sample-for-customers/embed-sample-for-customers-028.png)

    È ora possibile visualizzare il report nel servizio Power BI online.

   ![Report di PBI Desktop](media/embed-sample-for-customers/embed-sample-for-customers-029.png)

## <a name="embed-your-content"></a>Incorporare il contenuto

1. Scaricare l'esempio [App Owns Data](https://github.com/Microsoft/PowerBI-Developer-Samples) da GitHub per iniziare.

    ![Applicazione di esempio App Owns Data](media/embed-sample-for-customers/embed-sample-for-customers-026.png)

2. Aprire il file Web.config nell'applicazione di esempio. Ci sono cinque campi che è necessario compilare per eseguire correttamente l'applicazione: **clientID**, **groupId**, **reportId**, **pbiUsername** e **pbiPassword**.

      ![File Web.config](media/embed-sample-for-customers/embed-sample-for-customers-030.png)

    * Compilare il campo **clientId** con l'**ID applicazione** di **Azure**. **clientId** viene usato dall'applicazione per identificare se stessa nei confronti degli utenti da cui si richiedono le autorizzazioni. Per ottenere il valore per il campo **clientId**, seguire questi passaggi:

        1. Accedere al [portale di Azure](https://portal.azure.com).

        ![Pagina principale del portale di Azure](media/embed-sample-for-customers/embed-sample-for-customers-002.png)

        2. Nel riquadro di spostamento a sinistra scegliere **Tutti i servizi** e selezionare **Registrazioni per l'app**.

        ![Ricerca di Registrazioni per l'app](media/embed-sample-for-customers/embed-sample-for-customers-003.png)
        3. Selezionare l'applicazione per cui si vuole recuperare il valore **clientId**.

        ![Scelta dell'app](media/embed-sample-for-customers/embed-sample-for-customers-006.png)

      4. Dovrebbe essere visualizzato un **ID applicazione** che viene elencato come GUID. Usare questo **ID applicazione** come **clientId** per l'applicazione.

        ![clientId](media/embed-sample-for-customers/embed-sample-for-customers-007.png)     

    * Compilare il campo **groupId** con il **GUID dell'area di lavoro per le app** di Power BI.

        ![groupId](media/embed-sample-for-customers/embed-sample-for-customers-031.png)

    * Compilare il campo **reportId** con il **GUID del report** di Power BI.

        ![reportId](media/embed-sample-for-customers/embed-sample-for-customers-032.png)    

    * Compilare il campo **pbiUsername** con l'account utente master Power BI.
    * Compilare il campo **pbiPassword** con la password per l'account utente master Power BI.

3. Eseguire l'applicazione.

    Per prima cosa, selezionare **Esegui** in **Visual Studio**.

    ![Eseguire l'applicazione](media/embed-sample-for-customers/embed-sample-for-customers-033.png)

    Selezionare quindi **Incorpora report**. A seconda del contenuto con cui si sceglie di eseguire il test (report, dashboard o riquadri), selezionare l'opzione corrispondente nell'applicazione.

    ![Selezionare il contenuto](media/embed-sample-for-customers/embed-sample-for-customers-034.png)
 
    È ora possibile visualizzare il report nell'applicazione di esempio.

    ![Visualizzare l'applicazione](media/embed-sample-for-customers/embed-sample-for-customers-035.png)

Per un esempio completo dell'uso dell'API JavaScript, è possibile usare lo [strumento Playground](https://microsoft.github.io/PowerBI-JavaScript/demo), che consente di riprodurre in modo rapido i diversi tipi di esempi di Power BI Embedded. È anche possibile ottenere maggiori informazioni sull'API JavaScript visitando la pagina del [wiki Power BI-JavaScript](https://github.com/Microsoft/powerbi-javascript/wiki).

Per altre domande su Power BI Embedded, visitare la pagina [Domande frequenti](embedded-faq.md).  In caso di problemi con Power BI Embedded all'interno dell'applicazione, visitare la pagina [Risoluzione dei problemi](embedded-troubleshoot.md).

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/) 