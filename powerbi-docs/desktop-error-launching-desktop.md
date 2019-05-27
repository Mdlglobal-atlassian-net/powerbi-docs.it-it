---
title: Risolvere i problemi relativi all'avvio di Power BI Desktop
description: Risolvere i problemi relativi all'avvio di Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 19dc98b4f402176b2ae511236015ea25d7e4178b
ms.sourcegitcommit: 2116af72f435cd30f1401bb9c7afdcbc76b1c3ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65454419"
---
# <a name="resolve-issues-when-power-bi-desktop-will-not-launch"></a>Risolvere i problemi relativi al mancato avvio di Power BI Desktop
In **Power BI Desktop** è possibile che gli utenti che hanno installato il **gateway dati locale di Power BI** o ne eseguono una versione precedente non possano avviare Power BI Desktop a causa di restrizioni dei criteri amministrativi applicate dal gateway dati locale di Power BI sulle named pipe nel computer locale. 

## <a name="resolve-issues-with-the-on-premises-data-gateway-and-power-bi-desktop"></a>Risolvere i problemi del gateway dati locale e di Power BI Desktop
Sono disponibili tre opzioni per la risoluzione del problema associato al gateway dati locale e per consentire l'avvio di Power BI Desktop:

### <a name="resolution-1-install-the-latest-version-of-power-bi-on-premises-data-gateway"></a>Soluzione 1: installare la versione più recente del gateway dati locale di Power BI
La versione più recente del gateway dati locale di Power BI non applica restrizioni sulle named pipe nel computer locale e consente a Power BI Desktop di essere avviato correttamente. Se si vuole continuare a usare il gateway dati locale di Power BI, questa è la soluzione consigliata. È possibile scaricare la versione più recente del gateway dati locale di Power BI da [questo percorso](https://go.microsoft.com/fwlink/?LinkId=698863). Si noti che il collegamento è un collegamento diretto all'eseguibile dell'installazione.

### <a name="resolution-2-uninstall-or-stop-the-power-bi-on-premises-data-gateway-windows-service"></a>Soluzione 2: disinstallare o arrestare il servizio di Windows gateway dati locale di Power BI
Se il gateway dati locale di Power BI non è più necessario, è possibile disinstallarlo oppure arrestare il servizio di Windows Gateway dati locale di Power BI. In questo modo viene rimossa la restrizione dei criteri e viene consentito l'avvio di Power BI Desktop.

### <a name="resolution-3-run-power-bi-desktop-with-administrator-privilege"></a>Soluzione 3: eseguire Power BI Desktop con privilegi di amministratore
In alternativa, è possibile avviare Power BI Desktop come amministratore. È comunque consigliabile installare la versione più recente del gateway dati locale di Power BI, come descritto in precedenza in questo articolo.

È importante notare che Power BI Desktop è progettato come architettura multiprocesso e vari di questi processi comunicano tramite named pipe di Windows. Potrebbero essere presenti altri processi che interferiscono con queste named pipe. Il motivo più comune per tali interferenze è la sicurezza, incluse le situazioni in cui il software antivirus o i firewall potrebbero bloccare le pipe o reindirizzare il traffico a una porta specifica. L'avvio di Power BI Desktop con privilegi di amministratore potrebbe risolvere il problema. Se non è possibile eseguire l'avvio con privilegi di amministratore, contattare l'amministratore per determinare quali regole di sicurezza applicate impediscono comunicazioni corrette per le named pipe e per aggiungere Power BI Desktop e i rispettivi sottoprocessi all'elenco elementi consentiti.

## <a name="resolve-issues-when-connecting-to-sql-server"></a>Risolvere i problemi di connessione a SQL Server
Se durante la connessione a un database di SQL Server viene visualizzato un messaggio di errore simile al seguente, in molti casi è possibile risolvere il problema avviando **Power BI Desktop** come amministratore, quindi attivando la connessione a SQL Server:

    "An error happened while reading data from the provider: 'Could not load file or assembly 'System.EnterpriseServices, Version=4.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxx' or one of its dependencies. Either a required impersonation level was not provided, or the provided impersonation level is invalid. (Exception from HRESULT: 0x80070542)'"

Dopo l'avvio con privilegi di amministratore e l'attivazione della connessione, le DLL necessarie vengono registrate correttamente. Dopo questa operazione non è necessario avviare Power BI Desktop come amministratore.

## <a name="help-with-other-issues-when-launching-power-bi-desktop"></a>Risolvere altri problemi di avvio di Power BI Desktop
Microsoft si impegna per risolvere il numero maggiore possibile dei problemi relativi a **Power BI Desktop**. Vengono esaminati regolarmente i problemi che potrebbero influire su molti clienti, che saranno poi inclusi negli articoli.

Se il problema relativo all'avvio di **Power BI Desktop** non è associato al gateway dati locale oppure se le soluzioni precedenti non funzionano, è possibile inviare una richiesta di assistenza al [supporto tecnico di Power BI](https://support.powerbi.com) (https://support.powerbi.com) per identificare e risolvere il problema.

Per altri problemi futuri relativi a **Power BI Desktop** potrebbe risultare utile attivare la traccia e raccogliere i file di log, per isolare e identificare in modo più efficace il problema. Per attivare la traccia, selezionare **File > Opzioni e impostazioni > Options**, quindi selezionare **Diagnostica** e infine **Abilita traccia** in *Opzioni di diagnostica*. È necessario che **Power BI Desktop** sia in esecuzione per configurare questa opzione, che risulta utile per problemi futuri associati all'avvio di **Power BI Desktop**.

