---
title: Parametri dei report in Generatore report di Power BI
description: Questo argomento descrive gli usi comuni per i parametri dei report di Generatore report impaginati di Power BI, le proprietà che è possibile impostare e molto altro ancora.
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.custom: ''
ms.date: 06/06/2019
ms.openlocfilehash: d31036676a5960f7f6eb0f346c2c02ab979ff9bc
ms.sourcegitcommit: 01de0b01f66f28ca45b8d309d7864f261d6c9a85
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2019
ms.locfileid: "74128434"
---
# <a name="report-parameters-in-power-bi-report-builder"></a>Parametri dei report in Generatore report di Power BI

Questo argomento descrive gli usi comuni per i parametri dei report di Generatore report impaginati di Power BI, le proprietà che è possibile impostare e molto altro ancora. I parametri dei report consentono di controllare i dati dei report, connettere report correlati e variare la presentazione dei report. È possibile usare i parametri dei report nei report impaginati creati in Generatore report.

## <a name="bkmk_Common_Uses_for_Parameters"></a> Usi comuni per i parametri

 Ecco alcuni dei modi d'uso più comuni dei parametri.  
  
**Controllo dei dati dei report impaginati**
  
- È possibile filtrare i dati dei report impaginati a livello di origine dati tramite la scrittura di query contenenti variabili da eseguire sul set di dati.  
  
- È possibile consentire agli utenti di specificare valori per la personalizzazione dei dati di un report impaginato. Specificare, ad esempio, due parametri, rispettivamente per la data di inizio e la data di fine, per una serie di dati di vendita.  
  
**Presentazione variata dei report**
  
- È possibile consentire agli utenti di specificare valori per la personalizzazione dell'aspetto di un report. Specificare, ad esempio, un parametro booleano per indicare se espandere o comprimere tutti i gruppi di righe annidati in una tabella.  
  
- È possibile consentire agli utenti di personalizzare i dati e l'aspetto del report tramite l'inserimento di parametri in un'espressione.  
  
## <a name="UserInterface"></a> Visualizzazione di un report con parametri

Quando si apre un report con parametri, nella barra degli strumenti del Visualizzatore di report viene visualizzato ogni parametro in modo da poter specificare i valori in modo interattivo. La figura seguente mostra l'area dei parametri di un report con i parametri @ReportMonth, @ReportYear, @EmployeeID, @ShowAll, @ExpandTableRows, @CategoryQuota e @SalesDate.  

![Visualizzare un report con parametri](media/report-builder-parameters/report-builder-parameters-power-bi-service.png "Visualizzare un report con parametri")
  
1. **Riquadro dei parametri** La barra degli strumenti del Visualizzatore di report visualizza una richiesta di inserimento e un valore predefinito per ogni parametro. È possibile personalizzare il layout dei parametri nel riquadro dei parametri.  
  
2. **@SalesDate parametro** il parametro @SalesDate è di tipo di dati **DateTime**. Accanto alla casella di testo è visualizzata la richiesta Selezionare la data. Per modificare la data, digitare una nuova data nella casella di testo o usare il controllo calendario.  
  
3. **@ShowAll parametro** il parametro @ShowAll è di tipo di dati **booleano**. Usare i pulsanti di opzione per specificare **Vero** o **Falso**.  
  
4. **Quadratino di ridimensionamento Mostra o Nascondi area parametri** Sulla barra degli strumenti del Visualizzatore di report fare clic su questa freccia per visualizzare o nascondere il riquadro dei parametri.  
  
5. **@CategoryQuota parametro** il parametro @CategoryQuota è di tipo di dati **Float**, in modo che accetta un valore numerico.  @CategoryQuota è impostato in modo da consentire più valori.  
  
6. **Visualizza report** Dopo avere immesso i valori dei parametri, fare clic su **Visualizza report** per eseguire il report. Se a tutti i parametri sono associati valori predefiniti, il report viene eseguito automaticamente alla prima visualizzazione.  
  
## <a name="bkmk_Create_Parameters"></a> Creazione di parametri

