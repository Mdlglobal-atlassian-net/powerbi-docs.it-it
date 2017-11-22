---
title: Esaminare oggetti visivi personalizzati per la sicurezza e la privacy
description: "Prima di abilitare un oggetto visivo personalizzato è necessario esaminarlo per la sicurezza e la privacy e assicurarsi che si adatti agli standard della propria organizzazione."
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
ms.date: 09/05/2017
ms.author: asaxton
ms.openlocfilehash: 20a697cbc4698e237f3ac09b031ea0c4cb734a52
ms.sourcegitcommit: 12236d08c27c7ee3fabb7ef9d767e9dee693f8aa
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="review-custom-visuals-for-security-and-privacy"></a>Esaminare oggetti visivi personalizzati per la sicurezza e la privacy
Prima di abilitare un oggetto visivo personalizzato è necessario esaminarlo per la sicurezza e la privacy e assicurarsi che si adatti agli standard della propria organizzazione.

## <a name="enable-a-custom-visual"></a>Abilitare un oggetto visivo personalizzato
<a name="enable"></a>Un oggetto visivo personalizzato nel report è disabilitato finché non si sceglie **Abilita oggetti visivi personalizzati** come illustrato di seguito.  

![](media/service-custom-visuals-review-for-security-and-privacy/emptyvisual.png)

## <a name="considerations-before-you-enable-a-custom-visual"></a>Considerazioni prima di abilitare un oggetto visivo personalizzato
<a name="considerations"></a>

> [!WARNING]
> un oggetto visivo personalizzato può contenere codice con rischi per la sicurezza o per la privacy; per questo motivo, un oggetto visivo personalizzato nel report è disabilitato finché non si sceglie Abilita oggetti visivi personalizzati. Di seguito sono riportate alcune considerazioni per decidere se abilitare un oggetto visivo personalizzato:
> 
> 

1. Assicurarsi di considerare attendibile l'autore e l'origine degli oggetti visivi personalizzati usati nel report
2. Se non si è sicuri su come procedere, rivolgersi al team IT per valutare se è necessario abilitare gli oggetti visivi personalizzati per i report visualizzati.
3. Se qualcuno, anche un collega, condivide con l'utente un report che contiene un oggetto visivo personalizzato, non occorre sentirsi obbligati ad abilitare l'oggetto visivo personalizzato. È perfettamente accettabile fare un passo indietro e considerare se è fondamentale per l'attività in questione. È sempre opportuno chiedere di fornire un report senza gli oggetti visivi personalizzati se non li si ritiene attendibili.

## <a name="security-best-practices-for-it-professionals-to-enable-a-custom-visual"></a>Procedure ottimali di sicurezza per i professionisti IT per abilitare un oggetto visivo personalizzato
<a name="security"></a>

> [!WARNING]
> un oggetto visivo personalizzato può contenere codice con rischi per la sicurezza o per la privacy; per questo motivo, un oggetto visivo personalizzato nel report è disabilitato finché non si sceglie Abilita oggetti visivi personalizzati. Ci sono diverse procedure consigliate che è possibile seguire per valutare un oggetto visivo personalizzato per la sicurezza e la privacy.
> 
> 

1. Implementare un processo di verifica per gli oggetti visivi personalizzati all'interno dell'organizzazione. Gli oggetti visivi personalizzati esaminati sarebbero condivisi con gli utenti interni attraverso un sito Web interno, ad esempio una raccolta documenti di SharePoint o un documento di OneNote.
2. Fornire agli utenti aziendali le linee guida sull'uso appropriato degli oggetti visivi personalizzati e un gruppo di posta elettronica a cui gli utenti aziendali possono inviare domande relative a sicurezza e privacy.
3. Valutare il codice JavaScript nel file PBVIZ dell'oggetto visivo personalizzato.

**Per valutare il codice JavaScript in un oggetto visivo personalizzato**

Un oggetto visivo personalizzato usa JavaScript, quindi può contenere rischi per la sicurezza o per la privacy. Se si riceve un oggetto visivo personalizzato o un file PBIX con un oggetto visivo personalizzato da un'origine sconosciuta, si consiglia di esaminare il codice JavaScript per vedere se è sicuro.

Per valutare il codice JavaScript in un oggetto visivo personalizzato, estrarre il codice dell'oggetto visivo personalizzato. Di seguito viene illustrato come estrarre il codice:  

1. Salvare il file con estensione pbiviz in una cartella.
2. Rinominare il file in un file con estensione zip.
3. Estrarre il file ZIP in una cartella locale.

## <a name="custom-visual-file-contents"></a>Contenuti del file dell'oggetto visivo personalizzato
Di seguito sono illustrati i contenuti di un file PBIVIZ:

