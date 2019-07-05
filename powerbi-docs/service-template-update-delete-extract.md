---
title: Aggiornare, eliminare ed estrarre un'app modello di Power BI
description: Come aggiornare, eliminare ed estrarre un'app modello.
author: teddybercovitz
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/10/2019
ms.author: tebercov
ms.openlocfilehash: 273734493c761739f9780e6a7fe6e781900723f9
ms.sourcegitcommit: 7d52401f50944feaaa112c84113ee47f606dbf68
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/13/2019
ms.locfileid: "67125879"
---
# <a name="update-delete-and-extract-template-app"></a>Aggiornare, eliminare ed estrarre un'app modello

Ora che l'app è in fase di produzione è possibile riattivare la fase di test, senza alcun effetto sull'app nell'ambiente di produzione.
## <a name="update-your-app"></a>Aggiornare l'app


1. Nel riquadro **Release Management** selezionare **Crea app**.
2. Ripetere il processo di creazione app.
3. Dopo aver impostato le opzioni in **Personalizzazione**, **Contenuto**, **Controllo** e **Accesso** selezionare di nuovo **Crea app**.
4. Selezionare **Chiudi** e tornare a **Release Management**.

   Ora sono disponibili due versioni: la versione nell'ambiente di produzione e una nuova versione di test.

    ![Due versioni di un'app modello](media/service-template-apps-update-extract-delete/power-bi-template-app-update.png)

5. Quando si è pronti per alzare di livello l'app alla pre-produzione per altri test all'esterno del tenant, tornare al riquadro Gestione del rilascio e selezionare **Alza di livello app** accanto a **Test**.
6. Il collegamento è ora attivo. Eseguire di nuovo l'invio al portale Cloud Partner (CPP) seguendo la procedura in [Aggiornare un'offerta di app Power BI](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-update-existing-offer).
7. Nel portale Cloud Partner è necessario **pubblicare** di nuovo l'offerta e farla convalidare di nuovo.

>[!NOTE]
>Alzare di livello l'app alla fase di produzione solo dopo che l'app è stata approvata nel portale Cloud Partner e pubblicata.

## <a name="extract-workspace"></a>Estrarre l'area di lavoro
Eseguire il rollback alla versione precedente di un'app modello è ora più facile che mai grazie alla funzionalità di estrazione. La procedura seguente consente di estrarre una versione specifica dell'app da diverse fasi di rilascio in una nuova area di lavoro:

1. Nel riquadro di gestione del rilascio premere **(...)** e quindi **Estrai**.

    ![estrarre una versione dell'app modello](media/service-template-apps-update-extract-delete/power-bi-template-app-extract.png) ![estrarre una versione dell'app modello](media/service-template-apps-update-extract-delete/power-bi-template-app-extract-dialog.png)
2. Nella finestra di dialogo immettere il nome dell'area di lavoro estratta. Verrà aggiunta una nuova area di lavoro.

Il controllo delle versioni della nuova area di lavoro viene reimpostato ed è possibile continuare a sviluppare e distribuire l'app modello dalla nuova area di lavoro estratta.

## <a name="delete-template-app-version"></a>Eliminare una versione dell'app modello
Un'area di lavoro di un'app di modello è l'origine di un'app modello distribuita attiva. Per proteggere gli utenti dell'app modello, non è possibile eliminare un'area di lavoro senza prima rimuovere tutte le versioni dell'app create nell'area di lavoro.
L'eliminazione di una versione dell'app comporta anche l'eliminazione dell'URL dell'app, che non funzionerà più.

1. Nel riquadro di gestione del rilascio selezionare i puntini di sospensione **(...)** e quindi **Elimina**.
 ![Eliminare una versione dell'app modello](media/service-template-apps-update-extract-delete/power-bi-template-app-delete.png)
 ![Eliminare una versione dell'app modello](media/service-template-apps-update-extract-delete/power-bi-template-app-delete-dialog.png)

>[!NOTE]
>Assicurarsi di non eliminare una versione dell'app in uso dai clienti o in **AppSource**, in quanto in tal caso non funzionerà più.

## <a name="next-steps"></a>Passaggi successivi

Osservare come i clienti interagiscono con l'app modello in [Install, customize, and distribute template apps in your organization](service-template-apps-install-distribute.md) (Installare, personalizzare e distribuire app modello nell'organizzazione).

Per informazioni dettagliate sulla distribuzione dell'app, vedere [Offerta di applicazione Power BI](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer).
