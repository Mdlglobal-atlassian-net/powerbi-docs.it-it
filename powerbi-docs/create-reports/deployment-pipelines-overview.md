---
title: Panoramica delle pipeline di distribuzione
description: Informazioni sulle pipeline di distribuzione in Power BI
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-service
ms.date: 05/06/2020
ms.openlocfilehash: be945d1d9612804a90c14c47d2c468f5ed5a843f
ms.sourcegitcommit: 008467dc9d4f88f91728c59caeb68b7db94f267c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2020
ms.locfileid: "82885031"
---
# <a name="introduction-to-deployment-pipelines-preview"></a>Introduzione alle pipeline di distribuzione (anteprima)

Nel mondo di oggi l'analisi è un componente essenziale del processo decisionale in quasi tutte le organizzazioni. L'uso crescente di Power BI come strumento di analisi richiede che possa usare più dati, che sia accattivante nonché intuitivo. Power BI deve comunque essere prima di tutto sempre disponibile e affidabile. Per soddisfare questi requisiti, i creatori di BI devono collaborare in modo efficace.

Le pipeline di distribuzione sono uno strumento efficiente e riutilizzabile che consente agli autori di BI in un'azienda con capacità Premium di gestire il ciclo di vita del contenuto aziendale. In questo modo è possibile sviluppare e testare contenuto Power BI, ad esempio report, dashboard e set di dati prima che vengano utilizzati dagli utenti finali.

Lo strumento è progettato come una pipeline a tre fasi:

* **<a name="development"></a>Sviluppo**
    
    Questa fase viene usata per progettare, creare e caricare nuovo contenuto con altri autori. Si tratta della prima fase delle pipeline di distribuzione.

* **<a name="test"></a>Test**

    Dopo aver caricato il contenuto e aver apportato tutte le modifiche nella fase di sviluppo, il contenuto può essere spostato in questa fase per essere sottoposto a test. Di seguito sono riportati tre esempi di operazioni possibili nell'ambiente di test:

    * Condividere il contenuto con tester e revisori

    * Caricare ed eseguire test con volumi di dati più elevati

    * Testare l'app per vedere come sarà visualizzata dagli utenti finali

* **<a name="production"></a>Produzione**

    Dopo aver testato il contenuto, usare la fase di produzione per condividere la versione finale del contenuto con gli utenti aziendali all'interno dell'organizzazione.

![pipeline di distribuzione](media/deployment-pipelines-overview/deployment-pipelines.png)

## <a name="next-steps"></a>Passaggi successivi

>[!div class="nextstepaction"]
>[Iniziare a usare le pipeline di distribuzione](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[Informazioni sul processo delle pipeline di distribuzione](deployment-pipelines-process.md)

>[!div class="nextstepaction"]
>[Risoluzione dei problemi delle pipeline di distribuzione](deployment-pipelines-troubleshooting.md)

>[!div class="nextstepaction"]
>[Procedure consigliate per le pipeline di distribuzione](deployment-pipelines-best-practices.md)