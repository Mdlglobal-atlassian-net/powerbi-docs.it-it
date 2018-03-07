---
title: Risolvere i problemi relativi all'avvio di Power BI Desktop
description: Risolvere i problemi relativi all'avvio di Power BI Desktop
services: powerbi
documentationcenter: 
author: davidiseminger
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
ms.date: 01/24/2018
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 6d5e4592d1bf041672f89dd38f03ddc6ff196735
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/24/2018
---
# <a name="resolve-issues-when-power-bi-desktop-will-not-launch"></a>Risolvere i problemi relativi al mancato avvio di Power BI Desktop
In **Power BI Desktop** gli utenti che hanno installato ed eseguono versioni precedenti del **gateway dati locale di Power B** potrebbero non riuscire ad avviare Power BI Desktop a causa di restrizioni dei criteri amministrativi applicate dal gateway dati locale di Power BI sulle named pipe nel computer locale. 

## <a name="resolve-issues-with-the-on-premises-data-gateway-and-power-bi-desktop"></a>Risolvere i problemi del gateway dati locale e di Power BI Desktop
Sono disponibili tre opzioni per la risoluzione del problema associato al gateway dati locale e per consentire l'avvio di Power BI Desktop:

### <a name="resolution-1-install-the-latest-version-of-power-bi-on-premises-data-gateway"></a>Soluzione 1: Installare la versione più recente del gateway dati locale di Power BI
La versione più recente del gateway dati locale di Power BI non applica restrizioni delle named pipe nel computer locale e consente a Power BI Desktop di avviarsi correttamente. Se si vuole continuare a usare il gateway dati locale di Power BI, questa è la soluzione consigliata. È possibile scaricare la versione più recente del gateway dati locale di Power BI da [questo percorso](https://go.microsoft.com/fwlink/?LinkId=698863). Si noti che il collegamento è un collegamento diretto all'eseguibile dell'installazione.

### <a name="resolution-2-uninstall-or-stop-the-power-bi-on-premises-data-gateway-windows-service"></a>Soluzione 2: Disinstallare o arrestare il servizio di Windows Gateway dati locale di Power BI
Se il gateway dati locale di Power BI non è più necessario, è possibile disinstallarlo oppure arrestare il servizio di Windows Gateway dati locale di Power BI. In questo modo viene rimossa la restrizione dei criteri e viene consentito l'avvio di Power BI Desktop.

### <a name="resolution-3-run-power-bi-desktop-with-administrator-privilege"></a>Soluzione 3: eseguire Power BI Desktop con privilegi di amministratore
In alternativa, è possibile avviare Power BI Desktop come amministratore. È comunque consigliabile installare la versione più recente del gateway dati locale di Power BI, come descritto in precedenza in questo articolo.

## <a name="help-with-other-issues-when-launching-power-bi-desktop"></a>Risolvere altri problemi di avvio di Power BI Desktop
Microsoft si impegna per risolvere il numero maggiore possibile dei problemi relativi a **Power BI Desktop**. Vengono esaminati regolarmente i problemi che potrebbero influire su molti clienti, che saranno poi inclusi negli articoli.

Se il problema relativo all'avvio di **Power BI Desktop** non è associato al gateway dati locale oppure se le soluzioni precedenti non funzionano, è possibile inviare una richiesta di assistenza al [supporto tecnico di Power BI](https://support.powerbi.com) (https://support.powerbi.com) per identificare e risolvere il problema.

Per altri problemi futuri relativi a **Power BI Desktop** potrebbe risultare utile attivare la traccia e raccogliere i file di log, per isolare e identificare in modo più efficace il problema. Per attivare la traccia, selezionare **File > Opzioni e impostazioni > Options**, quindi selezionare **Diagnostica** e infine **Abilita traccia** in *Opzioni di diagnostica*. È necessario che **Power BI Desktop** sia in esecuzione per configurare questa opzione, che risulta utile per problemi futuri associati all'avvio di **Power BI Desktop**.