È possibile creare parametri di report in alcuni modi diversi.
  
> [!NOTE]
>  Non tutte le origini dati supportano parametri.
  
**Query o stored procedure con parametri per il set di dati**
  
 Aggiungere una query contenente variabili o una stored procedure contenente parametri di input per il set di dati. Per ogni variabile o parametro di input viene creato un parametro di set di dati e per ogni parametro di set di dati viene creato un parametro di report.  
  
![Proprietà del set di dati relative ai parametri in Generatore report](media/report-builder-parameters/report-builder-parameter-dataset.png "Proprietà del set di dati relative ai parametri in Generatore report")

  
 Questa immagine di Generatore report illustra:  
  
1.  I parametri del report nel riquadro Dati report.  
  
2.  Il set di dati con i parametri.  
  
3.  Il riquadro Parametri.  
  
4.  I parametri elencati nella finestra di dialogo Proprietà Set di dati.  
  
**Creare un parametro manualmente**
  
È possibile creare un parametro manualmente dal riquadro dei dati del report. È possibile configurare i parametri di un report in modo che un utente possa immettere valori in modo interattivo per facilitare la personalizzazione del contenuto o dell'aspetto del report. È anche possibile configurare i parametri del report in modo che un utente non possa modificare i valori preconfigurati.  
  
> [!NOTE]  
>  Poiché i parametri vengono gestiti in modo indipendente nel server, una nuova pubblicazione di un report principale con nuove impostazioni dei parametri non sovrascrive le impostazioni dei parametri esistenti nel report.  

### <a name="parameter-values"></a>Valori dei parametri

 Di seguito sono indicate le opzioni per la selezione dei valori dei parametri nel report.  
  
- Selezionare un singolo valore di parametro da un elenco a discesa.  
  
- Selezionare più valori di parametro da un elenco a discesa.  
  
- Selezionare un valore da un elenco a discesa per un parametro che determina i valori disponibili nell'elenco a discesa per un altro parametro. È il caso dei parametri a catena. I parametri a catena consentono di filtrare in successione i valori dei parametri dall'ordine delle migliaia a un numero gestibile.  
  
- Eseguire il report senza dover per prima cosa selezionare il valore di un parametro, perché per quest'ultimo è stato creato un valore predefinito.  
  
## <a name="bkmk_Report_Parameters"></a> Proprietà dei parametri dei report

 È possibile modificare le proprietà dei parametri dei report usando la finestra di dialogo Proprietà report. La tabella seguente riepiloga le proprietà che è possibile impostare per ogni parametro:  
  
