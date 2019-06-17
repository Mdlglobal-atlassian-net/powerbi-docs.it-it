---
title: Da cartella di lavoro di Excel a straordinari report in pochissimo tempo
description: Da cartella di lavoro di Excel a straordinari report in pochissimo tempo
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/28/2018
ms.author: maggies
LocalizationGroup: Data from files
ms.openlocfilehash: cd75aebb09c7b6c54c1ff3f68635bfd5033c7f80
ms.sourcegitcommit: 762857c8ca09ce222cc3f8b006fa1b65d11e4ace
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2019
ms.locfileid: "66721474"
---
# <a name="from-excel-workbook-to-stunning-report-in-no-time"></a>Da cartella di lavoro di Excel a straordinari report in pochissimo tempo
Il manager desidera visualizzare un report sulle ultime cifre di vendita combinate con le ultime impressioni sulla campagna entro la fine del giorno. Mentre i dati più recenti si trovano su vari sistemi di terze parti e sui file nel computer portatile. In passato si avrebbero impiegato ore per creare elementi visivi e formattare un report. L'ansia sale.

Niente panico. Con Power BI, è possibile creare un report straordinario in poco tempo.

In questo esempio, si caricherà un file di Excel da un sistema locale, si creerà un nuovo report e lo si condividerà con i colleghi, tutto da Power BI.

## <a name="prepare-your-data"></a>Preparare i dati
Si prenderà un semplice file di Excel come esempio. Prima di caricare il file di Excel in Power BI, è necessario organizzare i dati in una tabella flat. Ciò significa che ogni colonna contiene lo stesso tipo di dati, ad esempio, testo, data, numero o valuta. È necessaria una riga di intestazione, ma non dovrebbe essere presente una colonna o una riga in cui vengono visualizzati i totali.

![Dati organizzati in Excel](media/service-from-excel-to-stunning-report/pbi_excel_file.png)

Successivamente, formattare i dati come una tabella. In Excel, nella scheda Home, nel gruppo di stili, selezionare **Formatta come tabella**. Selezionare uno stile di tabella da applicare al foglio di lavoro. Il foglio di lavoro di Excel è ora pronto per essere caricato in Power BI.

![Dati formattati come tabella](media/service-from-excel-to-stunning-report/pbi_excel_table.png)

