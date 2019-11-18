---
title: Conformità dell'estensione per il rendering PDF alle specifiche ISO 14289-1 - Server di report di Power BI
description: Questo documento descrive la conformità dell'estensione per il rendering PDF del Server di report di Power BI e di SQL Reporting Services alle specifiche ISO 14289-1 (PDF/UA).
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 11/04/2019
ms.author: maggies
ms.openlocfilehash: c800ee995bc3c03b3cbcda91503e6dea9495f6b5
ms.sourcegitcommit: 721cf375627b010e8ad12c4c668295f38d450a17
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2019
ms.locfileid: "73638081"
---
# <a name="pdf-rendering-extension-conformance-to-iso-14289-1---power-bi-report-server"></a>Conformità dell'estensione per il rendering PDF alle specifiche ISO 14289-1 - Server di report di Power BI 

Si applica a: Server di report di Power BI e SQL Reporting Services

Questo documento descrive la conformità dell'estensione per il rendering PDF del Server di report di Power BI e di SQL Reporting Services alle specifiche [ISO 14289-1 (PDF/UA)](https://www.pdfa.org/publication/pdfua-in-a-nutshell/).

> [!NOTE]
> Per salvare o stampare questo white paper, selezionare **Stampa** nel browser, quindi selezionare **Salva come PDF**.

## <a name="1--scope"></a>1.  Ambito

Non applicabile

## <a name="2--normative-references"></a>2.  Riferimenti normativi

Non applicabile

## <a name="3--terms-and-definitions"></a>3.  Termini e definizioni

Non applicabile

## <a name="4--notation"></a>4.  Notazione

Non applicabile

## <a name="5-version-identification"></a>5. Identificazione della versione

L'estensione per il rendering PDF fornisce il supporto per lo standard PDF/UA come descritto in questo documento. In alcuni casi, come indicato di seguito, è responsabilità dell'utente eseguire le operazioni necessarie per garantire che un file PDF sia completamente conforme allo standard PDF/UA.  L'utente dovrà aggiungere gli identificatori di conformità e la versione di PDF/UA appropriati nell'ultimo passaggio di questo processo, a indicare che sono state eseguite le operazioni necessarie per rendere il PDF interamente conforme allo standard PDF/UA.

Tutti i requisiti elencati in questo documento sono basati sul rendering di un documento PDF con l'impostazione relativa alle informazioni sul dispositivo AccessiblePdf impostata su `true`. In alcuni casi, le limitazioni di conformità sono dovute alle limitazioni previste in Report Definition Language (RDL).

## <a name="6--conformance-requirements"></a>6.  Requisiti di conformità

|     Criteri     |     Supporto funzionalità     |     Osservazioni      |
|----|--------|--------|
|    6.1 General    |                 Supportato    |    L'estensione per il rendering PDF crea un file PDF versione 1.7.    |
|    6.2 Conforming files    |                 Supportata con eccezioni    |    Vedere le note nella sezione 7 - Requisiti per il formato di file.    |
|    6.3 Conforming reader    |     Non applicabile     |         |
|    6.4 Conforming assistive technology    |     Non applicabile     |         |

## <a name="7--file-format-requirements"></a>7.  Requisiti per il formato di file