|Property|Descrizione|  
|--------------|-----------------|  
|Nome|Digitare un nome con distinzione maiuscole/minuscole per il parametro. Il nome deve iniziare con una lettera e può contenere lettere, numeri e un carattere di sottolineatura (_). Il nome non può contenere spazi. Per i parametri generati automaticamente, il nome corrisponde al parametro nella query del set di dati. Per impostazione predefinita, i nomi dei parametri creati manualmente sono simili a ParametroReport1.|  
|Messaggio di richiesta|Il testo visualizzato accanto al parametro sulla barra degli strumenti del Visualizzatore di report.|  
|Tipo di dati|Il tipo di un parametro di report deve essere uno dei seguenti:<br /><br /> **Boolean**. L'utente seleziona Vero o Falso da un pulsante di opzione.<br /><br /> **DateTime**. L'utente seleziona una data da un controllo calendario.<br /><br /> **Integer**. L'utente digita valori in una casella di testo.<br /><br /> **Float**. L'utente digita valori in una casella di testo.<br /><br /> **Text**. L'utente digita valori in una casella di testo.<br /><br /> Quando per un parametro sono disponibili valori definiti, l'utente sceglie i valori da un elenco a discesa, anche quando il tipo di dati è **DateTime**.|  
|Consenti nessun valore|Selezionare questa opzione se il valore del parametro può essere una stringa vuota o uno spazio.<br /><br /> Se si specificano valori validi per un parametro e si vuole che un valore vuoto sia uno dei valori validi, è necessario includere tale valore tra i valori specificati. Selezionando questa opzione non si include automaticamente un valore vuoto come valore disponibile.|  
|Consenti valore Null|Selezionare questa opzione se il valore del parametro può essere Null.<br /><br /> Se si specificano valori validi per un parametro e si vuole che Null sia uno dei valori validi, è necessario includere Null tra i valori specificati. Selezionando questa opzione non si include automaticamente Null come valore disponibile.|  
|Consenti più valori|Specificare i valori disponibili per creare un elenco a discesa da cui gli utenti possono scegliere. Si tratta di un metodo efficace per assicurarsi che vengano inviati solo valori validi nella query di set di dati.<br /><br /> Selezionare questa opzione se il parametro può avere più valori tra quelli visualizzati in un elenco a discesa. I valori Null non sono consentiti. Quando questa opzione è selezionata, all'elenco dei valori disponibili nell'elenco a discesa del parametro vengono aggiunte caselle di controllo. Nella parte superiore dell'elenco è presente la casella di controllo **Seleziona tutto**. Gli utenti possono selezionare i valori voluti.<br /><br /> Se i dati che rappresentano i valori cambiano rapidamente, l'elenco visualizzato dall'utente può non essere il più aggiornato.|  
|Visibile|Selezionare questa opzione per visualizzare il parametro del report nella parte superiore del report stesso quando viene eseguito. Questa opzione consente agli utenti di selezionare valori dei parametri in fase di esecuzione.|  
|Nascosto|Selezionare questa opzione per nascondere il parametro nel report pubblicato. I valori del parametro del report possono comunque essere impostati nell'URL del report, nella definizione di una sottoscrizione o nel server di report.|  
|Interni|Selezionare questa opzione per nascondere il parametro del report. Nel report pubblicato, il parametro potrà essere visualizzato solo nella definizione del report.|  
|Valori disponibili|Se sono stati specificati valori disponibili per un parametro, i valori validi vengono sempre visualizzati sotto forma di elenco a discesa. Se ad esempio si specificano valori disponibili per un parametro **DateTime**, nel riquadro del parametro viene visualizzato un elenco a discesa per le date, anziché un controllo calendario.<br /><br /> Per garantire la coerenza di un elenco di valori tra report e sottoreport, è possibile impostare un'opzione nell'origine dati in modo da usare un'unica transazione per tutte le query nei set di dati associati a un'origine dati.<br /><br /> **Nota sulla sicurezza** In qualsiasi report che includa un parametro con tipo di dati **Text** assicurarsi di usare un elenco di valori disponibili (detto anche elenco di valori validi) e verificare che tutti gli utenti che eseguono il report abbiano solo le autorizzazioni necessarie per visualizzare i dati all'interno del report.|  
|Valori predefiniti|Impostare i valori predefiniti da una query o da un elenco statico.<br /><br /> Se a ogni parametro è associato un valore predefinito, il report viene eseguito automaticamente alla prima visualizzazione.|  
|Avanzate|Impostare l'attributo di definizione del report **UsedInQuery**, un valore che indica se questo parametro influisce direttamente o indirettamente sui dati in un report.<br /><br /> **Determina automaticamente quando eseguire l'aggiornamento**<br /> Scegliere questa opzione se si vuole che il componente Elaborazione report determini un'impostazione per questo valore. Il valore è **True** se il componente Elaborazione report rileva una query del set di dati con un riferimento diretto o indiretto a questo parametro o se il report contiene sottoreport.<br /><br /> **Aggiorna sempre**<br /> Scegliere questa opzione se il parametro di report viene usato direttamente o indirettamente in una query di set di dati o un'espressione di parametro. Questa opzione imposta **UsedInQuery** su True.<br /><br /> **Non aggiornare mai**<br /> Scegliere questa opzione se il parametro di report non viene usato direttamente o indirettamente in una query di set di dati o in un'espressione di parametro. Questa opzione imposta **UsedInQuery** su False.<br /><br /> **Attenzione** Usare **Non aggiornare mai** con cautela. Nel server di report, l'attributo **UsedInQuery** viene usato per consentire il controllo delle opzioni della cache per i dati di report e per i report visualizzabili, nonché le opzioni di parametro per i report snapshot. Se si imposta **Non aggiornare mai** in modo errato, si può provocare la memorizzazione nella cache di dati di report o di report non corretti o causare l'incoerenza dei dati di un report snapshot. |  
  
