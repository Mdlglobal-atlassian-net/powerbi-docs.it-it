---
title: Usare SAP HANA in Power BI Desktop
description: Usare SAP HANA in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 9b205a0ae9b58acf054a9afe43196e77ee404c84
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "76753111"
---
# <a name="connect-to-sap-hana-databases-in-power-bi-desktop"></a>Connettersi a database SAP HANA in Power BI Desktop

Con Power BI Desktop è ora possibile accedere ai database *SAP HANA* . Per usare SAP HANA, il driver ODBC di SAP HANA deve essere installato nel computer client locale in modo che la connessione dati SAP HANA di Power BI Desktop funzioni correttamente. È possibile scaricare gli strumenti client di SAP HANA dalla pagina degli [strumenti di sviluppo SAP](https://tools.hana.ondemand.com/#hanatools), in cui è presente il driver ODBC necessario. In alternativa, è possibile scaricarlo dalla pagina [SAP Software Download Center](https://support.sap.com/en/my-support/software-downloads.html). Nel portale Software cercare il *CLIENT SAP HANA* per computer Windows. Dato che SAP Software Download Center cambia struttura di frequente, non sono disponibili indicazioni più specifiche per la navigazione nel sito.

Per connettersi a un database SAP HANA, selezionare **Recupera dati**, scegliere **Database** > **Database SAP HANA** e quindi selezionare **Connetti**:

![Database SAP HANA, finestra di dialogo Recupera dati, Power BI Desktop](media/desktop-sap-hana/sap-hana-1.png)

Quando ci si connette a un database SAP HANA, specificare il nome del server. Specificare quindi la porta nella casella di riepilogo a discesa e di input.

In questa versione SAP HANA in modalità [DirectQuery](desktop-directquery-sap-hana.md) è supportato in Power BI Desktop e nel servizio Power BI. È possibile pubblicare e caricare nel servizio Power BI i report che usano SAP HANA in modalità DirectQuery. È anche possibile pubblicare e caricare i report nel servizio Power BI se non si usa SAP HANA nella modalità DirectQuery.

## <a name="supported-features-for-sap-hana"></a>Funzionalità supportate per SAP HANA

Questa versione presenta molte funzionalità per SAP HANA, come illustrato nell'elenco seguente:

* Il connettore di Power BI per SAP HANA usa il driver ODBC di SAP per offrire la migliore esperienza utente.

* SAP HANA supporta le opzioni di DirectQuery Import.

* Power BI supporta i modelli informativi HANA, ad esempio le viste di analisi e di calcolo, e la navigazione è ottimizzata.

* Con SAP HANA è possibile usare anche la funzionalità di SQL diretta per la connessione alle tabelle con righe e colonne.

* Power BI include la navigazione ottimizzata per i modelli HANA.

* Power BI supporta le variabili e i parametri di input di SAP HANA.

* Power BI supporta le viste di calcolo basate su contenitori HDI.

  * Il supporto per le viste di calcolo basate su contenitori HDI è in anteprima pubblica nella versione di agosto 2019 di Power BI Desktop. Per accedere alle viste di calcolo basate su contenitori HDI in Power BI, assicurarsi che gli utenti del database HANA usati con Power BI abbiano le autorizzazioni per accedere al contenitore di runtime HDI che archivia le viste a cui si vuole accedere. Per concedere questo accesso, creare un ruolo che consenta l'accesso al contenitore HDI, quindi assegnare il ruolo all'utente del database HANA che si userà con Power BI. Questo utente deve anche avere l'autorizzazione per leggere dalle tabelle di sistema nello schema \_SYS\_BI, come di consueto. Consultare la documentazione di SAP ufficiale per istruzioni dettagliate su come creare e assegnare i ruoli del database. [Questo post del blog SAP](https://blogs.sap.com/2018/01/24/the-easy-way-to-make-your-hdi-container-accessible-to-a-classic-database-user/) può essere un buon punto di partenza.

  * Esistono attualmente alcune limitazioni per le variabili HANA associate alle viste di calcolo basate su HDI. Queste limitazioni sono dovute a errori sul lato HANA.
  
    In primo luogo, non è possibile applicare una variabile HANA a una colonna condivisa di una vista di calcolo basata su contenitori HDI. Per evitare questa limitazione, eseguire l'aggiornamento a HANA 2 versione 37.02 e successive o a HANA 2 versione 42 e successive. In secondo luogo, i valori predefiniti a più voci per variabili e parametri attualmente non vengono visualizzati nell'interfaccia utente di Power BI. Un errore in SAP HANA causa questa limitazione, ma SAP non ha ancora annunciato una correzione.

## <a name="limitations-of-sap-hana"></a>Limitazioni di SAP HANA

Esistono anche alcune limitazioni all'uso di SAP HANA, elencate di seguito:

* Le stringhe NVARCHAR vengono troncate a una lunghezza massima di 4000 caratteri Unicode.
* SMALLDECIMAL non è supportato.
* VARBINARY non è supportato.
* Le date valide sono comprese tra 30/12/1899 e 31/12/9999.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su DirectQuery e SAP HANA, vedere le risorse seguenti:

* [DirectQuery e SAP HANA](desktop-directquery-sap-hana.md)
* [Uso di DirectQuery in Power BI](desktop-directquery-about.md)
* [Origini dati di Power BI](power-bi-data-sources.md)
* [Abilitare la crittografia per SAP HANA](desktop-sap-hana-encryption.md)
