---
title: Come trovare il codice Product Key del server di report
description: "Informazioni su come è possibile trovare il codice Product Key del server di report di Power BI per installare il server in un ambiente di produzione."
services: powerbi
documentationcenter: 
author: guyinacube
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
ms.date: 11/01/2017
ms.author: maghan
ms.openlocfilehash: 13bf32939630a813f2f942fc2075f25c7bc1374a
ms.sourcegitcommit: eec6b47970bf69ed30638d1a20051f961ba792f2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/06/2018
---
# <a name="how-to-find-your-report-server-product-key"></a>Come trovare il codice Product Key del server di report
Informazioni su come è possibile trovare il codice Product Key del server di report di Power BI per installare il server in un ambiente di produzione.

<iframe width="640" height="360" src="https://www.youtube.com/embed/6CQnf-NGtpU?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

Si è scaricato il server di report di Power BI e sottoscritto un contratto SQL Server Enterprise Software Assurance oppure si è acquistato Power BI Premium. Si vuole installare il server in un ambiente di produzione, ma è necessario un codice Product Key a tale scopo. Dove è il codice Product Key? 

Il codice Product Key sarà in una di due posizioni a seconda di ciò che è stato acquistato.

## <a name="purchased-power-bi-premium"></a>Acquisto di Power BI Premium
Se è stato acquistato Power BI Premium, nella scheda **Impostazioni di capacità** del portale di amministratore di Power BI, si avrà accesso al codice Product Key del Server di Report di Power BI. Questo sarà disponibile solo per gli amministratori globali o per gli utenti a cui è stato assegnato il ruolo di amministratore del servizio Power BI.

![Codice Product Key del Server di report di Power BI all'interno di Impostazioni Premium](media/find-product-key/pbirs-product-key.png)

Se si seleziona **Chiave del server di report di Power BI** viene visualizzata una finestra di dialogo contenente il codice Product Key. È possibile copiarlo e usarlo durante l'installazione.

![Codice Product Key del Server di report Power BI](media/find-product-key/pbirs-product-key-dialog.png)

## <a name="purchased-software-assurance-agreeemnt"></a>Acquisto del contratto Software Assurance
Se si ha un contratto SQL Server Enterprise SA, è possibile ottenere il codice Product Key dal [Centro servizi per contratti multilicenza](https://www.microsoft.com/Licensing/servicecenter/). Cercare l'ultima versione di SQL Server nel service pack più recente. Se non è presente, cercare nell'ultima versione RTM di SQL Server.

> [!NOTE]
> È necessario cercare nella sezione dedicata ai download, non in quella delle chiavi.
> 
> 

![](media/find-product-key/vlsc-download.png "Centro servizi per contratti multilicenza")

## <a name="next-steps"></a>Passaggi successivi
[Avvio rapido: installazione del Server di report di Power BI](quickstart-install-report-server.md)  
[Installare Power BI Desktop ottimizzato per il server di report di Power BI](install-powerbi-desktop.md)  
[Installare Generatore report](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Scaricare SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)

