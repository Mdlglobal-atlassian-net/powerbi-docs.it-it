---
title: Connettersi a un database Oracle
description: Passaggi e download necessari per connettere Oracle a Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 3dce16287c9cdcb7882e332e338137f7598b4010
ms.sourcegitcommit: a00fe5fb545c3df13b7cd13a701fd6a2b2521a17
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/31/2019
ms.locfileid: "70200900"
---
# <a name="connect-to-an-oracle-database"></a>Connettersi a un database Oracle
Per connettersi a un database Oracle con **Power BI Desktop**, è necessario che nel computer che esegue Power BI Desktop sia installato il software client Oracle appropriato. La versione del software client Oracle dipende dalla versione di Power BI Desktop installata, a **32 bit** o a **64 bit**.

**Versioni supportate**: Oracle 9 e versioni successive, software client Oracle 8.1.7 e versioni successive.

## <a name="determining-which-version-of-power-bi-desktop-is-installed"></a>Determinazione della versione di Power BI Desktop installata
Per determinare quale versione di Power BI Desktop è installata, selezionare **File > ? > Informazioni su** ed esaminare la riga **Versione:** . Nel caso della figura seguente è installata una versione a 64 bit di Power BI Desktop:

![](media/desktop-connect-oracle-database/connect-oracle-database_1.png)

## <a name="installing-the-oracle-client"></a>Installazione del client Oracle
Per le versioni a **32 bit** di Power BI Desktop, usare il collegamento seguente per scaricare e installare il client Oracle a **32 bit**:

* [Oracle Data Access Components (ODAC) a 32 bit con strumenti di sviluppo Oracle per Visual Studio (12.1.0.2.4)](http://www.oracle.com/technetwork/topics/dotnet/utilsoft-086879.html)

Per le versioni a **64 bit** di Power BI Desktop, usare il collegamento seguente per scaricare e installare il client Oracle a **64 bit**:

* [ODAC 12c versione 4 (12.1.0.2.4) a 64 bit per Windows x64](http://www.oracle.com/technetwork/database/windows/downloads/index-090165.html)

## <a name="connect-to-an-oracle-database"></a>Connettersi a un database Oracle
Dopo aver installato il driver del client Oracle corrispondente, è possibile connettersi a un database Oracle. Per stabilire la connessione, seguire la procedura illustrata di seguito:

1. Nella finestra Recupera dati selezionare **Database > Database Oracle**
   
   ![](media/desktop-connect-oracle-database/connect-oracle-database_2.png)
2. Nella finestra di dialogo **Database Oracle** visualizzata specificare il nome del server e selezionare **Connetti**. Se è necessario un SID, è possibile specificarlo nel formato *NomeServer/SID*, dove SID è il nome univoco del database. Se il formato *NomeServer/SID* non funziona, provare a usare *NomeServer/NomeServizio*, dove NomeServizio è l'alias usato durante la connessione.


   ![](media/desktop-connect-oracle-database/connect-oracle-database_3.png)

   > [!TIP]
   > Se si incontrano problemi di connessione in questo passaggio, provare a usare il formato seguente nel campo Nome del server: (DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=host_name)(PORT=port_num))(CONNECT_DATA=(SERVICE_NAME=service_name)))
   
3. Per importare i dati usando una query nativa sul database, è possibile inserire la query nella casella **Istruzione SQL**, disponibile espandendo la sezione **Opzioni avanzate** della finestra di dialogo **Database Oracle**.
   
   ![](media/desktop-connect-oracle-database/connect-oracle-database_4.png)
4. Dopo avere immesso le informazioni sul database Oracle nella finestra di dialogo Database Oracle (incluse eventuali informazioni facoltative, come un SID o una query nativa sul database), selezionare **OK** per stabilire la connessione.
5. Se il database Oracle richiede credenziali utente, immettere tali credenziali nella finestra di dialogo quando viene chiesto.


## <a name="troubleshooting"></a>Risoluzione dei problemi

Se Power BI Desktop è stato scaricato da Microsoft Store, è possibile che la connessione ai database Oracle non riesca a causa di un problema di driver di Oracle. Se si verifica questo problema, il messaggio di errore restituito è di tipo "Riferimento oggetto non impostato". Per risolvere il problema eseguire una di queste operazioni:

* Scaricare Power BI Desktop da https://powerbi.microsoft.com/desktop.

* Se si vuole usare la versione di Microsoft Store nel computer locale, copiare oraons.dll da _12.X.X\client_X_ a _12.X.X\client_X\bin_. Le X rappresentano numeri di versione e directory.

Se viene visualizzato il messaggio di errore *Riferimento all'oggetto non impostato* in Power BI Gateway durante la connessione a un database Oracle, è possibile risolvere il problema seguendo le istruzioni riportate nell'articolo [Gestire l'origine dati - Oracle](service-gateway-onprem-manage-oracle.md).
