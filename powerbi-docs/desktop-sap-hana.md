---
title: Usare SAP HANA in Power BI Desktop
description: Usare SAP HANA in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/21/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 1932848cb2f8ad7d75e841870265cc22308467c2
ms.sourcegitcommit: a00fe5fb545c3df13b7cd13a701fd6a2b2521a17
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/31/2019
ms.locfileid: "70200854"
---
# <a name="use-sap-hana-in-power-bi-desktop"></a>Usare SAP HANA in Power BI Desktop
Con Power BI Desktop è ora possibile accedere ai database **SAP HANA** . Per usare **SAP HANA**, il driver ODBC di SAP HANA deve essere installato nel computer client locale in modo che la connessione dati **SAP HANA** di Power BI Desktop funzioni correttamente. È possibile scaricare il driver ODBC di SAP HANA da [SAP Software Download Center](https://support.sap.com/swdc). Da qui, cercare il CLIENT SAP HANA per i computer Windows. Dal momento che **SAP Software Download Center** cambia struttura di frequente, non sono disponibili indicazioni più specifiche per la navigazione.

Per connettersi a un database **SAP HANA**, selezionare **Recupera dati > Database > Database SAP HANA** come illustrato nella figura seguente:

![](media/desktop-sap-hana/sap-hana-1.png)

Quando ci si connette a un database SAP HANA, specificare il nome del server. Specificare quindi la porta nella casella di riepilogo a discesa e di input.

In questa versione, **SAP HANA** in modalità [DirectQuery](desktop-directquery-sap-hana.md) è supportato in Power BI Desktop e nel servizio Power BI ed è possibile pubblicare e caricare report che usano **SAP HANA** in modalità DirectQuery nel servizio Power BI. È anche possibile pubblicare e caricare i report nel servizio Power BI se non si usa **SAP HANA** nella modalità DirectQuery.

## <a name="supported-features-for-sap-hana"></a>Funzionalità supportate per SAP HANA
Questa versione presenta molte funzionalità per **SAP HANA**, come illustrato nell'elenco seguente:

* Il connettore di Power BI per **SAP HANA** usa il driver ODBC di SAP per offrire la migliore esperienza di utilizzo
* **SAP HANA** supporta le opzioni di DirectQuery e Import
* Power BI supporta i modelli informativi HANA (quali le viste analitiche e di calcolo) e dispone di navigazione ottimizzata
* Con **SAP HANA** è possibile usare anche la funzionalità SQL diretta per la connessione alle tabelle Riga e Colonna
* Esso include la struttura ottimizzata per i modelli HANA
* Power BI supporta le variabili e i parametri di input di **SAP HANA**
* Viste di calcolo basate su contenitori HDI
  * Il supporto per le viste di calcolo basate su contenitori HDI è in anteprima pubblica nella versione di agosto 2019 di Power BI Desktop. Per accedere alle viste di calcolo basate su contenitori HDI in Power BI, assicurarsi che gli utenti del database HANA usati con Power BI abbiano le autorizzazioni per accedere al contenitore di runtime HDI che archivia le viste a cui si vuole accedere. Per concedere questo accesso, è necessario creare un ruolo che consenta l'accesso al contenitore HDI e assegnare il ruolo all'utente del database HANA che verrà usato con Power BI. L'utente deve anche avere le autorizzazioni di lettura dalle tabelle di sistema nello schema \_SYS\_BI, come di consueto. Consultare la documentazione di SAP ufficiale per istruzioni dettagliate su come creare e assegnare i ruoli del database. [Questo post del blog SAP](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fblogs.sap.com%2F2018%2F01%2F24%2Fthe-easy-way-to-make-your-hdi-container-accessible-to-a-classic-database-user%2F&data=02%7C01%7Cv-adbold%40microsoft.com%7Cf7e0a405fe334598ba0608d7096ef5b4%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636988244476739316&sdata=PuRu61GPRYp34mLuGbQk6gdbRikdgbxfqo8q1RBQtm0%3D&reserved=0) può essere un buon punto di partenza.
  * Si noti che esistono attualmente alcune limitazioni per le variabili HANA associate alle viste di calcolo basate su HDI. Queste limitazioni sono dovute a errori sul lato HANA e verranno superate nelle versioni future di SAP HANA. In primo luogo, non è possibile applicare una variabile HANA a una colonna condivisa di una vista di calcolo basata su contenitori HDI. Questa limitazione può essere evitata eseguendo l'aggiornamento a HANA 2 versione 37.02 e successive o a HANA 2 versione 42 e successive. In secondo luogo, i valori predefiniti multi-voce per variabili e parametri attualmente non vengono visualizzati nell'interfaccia utente di Power BI. Ciò è dovuto anche a un errore in SAP HANA. Tuttavia, SAP non ha ancora annunciato una correzione.

## <a name="limitations-of-sap-hana"></a>Limitazioni di SAP HANA
Esistono inoltre alcune limitazioni all'uso di **SAP HANA**, come illustrato di seguito:

* Le stringhe NVARCHAR vengono troncate alla lunghezza massima di 4000 caratteri Unicode
* SMALLDECIMAL non è supportato
* VARBINARY non è supportato
* Le date valide sono comprese tra 30/12/1899 e 31/12/9999


## <a name="next-steps"></a>Passaggi successivi
Per altre informazioni su DirectQuery e SAP HANA, vedere le risorse seguenti:

* [DirectQuery and SAP HANA](desktop-directquery-sap-hana.md) (DirectQuery e SAP HANA)
* [DirectQuery in Power BI](desktop-directquery-about.md)
* [Data sources supported by DirectQuery](desktop-directquery-data-sources.md) (Origini dati supportate da DirectQuery)
* [Abilitare la crittografia per SAP HANA](desktop-sap-hana-encryption.md)


