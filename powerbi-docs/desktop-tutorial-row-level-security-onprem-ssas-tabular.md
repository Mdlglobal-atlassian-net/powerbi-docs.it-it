---
title: Sicurezza dinamica a livello di riga con il modello tabulare di Analysis Services
description: Sicurezza dinamica a livello di riga con il modello tabulare di Analysis Services
author: davidiseminger
ms.reviewer: davidi
editor: davidi
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 01/17/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 83cf7517fac569f8439f1debcdf621a786835d2c
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "77427370"
---
# <a name="implement-row-level-security-in-an-analysis-services-tabular-model"></a>Implementare la sicurezza a livello di riga in un modello tabulare di Analysis Services

Partendo da un set di dati di esempio da usare nella procedura descritta di seguito, questa esercitazione illustra come implementare la [**sicurezza a livello di riga**](service-admin-rls.md) in un *modello tabulare di Analysis Services* e applicarla in un report di Power BI.

* Creare una nuova tabella di sicurezza nel database [AdventureworksDW2012 database](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)
* Compilare il modello tabulare con tabelle dei fatti e delle dimensioni
* Definire ruoli utente e autorizzazioni
* Distribuire il modello in un'istanza *tabulare di Analysis Services*
* Compilare un report di Power BI Desktop che visualizzi i dati personalizzati per l'utente che accede al report
* Distribuire il report nel *servizio Power BI*
* Creare un nuovo dashboard sulla base del report
* Condividere il dashboard con i colleghi

Per questa esercitazione è necessario il [database AdventureworksDW2012](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).

## <a name="task-1-create-the-user-security-table-and-define-data-relationship"></a>Attività 1: Creare la tabella di sicurezza utente e definire le relazioni di dati

Esistono molti articoli che descrivono come definire la sicurezza dinamica a livello di riga con il modello *tabulare di SQL Server Analysis Services (SSAS)* . Per questo esempio si seguiranno le istruzioni dell'articolo [Implementare la sicurezza dinamica tramite filtri di riga](/analysis-services/tutorial-tabular-1200/supplemental-lesson-implement-dynamic-security-by-using-row-filters).

Per eseguire questi passaggi è necessario usare il database relazionale AdventureworksDW2012.

1. In AdventureworksDW2012 creare la tabella `DimUserSecurity` come illustrato di seguito. Per creare la tabella, è possibile usare [SQL Server Management Studio (SSMS)](/sql/ssms/download-sql-server-management-studio-ssms).

   ![Creare la tabella DimUserSecurity](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable.png)

1. Dopo aver creato e salvato la tabella, è necessario stabilire la relazione tra la colonna `SalesTerritoryID` della tabella `DimUserSecurity` e la colonna `SalesTerritoryKey` della tabella `DimSalesTerritory`, come illustrato di seguito.

   In SSMS fare clic con il pulsante destro del mouse su **DimUserSecurity** e selezionare **Progetta**. Selezionare quindi **Progettazione tabelle** > **Relazioni**. Al termine, salvare la tabella.

   ![Relazioni chiavi esterne](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_keys.png)

1. Aggiungere utenti alla tabella. Fare clic con il pulsante destro del mouse su **DimUserSecurity** e selezionare **Modifica le prime 200 righe**. Dopo l'aggiunta di utenti, la tabella `DimUserSecurity` dovrebbe assumere un aspetto simile all'esempio seguente:

   ![Tabella DimUserSecurity con utenti di esempio](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_users.png)

   Si tornerà a questi utenti nelle attività successive.

1. A questo punto, eseguire un *inner join* con la tabella `DimSalesTerritory` che contiene i dettagli delle aree associate agli utenti. Il codice SQL seguente esegue l'inner join, quindi l'immagine mostra l'aspetto della tabella.

    ```sql
    select b.SalesTerritoryCountry, b.SalesTerritoryRegion, a.EmployeeID, a.FirstName, a.LastName, a.UserName from [dbo].[DimUserSecurity] as a join [dbo].[DimSalesTerritory] as b on a.[SalesTerritoryID] = b.[SalesTerritoryKey]
    ```

   La tabella risultante dal join mostra chi è il responsabile di ogni area di vendita, grazie alla relazione creata nel passaggio 2. Si può ad esempio vedere che *Rita Santos* è responsabile dell'area *Australia*.

