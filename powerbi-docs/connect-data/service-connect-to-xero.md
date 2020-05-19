---
title: Connettersi a Xero con Power BI
description: Xero per Power BI
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 03/06/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: adb2f66b043b09ecb584870cf96f4c491960d59b
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83348437"
---
# <a name="connect-to-xero-with-power-bi"></a>Connettersi a Xero con Power BI
Xero è un software per la contabilità online facile da usare, progettato in modo specifico per le piccole imprese. È possibile creare visualizzazioni accattivanti basate sui dati finanziari di Xero con questa app modello per Power BI. Il dashboard predefinito include molte metriche relative alle piccole imprese, ad esempio disponibilità liquide, ricavi e costi, tendenza profitti e perdite, scadenziario e ritorno sugli investimenti.

Connettersi all'[app modello Xero](https://app.powerbi.com/getdata/services/xero) per Power BI oppure ottenere altre informazioni sull'integrazione tra [Xero e Power BI](https://help.xero.com/Power-BI).

## <a name="how-to-connect"></a>Come connettersi

[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]

3. Selezionare **Xero** \> **Scarica adesso**.
4. In **Installare questa app di Power BI?** selezionare **Installa**.

    ![Installare Xero](media/service-connect-to-xero/power-bi-install-xero.png)

4. Nel riquadro **App** selezionare il riquadro **Xero**.

   ![Selezionare il riquadro Xero](media/service-connect-to-xero/power-bi-start-xero.png)

6. In **Operazioni iniziali con la nuova app** selezionare **Connetti**.

    ![Operazioni iniziali con la nuova app](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

4. Immettere un nome alternativo per l'organizzazione associata all'account Xero. È possibile usare qualsiasi valore. Questo nome serve principalmente per aiutare gli utenti con più organizzazioni di Xero a gestirle in modo ottimale. Vedere i dettagli sul [reperimento dei parametri](#FindingParams) più avanti in questo articolo.

    ![Nome alternativo organizzazione](media/service-connect-to-xero/params.png)

5. In **Metodo di autenticazione** selezionare **OAuth**. Quando richiesto accedere all'account Xero e selezionare l'organizzazione a cui connettersi. Effettuato l'accesso, selezionare **Accedi** per avviare il processo di caricamento.
   
    ![Metodo di autenticazione](media/service-connect-to-xero/creds.png)
   
    ![Welcome to Xero](media/service-connect-to-xero/creds2.png)
6. Dopo l'approvazione, il processo di importazione inizierà automaticamente. Al termine, nel riquadro di spostamento verranno visualizzati un nuovo dashboard, un nuovo report e un nuovo modello. Selezionare il dashboard per visualizzare i dati importati.
   
     ![Dashboard di Xero](media/service-connect-to-xero/power-bi-xero-dashboard.png)

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](../consumer/end-user-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](../create-reports/service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](../consumer/end-user-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificarne la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="whats-included"></a>Cosa è incluso
Il dashboard dell'app modello include riquadri e metriche relative a diverse aree, con report corrispondenti che contengono altre informazioni:  

| Area | Riquadro del dashboard | Report |
| --- | --- | --- |
| Cassa |Flusso di cassa giornaliero <br>Incassi <br>Flussi di cassa in uscita <br>Saldo di chiusura per account <br>Saldo di chiusura odierno |Conti correnti bancari |
| Cliente |Vendite fatturate <br>Vendite fatturate per cliente <br>Tendenza di incremento delle vendite fatturate <br>Fatture in scadenza <br>Crediti in sospeso <br>Crediti scaduti |Cliente <br>Inventory |
| Fornitore |Acquisti fatturati <br>Acquisti fatturati per fornitore <br>Tendenza di incremento degli acquisti fatturati <br> Pagamenti in scadenza <br>Pagamenti in sospeso <br>Pagamenti scaduti |Fornitori <br>Inventory |
| Inventory |Importo di vendite mensili per prodotto |Inventory |
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
* Elementi  
* Fine mese  
* Organizzazione  
* Trial Balance  
* Account Xero

## <a name="system-requirements"></a>Requisiti di sistema
I ruoli seguenti sono necessari per accedere all'app modello Xero: "Standard + Report" o "Advisor".

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Individuazione dei parametri
Specificare un nome per l'organizzazione di cui tenere traccia in Power BI. Un nome specifico consente di connettersi a più organizzazioni diverse. Non è possibile connettersi più volte alla stessa organizzazione, perché ciò influirà sull'aggiornamento pianificato.   

## <a name="troubleshooting"></a>Risoluzione dei problemi
* Gli utenti Xero devono avere i ruoli seguenti per accedere all'app modello Xero per Power BI: "Standard + Report" o "Advisor". L'app modello si basa sulle autorizzazioni basate sugli utenti per accedere ai dati di creazione di report con Power BI.
* Durante il caricamento, i riquadri nel dashboard sono in stato di caricamento generico. Rimangono in questo stato fino al termine del caricamento completo. Se si riceve una notifica che il caricamento è stato completato ma i riquadri sono ancora in fase di caricamento, provare ad aggiornare i riquadri del dashboard usando ... nella parte superiore destra del dashboard.
* Se l'app modello non viene aggiornata, assicurarsi di non essersi connessi più volte alla stessa organizzazione in Power BI. Xero consente solo una singola connessione attiva a un'organizzazione e potrebbe essere visualizzato un errore che indica che le credenziali non sono valide se ci si connette più volte alla stessa organizzazione.  
* Per problemi di connessione all'app modello Xero per Power BI, ad esempio messaggi di errore o tempi di caricamento lenti, cancellare prima di tutto la cache o i cookie e riavviare il browser, quindi riconnettersi a Power BI.  

Per altri problemi, inviare un ticket all'indirizzo https://support.powerbi.com se il problema persiste.

## <a name="next-steps"></a>Passaggi successivi
[Introduzione a Power BI](../fundamentals/service-get-started.md)

[Recuperare dati in Power BI](service-get-data.md)
