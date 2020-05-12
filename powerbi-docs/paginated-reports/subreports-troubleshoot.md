---
title: Risolvere i problemi relativi ai sottoreport nei report impaginati di Power BI
description: In questo articolo sono descritte le origini dati supportate per i report impaginati del servizio Power BI ed è illustrato come connettersi alle origini dati del database SQL di Azure.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 04/29/2020
ms.openlocfilehash: 6de85f6dda69e902a98d6ee63d1fc4b86fb4180b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82615635"
---
# <a name="troubleshoot-subreports-in-power-bi-paginated-reports"></a>Risolvere i problemi relativi ai sottoreport nei report impaginati di Power BI

In alcuni casi, quando si usano sottoreport nei report impaginati, è possibile ottenere un risultato imprevisto oppure la funzionalità non corrisponde alle aspettative. In questo articolo vengono fornite soluzioni per i problemi comuni relativi all'uso dei sottoreport. Un *sottoreport* è un elemento del report in cui viene visualizzato un altro report all'interno del corpo del report impaginato principale. Per altre informazioni, vedere [Sottoreport nei report impaginati di Power BI](subreports.md).

## <a name="subreport-couldnt-be-found"></a>Non è possibile trovare il sottoreport

**Descrizione:** non viene eseguito il rendering del sottoreport. Viene invece visualizzato un messaggio di errore.

### <a name="message"></a>Message

"Non è stato possibile trovare il sottoreport 'Subreport1' nel percorso specificato 'CustomerDetails'. Verificare che il sottoreport sia stato pubblicato e che il nome sia corretto."

### <a name="possible-reasons"></a>Motivi possibili

- Non esiste un sottoreport con il nome specificato nella stessa area di lavoro o app del report principale.
- L'utente non ha accesso al sottoreport.
- Il numero di sottoreport nel report principale ha raggiunto il limite di sottoreport (50 sottoreport).

### <a name="troubleshooting-steps"></a>Passaggi per la risoluzione dei problemi

**In un'area di lavoro**

- Verificare che il report con il nome nel messaggio di errore esista. Per il nome non viene fatta distinzione tra maiuscole e minuscole.

**In un'app**

- Verificare che il report con il nome nel messaggio di errore esista nell'app. Per ulteriore assistenza, contattare l'autore dell'app.

**Se il report è condiviso**

1. Verificare che il report con il nome nel messaggio di errore sia stato condiviso con l'utente che riscontra il problema.
2. Se il report esiste, verificare che il nome del proprietario sia lo stesso per il report principale e il sottoreport. Contattare quindi il proprietario del report principale con tali informazioni.

## <a name="subreport-renders-with-unexpected-content"></a>Il rendering del sottoreport viene eseguito con contenuto imprevisto

### <a name="possible-reason"></a>Possibile motivo

Power BI consente agli utenti di avere più report con lo stesso nome nella stessa area di lavoro

### <a name="troubleshooting-steps-for-report-authors"></a>Passaggi per la risoluzione dei problemi (per gli autori di report)

1. Aprire il report principale in Power BI Report Builder e determinare il nome del sottoreport.
2. Cercare report con lo stesso nome nell'area di lavoro.
3. Individuare il report previsto e rinominare i restanti.

**Per gli utenti non autori:** contattare l'autore.

## <a name="data-retrieval-fails"></a>Errore di recupero dei dati

**Descrizione:** il recupero dei dati ha esito negativo durante il rendering del sottoreport. Non viene eseguito il rendering del sottoreport. Viene invece visualizzato un messaggio di errore.

### <a name="message"></a>Message

"Il recupero dei dati non è riuscito per il sottoreport 'Subreport1' nel percorso 'InvoiceDetails'. Per altre informazioni, vedere i file di log."

### <a name="troubleshooting-steps"></a>Passaggi per la risoluzione dei problemi

Uguale ai passaggi per la risoluzione dei problemi generali relativi ai report con problemi di accesso ai dati.

## <a name="rendering-fails-unspecified-parameters"></a>Errore di rendering: parametri non specificati

**Descrizione:** il rendering del sottoreport non riesce a causa di parametri non specificati. Il sottoreport ha parametri obbligatori, ma il report principale non li imposta tutti.

### <a name="message"></a>Message 
Non sono stati specificati uno o più parametri per il sottoreport 'Subreport1' nel percorso 'SubreportAWithDS'."

### <a name="troubleshooting-steps-for-the-report-author"></a>Passaggi per la risoluzione dei problemi (per gli autori di report)

1. Aprire il report principale in Power BI Report Builder.
2. Aprire il sottoreport in Power BI Report Builder.
3. Verificare che il set di parametri passati all'interno dell'elemento del report del sottoreport nel report principale corrisponda al set di parametri nel sottoreport.

**Per gli utenti non autori:** contattare l'autore.

## <a name="rendering-fails-recursion-limit"></a>Errore di rendering: limite di ricorsione

**Descrizione:** il rendering del sottoreport non riesce a causa del limite di ricorsione. I sottoreport non possono essere annidati più di 20 livelli.

### <a name="message"></a>Message

"Il report o il sottoreport include un sottoreport ricorsivo 'Subreport1', che ha superato il limite massimo consentito per le ricorsioni."

### <a name="troubleshooting-steps-for-report-authors"></a>Passaggi per la risoluzione dei problemi (per gli autori di report)

- Ridurre l'annidamento.
- Riprogettare la struttura del report.

## <a name="other-errors"></a>Altri errori

**Descrizione:** errori che non rientrano nelle categorie precedenti.

### <a name="message"></a>Message

"Error: impossibile visualizzare il sottoreport."

### <a name="possible-reasons"></a>Motivi possibili

- Più errori durante il rendering del sottoreport, ad esempio parametri non corrispondenti con problemi di recupero dei dati.
- Errori imprevisti.

### <a name="troubleshooting-steps-for-report-authors"></a>Passaggi per la risoluzione dei problemi (per gli autori di report)

1. Verificare che sia possibile eseguire direttamente il rendering del sottoreport.
2. Se è possibile eseguire il rendering del sottoreport, controllare i parametri sia nel sottoreport che nel report principale.
3. Verificare che il report principale non contenga più di 50 sottoreport univoci e che il sottoreport non includa più di 20 livelli di annidamento.
4. Se non è possibile risolvere il problema, contattare il supporto tecnico di Power BI.

**Per gli utenti non autori:** contattare l'autore.

## <a name="next-steps"></a>Passaggi successivi

[Sottoreport nei report impaginati di Power BI](subreports.md)

[Visualizzare un report impaginato nel servizio Power BI](../consumer/paginated-reports-view-power-bi-service.md)

Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)