|     Criteri     |     Supporto funzionalità     |     Osservazioni      |
|-----|-------|------------------------|
|    7.1 General    |                 Supportata con eccezioni    |    Tutto il contenuto effettivo verrà contrassegnato come definito nella specifica ISO 32000-1:2008, 14.8. Gli artefatti (ISO 32000-1:2008, 14.8.2.2.2) non devono essere contrassegnati con tag nell'albero della struttura. <li> L'estensione per il rendering PDF non offre la flessibilità necessaria per contrassegnare in modo esplicito singoli elementi come gli artefatti,quindi contrassegnerà come artefatti tutti gli elementi corrispondenti ai criteri nella specifica ISO 32000-1:2008, 14.8.2.2.2.<br>Il contenuto verrà contrassegnato nell'albero della struttura con tag semanticamente appropriati in un ordine di lettura logico. <br> **Nota** 4 La linea guida 1.4 per l'accessibilità dei contenuti Web (WCAG 2.0) illustra i problemi relativi a contrasto, colore e altre formattazioni per l'accessibilità. <br><li> L'utente deve verificare che il documento non sia soggetto a tali problemi. <br>I tag standard definiti nella specifica ISO 32000-1:2008, 14.8.4, non devono essere mappati nuovamente. <li> L'estensione per il rendering PDF non esegue il remapping dei tag standard. I documenti iniziano con l'elemento radice documento. <br>I file che dichiarano la conformità a questo standard internazionale dovranno avere un valore Suspects false (ISO 32000-1:2008, tabella 321). <li> L'estensione per il rendering PDF non contiene la voce Suspects. Questa proprietà è facoltativa.    |
|    7.2 Text    |                 Supportata con eccezioni    |    Il contenuto dovrà essere contrassegnato con tag nell'ordine di lettura logico. Sarà necessario usare tag più appropriato a livello semantico per ogni elemento logico nel contenuto del documento. <br><li> L'estensione per il rendering PDF assegna tag al contenuto nell'ordine di lettura logico per quanto possibile.<br>I codici di caratteri dovranno essere mappati a Unicode, come descritto nella specifica ISO 32000-1:2008, 14.8.2.4.2. I caratteri non inclusi nella specifica Unicode possono usare l'area di utilizzo privato Unicode o dichiarare un'altra codifica dei caratteri. <br>Il linguaggio naturale dovrà essere dichiarato come illustrato nella specifica ISO 32000-1:2008, 14.9.2 e/o come descritto nella specifica ISO 32000-1:2008, 7.9.2. Le modifiche apportate al linguaggio naturale dovranno essere dichiarate. Le modifiche al linguaggio naturale all'interno delle stringhe di testo, ad esempio all'interno di descrizioni alternative, dovranno essere dichiarate usando un identificatore di lingua, come descritto nella specifica ISO 32000-1:2008, 14.9.2.2. <br><li> L'estensione per il rendering PDF dichiara solo il linguaggio naturale a livello del documento    |
|    7.3 Graphics    |                 Supportata con eccezioni    |    Gli oggetti grafici, diversi dagli oggetti testo, devono essere contrassegnati con un tag Figure come descritto nella specifica ISO 32000-1:2008, 14.8.4.5, tabella 340. Se una delle eccezioni seguenti è vera, l'elemento grafico dovrà essere contrassegnato come artefatto: <br><li> l'elemento grafico non rappresenta contenuto significativo oppure <li>  l'elemento grafico viene visualizzato come sfondo di un'annotazione di collegamento, nel qual caso il testo alternativo sul collegamento dovrà descrivere sia l'elemento grafico che il collegamento. <li> L'estensione per il rendering PDF contrassegna gli oggetti grafici con il tag Figure. <br>Una didascalia associata a una figura dovrà essere contrassegnata con un tag Caption. <li> L'estensione per il rendering PDF attualmente non contrassegna le didascalie delle figure con un tag Caption. <br>I tag Figure includono una rappresentazione alternativa o un testo di sostituzione che rappresenta il contenuto contrassegnato con il tag Figure come indicato nella specifica ISO 32000-1:2008, 14.7.2, tabella 323. <br>**Nota** 1 vedere anche la linea guida 1.1 per l'accessibilità dei contenuti Web (WCAG 2.0). <br>Se il testo rappresentato in un elemento grafico non è testo in un linguaggio naturale che deve essere letto da un lettore umano, sarà necessario fornire un testo alternativo che descriva la natura o lo scopo dell'elemento grafico. <br>**Nota** 2 Testo costituito da un esempio del tipo o un esempio del sistema di scrittura usato da un linguaggio sono esempi di testo non costituito da linguaggio naturale.   L'estensione per il rendering PDF supporta il testo alternativo per le figure, anche se spetta all'utente scegliere se aggiungere il testo alternativo o meno. <br>Nota aggiuntiva sull'attributo BBox: <br><li> l'estensione per il rendering PDF attualmente non esegue la scrittura dell'attributo BBox. <li> Una soluzione alternativa consiste nel ricontrassegnare con tag manualmente le illustrazioni come nuove figure o come artefatti.    |
|    7.4 Headings    |                 Non applicabile    |    RDL non supporta l'assegnazione di tag alle intestazioni in alcun modo. È responsabilità dell'utente assegnare i tag alle intestazioni come appropriato.    |
|    7.5 Tables    |                 Supportata con eccezioni    |    Le tabelle devono includere le intestazioni. Le intestazioni di tabella devono essere contrassegnate in base alla specifica ISO 32000-1:2008, tabella 337 e tabella 349. <br>**Nota** 1 Le tabelle possono contenere intestazioni di colonna, intestazioni di riga o entrambe. <br>**Nota** 2 Quando si fa affidamento ad Assistive Technology, è necessario rendere disponibili tutte le informazioni possibili relative alla struttura delle tabelle. Le intestazioni svolgono un ruolo fondamentale per fornire informazioni strutturali. <br><li> È responsabilità dell'utente includere le intestazioni nelle tabelle. RDL e l'estensione per il rendering PDF forniscono supporto per le intestazioni di riga. <br>  Gli elementi della struttura di tipo TH dovranno contenere un attributo Scope.   <li> L'estensione per il rendering PDF include un attributo Scope sugli elementi TH per i membri di colonna e di riga, ma non per le celle d'angolo.<br>Le strutture di assegnazione di tag alle tabelle devono essere usate solo per contrassegnare il contenuto presentato all'interno di relazioni logiche di riga e/o colonna.   <li> Questo dipende dalla modalità con cui l'utente ha scelto di usare le tabelle nel linguaggio RDL.    |
|    7.6 Lists    |                 Non applicabile    |    RDL non supporta l'assegnazione di tag agli elenchi. Nel linguaggio RDL equivalgono strutturalmente a una tabella con una singola cella di tabella. <br>È responsabilità dell'utente riassegnare i tag agli elenchi come appropriato.    |
|    7.7 Mathematical expressions    |                 Supportata con eccezioni    |    Tutte le espressioni matematiche devono essere racchiuse in un tag Formula come descritto in dettaglio nella specifica ISO 32000-1:2008, 14.8.4.5 e devono contenere un attributo alt. <br><li> L'estensione per il rendering PDF non racchiude attualmente le espressioni matematiche all'interno di un tag Formula. <br>I requisiti relativi al mapping dei caratteri a Unicode verranno applicati alle espressioni matematiche come indicato nella specifica ISO 32000-1:2008, 9.10.2 e 14.8.2.4. <br><li> Supportata dall'estensione per il rendering PDF.    |
|    7.8 Page headers and footers    |                 Supportato    |    Le intestazioni e i piè di pagina dovranno essere identificati come artefatti di paginazione e classificati come sottotipi intestazione o piè di pagina in base alla specifica ISO 32000-1:2008, 14.8.2.2.2, tabella 330. <br><li> Le intestazioni o i piè di pagina vengono considerati e contrassegnati come artefatti.    |
|    7.9 Notes and references    |                 Non applicabile    |    L'estensione per il rendering PDF non supporta l'assegnazione di tag a note e riferimenti. <br>È responsabilità dell'utente assegnare i tag corrispondenti come appropriato.    |
|    7.10 Optional content    |                 Non applicabile    |         |
|    7.11 Embedded files    |                 Non applicabile    |         |
|    7.12 Article threads    |                 Non applicabile    |         |
|    7.13 Digital signatures    |                 Non applicabile    |         |
|    7.14 Non-interactive forms    |                 Non applicabile    |         |
|    7.15 XFA    |                 Non applicabile    |         |
|    7.16 Security    |                 Non applicabile    |         |
|    7.17 Navigation    |                 Supportato    |    Un documento deve includere una struttura documento corrispondente all'ordine di lettura e al livello delle destinazioni di spostamento (ISO 32000-1:2008, 12.3.3). <br><li> Il linguaggio RDL supporta i segnalibri per un elemento del report, ma è necessario che l'utente selezioni questa opzione. L'estensione per il rendering PDF esegue quindi il rendering dei segnalibri come struttura documento. <br>Se presenti, le voci nell'albero dei numeri PageLabels (ISO 32000-1:2008, 7.7.2, tabella 28) devono essere appropriate a livello semantico. <br><li> L'estensione per il rendering PDF non include un albero dei numeri PageLabels.    |
|    7.18 Annotations    |                 Non applicabile    |    Il linguaggio RDL non supporta le annotazioni    |
|    7.21 Fonts    |                 Supportato    |         |
|    7.21.1 General    |                 Supportato    |         |
|    7.21.2 Font types    |                 Supportato    |         |
|    7.21.3 Composite fonts    |                 Supportato    |         |
|    7.21.3.1 General    |                 Supportato    |         |
|    7.21 3.2 CIDFonts    |                 Supportato    |         |
|    7.21.3.3 CMaps    |                 Supportato    |         |
|    7.21.4 Embedding    |                 Supportato    |         |
|    7.21.4.1 General    |                 Supportato    |         |
|    7.21.4.2 Subset embedding    |                 Supportato    |         |
|    7.21.5 Font metrics    |                 Supportato    |         |
|    7.21.6 Character encodings    |                 Supportato    |         |
|    7.21.7 Unicode character maps    |                 Supportato    |         |
|    7.21.8 Use of .notdef glyph    |                 Supportato    |         |

## <a name="8--conforming-reader-requirements"></a>8.  Requisiti di conformità per il lettore

Non applicabile

## <a name="9--at-requirements"></a>9.  Requisiti Assistive Technology

Non applicabile

## <a name="disclaimer"></a>Disclaimer

© 2017 Microsoft Corporation. All rights reserved. The names of actual companies and products mentioned herein may be the trademarks of their respective owners. The information contained in this document represents the current view of Microsoft Corporation on the issues discussed as of the date of publication. Microsoft cannot guarantee the accuracy of any information presented after the date of publication. Microsoft regularly updates its websites with new information about the accessibility of products as that information becomes available.

Customization of the product voids this conformance statement from Microsoft. Please consult with Assistive Technology (AT) vendors for compatibility specifications of specific AT products.

This document is for informational purposes only. MICROSOFT MAKES NO WARRANTIES, EXPRESS OR IMPLIED, IN THIS DOCUMENT.


## <a name="next-steps"></a>Passaggi successivi
[Panoramica amministratore](admin-handbook-overview.md)  

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)