##  <a name="bkmk_Dataset_Parameters"></a> Query di set di dati  
 Per filtrare i dati in una query di set di dati, è possibile includere una clausola di restrizione che limiti i dati recuperati specificando i valori da includere o escludere dal set di risultati.  
  
 Usare la funzionalità di progettazione query per l'origine dati per creare una query con parametri in modo più semplice.  
  
-   Per le query Transact-SQL, origini dati diverse supportano una sintassi diversa per i parametri. Supportano intervalli di parametri identificati nella query in base alla posizione o al nome. Nella progettazione query relazionale, per creare una query con parametri è necessario selezionare l'opzione relativa ai parametri.   
  
-   Per le query basate su un'origine dati multidimensionale, ad esempio Microsoft SQL Server Analysis Services, è possibile specificare se creare un parametro basato su un filtro specificato dall'utente nella progettazione query. 
  
##  <a name="bkmk_Manage_Parameters"></a> Gestione dei parametri per un report pubblicato  
 Quando si progetta un report, i parametri di questo vengono salvati nella relativa definizione. Quando si pubblica un report, i parametri di questo vengono salvati e gestiti separatamente dalla sua definizione.  
  
 Per un report pubblicato, è possibile usare quanto segue:  
  
-   **Proprietà dei parametri dei report.** Modificare i valori dei parametri del report direttamente nel server di report, indipendentemente dalla definizione del report.  
  
-   **Sottoscrizioni report.** È possibile specificare valori di parametri per filtrare i dati e recapitare report tramite sottoscrizioni. 
  
 Le proprietà dei parametri per un report pubblicato vengono mantenute se si pubblica di nuovo la definizione del report. Se la definizione del report usata di nuovo per pubblicare lo stesso report e i tipi di dati e i nomi dei parametri rimangono invariati, le impostazioni delle proprietà vengono mantenute. Se si aggiungono o eliminano parametri nella definizione del report o si cambia il tipo di dati o il nome di un parametro esistente, può essere necessario modificare le proprietà dei parametri nel report pubblicato.  
  
 Non tutti i parametri possono essere modificati in tutti i casi. Se a un parametro di un report viene assegnato un valore predefinito da una query di set di dati, tale valore non può essere modificato per un report pubblicato e non può essere modificato nel server di report. Il valore usato in fase di esecuzione viene determinato quando viene eseguita la query o, nel caso di parametri basati su espressione, quando l'espressione viene valutata.  
  
 Le opzioni di esecuzione di un report possono influire sulla modalità di elaborazione dei parametri. Un report eseguito come snapshot può usare parametri derivati da una query solo se la query include valori predefiniti per i parametri.  
  
##  <a name="bkmk_Parameters_Subscription"></a> Parametri per una sottoscrizione  
 È possibile definire una sottoscrizione per un report su richiesta o per un report snapshot e specificare i valori dei parametri da usare durante l'elaborazione della sottoscrizione.  
  
-   **Report su richiesta.**  Per un report su richiesta è possibile specificare un valore di parametro diverso da quello pubblicato per ogni parametro elencato per il report. Si supponga, ad esempio, che il report di un servizio di assistenza telefonica usi il parametro*Periodo di tempo* per restituire le richieste di assistenza dei clienti per il giorno, la settimana o il mese corrente. Se il valore predefinito del parametro per il report è impostato su **oggi**, la sottoscrizione può usare un valore diverso del parametro (ad esempio **settimana** o **mese**) per generare un report che contenga i dati settimanali o mensili.  
  
## <a name="next-steps"></a>Passaggi successivi

- [Che cosa sono i report impaginati in Power BI Premium?](paginated-reports-report-builder-power-bi.md)  
 
 
