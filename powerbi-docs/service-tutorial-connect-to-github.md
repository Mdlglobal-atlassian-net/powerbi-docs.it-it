---
title: 'Esercitazione: Connettersi a un repository GitHub con Power BI'
description: In questa esercitazione si esegue la connessione ai dati reali nel servizio GitHub usando Power BI, il quale crea automaticamente dashboard e report.
author: maggiesMSFT
ms.reviewer: SarinaJoan
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 08/07/2019
ms.author: maggies
LocalizationGroup: Connect to services
ms.openlocfilehash: a3c87a700df1c35596b6520cc64d9b580ccb74eb
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "80403398"
---
# <a name="tutorial-connect-to-a-github-repo-with-power-bi"></a>Esercitazione: Connettersi a un repository GitHub con Power BI
In questa esercitazione si esegue la connessione ai dati reali nel servizio GitHub usando Power BI, il quale crea automaticamente dashboard e report. È possibile connettersi al *repository* pubblico di contenuti di Power BI e trovare risposte a domande relative a: sul numero di persone che contribuiscono al contento pubblico di Power BI, sapere chi contribuisce di più, in quale giorno della settimana si registrano più contributi e altre domande. 

![Report di GitHub in Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-punch-card.png)

In questa esercitazione viene completata la procedura seguente:

> [!div class="checklist"]
> * Registrarsi a GitHub per ottenere un account se non se ne ha ancora uno 
> * Accedere all'account Power BI o registrarsi se non si ha ancora un account
> * Aprire il servizio Power BI
> * Individuare l'app GitHub
> * Immettere le informazioni per il repository GitHub pubblico in Power BI
> * Visualizzare il dashboad e il report con dati di GitHub
> * Pulire le risorse eliminando l'app

Se non si è ancora iscritti a Power BI, [iscriversi per ottenere una versione di prova gratuita](https://app.powerbi.com/signupredirect?pbi_source=web) prima di iniziare.

## <a name="prerequisites"></a>Prerequisiti

Per completare questa esercitazione, è necessario un account GitHub, se non se ne ha già uno. 

- Registrarsi per ottenere un [account GitHub](https://docs.microsoft.com/contribute/get-started-setup-github).


## <a name="how-to-connect"></a>Come connettersi
1. Accedere al servizio Power BI (`https://app.powerbi.com`). 
2. Nel riquadro di spostamento selezionare **App** e quindi **Scarica app**.
   
   ![Scarica app in Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial.png) 

3. Selezionare **App**, digitare **GitHub** nella casella di ricerca > **Scarica adesso**.
   
   ![Scaricare GitHub in Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-app-source.png) 

4. In **Installare questa app di Power BI?** selezionare **Installa**.
5. In **La nuova app è pronta** selezionare **Vai all'app**.
6. In **Operazioni iniziali con la nuova app** selezionare **Connetti**.

    ![Operazioni iniziali con la nuova app](media/service-tutorial-connect-to-github/power-bi-new-app-connect-get-started.png)

7. Immettere il nome del repository e il proprietario del repository. L'URL del repository è https://github.com/MicrosoftDocs/powerbi-docs, quindi **Proprietario repository** è **MicrosoftDocs** e **Repository** è **powerbi-docs**. 
   
    ![Nome del repository di GitHub in Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect.png)

5. Immettere le credenziali create per GitHub. Power BI potrebbe ignorare questo passaggio se già stato eseguito l'accesso a GitHub nel browser. 

6. Per **Metodo di autenticazione**, lasciare selezionata l'opzione **OAuth2** \> **Accedi**.

7. Seguire le istruzioni nelle schermate di autenticazione di GitHub. Concedere le autorizzazioni di Power BI ai dati di GitHub.
   
   A questo punto Power BI può connettersi a GitHub e ai dati.  I dati vengono aggiornati una volta al giorno.

8. Quando Power BI importa i dati, vengono visualizzati i contenuti della nuova area di lavoro GitHub. 
9. Selezionare la freccia accanto al nome dell'area di lavoro nel riquadro di spostamento. È possibile vedere che l'area di lavoro contiene un dashboard e un report. 

    ![App nel riquadro di spostamento](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav-expanded.png)

10. Selezionare **Altre opzioni** (...) accanto al nome del dashboard > **Rinomina** > digitare **Dashboard GitHub**.
 
    ![Riquadro di GitHub in Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav.png) 

8. Selezionare l'icona di spostamento globale per ridurre a icona il riquadro di spostamento e avere più spazio.

    ![Icona di spostamento globale](media/service-tutorial-connect-to-github/power-bi-global-navigation-icon.png)

10. Selezionare il dashboard GitHub.
    
    Il dashboard GitHub contiene dati dinamici, quindi i valori visualizzati potrebbero essere diversi.

    ![Dashboard di GitHub in Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-new-dashboard.png)

    

## <a name="ask-a-question"></a>Porre una domanda

1. Posizionare il cursore in **Porre una domanda sui dati**. Power BI fornisce alcune indicazioni in **Domande per iniziare**. 

1. Selezionare **how many users are there**.
 
    ![Chiedere il numero di utenti presenti](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-qna-how-many-users.png)

13. Tra **how many** e **users are there** digitare **pull requests per**. 

     Power BI crea un grafico a barre che mostra il numero di richieste pull per persona.

    ![Chiedere il numero di richieste pull per utente](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-qna-how-many-prs.png)


13. Selezionare l'icona a forma di puntina per l'aggiunta al dashboard e quindi fare clic su **Chiudi Domande e risposte**.

## <a name="view-the-github-report"></a>Visualizzare il report di GitHub 

1. Nel dashboard GitHub selezionare l'istogramma **Pull Requests by Month** per aprire il report correlato.

    ![Istogramma relativo alle richieste pull al mese](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-column-chart.png)

2. Selezionare il nome di un utente nel grafico **Total pull requests by user**. In questo esempio è possibile notare che la maggior parte delle ore è in febbraio.

    ![Evidenziazione del report di GitHub in Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-cross-filter-total-prs.png)

3. Selezionare la scheda **Punch Card** (Scheda perforata) per visualizzare la pagina successiva del report. 
 
    ![Scheda perforata del report di GitHub in Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-tues-3pm.png)

    Apparentemente sembra che martedì alle 15 sia il momento più comune per i *commit*, quando gli utenti archiviano il lavoro.

## <a name="clean-up-resources"></a>Pulire le risorse

Dopo aver completo l'esercitazione, è possibile eliminare l'app GitHub. 

1. Nel riquadro di spostamento selezionare **App**.
2. Passare il mouse sul riquadro di GitHub e selezionare l'icona a forma di bidone della spazzatura **Delete** (Elimina).

    ![Eliminare l'app GitHub](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-delete.png)

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione è stata eseguita la connessione a un repository pubblico di GitHub e sono stati ottenuti i dati che Power BI ha formattato sotto forma di dashboard e report. Esplorando il dashboard e il report è stato possibile ottenere le risposte ad alcune domande relative ai dati. Ora è possibile scoprire come connettersi ad altri servizi, ad esempio Salesforce, Microsoft Dynamics e Google Analytics. 
 
> [!div class="nextstepaction"]
> [Connettersi ai servizi online usati](service-connect-to-services.md)


