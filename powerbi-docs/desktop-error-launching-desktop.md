---
title: Risolvere i problemi relativi all'avvio di Power BI Desktop
description: Risolvere i problemi relativi all'avvio di Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/14/2020
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 67c83f2cc0eb81e90f447961ed178a04e97e050e
ms.sourcegitcommit: 3d6b27e3936e451339d8c11e9af1a72c725a5668
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2020
ms.locfileid: "76160904"
---
# <a name="troubleshoot-opening-power-bi-desktop"></a>Risolvere i problemi di apertura di Power BI Desktop

In Power BI Desktop è possibile che gli utenti che hanno installato il *gateway dati locale di Power BI* o ne eseguono una versione precedente non possano aprire Power BI Desktop a causa di restrizioni dei criteri amministrativi applicate dal gateway dati locale di Power BI sulle named pipe nel computer locale.

## <a name="resolve-issues-with-the-on-premises-data-gateway-and-power-bi-desktop"></a>Risolvere i problemi del gateway dati locale e di Power BI Desktop

Sono disponibili tre opzioni per la risoluzione del problema associato al gateway dati locale e per consentire l'apertura di Power BI Desktop:

### <a name="resolution-1-install-the-latest-version-of-power-bi-on-premises-data-gateway"></a>Soluzione 1: installare la versione più recente del gateway dati locale di Power BI

La versione più recente del gateway dati locale di Power BI non applica restrizioni sulle named pipe nel computer locale e consente a Power BI Desktop di essere aperto correttamente. Se si vuole continuare a usare il gateway dati locale di Power BI, la soluzione consigliata è aggiornarlo. È possibile scaricare la [versione più recente del gateway dati locale di Power BI](https://go.microsoft.com/fwlink/?LinkId=698863). Il collegamento è un collegamento diretto all'eseguibile dell'installazione.

### <a name="resolution-2-uninstall-or-stop-the-power-bi-on-premises-data-gateway-microsoft-service"></a>Soluzione 2: Disinstallare o arrestare il servizio Microsoft gateway dati locale di Power BI

È possibile disinstallare il gateway dati locale di Power BI se non è più necessario. Oppure è possibile arrestare il servizio Microsoft gateway dati locale di Power BI, che rimuove le restrizioni imposte dai criteri e consente l'apertura di Power BI Desktop.

### <a name="resolution-3-run-power-bi-desktop-with-administrator-privilege"></a>Soluzione 3: eseguire Power BI Desktop con privilegi di amministratore

È anche possibile avviare Power BI Desktop come amministratore, operazione che consente di aprire correttamente Power BI Desktop. È comunque consigliabile installare la versione più recente del gateway dati locale di Power BI, come descritto in precedenza.

Power BI Desktop è progettato come architettura multiprocesso e alcuni di questi processi comunicano usando named pipe di Windows. Potrebbero essere presenti altri processi che interferiscono con queste named pipe. Il motivo più comune per tali interferenze è la sicurezza, incluse le situazioni in cui il software antivirus o i firewall possono bloccare le pipe o reindirizzare il traffico a una porta specifica. L'apertura di Power BI Desktop con privilegi di amministratore potrebbe risolvere il problema. Qualora non sia possibile aprirlo con i privilegi di amministratore, rivolgersi al proprio amministratore per determinare quali regole di sicurezza impediscono alle named pipe di comunicare in modo appropriato. Quindi autorizzare Power BI Desktop e i rispettivi sottoprocessi.

## <a name="resolve-issues-when-connecting-to-sql-server"></a>Risolvere i problemi di connessione a SQL Server

Quando si tenta di connettersi a un database SQL Server è possibile che venga visualizzato un messaggio di errore simile al seguente:

`"An error happened while reading data from the provider:`\
`'Could not load file or assembly 'System.EnterpriseServices, Version=4.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxx' or one of its dependencies.`\
`Either a required impersonation level was not provided, or the provided impersonation level is invalid. (Exception from HRESULT: 0x80070542)'"`

Il problema spesso può essere risolto aprendo Power BI Desktop come amministratore prima di effettuare la connessione a SQL Server.

Dopo l'apertura di Power BI Desktop con privilegi di amministratore e l'attivazione della connessione, le DLL necessarie vengono registrate correttamente. Dopo questa operazione non è necessario aprire Power BI Desktop come amministratore.

## <a name="get-help-with-other-launch-issues"></a>Richiedere assistenza per altri problemi di avvio

Microsoft si impegna per risolvere il numero maggiore possibile dei problemi relativi a Power BI Desktop. Vengono esaminati regolarmente i problemi che potrebbero influire su molti clienti, che saranno poi inclusi negli articoli.

Se il problema relativo all'apertura di Power BI Desktop non è associato al gateway dati locale o se le soluzioni precedenti non funzionano, è possibile inviare una richiesta di assistenza al *supporto tecnico di Power BI* (<https://support.powerbi.com>) per identificare e risolvere il problema.

Nel caso in cui in futuro si riscontrino altri problemi con Power BI Desktop, è utile attivare la traccia e raccogliere i file di log. I file di log possono aiutare a isolare e identificare il problema. Per attivare la traccia, scegliere **File** > **Opzioni e impostazioni** > **Opzioni**, selezionare **Diagnostica**, quindi selezionare **Abilita traccia**. Power BI Desktop deve essere in esecuzione per configurare questa opzione, utile in caso di problemi futuri associati all'apertura di Power BI Desktop.
