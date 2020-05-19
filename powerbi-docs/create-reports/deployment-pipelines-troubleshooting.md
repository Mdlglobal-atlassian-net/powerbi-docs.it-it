---
title: Risoluzione dei problemi delle pipeline di distribuzione
description: Risolvere i problemi delle pipeline di distribuzione in Power BI
author: KesemSharabi
ms.author: kesharab
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-service
ms.date: 05/06/2020
ms.openlocfilehash: fda846a19b5c6081c59f08f2bf9f94eddbc9852c
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83148566"
---
# <a name="deployment-pipelines-troubleshooting-preview"></a>Risoluzione dei problemi delle pipeline di distribuzione (anteprima)

Usare questo articolo per risolvere i problemi delle pipeline di distribuzione.

## <a name="general"></a>Generale

### <a name="whats-deployment-pipelines-in-power-bi"></a>Cosa sono le pipeline di distribuzione in Power BI

Per informazioni sulle pipeline di distribuzione in Power BI, vedere la [panoramica delle pipeline di distribuzione](deployment-pipelines-overview.md).

### <a name="how-do-i-get-started-with-deployment-pipelines"></a>Come iniziare a usare le pipeline di distribuzione?

Per iniziare a usare le pipeline di distribuzione, vedere le [istruzioni per iniziare](deployment-pipelines-get-started.md).

### <a name="why-cant-i-see-the-deployment-pipelines-button"></a>Perché non è possibile visualizzare il pulsante delle pipeline di distribuzione?

Se non vengono soddisfatte le condizioni seguenti, non sarà possibile visualizzare il pulsante delle pipeline di distribuzione.

* Essere un utente di [Power BI Pro](../admin/service-admin-purchasing-power-bi-pro.md)

* Appartenere a un'organizzazione con capacità Premium

* Un'area di lavoro può essere assegnata solo a una singola pipeline

* Essere un amministratore di una nuova area di lavoro

## <a name="licensing"></a>Gestione delle licenze

### <a name="what-licenses-are-needed-to-work-with-deployment-pipelines"></a>Quali sono le licenze necessarie per lavorare con le pipeline di distribuzione?

