---
title: Sottoreport nei report impaginati di Power BI
description: In questo articolo sono descritte le origini dati supportate per i report impaginati del servizio Power BI ed è illustrato come connettersi alle origini dati del database SQL di Azure.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 04/29/2020
ms.openlocfilehash: 65d1401a66f8e670df1af3097f0e99fb6b647022
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82615704"
---
# <a name="subreports-in-power-bi-paginated-reports"></a>Sottoreport nei report impaginati di Power BI

Un *sottoreport* è un elemento del report impaginato in cui viene visualizzato un altro report impaginato all'interno del corpo del report impaginato principale. A livello concettuale, un sottoreport in un report è simile a un frame in una pagina Web. Un sottoreport viene usato per incorporare un report in un altro report. È possibile usare qualsiasi report come sottoreport. Il report visualizzato come sottoreport viene archiviato nella stessa area di lavoro Premium del report padre. È possibile progettare il report padre per il passaggio di parametri al sottoreport. Un sottoreport può essere ripetuto all'interno delle aree dati, usando un parametro per filtrare i dati in ogni istanza del sottoreport.  
  
 ![Sottoreport in un report impaginato](media/subreports/paginated-report-subreport.png "Riepilogo dei report impaginati")  
  
 In questa illustrazione, le informazioni di contatto visualizzate nel report Sales Order principale provengono da un sottoreport Contacts.  
  
È possibile creare e modificare i file di definizione di report impaginati (con estensione rdl) in Power BI Report Builder. È possibile caricare i sottoreport archiviati in SQL Server Reporting Services in un'area di lavoro Premium nel servizio Power BI. I report principali e i sottoreport devono essere pubblicati nella stessa area di lavoro. Installare [Power BI Report Builder](https://go.microsoft.com/fwlink/?linkid=2086513).
  
## <a name="work-with-report-builder-and-the-power-bi-service"></a>Usare Report Builder e il servizio Power BI

Power BI Report Builder può funzionare con i report impaginati nel computer (noti come report locali) o con i report nel servizio Power BI.  Quando si apre Report Builder per la prima volta, viene chiesto di accedere al proprio account di Power BI. In caso contrario, selezionare **Accedi** nell'angolo superiore destro.

:::image type="content" source="media/subreports/report-builder-sign-in.png" alt-text="Accedere a Power BI":::

Dopo aver eseguito l'accesso, viene visualizzata un'opzione **Servizio Power BI** in Power BI Report Builder per le opzioni **Apri** e **Salva con nome** nel menu **File**. Quando si seleziona l'opzione **Servizio Power BI** per salvare un report, si crea una connessione in tempo reale tra Power BI Report Builder e il servizio Power BI. 

:::image type="content" source="media/subreports/report-builder-subreport-open-service.png" alt-text="Apertura dal servizio Power BI":::

## <a name="save-a-local-report-to-the-power-bi-service"></a>Salvare un report locale nel servizio Power BI

Prima di poter aggiungere un sottoreport a un report principale, è necessario creare i due report e salvarli nella stessa area di lavoro di Power BI Premium. 

1. Per aprire un report locale esistente, scegliere **Apri** > **Questo PC** dal menu **File** e selezionare un file con estensione rdl.  

2. Scegliere **Salva con nome** > **Servizio Power BI** dal menu **File**.  Per informazioni dettagliate, vedere [Pubblicare un report impaginato nel servizio Power BI](paginated-reports-save-to-power-bi-service.md).

    > [!NOTE]
    > È anche possibile caricare un report iniziando dal servizio Power BI. Sono disponibili informazioni dettagliate nello stesso articolo, [Pubblicare un report impaginato nel servizio Power BI](paginated-reports-save-to-power-bi-service.md).

3. Nella finestra di dialogo **Salva come** selezionare un'area di lavoro di Power BI Premium in cui è possibile archiviare i report impaginati.  Le aree di lavoro Premium sono contraddistinte da un'icona a forma di diamante ![icona a forma di diamante Premium](media/subreports/report-builder-premium-diamond.png) accanto al nome.

    :::image type="content" source="media/subreports/report-builder-subreport-save-as-service.png" alt-text="Salva con nome nel servizio Power BI":::

4. Selezionare **Salva**.

## <a name="add-a-subreport-to-a-report"></a>Aggiungere un sottoreport a un report

Ora che sono stati salvati entrambi i report nella stessa area di lavoro Premium, è possibile aggiungerne uno all'altro come sottoreport. È possibile aggiungere un sottoreport in due modi. 

1. Sulla barra multifunzione **Inserisci** selezionare il pulsante **Sottoreport** oppure fare clic con il pulsante destro del mouse sul canvas del report e scegliere **Inserisci** > **Sottoreport**.

    :::image type="content" source="media/subreports/report-builder-insert-subreport.png" alt-text="Inserire un sottoreport in un report":::

    Verrà visualizzata la finestra di dialogo **Proprietà sottoreport**.  

2. Selezionare il pulsante **Sfoglia** e passare al report che si vuole usare come sottoreport, quindi specificare il nome del sottoreport nella casella di testo **Nome**.

