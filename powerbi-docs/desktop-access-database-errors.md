---
title: Risolvere i problemi di importazione dei file di Access e XLS in Power BI Desktop
description: Risolvere problemi di importazione dei database di Access e fogli di calcolo XLS in Power BI Desktop e Power Query
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/21/2019
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 1816fb7926ed378cdb70ce2e0ade08893828ce4c
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "75761957"
---
# <a name="troubleshoot-importing-access-and-excel-xls-files-in-power-bi-desktop"></a>Risolvere i problemi di importazione di file XLS di Access e di Excel in Power BI Desktop

In Power BI Desktop, sia i database di Access che le prime versioni delle cartelle di lavoro di Excel (file con estensione XLS di tipo Excel 97-2003) usano il *motore di database di Access*. Esistono tre situazioni comuni che possono impedire il corretto funzionamento del motore di database di Access.

## <a name="situation-1-no-access-database-engine-is-installed"></a>Situazione 1: nessun motore di database di Access installato

Se il messaggio di errore di Power BI Desktop indica che il motore di database di Access non è installato, è necessario installare la versione del motore di database di Access, a 32 bit o a 64 bit, che corrisponde alla propria versione di Power BI Desktop. È possibile installare il motore di database di Access dalla [pagina dei download](https://www.microsoft.com/download/details.aspx?id=13255).

>[!NOTE]
>Se la versione di bit del motore di database di Access installata è diversa dalla versione di bit dell'installazione di Microsoft Office, le applicazioni di Office non riescono a usare il motore di database di Access.

## <a name="situation-2-the-access-database-engine-bit-version-32-bit-or-64-bit-is-different-from-your-power-bi-desktop-bit-version"></a>Situazione 2: la versione di bit del motore di database di Access (32 bit o 64 bit) è diversa dalla versione di bit di Power BI Desktop in uso

Spesso questa situazione si verifica quando la versione installata di Microsoft Office è a 32 bit e la versione di Power BI Desktop installata è a 64 bit. Può verificarsi anche il contrario e la mancata corrispondenza di versione di bit si verificherà in entrambi i casi. Se si usa una sottoscrizione di Office 365, vedere [Situazione 3](#situation-3-trouble-using-access-or-xls-files-with-an-office-365-subscription) per un problema e una risoluzione diversi. Una delle seguenti soluzioni può risolvere l'errore di mancata corrispondenza di versione di bit:

### <a name="solution-1"></a>Soluzione 1

Modificare la versione di Power BI Desktop in modo che corrisponda alla versione di bit dell'installazione di Microsoft Office. 

1. Per modificare la versione di bit di Power BI Desktop, disinstallare Power BI Desktop e quindi installare la versione di Power BI Desktop corrispondente all'installazione di Office. 

1. Per selezionare una versione di Power BI Desktop, nella pagina di download di Power BI Desktop selezionare **Opzioni avanzate di download**.
   
   ![Opzioni avanzate di download nella pagina di download di Power BI Desktop](media/desktop-access-database-errors/desktop-access-errors-1.png)
   
1. Nella pagina di download che viene visualizzata, scegliere la lingua e quindi selezionare il pulsante **Scarica** . 
 
1. Nella schermata visualizzata selezionare la casella di controllo accanto a PBIDesktop.msi per la versione a 32 bit o la casella di controllo accanto a PBIDesktop_x64.msi per la versione a 64 bit. 

   Nello screenshot seguente è selezionata la versione a 64 bit.
   
   ![Scegliere il tipo di download di Power BI Desktop](media/desktop-access-database-errors/desktop-access-errors-2.png)
   
   >[!NOTE]
   >Se si usa la versione a 32 bit di Power BI Desktop per la creazione di modelli di dati di dimensioni molto grandi, si potrebbero riscontrare problemi di esaurimento della memoria.

### <a name="solution-2"></a>Soluzione 2

Cambiare la versione di bit di Microsoft Office in modo che corrisponda alla versione di bit dell'installazione di Power BI Desktop in uso:

1. Disinstallare Microsoft Office

2. Installare la versione di Office che corrisponde all'installazione di Power BI Desktop in uso.

### <a name="solution-3"></a>Soluzione 3

Se l'errore si verifica quando si tenta di aprire un file con estensione XLS (cartella di lavoro di Excel 97-2003), è possibile evitare di usare il motore di database di Access aprendo il file con estensione XLS in Excel e salvandolo come file con estensione XLSX.

### <a name="solution-4"></a>Soluzione 4

Se le tre soluzioni precedenti non sono applicabili, è possibile installare entrambe le versioni del motore di database di Access. Questa soluzione alternativa, tuttavia, non è consigliata. Anche se l'installazione di entrambe le versioni risolve il problema per Power Query per Excel e Power BI Desktop, introduce errori e problemi per qualsiasi applicazione che usi automaticamente (per impostazione predefinita) la versione di bit del motore di database di Access che è stata installata per prima. 

Per installare entrambe le versioni di bit del motore di database di Access, seguire questa procedura:

1. Installare entrambe le versioni di bit del motore di database di Access dalla [pagina di download](https://www.microsoft.com/download/details.aspx?id=13255). 

1. Eseguire ogni versione del motore di database di Access usando l'opzione */passive*. Ad esempio:
   
       c:\users\joe\downloads\AccessDatabaseEngine.exe /passive
   
       c:\users\joe\downloads\AccessDatabaseEngine_x64.exe /passive

## <a name="situation-3-trouble-using-access-or-xls-files-with-an-office-365-subscription"></a>Situazione 3: problemi nell'uso di file Access o XLS con una sottoscrizione di Office 365

Se si usa una sottoscrizione di Office 365, che sia **Office 2013** o **Office 2016**, il provider del motore di database di Access è registrato in un percorso del Registro di sistema virtuale accessibile *solo* ai processi di Microsoft Office. Di conseguenza, il motore Mashup (responsabile dell'esecuzione di Excel non Office 365 e di Power BI Desktop), che non è un processo di Office, non può usare il provider del motore di database di Access.

Per risolvere questo problema, [scaricare e installare il motore di database di Access ridistribuibile](https://www.microsoft.com/download/details.aspx?id=13255) che corrisponde alla versione di bit dell'installazione di Power BI Desktop. Per altre informazioni sulle versioni di bit, vedere le sezioni precedenti di questo articolo.

## <a name="other-situations-that-can-cause-import-issues"></a>Altre situazioni che possono causare problemi di importazione

Microsoft si impegna a coprire tutti i problemi possibili che si verificano con i file XLS o di Access. Se si verifica un problema che non viene trattato in questo articolo, inviare una domanda attinente al [supporto di Power BI](https://powerbi.microsoft.com/support/). Vengono esaminati regolarmente i problemi che potrebbero influire su molti clienti, che saranno poi inclusi negli articoli.