| **File** | **Descrizione** |
|:--- |:--- |
| ./package.json |File manifesto che indica i file da caricare per l'oggetto visivo personalizzato. |
| ./resources |Contiene lo stile CSS, il codice TypeScript e il codice JavaScript usati dall'oggetto visivo personalizzato. |
| ./resources/&lt;nome&gt; |&lt;nome&gt; è il nome dell'oggetto visivo personalizzato. |
| ./resources/&lt;nome&gt;.css |File di risorse css per l'oggetto visivo personalizzato. |
| ./resources/&lt;nome&gt;.js |Il codice che viene eseguito quando un utente fa clic su Abilita oggetti visivi personalizzati o dopo l'importazione di un oggetto visivo personalizzato. Avviso: il codice JavaScript può comportare rischi per la sicurezza o per la privacy. |
| ./resources/&lt;nome&gt;.ts |Il codice sorgente di JavaScript per l'oggetto visivo in formato TypeScript. Avviso: il codice JavaScript o TypeScript può comportare rischi per la sicurezza o per la privacy. |
| ./resources/&lt;nome&gt;.png |L'icona visualizzata per l'oggetto visivo. |

Dopo aver estratto il file PBIVIZ, è possibile valutare il codice. Ecco alcune procedure consigliate e minacce da cercare.

## <a name="best-practices-to-evaluate-the-javascript-or-typescript-code"></a>Procedure consigliate per valutare il codice JavaScript o TypeScript
Il codice **JavaScript** o **TypeScript** può contenere rischi per la sicurezza o per la privacy. Ecco alcune procedure consigliate e minacce da cercare.

### <a name="best-practices-to-evaluate-javascript-code"></a>Procedure consigliate per valutare il codice JavaScript
* Valutare sempre il contenuto del file JS, cioè il codice che viene effettivamente eseguito. Il contenuto del file TS potrebbe non essere compilato nel file JS incluso nell'oggetto visivo.
* Valutare sempre il contenuto del file TS. È possibile caricare il file TS in **Strumenti di sviluppo**, esportare l'oggetto visivo e confrontare il file JS risultante nel file PBIVIZ appena creato con il file JS originale contenuto nell'oggetto visivo
* Verificare che l'icona per l'oggetto visivo personalizzato non assomigli troppo ad altri oggetti visivi con cui l'utente ha familiarità.
* Valutare sempre l'oggetto visivo in un account di prova con privilegi minimi e che non abbia accesso a dati riservati. In maniera ideale, l'account di prova è un account locale senza informazioni di accesso a servizi diversi da Power BI.

### <a name="threats-to-look-for-in-javascript-code"></a>Minacce da cercare nel codice JavaScript
* Controllare l'attività di rete quando viene usato l'oggetto visivo in modalità di modifica e di visualizzazione. Assicurarsi che le richieste effettuate corrispondano alle proprie aspettative. Non dovrebbero essere visualizzate le richieste alle risorse esterne al dominio di Power BI, a meno che l'autore dell'oggetto visivo lo abbia comunicato in anticipo.
* Eventuali dati visualizzati all'uscita dal dominio di Power BI dovranno corrispondere alle proprie aspettative di uso "normale". Ad esempio, se l'oggetto visivo implementa un lettore video che usa un iFrame per visualizzare un video da un altro sito, alcune informazioni dovrebbero essere trasferite nelle richieste di IFrame per il corretto rendering del video. Tuttavia, se viene visualizzato l'intero set di dati inviato in rete, potrebbe essere utile indagare ulteriormente se ciò è necessario e auspicabile.
* Controllare se i dati personali vengono inviati o memorizzati dall'oggetto visivo personalizzato.
* Controllare se l'oggetto visivo personalizzato sta provando ad accedere alle risorse del computer locale, ad esempio la scrittura di file su disco o l'accesso ai cookie.
* Controllare se l'oggetto visivo personalizzato contiene codice apparentemente poco comprensibile o senza uno scopo evidente.
* Salvare copie di ciascun oggetto visivo esaminato in precedenza.
* Se si sta esaminando un aggiornamento di un oggetto visivo che è stato esaminato in precedenza, assicurarsi di controllare le modifiche. Applicare agli aggiornamenti sempre lo stesso rigore della prima volta che è stato ricevuto l'oggetto visivo per la revisione
* Se si trova qualcosa di sospetto o poco chiaro, contattare l'assistenza.

## <a name="next-steps"></a>Passaggi successivi
[Visualizzazioni in Power BI](power-bi-report-visualizations.md)  
[Visualizzazioni personalizzate in Power BI](power-bi-custom-visuals.md)  
[Pubblicare oggetti visivi personalizzati in Office Store](developer/office-store.md)  
[Introduzione agli strumenti di sviluppo per oggetti visivi personalizzati](service-custom-visuals-getting-started-with-developer-tools.md)  
[Come certificare un oggetto visivo personalizzato](power-bi-custom-visuals-certified.md)    
[Video: Creazione di visualizzazioni personalizzate per Power BI con Sachin Patney e Nico Cristache](https://www.youtube.com/watch?v=kULc2VbwjCc)  

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

