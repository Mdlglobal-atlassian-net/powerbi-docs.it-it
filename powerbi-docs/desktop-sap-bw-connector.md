---
title: Usare SAP BW Connector in Power BI Desktop
description: Usare SAP BW Connector in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 04/09/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 79fcd556827c0c5c34615021e45e3abfadfd50e2
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="use-the-sap-bw-connector-in-power-bi-desktop"></a>Usare SAP BW Connector in Power BI Desktop
Con Power BI Desktop è possibile accedere ai dati **SAP BusinessWarehouse (BW)**.

Per informazioni su come i clienti SAP possono trarre vantaggio dal collegamento di Power BI ai propri sistemi SAP Business Warehouse (BW) esistenti, vedere il [white paper su Power BI e SAP BW](https://aka.ms/powerbiandsapbw).

## <a name="installation-of-sap-bw-connector"></a>Installazione di SAP BW Connector
Per usare **SAP BW Connector**, eseguire i passaggi di installazione seguenti:

1. Installare la libreria **SAP NetWeaver** nel computer locale. È possibile ottenere la libreria **SAP Netweaver** dall'amministratore di SAP o direttamente da [SAP Software Download Center](https://support.sap.com/swdc). Dal momento che **SAP Software Download Center** cambia struttura di frequente, non sono disponibili indicazioni più specifiche per la navigazione. La libreria **SAP NetWeaver** solitamente è inclusa anche nell'installazione di Strumenti client SAP.
   
   Si potrebbe cercare la *nota SAP 1025361* per ottenere il percorso di download per la versione più recente. Assicurarsi che l'architettura per la libreria **SAP NetWeaver** (a 32 o 64 bit) corrisponda all'installazione di **Power BI Desktop**, quindi installare tutti i file inclusi in **SAP NetWeaver RFC SDK** secondo la nota SAP.
2. La finestra di dialogo **Recupera dati** include voci **Server applicazioni SAP Business Warehouse** e **Server messaggi SAP Business Warehouse** nella categoria **Database**.
   
   ![](media/desktop-sap-bw-connector/sap_bw_2a.png)

## <a name="sap-bw-connector-features"></a>Funzionalità SAP BW Connector
**SAP BW Connector** in Power BI Desktop consente di importare dati dai cubi **Server SAP Business Warehouse** o di usare DirectQuery. 

Per altre informazioni su **SAP BW Connector** e su come usarlo con DirectQuery, vedere l'articolo [DirectQuery e SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md).

Per stabilire la connessione è necessario specificare valori per *Server*, *Numero sistema* e *ID client*.

![](media/desktop-sap-bw-connector/sap_bw_3a.png)

È anche possibile specificare altre due **Opzioni avanzate**: Codice lingua e un'istruzione MDX personalizzata da eseguire nel server specificato.

![](media/desktop-sap-bw-connector/sap_bw_4a.png)

Se non è stata specificata alcuna istruzione MDX, viene visualizzata la finestra **Strumento di navigazione** che visualizza l'elenco dei cubi disponibili nel server e offre la possibilità di eseguire il drill-down e di selezionare gli elementi dai cubi disponibili, tra cui dimensioni e misure. Power BI espone le query e i cubi esposti dai [BAPI OLAP dell'interfaccia di analisi aperta BW](https://help.sap.com/saphelp_nw70/helpdata/en/d9/ed8c3c59021315e10000000a114084/content.htm).

Quando si seleziona uno o più elementi dal server, viene creata un'anteprima della tabella di output in base alla loro selezione.

![](media/desktop-sap-bw-connector/sap_bw_5.png)

La finestra **Strumento di navigazione** offre anche alcune **Opzioni di visualizzazione** che consentono di eseguire le operazioni seguenti:

* **Visualizza *Solo gli elementi selezionati* oppure *Tutti gli elementi* (visualizzazione predefinita):** questa opzione è utile per verificare il set finale di elementi selezionati. Un approccio alternativo a questa modalità di visualizzazione consiste nel selezionare i *Nomi colonne* nell'area *Anteprima*.
* **Abilita anteprime dati (comportamento predefinito):** è possibile controllare anche se visualizzare le anteprime dei dati in questa finestra di dialogo. La disabilitazione delle anteprime dei dati riduce la quantità di chiamate al server, perché non richiede dati per le anteprime.
* **Nomi tecnici:** SAP BW supporta il concetto di *nomi tecnici* per gli oggetti all'interno di un cubo. I nomi tecnici consentono al proprietario di un cubo di esporre nomi *descrittivi* per gli oggetti cubo, anziché esporre solo i *nomi fisici* per tali oggetti nel cubo.

![](media/desktop-sap-bw-connector/sap_bw_6.png)

Dopo aver selezionato tutti gli oggetti necessari nella finestra **Strumento di navigazione**, è possibile decidere cosa fare successivamente, selezionando uno dei pulsanti seguenti nella parte inferiore della **finestra** :

* Se si seleziona **Carica** verrà attivato il caricamento dell'intero set di righe per la tabella di output nel modello di dati di Power BI Desktop, quindi viene visualizzata la vista **Report**, in cui è possibile iniziare a visualizzare i dati o ad apportare ulteriori modifiche usando le viste **Dati** o **Relazioni**.
* Se si seleziona **Modifica** viene visualizzato l'**Editor di query**, in cui è possibile eseguire passaggi aggiuntivi di trasformazione e filtro dei dati prima di importare l'intero set di righe nel modello di dati di Power BI Desktop.

Oltre a importare dati dai cubi **SAP BW**, tenere presente che è anche possibile importare dati da un'ampia gamma di altre origini dati in Power BI Desktop, che quindi è possibile combinare in un singolo report. Questa operazione presenta ogni tipo di scenario interessante per i report e l'analisi oltre ai dati **SAP BW**.

## <a name="troubleshooting"></a>Risoluzione dei problemi
Questa sezione vengono fornisce situazioni (e soluzioni) di risoluzione dei problemi per l'utilizzo di questa versione di anteprima di **SAP BW** Connector.

1. I dati numerici da **SAP BW** restituiscono decimali anziché virgole. Ad esempio, 1,000,000 viene restituito come 1.000.000.
   
   **SAP BW** restituisce dati decimali con una *,* (virgola) o un *.* (punto) come separatore decimale. Per specificare quali di questi **SAP BW** dovrebbe usare come separatore decimale, il driver usato da **Power BI Desktop** effettua una chiamata a *BAPI_USER_GET_DETAIL*. Questa chiamata restituisce una struttura denominata **DEFAULTS**, con un campo denominato *DCPFM* che archivia *Decimal Format Notation* (Notazione in formato decimale). È necessario uno dei tre valori seguenti:
   
       ‘ ‘ (space) = Decimal point is comma: N.NNN,NN
       'X' = Decimal point is period: N,NNN.NN
       'Y' = Decimal point is N NNN NNN,NN
   
   I clienti che hanno segnalato questo problema hanno riscontrato che la chiamata a *BAPI_USER_GET_DETAIL* non riesce per un determinato utente (quello per cui sono visualizzati i dati non corretti), con un messaggio di errore simile al seguente:
   
       You are not authorized to display users in group TI:
           <item>
               <TYPE>E</TYPE>
               <ID>01</ID>
               <NUMBER>512</NUMBER>
               <MESSAGE>You are not authorized to display users in group TI</MESSAGE>
               <LOG_NO/>
               <LOG_MSG_NO>000000</LOG_MSG_NO>
               <MESSAGE_V1>TI</MESSAGE_V1>
               <MESSAGE_V2/>
               <MESSAGE_V3/>
               <MESSAGE_V4/>
               <PARAMETER/>
               <ROW>0</ROW>
               <FIELD>BNAME</FIELD>
               <SYSTEM>CLNTPW1400</SYSTEM>
           </item>
   
   Per risolvere questo errore, gli utenti devono chiedere all'amministratore SAP di concedere all'utente SAPBW usato in Power BI il diritto di eseguire *BAPI_USER_GET_DETAIL*. Vale anche la pena verificare che l'utente abbia il valore *DCPFM* richiesto, come descritto in precedenza in questa soluzione.
2. **Connettività per le query BEx SAP**
   
   È possibile eseguire query **BEx** in Power BI Desktop abilitando una proprietà specifica, come illustrato nella figura seguente:
   
   ![](media/desktop-sap-bw-connector/sap_bw_8.png)

## <a name="next-steps"></a>Passaggi successivi
Per altre informazioni su SAP HANA e DirectQuery, vedere le risorse seguenti:

* [DirectQuery and SAP HANA](desktop-directquery-sap-hana.md) (DirectQuery e SAP HANA)
* [DirectQuery in Power BI](desktop-directquery-about.md)
* [Data sources supported by DirectQuery](desktop-directquery-data-sources.md) (Origini dati supportate da DirectQuery)
* [White paper su Power BI e SAP BW](https://aka.ms/powerbiandsapbw)