Per usare le pipeline di distribuzione, è necessario essere un utente [Power BI Pro](../admin/service-admin-purchasing-power-bi-pro.md) con [capacità Premium](../admin/service-premium-what-is.md). Per altre informazioni, vedere [Accedere alle pipeline di distribuzione](deployment-pipelines-get-started.md#accessing-deployment-pipelines).

### <a name="what-type-of-capacity-can-i-assign-to-a-workspace-in-a-pipeline"></a>Quale tipo di capacità è possibile assegnare a un'area di lavoro in una pipeline?

Tutte le aree di lavoro in una pipeline di distribuzione devono trovarsi all'interno di una capacità dedicata affinché la pipeline sia funzionante. Tuttavia, è possibile usare capacità diverse per aree di lavoro diverse in una pipeline. È anche possibile usare tipi di capacità diversi per aree di lavoro diverse nella stessa pipeline.

Per lo sviluppo e il test, è possibile usare una capacità A o EM insieme a un account Power BI Pro per ogni utente.

Per le aree di lavoro di produzione, è necessaria una capacità P. Gli ISV che distribuiscono contenuti tramite applicazioni incorporate possono anche usare le capacità A o EM per la produzione.

## <a name="technical"></a>Informazioni tecniche

### <a name="why-cant-i-see-all-my-workspaces-when-i-try-to-assign-a-workspace-to-a-pipeline"></a>Perché non è possibile visualizzare tutte le aree di lavoro quando si tenta di assegnare un'area di lavoro a una pipeline?

Per assegnare un'area di lavoro a una pipeline, è necessario che siano soddisfatte le condizioni seguenti:

* L'area di lavoro è una [esperienza delle nuove aree di lavoro](../collaborate-share/service-create-the-new-workspaces.md)

* Essere un amministratore di un'area di lavoro

* L'area di lavoro non è assegnata ad altre pipeline

* L'area di lavoro risiede in una [capacità Premium](../admin/service-premium-what-is.md)

Le aree di lavoro che non soddisfano queste condizioni non vengono visualizzate nell'elenco delle aree di lavoro che è possibile selezionare.

### <a name="how-can-i-assign-workspaces-to-all-the-stages-in-a-pipeline"></a>Come si assegnano le aree di lavoro a tutte le fasi di una pipeline?

È possibile assegnare un'area di lavoro per pipeline. Una volta assegnata un'area di lavoro a una pipeline, è possibile distribuirla nelle fasi successive della pipeline. Durante la prima distribuzione, viene creata una nuova area di lavoro con copie degli elementi nella fase di origine. Vengono mantenute le relazioni degli elementi copiati. Per altre informazioni, vedere come [assegnare un'area di lavoro a una pipeline di distribuzione](deployment-pipelines-get-started.md#step-2---assign-a-workspace-to-a-deployment-pipeline).

### <a name="why-did-my-first-deployment-fail"></a>Perché la prima distribuzione non è riuscita?

La prima distribuzione potrebbe non riuscire a causa di diversi motivi. La tabella seguente ne elenca alcuni.

|Errore  |Azione  |
|---------|---------|
|Non si hanno le [autorizzazioni di capacità Premium](deployment-pipelines-process.md#creating-a-premium-capacity-workspace).     |Per ottenere le autorizzazioni di capacità Premium, chiedere a un amministratore della capacità di aggiungere l'area di lavoro a una capacità o richiedere autorizzazioni di assegnazione per la capacità. Quando l'area di lavoro è in una capacità, ridistribuirla.        |
|Non si hanno le autorizzazioni per l'area di lavoro.     |Per eseguire la distribuzione, è necessario essere un membro dell'area di lavoro. Richiedere all'amministratore dell'area di lavoro di concedere le autorizzazioni appropriate.         |
|L'amministratore di Power BI ha disabilitato la creazione di aree di lavoro.     |Contattare l'amministratore di Power BI per il supporto.         |
|L'area di lavoro non è una [esperienza delle nuove aree di lavoro](../collaborate-share/service-create-the-new-workspaces.md).     |Creare il contenuto nell'esperienza delle nuove aree di lavoro. Se si hanno contenuti in un'area di lavoro classica, è possibile [aggiornarlo](../collaborate-share/service-upgrade-workspaces.md) a una esperienza delle nuove aree di lavoro.         |
|Si sta usando la [distribuzione selettiva](deployment-pipelines-get-started.md#selective-deployment) e non viene selezionato il set di dati del contenuto.     |Eseguire una di queste operazioni: </br></br>Deselezionare il contenuto collegato al set di dati. Il contenuto non selezionato, ad esempio report o dashboard, non verrà copiato nella fase successiva. </br></br>Selezionare il set di dati collegato al contenuto selezionato. Il set di dati verrà copiato nella fase successiva.         |

### <a name="im-getting-a-warning-that-i-have-unsupported-artifacts-in-my-workspace-when-im-trying-to-deploy-how-can-i-know-which-artifacts-are-not-supported"></a>Quando si tenta di eseguire la distribuzione, viene visualizzato un avviso che indica che sono presenti artefatti non supportati nell'area di lavoro. Come è possibile stabilire quali artefatti non sono supportati?

Per un elenco completo di elementi e artefatti non supportati nelle pipeline di distribuzione, vedere le sezioni seguenti:

* [Elementi non supportati](deployment-pipelines-process.md#unsupported-items)

* [Proprietà degli elementi che non vengono copiate](deployment-pipelines-process.md#item-properties-that-are-not-copied)

### <a name="why-did-my-deployment-fail-due-to-broken-rules"></a>Perché la distribuzione ha avuto esito negativo a causa di regole interrotte?

Se si verificano problemi durante la configurazione delle regole del set di dati, vedere le [regole del set di dati](deployment-pipelines-get-started.md#step-4---create-dataset-rules) e assicurarsi di seguire le [limitazioni delle regole del set di dati](deployment-pipelines-get-started.md#dataset-rule-limitations).

Se la distribuzione è riuscita in precedenza e si verifica improvvisamente un errore con regole interrotte, il problema potrebbe essere dovuto alla ripubblicazione di un set di dati. Le modifiche seguenti apportate al set di dati di origine generano una distribuzione non riuscita:

**Regole dei parametri**

* Parametro rimosso

* Nome parametro modificato

**Regole delle origini dati**

Vi sono valori mancanti per le regole del set di dati. Questo potrebbe essere dovuto a una modifica del set di dati.

![regola interrotta](media/deployment-pipelines-troubleshooting/broken-rule.png)

Quando una distribuzione che in precedenza era riuscita ha esito negativo a causa di collegamenti interrotti, viene visualizzato un avviso. È possibile fare clic su **Configura regole** per passare al riquadro delle impostazioni della distribuzione, in cui il set di dati con errori è contrassegnato. Quando si fa clic sul set di dati, le regole interrotte vengono contrassegnate.

Per eseguire correttamente la distribuzione, correggere o rimuovere le regole interrotte ed eseguire nuovamente la distribuzione.

### <a name="how-can-i-change-the-data-source-in-the-pipeline-stages"></a>Come modificare l'origine dati nelle fasi della pipeline?

Non è possibile modificare la connessione dell'origine dati nel servizio Power BI.

Se si vuole modificare l'origine dati nelle fasi di test o di produzione, è possibile usare le [regole del set di dati](deployment-pipelines-get-started.md#step-4---create-dataset-rules) o le [API](https://docs.microsoft.com/rest/api/power-bi/datasets/updateparametersingroup). Le regole del set di dati verranno applicate solo dopo la distribuzione successiva.

### <a name="i-fixed-a-bug-in-production-but-now-i-cant-click-the-deploy-to-previous-stage-button-why-is-it-greyed-out"></a>È stato corretto un bug in produzione, ma ora non è possibile fare clic sul pulsante Distribuisci in fase precedente. Perché è disattivato?

È possibile eseguire la distribuzione nella fase precedente solo se tale fase è vuota. Se si hanno contenuti nella fase di test, non sarà possibile eseguirvi la distribuzione dalla fase di produzione.

Dopo aver creato la pipeline, usare la fase di sviluppo per sviluppare il contenuto e le fasi di test per esaminarlo e testarlo. È possibile correggere i bug in queste fasi e quindi distribuire l'ambiente corretto nella fase di produzione.

>[!NOTE]
>La distribuzione nella fase precedente supporta solo la [distribuzione completa](deployment-pipelines-get-started.md#deploying-all-content), non la [distribuzione selettiva](deployment-pipelines-get-started.md#selective-deployment)

### <a name="does-deployment-pipelines-support-multi-geo"></a>Le pipeline di distribuzione supportano Multi-Geo?

La funzionalità Multi-Geo è supportata. Potrebbe essere necessario più tempo per distribuire il contenuto in fasi in aree geografiche diverse.

## <a name="permissions"></a>Autorizzazioni

### <a name="what-is-the-deployment-pipelines-permissions-model"></a>Qual è il modello delle autorizzazioni delle pipeline di distribuzione?

Il modello delle autorizzazioni delle pipeline di distribuzione è descritto nella sezione [autorizzazioni](deployment-pipelines-process.md#permissions).

### <a name="who-can-deploy-content-between-stages"></a>Chi può distribuire contenuto tra le fasi?

Il contenuto può essere distribuito in una fase vuota o in una fase che include contenuto. Il contenuto deve risiedere in una [capacità Premium](../admin/service-premium-what-is.md).

* **Distribuzione in una fase vuota**: qualsiasi utente di [Power BI Pro](../admin/service-admin-purchasing-power-bi-pro.md) che sia membro o amministratore dell'area di lavoro di origine.

* **Distribuzione in una fase con contenuto**: qualsiasi utente di [Power BI Pro](../admin/service-admin-purchasing-power-bi-pro.md) che sia membro o amministratore di entrambe le aree di lavoro nelle fasi di distribuzione di origine e di destinazione.

* **Esecuzione dell'override di un set di dati**: la distribuzione sostituisce ogni set di dati incluso nella fase di destinazione, anche se non è stato modificato. L'utente deve essere il proprietario di tutti i set di dati della fase di destinazione specificati nella distribuzione.

### <a name="which-permissions-do-i-need-to-configure-dataset-rules"></a>Quali sono le autorizzazioni necessarie per configurare le regole del set di dati?

Per configurare le regole del set di dati nelle pipeline di distribuzione è necessario essere il proprietario del set di dati.

### <a name="why-cant-i-see-workspaces-in-the-pipeline"></a>Perché non è possibile visualizzare le aree di lavoro nella pipeline?

Le autorizzazioni per le pipeline e per le aree di lavoro vengono gestite separatamente. È possibile avere le autorizzazioni per la pipeline, ma non per l'area di lavoro. Per altre informazioni, vedere la sezione delle [autorizzazioni](deployment-pipelines-process.md#permissions).

## <a name="next-steps"></a>Passaggi successivi

>[!div class="nextstepaction"]
>[Introduzione alle pipeline di distribuzione](deployment-pipelines-overview.md)

>[!div class="nextstepaction"]
>[Iniziare a usare le pipeline di distribuzione](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[Informazioni sul processo delle pipeline di distribuzione](deployment-pipelines-process.md)

>[!div class="nextstepaction"]
>[Procedure consigliate per le pipeline di distribuzione](deployment-pipelines-best-practices.md)