---
title: 'Errore: Non sono stati trovati dati nella cartella di lavoro di Excel'
description: 'Errore: Non sono stati trovati dati nella cartella di lavoro di Excel'
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: ea5312178d33986ebc3f4b9e8610012c87d54216
ms.sourcegitcommit: 72c9d9ec26e17e94fccb9c5a24301028cebcdeb5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53026032"
---
# <a name="error-we-couldnt-find-any-data-in-your-excel-workbook"></a>Errore: Non sono stati trovati dati nella cartella di lavoro di Excel

>[!NOTE]
>Le informazioni di questo articolo si applicano a Excel 2007 e versioni successive.

Quando si importa una cartella di lavoro di Excel in Power BI, è possibile che venga visualizzato l'errore seguente:

*Errore: Non sono stati trovati dati nella cartella di lavoro di Excel. I dati potrebbero non essere formattati correttamente. Sarà necessario modificare la cartella di lavoro in Excel e quindi importarla di nuovo.*

![Non sono stati trovati dati nella cartella di lavoro](media/service-admin-troubleshoot-excel-workbook-data/pbi_wecouldntfindanydata.png)

## <a name="quick-solution"></a>Soluzione rapida
1. Modificare la cartella di lavoro in Excel.
2. Selezionare l'intervallo di celle che contengono i dati. La prima riga deve contenere le intestazioni di colonna, ovvero i nomi di colonna.
3. Premere **CTRL+T** per creare una tabella.
4. Salvare la cartella di lavoro.
5. Tornare a Power BI e importare di nuovo la cartella di lavoro o, se si lavora in Excel 2016 e la cartella di lavoro è stata salvata in OneDrive for Business, fare clic su File > Pubblica.

## <a name="details"></a>Dettagli
### <a name="cause"></a>Causa
In Excel, è possibile creare una **tabella** da un intervallo di celle che rende più semplice l'ordinamento, il filtro e la formattazione dei dati.

Quando si importa una cartella di lavoro di Excel, Power BI cerca queste tabelle e le importa in un set di dati. Se non vengono trovate tabelle, appare questo messaggio di errore.

### <a name="solution"></a>Soluzione
1. Aprire la cartella di lavoro in Excel. 
    >[!NOTE]
    >Le immagini si riferiscono a Excel 2013. Se si usa una versione differente, le opzioni potrebbero essere leggermente diverse, ma la procedura è identica.
    
    ![Aprire la cartella di lavoro](media/service-admin-troubleshoot-excel-workbook-data/pbi_trb_xlwksht1.png)
2. Selezionare l'intervallo di celle che contengono i dati. La prima riga deve contenere le intestazioni di colonna, ovvero i nomi di colonna:
   
    ![Selezionare l'intervallo di celle](media/service-admin-troubleshoot-excel-workbook-data/pbi_trb_xlwksht2.png)
3. Nella barra multifunzione fare clic su **Tabella** nella scheda **INSERISCI**. oppure premere **CTRL+T**.
   
    ![Inserire la tabella](media/service-admin-troubleshoot-excel-workbook-data/pbi_trb_xlwksht3.png)
4. Verrà visualizzata la finestra di dialogo seguente. Assicurarsi che l'opzione **Tabella con intestazioni** sia selezionata e fare clic su **OK**:
   
    ![Creare la tabella](media/service-admin-troubleshoot-excel-workbook-data/pbi_trb_xlcreatetbl.png)
5. I dati risultano ora formattati in una tabella:
   
    ![Dati formattati come tabella](media/service-admin-troubleshoot-excel-workbook-data/pbi_trb_xltbl.png)
6. Salvare la cartella di lavoro.
7. Tornare a Power BI. Selezionare Recupera dati nella parte inferiore del riquadro di spostamento sinistro.
   
    ![Recupera dati](media/service-admin-troubleshoot-excel-workbook-data/pbi_getdata.png)
8. Nella casella **File** selezionare **Recupera**.
   
    ![Ottenere i file](media/service-admin-troubleshoot-excel-workbook-data/pbi_getfiles.png)
9. Importare di nuovo la cartella di lavoro di Excel. Questa volta la tabella verrà trovata e l'importazione riuscirà.
   
    Se l'importazione non riesce, segnalare il problema facendo clic su **Community** nel menu della Guida:
   
    ![Collegamento alla community](media/service-admin-troubleshoot-excel-workbook-data/pbi_questionmenucommunity.png)
