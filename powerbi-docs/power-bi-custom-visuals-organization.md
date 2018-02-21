---
title: Uso degli oggetti visivi personalizzati dell'organizzazione in Power BI
description: Usare, gestire e creare oggetti visivi personalizzati dell'organizzazione in Power BI
services: powerbi
documentationcenter: 
author: markingmyname
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
ms.date: 02/06/2018
ms.author: maghan
ms.openlocfilehash: 2c90ea4a7e95c354b6dfaec04cff7e5e4009b55f
ms.sourcegitcommit: db37f5cef31808e7882bbb1e9157adb973c2cdbc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="using-organization-custom-visuals-in-power-bi-preview"></a>Uso degli oggetti visivi personalizzati dell'organizzazione in Power BI (anteprima)

È possibile usare oggetti visivi personalizzati in Power BI per creare un tipo univoco di oggetto visivo personalizzato in base all'utente o alle informazioni che si desidera comunicare. Spesso questi oggetti visivi personalizzati vengono creati dagli sviluppatori e spesso vengono creati quando la grande varietà di oggetti visivi inclusi in Power BI non soddisfa esigenze specifiche. 

In alcune organizzazioni, gli oggetti visivi personalizzati sono ancora più importanti: potrebbero essere necessari per comunicare dati o informazioni approfondite specifici dell'organizzazione, potrebbero avere requisiti speciali per i dati oppure mettere in evidenza metodi aziendali privati. Queste organizzazioni hanno la necessità di sviluppare oggetti visivi personalizzati, condividerli in tutta l'organizzazione e accertarsi che vengono gestiti correttamente. Gli oggetti visivi personalizzati di Power BI (ora in anteprima) soddisfano proprio queste esigenze delle organizzazioni. 

La figura seguente illustra il processo di flusso degli oggetti visivi personalizzati dell'organizzazione (anteprima) in Power BI dall'amministratore allo sviluppo e alla manutenzione, fino all'analista di dati.

![](media/power-bi-custom-visuals-organizational/custom-visual-org-01.jpg)

## <a name="how-to-enable-organizational-custom-visuals-preview"></a>Come abilitare gli oggetti visivi personalizzati dell'organizzazione (anteprima)

Gli oggetti visivi personalizzati dell'organizzazione sono attualmente in anteprima, pertanto è necessario abilitare la funzionalità in Power BI Desktop. Per abilitare questa funzionalità di anteprima, sulla barra multifunzione selezionare File > Opzioni e impostazioni > Opzioni, nel riquadro sinistro selezionare Funzionalità di anteprima e quindi selezionare la casella di controllo accanto a Oggetti visivi personalizzati dell'organizzazione, come illustrato nella figura seguente.

![](media/power-bi-custom-visuals-organizational/custom-visual-org-02.jpg)

Gli oggetti visivi dell'organizzazione vengono distribuiti e gestiti dall'amministratore di Power BI dal portale di amministrazione. Dopo la distribuzione nel repository dell'organizzazione, gli utenti dell'organizzazione possono facilmente individuarli e importarli nei loro report direttamente da Power BI Desktop.

## <a name="using-organizational-custom-visuals"></a>Uso di oggetti visivi personalizzati dell'organizzazione

Per altre informazioni su come usare gli oggetti visivi personalizzati dell'organizzazione nei report creati, vedere [altre informazioni sull'importazione di oggetti visivi dell'organizzazione nei report](power-bi-custom-visuals.md).
 
## <a name="administering-organizational-custom-visuals"></a>Amministrazione degli oggetti visivi personalizzati dell'organizzazione

Per altre informazioni su come amministrare, distribuire e gestire gli oggetti visivi personalizzati dell'organizzazione all'interno dell'organizzazione, vedere [altre informazioni sulla distribuzione e gestione degli oggetti visivi personalizzati dell'organizzazione](https://go.microsoft.com/fwlink/?linkid=866790).

> [!WARNING]
> Gli oggetti visivi personalizzati possono contenere codice che comporta rischi per la sicurezza o per la privacy. Assicurarsi che l'autore e l'origine di qualsiasi oggetto visivo personalizzato siano attendibili prima di distribuirlo nel repository dell'organizzazione. 
> 

## <a name="considerations-and-limitations"></a>Considerazioni e limitazioni
 
Dato che gli oggetti visivi personalizzati dell'organizzazione sono disponibili in anteprima, esistono varie considerazioni e limitazioni da tenere presenti e prendere in considerazione.
 
Amministratore:

* Non sono supportati gli oggetti visivi personalizzati legacy (ad esempio gli oggetti visivi personalizzati non creati sulla base delle nuove API con controllo della versione)

* L'aggiornamento sul posto non è ancora supportato. Per aggiornare un oggetto visivo, è necessario caricare una nuova versione dell'oggetto visivo nel repository dell'organizzazione e verificare inoltre che abbia lo stesso ID nel file PBIVIZ. Gli autori di report possono quindi importare la nuova versione nei report ed eseguire una sostituzione sul posto della versione corrente dell'oggetto visivo nel report.

* Se un oggetto visivo personalizzato viene eliminato dal repository, non verrà più eseguito il rendering di tutti i report esistenti che usano l'oggetto visivo eliminato. L'operazione di eliminazione dal repository non è reversibile.
 
Utenti finali:

* Non è supportato l'uso dello stesso oggetto visivo (lo stesso ID di oggetto visivo) dal Marketplace pubblico (AppSource) e dal repository dell'organizzazione. In tale caso, verrà usato l'oggetto visivo più recente importato.

* La condivisione esterna di oggetti visivi dell'organizzazione nei dashboard e nei report non è supportata. Gli utenti esterni all'organizzazione che visualizzano un dashboard con un oggetto visivo personalizzato dell'organizzazione vedranno un oggetto visivo vuoto. 

* La raccolta di aree di lavoro di Power BI non è supportata per gli oggetti visivi dell'organizzazione

* Non verrà eseguito il rendering degli oggetti visivi personalizzati dell'organizzazione nei report pubblicati nel Web

* Non verrà eseguito il rendering degli oggetti visivi Visio, PowerApps e GlobeMap dal Marketplace AppSource se vengono distribuiti tramite il repository dell'organizzazione

* Se l'amministratore elimina un oggetto visivo personalizzato dal repository e tale oggetto viene usato in un report, non verrà eseguito il rendering dell'oggetto visivo che dovrà essere rimosso dal report per poterlo salvare