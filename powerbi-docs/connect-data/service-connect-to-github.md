---
title: Connettersi a GitHub con Power BI
description: GitHub per Power BI
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/25/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 1be2d3db9dbf341def86c087344ef7a32cd006a0
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83337720"
---
# <a name="connect-to-github-with-power-bi"></a>Connettersi a GitHub con Power BI
Questo articolo illustra come eseguire il pull dei dati dall'account GitHub con un'app modello di Power BI. L'app modello genera un'area di lavoro con un dashboard, un set di report e un set di dati, per consentire l'esplorazione dei dati di GitHub. L'app GitHub per Power BI permette di ottenere informazioni dettagliate su un repository GitHub con dati relativi a contributi, problemi, richieste pull e utenti attivi.

Dopo avere installato l'app modello, è possibile modificare il dashboard e il report. È quindi possibile eseguirne la distribuzione come app ai colleghi dell'organizzazione.

Connettersi all'[app modello GitHub](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.pbiapps-github) oppure leggere altre informazioni sull'[integrazione di GitHub](https://powerbi.microsoft.com/integrations/github) con Power BI.

È anche possibile provare l'[esercitazione su GitHub](service-tutorial-connect-to-github.md). Vengono installati dati di GitHub reali sul repository pubblico per la documentazione di Power BI.

>[!NOTE]
>Questa app modello richiede che l'account GitHub abbia accesso al repository. Di seguito sono fornite informazioni più dettagliate sui requisiti.
>
>Questa app modello non supporta GitHub Enterprise. 

## <a name="how-to-connect"></a>Come connettersi
[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]
   
3. Selezionare **GitHub** \> **Scarica adesso**.
4. In **Installare questa app di Power BI?** selezionare **Installa**.
4. Nel riquadro **App** selezionare il riquadro **GitHub**.

    ![Riquadro di GitHub in Power BI](media/service-connect-to-github/power-bi-github-tile.png)

6. In **Operazioni iniziali con la nuova app** selezionare **Connetti**.

    ![Operazioni iniziali con la nuova app](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

5. Immettere il nome del repository e il proprietario del repository. Per informazioni dettagliate su [come trovare questi parametri](#FindingParams), vedere più avanti.
   
    ![Nome del repository di GitHub in Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect.png)

5. Immettere le credenziali di GitHub. È possibile saltare questo passaggio se è già stato effettuato l'accesso nel browser. 
6. Per **Metodo di autenticazione**, selezionare **oAuth2** \> **Accedi**. 
7. Seguire le istruzioni nelle schermate di autenticazione di GitHub. Concedere all'app modello GitHub per Power BI le autorizzazioni per i dati di GitHub.
   
   ![Autorizzazione di Power BI per GitHub](media/service-connect-to-github/github_authorize.png)
   
    Power BI si connette a GitHub e ai dati.  I dati vengono aggiornati una volta al giorno. Quando Power BI importa i dati, vengono visualizzati i contenuti della nuova area di lavoro GitHub.

## <a name="modify-and-distribute-your-app"></a>Modificare e distribuire l'app

È stata installata l'app modello GitHub. Ciò significa che è stata anche creata l'area di lavoro GitHub. Nell'area di lavoro è possibile modificare il report e il dashboard e quindi eseguirne la distribuzione come *app* ai colleghi dell'organizzazione. 

1. Selezionare la freccia accanto al nome dell'area di lavoro nel riquadro di spostamento. È possibile vedere che l'area di lavoro contiene un dashboard e un report.

    ![App nel riquadro di spostamento](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav-expanded.png)

8. Selezionare il nuovo [dashboard GitHub](https://powerbi.microsoft.com/integrations/github).    
    ![Dashboard GitHub Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-new-dashboard.png)

3. Per visualizzare tutti i contenuti della nuova area di lavoro GitHub, nel riquadro di spostamento selezionare **Aree di lavoro** > **GitHub**.
 
   ![Area di lavoro GitHub nel riquadro di spostamento](media/service-connect-to-github/power-bi-github-left-nav.png)

    Questa visualizzazione rappresenta l'elenco di contenuti per l'area di lavoro. Nell'angolo in alto a destra è disponibile il comando **Aggiorna app**. Quando si è pronti per distribuire l'app ai colleghi, è possibile iniziare. 

    ![Elenco di contenuti di GitHub](media/service-connect-to-github/power-bi-github-content-list.png)

2. Selezionare **Report** e **Set di dati** per visualizzare gli altri elementi nell'area di lavoro.

    Leggere altre informazioni sulla [distribuzione di app](../collaborate-share/service-create-distribute-apps.md) ai colleghi.

## <a name="whats-included-in-the-app"></a>Elementi inclusi nell'app
I dati seguenti sono disponibili da GitHub in Power BI:     

| Nome tabella | Descrizione |
| --- | --- |
| Contributi |La tabella dei contributi fornisce il totale delle operazioni di aggiunta, eliminazione e commit effettuate dal collaboratore, aggregato per ogni settimana. Sono inclusi i 100 collaboratori principali. |
| Issues |Elenca tutti i problemi per il repository selezionato e include calcoli quali il tempo totale e medio per la chiusura di un problema, il numero totale di problemi aperti e il numero totale di problemi chiusi. Questa tabella sarà vuota se il repository non include alcun problema. |
| Pull requests |Questa tabella contiene tutte le richieste pull per il repository e gli autori di tali richieste. Contiene anche calcoli relativi a numero di richieste pull aperte, chiuse e totali, tempo necessario per il pull delle richieste e durata media delle richieste pull. Questa tabella sarà vuota se il repository non include alcun problema. |
| Utenti |Questa tabella fornisce un elenco di utenti o collaboratori di GitHub che hanno contribuito, hanno sottoposto problemi o hanno risolto richieste pull per il repository selezionato. |
| Milestones |Include tutte le attività cardine per il repository selezionato. |
| DateTable |Questa tabella contiene date a partire da quella corrente e per gli anni passati che consentono di analizzare i dati di GitHub in base alla data. |
| ContributionPunchCard |Questa tabella può essere usata come una scheda perforata di collaborazione per il repository selezionato. Mostra i commit in base al giorno della settimana e all'ora del giorno. Questa tabella non è connessa ad altre tabelle nel modello. |
| RepoDetails |Questa tabella fornisce dettagli per il repository selezionato. |

## <a name="system-requirements"></a>Requisiti di sistema
* Account GitHub autorizzato ad accedere al repository.  
* Autorizzazione concessa a Power BI per l'app GitHub durante il primo accesso. Vedere i dettagli riportati di seguito relativi alla revoca dell'accesso.  
* Chiamate API disponibili sufficienti per eseguire il pull e aggiornare i dati.
>[!NOTE]
>Questa app modello non supporta GitHub Enterprise.

### <a name="de-authorize-power-bi"></a>Rimuovere le autorizzazioni per Power BI
Per rimuovere le autorizzazioni per la connessione di Power BI al repository GitHub, è possibile revocare l'accesso in GitHub. Per informazioni dettagliate, vedere questo argomento della [guida di GitHub](https://help.github.com/articles/keeping-your-ssh-keys-and-application-access-tokens-safe/#reviewing-your-authorized-applications-oauth).

<a name="FindingParams"></a>
## <a name="finding-parameters"></a>Individuazione dei parametri
È possibile determinare il proprietario e il repository esaminando il repository in GitHub:

![Nome e proprietario del repository](media/service-connect-to-github/github_ownerrepo.png)

La prima parte, "Azure", è il proprietario e la seconda parte, "azure-sdk-for-php", è il repository stesso.  Questi due elementi sono visibili nell'URL del repository:

    <https://github.com/Azure/azure-sdk-for-php> .

## <a name="troubleshooting"></a>Risoluzione dei problemi
Se necessario, è possibile verificare le credenziali per GitHub.  

1. In un'altra finestra del browser passare al sito Web GitHub e accedere a GitHub. Per verificare se l'accesso è stato effettuato, vedere l'angolo superiore destro del sito GitHub.    
2. In GitHub passare all'URL del repository a cui si vuole accedere in Power BI. Ad esempio: https://github.com/dotnet/corefx.  
3. In Power BI provare a connettersi a GitHub. Nella finestra di dialogo di configurazione di GitHub usare i nomi del repository e del proprietario del repository per lo stesso repository.  

## <a name="next-steps"></a>Passaggi successivi

* [Esercitazione: Connettersi a un repository GitHub con Power BI](service-tutorial-connect-to-github.md)
* [Creare le nuove aree di lavoro in Power BI](../collaborate-share/service-create-the-new-workspaces.md)
* [Installare e usare app in Power BI](../consumer/end-user-apps.md)
* [Connettersi alle app Power BI per servizi esterni](service-connect-to-services.md)
* Domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
