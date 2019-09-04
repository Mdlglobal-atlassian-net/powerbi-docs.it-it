---
title: Parametri URL nei report impaginati - Generatore report di Power BI
description: Questo argomento descrive gli usi comuni per i parametri dei report di Generatore report impaginati di Power BI, le proprietà che è possibile impostare e molto altro ancora.
ms.service: powerbi
ms.subservice: report-builder
ms.custom: ''
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.date: 08/29/2019
ms.openlocfilehash: 4dae849a18bbfc6e85eedc7ae9e338ad205cb436
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/30/2019
ms.locfileid: "70189347"
---
# <a name="url-parameters-in-paginated-reports-in-power-bi"></a>Parametri URL nei report impaginati in Power BI

È possibile inviare comandi ai report impaginati in Power BI aggiungendo un parametro a un URL. È possibile, ad esempio, che il report sia stato visualizzato usando un set specifico di valori dei parametri del report. È possibile incapsulare queste informazioni nell'URL usando i parametri di accesso con URL predefiniti. Si può personalizzare ulteriormente il modo in cui Power BI elabora il report incorporando i parametri per il rendering dei formati o per l'aspetto della barra degli strumenti del report. Questo URL può quindi essere incollato direttamente in un messaggio di posta elettronica o in una pagina Web in modo che altri utenti possano visualizzare il report nello stesso modo nel browser. 

Ecco le azioni che è possibile eseguire tramite i parametri di accesso con URL: 

- Inviare parametri di report a un report. 
- Avviare l'esportazione del contenuto del report in un formato di file supportato. 
- Nascondere o visualizzare il riquadro dei parametri. 
- Specificare l'impostazione DeviceInfo. 

Per l'elenco completo dei comandi e delle impostazioni disponibili tramite l'accesso con URL, vedere  [Informazioni di riferimento per i parametri di accesso con URL](#url-access-parameter-reference) più avanti in questo articolo. 

## <a name="url-access-concepts"></a>Concetti relativi all'accesso con URL 

Le richieste URL per Power BI contengono parametri elaborati dal servizio. Il modo in cui il servizio gestisce le richieste URL dipende dai parametri, dai prefissi di parametro e dai tipi di elementi inclusi nell'URL. La funzionalità dell'URL per i report impaginati è compatibile con la maggior parte dei browser e delle applicazioni che supportano l'indirizzamento URL standard. 

## <a name="url-access-syntax"></a>Sintassi di accesso con URL 

Le richieste URL possono contenere più parametri, elencati in qualsiasi ordine. I parametri sono separati da una e commerciale (&). Le coppie nome/valore sono separate da un segno di uguale (=). ad esempio:

```
powerbiserviceurl?rp:parametervalueh&rdl:parameter=value  
```

## <a name="syntax-description"></a>Descrizione della sintassi 

### <a name="powerbiserviceurl"></a>powerbiserviceurl 

URL del servizio Web del tenant di Power BI. ad esempio: 

**&** Usato per separare le coppie di nome e valore dei parametri di accesso con URL.

**prefisso** Prefisso per il parametro URL (ad esempio, rp: o rdl:) che specifica un'azione nel servizio Power BI. 

> [!NOTE]
> I parametri di report richiedono un prefisso di parametro e fanno distinzione tra maiuscole e minuscole. 

**parameter** Nome del parametro. 

### <a name="value"></a>value 

Testo dell'URL corrispondente al valore del parametro usato. 

Per esempi relativi al passaggio di parametri di report nell'URL, vedere  [Passare un parametro del report in un URL](report-builder-url-pass-parameters.md).

## <a name="url-access-parameter-reference"></a>Informazioni di riferimento sui parametri di accesso con URL

È possibile usare i parametri seguenti come parte di un URL per configurare l'aspetto dei report impaginati in Power BI. I parametri più comuni sono elencati in questa sezione. I parametri non fanno distinzione tra maiuscole e minuscole e iniziano con il prefisso `rdl:` se correlati al formato di output.  

### <a name="report-commands-rdl"></a>Comandi del report (`rdl:`) 

**Formato di esportazione** Specifica il formato per il rendering e l'esportazione di un report. I valori includono: 
- PPTX 
- MHTML 
- IMMAGINE 
- EXCEL 
- WORD 
- CSV 
- PDF 
- XML 

## <a name="next-steps"></a>Passaggi successivi

- [Passare un parametro di report in un URL per un report impaginato in Power BI](report-builder-url-pass-parameters.md)
- [Che cosa sono i report impaginati in Power BI Premium?](paginated-reports-report-builder-power-bi.md)