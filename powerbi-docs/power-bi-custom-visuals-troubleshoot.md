---
title: Risoluzione dei problemi relativi a come sviluppare oggetti visivi personalizzati di Power BI
description: Questo articolo illustra alcuni problemi comuni che possono verificarsi quando si sviluppa o si crea un oggetto visivo personalizzato di Power BI.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 11/06/2018
ms.openlocfilehash: 3d9e8e46fdd84edbeb5b4ff5e8f7efe4a4291049
ms.sourcegitcommit: a739a99e1006834a0f56e387c0bd9d945fb8a76b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51679255"
---
# <a name="troubleshoot-power-bi-custom-visuals"></a>Risoluzione dei problemi relativi agli oggetti visivi personalizzati di Power BI

## <a name="debug"></a>Debug

**Comando Pbiviz non trovato (o errori simili)**

Se si esegue `pbiviz` nella riga di comando del terminal, verrà visualizzata la schermata della Guida in linea. In caso contrario, l'installazione non è stata eseguita correttamente. Assicurarsi di avere almeno la versione 4.0 di NodeJS installata.

**Non è possibile trovare l'oggetto visivo di debug nella scheda Visualizzazioni**

L'oggetto visivo di debug all'interno della scheda **Visualizzazioni** ha l'aspetto di un'icona di prompt dei comandi.

![Selezione oggetto visivo](media/power-bi-custom-visuals-troubleshoot/powerbi-developer-visual-selection.png)

Se non è visualizzata, verificare che sia stata abilitata nelle impostazioni di Power BI.

> [!NOTE]
> L'oggetto visivo di debug è attualmente disponibile solo nel servizio Power BI e non in Power BI Desktop o nell'app per dispositivi mobili. L'oggetto visivo in pacchetto continuerà a funzionare ovunque.

**Non è possibile contattare il server dell'oggetto visivo**

Eseguire il server dell'oggetto visivo con il comando `pbiviz start` nella riga di comando del terminal dalla radice del progetto di oggetto visivo. Se il server non è in esecuzione, è probabile che i certificati SSL non siano stati installati correttamente.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni e risposte, vedere le [Frequently asked questions about Power BI custom visuals](power-bi-custom-visuals-faq.md#organizational-custom-visuals) (Domande frequenti sugli oggetti visivi personalizzati di Power BI).
