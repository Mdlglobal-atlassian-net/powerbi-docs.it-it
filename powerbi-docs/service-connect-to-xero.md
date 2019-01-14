---
title: Connettersi a Xero con Power BI
description: Xero per Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 87e2ff9bf8e4eb87b4b915492bf8cfa4a97a9150
ms.sourcegitcommit: 750f0bfab02af24c8c72e6e9bbdd876e4a7399de
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54008857"
---
# <a name="connect-to-xero-with-power-bi"></a>Connettersi a Xero con Power BI
Xero è un software per la contabilità online facile da usare, progettato in modo specifico per le piccole imprese. È possibile creare visualizzazioni accattivanti basate sui dati finanziari di Xero con questo pacchetto di contenuto per Power BI. Il dashboard predefinito include molte metriche relative alle piccole imprese, ad esempio disponibilità liquide, ricavi e costi, tendenza profitti e perdite, scadenziario e ritorno sugli investimenti.

Connettersi al [pacchetto di contenuto Xero](https://app.powerbi.com/getdata/services/xero) per Power BI oppure ottenere altre informazioni sull'integrazione tra [Xero e Power BI](https://help.xero.com/Power-BI).

## <a name="how-to-connect"></a>Come connettersi
1. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro.
   
   ![](media/service-connect-to-xero/getdata.png)
2. Nella casella **Servizi** selezionare **Recupera**.
   
   ![](media/service-connect-to-xero/services.png)
3. Selezionare **Xero** \> **Recupera**.
   
   ![](media/service-connect-to-xero/connect.png)
4. Immettere un nome alternativo per l'organizzazione associata all'account Xero. È possibile usare qualsiasi valore. Questo nome serve principalmente per aiutare gli utenti con più organizzazioni di Xero a gestirle in modo ottimale. Visualizzare i dettagli [più avanti](#FindingParams).
   
   ![](media/service-connect-to-xero/params.png)
5. Per **Metodo di autenticazione** selezionare **OAuth**, quando richiesto accedere all'account Xero e selezionare l'organizzazione a cui connettersi. Al termine dell'accesso, selezionare **Accedi** per avviare il processo di caricamento.
   
    ![](media/service-connect-to-xero/creds.png)
   
    ![](media/service-connect-to-xero/creds2.png)
6. Dopo l'approvazione, il processo di importazione inizierà automaticamente. Al termine nel riquadro di spostamento verranno visualizzati un nuovo dashboard, un nuovo report e un nuovo set di dati. Selezionare il dashboard per visualizzare i dati importati.
   
     ![](media/service-connect-to-xero/dashboard.png)

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](consumer/end-user-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](consumer/end-user-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificarne la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="whats-included"></a>Cosa è incluso
Il dashboard del pacchetto di contenuto include riquadri e metriche relative a diverse aree, con report corrispondenti che forniscono altre informazioni:  

| Area | Riquadro del dashboard | Report |
| --- | --- | --- |
| Cassa |Flusso di cassa giornaliero <br>Incassi <br>Flussi di cassa in uscita <br>Saldo di chiusura per account <br>Saldo di chiusura odierno |Conti correnti bancari |
| Cliente |Vendite fatturate <br>Vendite fatturate per cliente <br>Tendenza di incremento delle vendite fatturate <br>Fatture in scadenza <br>Crediti in sospeso <br>Crediti scaduti |Cliente <br>Inventario |
| Fornitore |Acquisti fatturati <br>Acquisti fatturati per fornitore <br>Tendenza di incremento degli acquisti fatturati <br> Pagamenti in scadenza <br>Pagamenti in sospeso <br>Pagamenti scaduti |Fornitori <br>Inventario |
| Inventario |Importo di vendite mensili per prodotto |Inventario |
| Profitti e perdite |Profitti e perdite mensili <br>Profitti netti per l'anno fiscale <br>Profitti netti per il mese <br>Note spese principali |Profitti e perdite |
| Stato patrimoniale |Totale cespiti <br>Totale passività <br>Titoli azionari |Stato patrimoniale |
| Salute |Rapporto corrente <br>Percentuale di profitto lordo <br> Redditività dei cespiti totali <br>Totale passivo rapporto capitale netto |Salute <br>Glossario e note tecniche |

Il set di dati include anche le tabelle seguenti per personalizzare i report e i dashboard:  

* Indirizzi  
* Avvisi  
* Saldo giornaliero rendiconto bancario  
* Rendiconti bancari  
* Contatti  
* Note di rimborso spese  
* Voci della fattura  
* Fatture  
* Voci  
* Fine mese  
* Organizzazione  
* Bilancio di verifica  
* Account Xero

## <a name="system-requirements"></a>Requisiti di sistema
I ruoli seguenti sono necessari per accedere al pacchetto di contenuto Xero: "Standard + Report" o "Advisor".

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Individuazione dei parametri
Specificare un nome per l'organizzazione di cui tenere traccia in Power BI. Ciò consente di connettersi a più organizzazioni diverse. Si noti che non è possibile connettersi più volte alla stessa organizzazione, perché ciò influirà sull'aggiornamento pianificato.   

## <a name="troubleshooting"></a>Risoluzione dei problemi
* Gli utenti Xero devono avere i ruoli seguenti per accedere al pacchetto di contenuto Xero per Power BI: "Standard + Report" o "Advisor". Il pacchetto di contenuto si basa sulle autorizzazioni basate sugli utenti per accedere ai dati di creazione di report con Power BI.  
* Se viene visualizzato un errore dopo un certo tempo dall'inizio del caricamento, verificare quanto tempo è trascorso prima di visualizzare il messaggio. Si noti che il token di accesso fornito da Xero è valido solo per 30 minuti. In questo modo, non sarà possibile caricare gli account che possono essere caricati in quell'intervallo di tempo ma che contengono più dati. Il problema è in fase di lavorazione.
* Durante il caricamento, i riquadri nel dashboard saranno in stato di caricamento generico. Questo stato non dovrebbe modificarsi finché non viene completato il caricamento. Se si riceve una notifica che il caricamento è stato completato ma i riquadri sono ancora in fase di caricamento, provare ad aggiornare i riquadri del dashboard usando ... nella parte superiore destra del dashboard.
* Se il pacchetto di contenuto non viene aggiornato, assicurarsi di non essersi connessi più volte alla stessa organizzazione in Power BI. Xero consente solo una singola connessione attiva a un'organizzazione e potrebbe essere visualizzato un errore che indica che le credenziali non sono valide se ci si connette più volte alla stessa organizzazione.  
* Per problemi di connessione al pacchetto di contenuto Xero per Power BI, ad esempio messaggi di errore o tempi di caricamento molto lenti, cancellare prima di tutto la cache o i cookie e riavviare il browser, quindi riconnettersi a Power BI.  

Per altri problemi, inviare un ticket all'indirizzo http://support.powerbi.com se il problema persiste.

## <a name="next-steps"></a>Passaggi successivi
[Introduzione a Power BI](service-get-started.md)

[Recuperare dati in Power BI](service-get-data.md)

