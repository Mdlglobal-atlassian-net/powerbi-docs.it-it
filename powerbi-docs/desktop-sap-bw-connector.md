---
title: Usare SAP BW Connector in Power BI Desktop
description: Usare SAP BW Connector in Power BI Desktop
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
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: 13f6a3fa5fc5ae5c2bea2fb6b91250216eebcc01
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/06/2017
---
# <a name="use-the-sap-bw-connector-in-power-bi-desktop"></a>Usare SAP BW Connector in Power BI Desktop
Con Power BI Desktop è possibile accedere ai dati **SAP BusinessWarehouse (BW)**.

## <a name="installation-of-sap-bw-connector"></a>Installazione di SAP BW Connector
Per usare **SAP BW Connector**, eseguire i passaggi di installazione seguenti:

1. Installare la libreria **SAP NetWeaver** nel computer locale. È possibile ottenere la libreria **SAP Netweaver** dall'amministratore di SAP o direttamente da [SAP Software Download Center](https://support.sap.com/swdc). Dal momento che **SAP Software Download Center** cambia struttura di frequente, non sono disponibili indicazioni più specifiche per la navigazione. La libreria **SAP NetWeaver** solitamente è inclusa anche nell'installazione di Strumenti client SAP.
   
   Si potrebbe cercare la *nota SAP 1025361* per ottenere il percorso di download per la versione più recente. Assicurarsi che l'architettura per la libreria **SAP NetWeaver** (a 32 o 64 bit) corrisponda all'installazione di **Power BI Desktop**, quindi installare tutti i file inclusi in **SAP NetWeaver RFC SDK** secondo la nota SAP.
2. La finestra di dialogo **Recupera dati** include una voce per **SAP Business Warehouse Server** nella categoria **Database**.
   
   ![](media/desktop-sap-bw-connector/sap_bw_2a.png)

## <a name="sap-bw-connector-features"></a>Funzionalità SAP BW Connector
L'anteprima di **SAP BW Connector** in Power BI Desktop consente agli utenti di importare i dati dai rispettivi cubi del **Server SAP Business Warehouse**. È possibile usare anche DirectQuery con il **Connettore SAP BW**. È necessario specificare *Server*, *Numero sistema* e *ID client* per stabilire la connessione.

![](media/desktop-sap-bw-connector/sap_bw_3a.png)

È anche possibile specificare altre due **Opzioni avanzate**: Codice lingua e un'istruzione MDX personalizzata da eseguire nel server specificato.

![](media/desktop-sap-bw-connector/sap_bw_4a.png)

Se non è stata specificata alcuna istruzione MDX, viene visualizzata la finestra **Strumento di navigazione** che visualizza l'elenco dei cubi disponibili nel server, l'opzione per eseguire il drill-down e selezionare gli elementi dai cubi disponibili, tra cui dimensioni e misure. Power BI espone le query e i cubi esposti dai [BAPI OLAP dell'interfaccia di analisi aperta BW](https://help.sap.com/saphelp_nw70/helpdata/en/d9/ed8c3c59021315e10000000a114084/content.htm).

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