## <a name="task-2-create-the-tabular-model-with-facts-and-dimension-tables"></a>Attività 2: Compilare il modello tabulare con tabelle dei fatti e delle dimensioni

Dopo aver creato il data warehouse relazionale, è necessario definire il modello tabulare. Il modello può essere creato usando [SQL Server Data Tools](/sql/ssdt/sql-server-data-tools) (SSDT). Per altre informazioni, vedere [Creare un nuovo progetto di modello tabulare](/sql/analysis-services/lesson-1-create-a-new-tabular-model-project).

1. Importare tutte le tabelle necessarie nel modello come illustrato di seguito.

    ![SQL Server importato per l'uso con Data Tools](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/ssdt_model.png)

1. Dopo aver importato le tabelle necessarie, è necessario definire un ruolo denominato *SalesTerritoryUsers* con autorizzazione di lettura. Selezionare il menu **Modello** in SQL Server Data Tools, quindi selezionare **Ruoli**. In **Gestione ruoli** selezionare **Nuovo**.

1. Nella scheda **Membri** della finestra di dialogo **Gestione ruoli** aggiungere gli utenti definiti nella tabella `DimUserSecurity` durante l'[attività 1](#task-1-create-the-user-security-table-and-define-data-relationship).

    ![Aggiungere utenti in Gestione ruoli](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/rolemanager.png)

1. Aggiungere quindi le funzioni appropriate per entrambe le tabelle `DimSalesTerritory` e `DimUserSecurity`, come illustrato di seguito nella scheda **Filtri di riga**.

    ![Aggiungere funzioni ai filtri di riga](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/rolemanager_complete.png)

1. La funzione `LOOKUPVALUE` restituisce i valori per una colonna in cui il nome utente di Windows è uguale a quello restituito dalla funzione `USERNAME`. È quindi possibile limitare le query al punto in cui i valori restituiti dalla funzione `LOOKUPVALUE` sono uguali a quelli presenti nella stessa tabella o in quella correlata. Nella colonna **Filtro DAX** digitare la formula seguente:

    ```dax
        =DimSalesTerritory[SalesTerritoryKey]=LOOKUPVALUE(DimUserSecurity[SalesTerritoryID], DimUserSecurity[UserName], USERNAME(), DimUserSecurity[SalesTerritoryID], DimSalesTerritory[SalesTerritoryKey])
    ```

    In questa formula la funzione `LOOKUPVALUE` restituisce tutti i valori per la colonna `DimUserSecurity[SalesTerritoryID]`, dove `DimUserSecurity[UserName]` corrisponde al nome utente di Windows attualmente connesso e `DimUserSecurity[SalesTerritoryID]` è uguale a `DimSalesTerritory[SalesTerritoryKey]`.

    > [!IMPORTANT]
    > Quando si usa la sicurezza a livello di riga, la funzione DAX [USERELATIONSHIP](/dax/userelationship-function-dax) non è supportata.

   Il set di `SalesTerritoryKey` di Sales restituito da `LOOKUPVALUE` viene quindi usato per limitare le righe visualizzate in `DimSalesTerritory`. Vengono visualizzate solo le righe in cui il valore `SalesTerritoryKey` si trova nel set di ID restituiti dalla funzione `LOOKUPVALUE`.

1. Per la tabella `DimUserSecurity`, aggiungere la formula seguente nella colonna **Filtro DAX**:

    ```dax
        =FALSE()
    ```

    Questa formula specifica che tutte le colonne vengono risolte in `false`, pertanto non è possibile eseguire query sulle colonne della tabella `DimUserSecurity`.

A questo punto è necessario elaborare e distribuire il modello. Per altre informazioni, vedere [Distribuzione](/sql/analysis-services/lesson-13-deploy).

## <a name="task-3-add-data-sources-within-your-on-premises-data-gateway"></a>Attività 3: Aggiungere origini dati all'interno del gateway dati locale

Quando il modello tabulare è stato distribuito ed è pronto per l'uso, è necessario aggiungere una connessione origine dati al server tabulare di Analysis Services locale.

1. Per consentire al servizio Power BI di accedere all'istanza di Analysis Services locale, è necessario che nell'ambiente sia installato e configurato un [gateway dati locale](service-gateway-onprem.md).

1. Dopo aver configurato correttamente il gateway, è necessario creare una connessione all'origine dati per l'istanza tabulare di *Analysis Services*. Per altre informazioni, vedere [Gestire l'origine dati - Analysis Services](service-gateway-enterprise-manage-ssas.md).

   ![Creare una connessione all'origine dati](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/pbi_gateway.png)

Al termine di questa procedura, il gateway è configurato e pronto per interagire con l'origine dati di Analysis Services locale.

## <a name="task-4-create-report-based-on-analysis-services-tabular-model-using-power-bi-desktop"></a>Attività 4: Creare un report basato sul modello tabulare di Analysis Services usando Power BI Desktop

1. Avviare Power BI Desktop e selezionare **Recupera dati** > **Database**.

1. Dall'elenco delle origini dati selezionare **Database di SQL Server Analysis Services**, quindi **Connetti**.

   ![Connettersi al database di SQL Server Analysis Services](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata.png)

1. Inserire i dettagli dell'istanza tabulare di Analysis Services e selezionare **Connessione dinamica**. Selezionare **OK**.
  
   ![Dettagli di Analysis Services](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata_connectlive.png)

   In Power BI la sicurezza dinamica funziona solo con una connessione dinamica.

1. È possibile notare che il modello distribuito si trova nell'istanza di Analysis Services. Selezionare il modello corrispondente, quindi selezionare **OK**.

   In Power BI Desktop sono ora visualizzati tutti i campi disponibili, a destra dell'area di disegno nel riquadro **Campi**.

1. Nel riquadro **Campi** selezionare la misura **SalesAmount** dalla tabella **FactInternetSales** e la dimensione **SalesTerritoryRegion** dalla tabella **SalesTerritory**.

1. Per mantenere la semplicità del report, al momento non verranno aggiunte altre colonne. Perché la rappresentazione dei dati sia più significativa, cambiare la visualizzazione in **Grafico ad anello**.

   ![Visualizzazione del grafico ad anello](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/donut_chart.png)

1. Quando il report è pronto, è possibile pubblicarlo direttamente nel portale di Power BI. Nella scheda **Home** della barra multifunzione di Power BI Desktop selezionare **Pubblica**.

## <a name="task-5-create-and-share-a-dashboard"></a>Attività 5: Creare e condividere un dashboard

Il report è stato creato e pubblicato nel servizio **Power BI**. A questo punto è possibile usare l'esempio creato nei passaggi precedenti per illustrare lo scenario di sicurezza del modello.

Nel ruolo di *Responsabile vendite*, l'utente Grace può visualizzare i dati di tutte le varie aree di vendita. Grace crea il report e lo pubblica nel servizio Power BI. Questo report è stato creato nelle attività precedenti.

Dopo la pubblicazione del report, il passaggio successivo consiste nel creare un dashboard del servizio Power BI denominato *TabularDynamicSec*, in base a tale report. Nella figura seguente si può notare che Grace può visualizzare i dati corrispondenti all'intera area di vendita.

   ![Dashboard del servizio Power BI](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/donut_chart_1.png)

Ora Grace condivide il dashboard con una collega, Rita, responsabile delle vendite nell'area Australia.

   ![Condividere un dashboard di Power BI](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/pbi_dashboard.png)

Quando Rita accede al servizio Power BI e visualizza il dashboard condiviso che Grace ha creato, può vedere solo le vendite dell'area Australia.

Congratulazioni! Il servizio Power BI illustra la sicurezza dinamica a livello di riga definita nel modello tabulare di Analysis Services locale. Power BI usa la proprietà `EffectiveUserName` per inviare le credenziali dell'utente di Power BI corrente all'origine dati locale per eseguire le query.

## <a name="task-6-understand-what-happens-behind-the-scenes"></a>Attività 6: Conoscere ciò che accade dietro le quinte

Questa attività presuppone che si abbia familiarità con [SQL Server Profiler](/sql/tools/sql-server-profiler/sql-server-profiler) perché è necessario acquisire una traccia di SQL Server Profiler nell'istanza tabulare di SSAS locale.

La sessione verrà inizializzata non appena l'utente Rita eseguirà l'accesso al dashboard nel servizio Power BI. È possibile notare che il ruolo **salesterritoryusers** avrà effetto immediato con il nome utente effettivo **<EffectiveUserName>rita@contoso.com</EffectiveUserName>**

       <PropertyList><Catalog>DefinedSalesTabular</Catalog><Timeout>600</Timeout><Content>SchemaData</Content><Format>Tabular</Format><AxisFormat>TupleFormat</AxisFormat><BeginRange>-1</BeginRange><EndRange>-1</EndRange><ShowHiddenCubes>false</ShowHiddenCubes><VisualMode>0</VisualMode><DbpropMsmdFlattened2>true</DbpropMsmdFlattened2><SspropInitAppName>PowerBI</SspropInitAppName><SecuredCellValue>0</SecuredCellValue><ImpactAnalysis>false</ImpactAnalysis><SQLQueryMode>Calculated</SQLQueryMode><ClientProcessID>6408</ClientProcessID><Cube>Model</Cube><ReturnCellProperties>true</ReturnCellProperties><CommitTimeout>0</CommitTimeout><ForceCommitTimeout>0</ForceCommitTimeout><ExecutionMode>Execute</ExecutionMode><RealTimeOlap>false</RealTimeOlap><MdxMissingMemberMode>Default</MdxMissingMemberMode><DisablePrefetchFacts>false</DisablePrefetchFacts><UpdateIsolationLevel>2</UpdateIsolationLevel><DbpropMsmdOptimizeResponse>0</DbpropMsmdOptimizeResponse><ResponseEncoding>Default</ResponseEncoding><DirectQueryMode>Default</DirectQueryMode><DbpropMsmdActivityID>4ea2a372-dd2f-4edd-a8ca-1b909b4165b5</DbpropMsmdActivityID><DbpropMsmdRequestID>2313cf77-b881-015d-e6da-eda9846d42db</DbpropMsmdRequestID><LocaleIdentifier>1033</LocaleIdentifier><EffectiveUserName>rita@contoso.com</EffectiveUserName></PropertyList>

In base alla richiesta del nome utente effettivo, Analysis Services converte la richiesta nelle credenziali `contoso\rita` effettive dopo l'esecuzione di una query sull'istanza di Active Directory locale. Dopo aver ottenuto le credenziali, Analysis Services restituisce i dati per i quali l'utente ha l'autorizzazione di visualizzazione e accesso.

Se vengono eseguite altre attività con il dashboard, in SQL Profiler si noterà una query specifica che viene nuovamente inviata al modello tabulare di Analysis Services come query DAX. Se, ad esempio, Rita passa dal dashboard al report sottostante, viene eseguita la query seguente.

   ![La query DAX torna al modello di Analysis Services](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/profiler1.png)

È anche possibile vedere di seguito la query DAX, eseguita per popolare i dati del report.
   
   ```dax
   EVALUATE
     ROW(
       "SumEmployeeKey", CALCULATE(SUM(Employee[EmployeeKey]))
     )
   
   <PropertyList xmlns="urn:schemas-microsoft-com:xml-analysis">``
             <Catalog>DefinedSalesTabular</Catalog>
             <Cube>Model</Cube>
             <SspropInitAppName>PowerBI</SspropInitAppName>
             <EffectiveUserName>rita@contoso.com</EffectiveUserName>
             <LocaleIdentifier>1033</LocaleIdentifier>
             <ClientProcessID>6408</ClientProcessID>
             <Format>Tabular</Format>
             <Content>SchemaData</Content>
             <Timeout>600</Timeout>
             <DbpropMsmdRequestID>8510d758-f07b-a025-8fb3-a0540189ff79</DbpropMsmdRequestID>
             <DbPropMsmdActivityID>f2dbe8a3-ef51-4d70-a879-5f02a502b2c3</DbPropMsmdActivityID>
             <ReturnCellProperties>true</ReturnCellProperties>
             <DbpropMsmdFlattened2>true</DbpropMsmdFlattened2>
             <DbpropMsmdActivityID>f2dbe8a3-ef51-4d70-a879-5f02a502b2c3</DbpropMsmdActivityID>
           </PropertyList>
   ```

## <a name="considerations"></a>Considerazioni

* La sicurezza a livello di riga locale in Power BI è disponibile solo con la connessione dinamica.

* Le eventuali modifiche apportate ai dati dopo l'elaborazione del modello saranno immediatamente disponibili per gli utenti che eseguiranno l'accesso tramite connessione dinamica dal servizio Power BI.