## <a name="upload-your-excel-file-into-power-bi"></a>Caricare il file di Excel in Power BI
Power BI si connette a molte origini dati, inclusi i file di Excel che risiedono nel computer in uso. Per iniziare, accedere al servizio Power BI. Se non si è ancora iscritti, [è possibile farlo gratuitamente](https://powerbi.com).

Si desidera creare un nuovo dashboard. Aprire **Area di lavoro personale** e selezionare l'icona **+ Crea**.

![Icona Crea](media/service-from-excel-to-stunning-report/power-bi-new-dash.png)

Selezionare **Dashboard**, immettere un nome e scegliere **Crea**. Verrà visualizzato il nuovo dashboard senza dati.

![Elenco a discesa Crea](media/service-from-excel-to-stunning-report/power-bi-create-dash.png)

Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro. Nella pagina Recupera dati, in Importa o Connetti ai dati, nella casella file, selezionare **Recupera**.

![Ottenere dati da file](media/service-from-excel-to-stunning-report/pbi_get_files.png)

Nella pagina del file, selezionare **File locale**. Passare al file della cartella di lavoro di Excel nel computer in uso e selezionarlo per caricarlo in Power BI. Selezionare **Importa**.

> **NOTA**: per proseguire questa esercitazione, usare la [cartella di lavoro di esempio Financial](sample-financial-download.md).
> 
> 

![Finestra Recupera dati > File](media/service-from-excel-to-stunning-report/pbi_local_file.png)

## <a name="build-your-report"></a>Creare il report
Dopo l'importazione del file di Excel in Power BI, è possibile iniziare a creare il report. Quando viene visualizzato il messaggio **Il set di dati è pronto**, selezionare **Visualizza set di dati**.  Power BI viene aperto nella Visualizzazione di modifica e visualizza l'area di disegno report. Sul lato destro sono presenti i riquadri Visualizzazioni, Filtri e Campi.

Si noti che i dati della tabella della cartella di lavoro di Excel vengono visualizzati nel riquadro Campi. Sotto il nome della tabella, Power BI elenca le intestazioni di colonna come campi individuali.

![Aspetto dei dati di Excel nel riquadro Campi](media/service-from-excel-to-stunning-report/pbi_report_fields.png)

È ora possibile iniziare a creare le visualizzazioni. Il manager desidera vedere i profitti nel tempo. Nel riquadro Campi trascinare **Profitti** all'area di disegno report. Power BI visualizza un grafico a barre per impostazione predefinita. Trascinare quindi **Data** all'area di disegno report. Power BI aggiorna il grafico a barre per visualizzare i profitti per data.

![Istogramma nell'editor di report](media/service-from-excel-to-stunning-report/pbi_report_pin-new.png)

> **SUGGERIMENTO**: se il grafico non soddisfa le aspettative, controllare le aggregazioni. Ad esempio, nell'area **Valore** fare clic con il pulsante destro del mouse sul campo appena aggiunto e assicurarsi che i dati vengano aggregati nel modo appropriato.  In questo esempio verrà usato **Somma**.
> 
> 

La manager desidera sapere quali sono i paesi più produttivi. Sarà stupita nel vedere una visualizzazione mappa. Selezionare un'area vuota nell'area di disegno e, dal riquadro Campi, trascinare semplicemente gli elementi sui campi **Country** e quindi **Profit**. Power BI crea una mappa di visualizzazione con bolle che rappresenta il profitto relativo di ogni località.

![Oggetto visivo mappa nell'editor di report](media/service-from-excel-to-stunning-report/pbi_report_map-new.png)

Visualizzazione delle vendite per prodotti e segmenti di mercato Facile. Nel riquadro Campi, selezionare le caselle di controllo accanto ai campi Vendite, Prodotto e Segmento. Power BI crea immediatamente un grafico a barre. Modificare il tipo di grafico scegliendo una delle icone nel menu Visualizzazioni. Ad esempio, modificarlo in un grafico a barre in pila.  Per ordinare il grafico, selezionare i puntini di sospensione (...) > **Ordina per**.

![Istogramma in pila nell'editor di report](media/service-from-excel-to-stunning-report/pbi_barchart-new.png)

Aggiungere tutte le visualizzazioni al Dashboard. Si è pronti per condividerle con i colleghi.

![Dashboard con 3 oggetti visivi aggiunti](media/service-from-excel-to-stunning-report/pbi_report.png)

## <a name="share-your-dashboard"></a>Condividere il dashboard
Si desidera condividere il dashboard con la manager, Paula. Con i colleghi che dispongono di un account Power BI, è possibile condividere il dashboard e il report sottostante. Possono modificare i report, ma non salvare le modifiche.

Per condividere il report, nella parte superiore del dashboard, selezionare **Condividi**.

![Icona di condivisione](media/service-from-excel-to-stunning-report/power-bi-share.png)

Power BI visualizza la pagina Condivisione dashboard. Nell'area superiore, immettere gli indirizzi di posta elettronica dei destinatari. Aggiungere un messaggio nel campo sottostante. Per consentire ai destinatari di condividere il dashboard con altri utenti, selezionare **Consenti ai destinatari di condividere il dashboard**. Seleziona **Condividi**.

![Finestra Condividi dashboard](media/service-from-excel-to-stunning-report/power-bi-share-dash-new.png)

Passaggi successivi

* [Introduzione al servizio Power BI](service-get-started.md)
* [Introduzione a Power BI Desktop](desktop-getting-started.md)
* [Concetti di base sulle finestre di progettazione del servizio Power BI](service-basic-concepts.md)
* Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