3. Configurare altre proprietà in base alle esigenze, inclusi i [parametri](#use-parameters-in-subreports).

## <a name="use-parameters-in-subreports"></a>Usare i parametri nei sottoreport  
 Per passare parametri dal report padre al sottoreport, definire un parametro di report nel report utilizzato come sottoreport. Quando si inserisce il sottoreport nel report padre, è possibile selezionare il parametro di report e un valore da passare dal report padre al parametro di report nel sottoreport.  
  
> [!NOTE]  
> Il parametro selezionato nel sottoreport è un parametro di *report* e non un parametro di *query*.  
  
 È possibile inserire un sottoreport nel corpo principale del report o in un'area dati. Se si inserisce un sottoreport in un'area dati, il sottoreport viene ripetuto per ogni istanza del gruppo o della riga nell'area dati. È possibile passare un valore dal gruppo o dalla riga al sottoreport. Nella proprietà del valore del sottoreport usare un'espressione di campo per il campo contenente il valore che si vuole passare al parametro del sottoreport.  
  
 Per altre informazioni sull'uso di parametri e sottoreport, vedere [Aggiungere un sottoreport e i parametri](https://docs.microsoft.com/sql/reporting-services/report-design/add-a-subreport-and-parameters-report-builder-and-ssrs.md) nella documentazione di SQL Server Reporting Services.  

## <a name="preview-paginated-reports-in-report-builder"></a>Visualizzare in anteprima i report impaginati in Report Builder

È possibile visualizzare in anteprima i report in Report Builder.

- Nella scheda **Home** della barra multifunzione selezionare **Esegui**. 

Essendo uno strumento di progettazione, la visualizzazione in anteprima del report in Report Builder potrebbe essere diversa dal rendering del report nel servizio Power BI.

### <a name="notes-about-previewing"></a>Note sull'anteprima

- Report Builder non archivia le credenziali per le origini dati usate nei report.  Report Builder richiede ogni set di credenziali durante l'anteprima.  
- Se le origini dati del report sono locali, è necessario configurare un gateway dopo aver salvato il report nell'area di lavoro di Power BI.
- Se Report Builder rileva un errore durante l'anteprima, viene restituito un messaggio generico.  Se è difficile eseguire il debug dell'errore, valutare la possibilità di eseguire il rendering del report nel servizio Power BI.  

## <a name="considerations"></a>Considerazioni

### <a name="maintaining-the-connection"></a>Gestione della connessione

Report Builder non salva in modo persistente la connessione a Power BI quando si chiude il file.  È possibile usare un report principale locale con sottoreport archiviati nell'area di lavoro di Power BI. Prima di chiudere il report, assicurarsi di salvare il report principale nell'area di lavoro di Power BI.  In caso contrario, potrebbe essere generato un messaggio 'non trovato' durante l'anteprima, perché non esiste una connessione dinamica al servizio Power BI.  In tal caso, passare a un sottoreport e selezionare le relative proprietà.  Aprire di nuovo il sottoreport dal servizio Power BI.  La connessione viene ristabilita e tutti gli altri sottoreport dovrebbero essere accessibili.

### <a name="renaming-a-subreport"></a>Ridenominazione di un sottoreport

Se si rinomina un sottoreport nell'area di lavoro, è necessario correggere il riferimento al nome nel report principale. In caso contrario, non verrà eseguito il rendering del sottoreport. Il rendering del report principale viene comunque eseguito con un messaggio di errore all'interno dell'elemento del sottoreport.

## <a name="migrate-large-reports"></a>Eseguire la migrazione di report di grandi dimensioni

Se si esegue la migrazione di report di grandi dimensioni a Power BI, valutare l'uso dello strumento [RdlMigration](../guidance/migrate-ssrs-reports-to-power-bi.md).  Lo strumento RdlMigration è stato aggiornato per gestire i nomi di sottoreport duplicati.  I nomi di sottoreport duplicati possono verificarsi quando due o più report condividono lo stesso nome ma risiedono in sottodirectory diverse.  Se i nomi non vengono risolti in modo univoco, viene riconosciuto solo il primo sottoreport.

Se si vuole usare Report Builder per eseguire la migrazione di report di grandi dimensioni, è consigliabile gestire prima di tutto i sottoreport. Salvare ognuno nell'area di lavoro di Power BI per evitare nomi di report duplicati.

## <a name="share-reports-with-subreports"></a>Condividere report con sottoreport

Come già indicato, il report principale e i sottoreport devono trovarsi nella stessa area di lavoro. In caso contrario, non viene eseguito il rendering del sottoreport. Quando si condivide il report principale, è necessario condividere anche i sottoreport. Se si condivide il report principale in un'app, assicurarsi di includere anche i sottoreport nell'app. Se si condivide il report principale con utenti o gruppi di utenti direttamente, assicurarsi di condividere anche ogni sottoreport con lo stesso set di utenti o gruppi di utenti.
  
## <a name="next-steps"></a>Passaggi successivi

[Risolvere i problemi relativi ai sottoreport nei report impaginati di Power BI](subreports-troubleshoot.md)

[Visualizzare un report impaginato nel servizio Power BI](../consumer/paginated-reports-view-power-bi-service.md)

Altre domande? [Contattare la community di Power BI](https://community.powerbi.com/)
