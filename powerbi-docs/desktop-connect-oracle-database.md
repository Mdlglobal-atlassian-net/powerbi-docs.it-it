---
title: Connettersi a un database Oracle
description: Passaggi e download necessari per connettere Oracle a Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/24/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: a118cd0874410e538ca8329e0b8c0ed1bdb430b7
ms.sourcegitcommit: 834cad24901f7fd966c4010e36a7904bc120e57f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2020
ms.locfileid: "82149609"
---
# <a name="connect-to-an-oracle-database"></a>Connettersi a un database Oracle
Per connettersi a un database Oracle con Power BI Desktop, è necessario che nel computer che esegue Power BI Desktop sia installato il software client Oracle appropriato. La versione del software client Oracle dipende dalla versione di Power BI Desktop installata: a 32 bit o a 64 bit.

Versioni di Oracle supportate: 
- Oracle 9 e versioni successive
- Software client Oracle 8.1.7 e versioni successive

> [!NOTE]
> Se si sta configurando un database Oracle per il server di report di Power BI, consultare le informazioni nell'articolo [Tipo di connessione Oracle](https://docs.microsoft.com/sql/reporting-services/report-data/oracle-connection-type-ssrs?view=sql-server-ver15). 


## <a name="determining-which-version-of-power-bi-desktop-is-installed"></a>Determinazione della versione di Power BI Desktop installata
Per determinare quale versione di Power BI Desktop è installata, selezionare **File** >  **?**  > **Informazioni su** e quindi esaminare la riga **Versione**. Nel caso della figura seguente è installata una versione a 64 bit di Power BI Desktop:

![Versione di Power BI Desktop](media/desktop-connect-oracle-database/connect-oracle-database_1.png)

## <a name="installing-the-oracle-client"></a>Installazione del client Oracle
- Per la versione a 32 bit di Power BI Desktop, [scaricare e installare il client Oracle a 32 bit](https://www.oracle.com/technetwork/topics/dotnet/utilsoft-086879.html).

- Per la versione a 64 bit di Power BI Desktop, [scaricare e installare il client Oracle a 64 bit](https://www.oracle.com/technetwork/database/windows/downloads/index-090165.html).

## <a name="connect-to-an-oracle-database"></a>Connettersi a un database Oracle
Dopo aver installato il driver del client Oracle corrispondente, è possibile connettersi a un database Oracle. Per stabilire la connessione, seguire la procedura illustrata di seguito:

1. Nella scheda **Home** selezionare **Recupera dati**. 

2. Nella finestra **Recupera dati** visualizzata selezionare **Altro** (se necessario), selezionare **Database** > **Database Oracle** e quindi selezionare **Connetti**.
   
   ![Connessione al database Oracle](media/desktop-connect-oracle-database/connect-oracle-database_2.png)
2. Nella finestra di dialogo **Database Oracle** visualizzata specificare il nome del **Server** e selezionare **OK**. Se è necessario un SID, specificarlo nel formato *NomeServer/SID*, dove *SID* è il nome univoco del database. Se il formato *NomeServer/SID* non funziona, usare *NomeServer/NomeServizio*, dove *NomeServizio* è l'alias usato durante la connessione.


   ![Immettere il nome del server Oracle](media/desktop-connect-oracle-database/connect-oracle-database_3.png)

   > [!TIP]
   > Se si incontrano problemi di connessione in questo passaggio, provare a usare il formato seguente nel campo **Server**: *(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=host_name)(PORT=port_num))(CONNECT_DATA=(SERVICE_NAME=service_name)))*
   
3. Per importare i dati usando una query nativa sul database, inserire la query nella casella **Istruzione SQL**, che viene visualizzata quando si espande la sezione **Opzioni avanzate** della finestra di dialogo **Database Oracle**.
   
   ![Espandere Opzioni avanzate](media/desktop-connect-oracle-database/connect-oracle-database_4.png)
4. Dopo avere immesso le informazioni sul database Oracle nella finestra di dialogo **Database Oracle** (incluse eventuali informazioni facoltative, come un SID o una query nativa sul database), selezionare **OK** per stabilire la connessione.
5. Se il database Oracle richiede credenziali utente, immettere tali credenziali nella finestra di dialogo quando viene chiesto.


## <a name="troubleshooting"></a>Risoluzione dei problemi

Se Power BI Desktop è stato scaricato da Microsoft Store, è possibile che la connessione ai database Oracle non riesca a causa di un problema di driver di Oracle. Se si verifica questo problema, il messaggio di errore restituito è: *Riferimento a oggetto non impostato*. Per risolvere il problema, eseguire una di queste operazioni:

* Scaricare Power BI Desktop dall'[Area download](https://www.microsoft.com/download/details.aspx?id=58494) anziché da Microsoft Store.

* Se si vuole usare la versione di Microsoft Store: nel computer locale copiare oraons.dll da _12.X.X\client_X_ a _12.X.X\client_X\bin_, dove _X_ rappresenta i numeri di versione e directory.

Se viene visualizzato il messaggio di errore *Riferimento a oggetto non impostato* in Power BI Gateway durante la connessione a un database Oracle, seguire le istruzioni in [Gestire l'origine dati - Oracle](service-gateway-onprem-manage-oracle.md).

Se si usa il server di report di Power BI, consultare le linee guida nell'articolo [Tipo di connessione Oracle](https://docs.microsoft.com/sql/reporting-services/report-data/oracle-connection-type-ssrs?view=sql-server-ver15).