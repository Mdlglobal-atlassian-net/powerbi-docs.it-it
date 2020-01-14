---
title: Sicurezza a livello di riga dinamica con il modello tabulare di Analysis Services
description: Sicurezza a livello di riga dinamica con il modello tabulare di Analysis Services
author: selvarms
ms.reviewer: davidi
editor: davidi
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 05/28/2019
ms.author: selvar
LocalizationGroup: Connect to data
ms.openlocfilehash: 09e4a9cc3e6a5c16f23532f0a4589fdcb1906549
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2020
ms.locfileid: "75759521"
---
# <a name="implement-row-level-security-in-an-analysis-services-tabular-model"></a>Implementare la sicurezza a livello di riga in un modello tabulare di Analysis Services

Partendo da un set di dati di esempio da usare durante la procedura descritta di seguito, questa esercitazione illustra come implementare la [**sicurezza a livello di riga**](service-admin-rls.md) in un **modello tabulare di Analysis Services** e usarlo in un report di Power BI. 

* Creare una nuova tabella di sicurezza nel database [**AdventureworksDW2012**](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)
* Compilare il modello tabulare con tabelle dei fatti e delle dimensioni
* Definire ruoli utente e autorizzazioni
* Distribuire il modello in un'istanza **tabulare di Analysis Services**
* Compilare un report di Power BI Desktop che visualizzi i dati personalizzati per l'utente che accede al report
* Distribuire il report nel **servizio Power BI**
* Creare un nuovo dashboard sulla base del report
* Condividere il dashboard con i colleghi 

In questa esercitazione è necessario il [**database AdventureworksDW2012**](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).

## <a name="task-1-create-the-user-security-table-and-define-data-relationship"></a>Attività 1: Creare la tabella di sicurezza utente e definire le relazioni di dati

Esistono molti articoli che descrivono come definire la sicurezza dinamica livello di riga con il modello **tabulare di SQL Server Analysis Services (SSAS)** . Per questo esempio si seguiranno le istruzioni dell'articolo [Implementare la sicurezza dinamica tramite filtri di riga](https://docs.microsoft.com/analysis-services/tutorial-tabular-1200/supplemental-lesson-implement-dynamic-security-by-using-row-filters). 

Per eseguire questi passaggi è necessario usare il database relazionale **AdventureworksDW2012**.

1. In **AdventureworksDW2012** creare la tabella **DimUserSecurity** come illustrato di seguito. Per creare la tabella, è possibile usare [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable.png)

2. Dopo aver creato e salvato la tabella, è necessario stabilire la relazione tra la colonna **SalesTerritoryID** della tabella **DimUserSecurity** e la colonna **SalesTerritoryKey** della tabella **DimSalesTerritory**, come illustrato nell'immagine seguente. 

   In **SSMS** fare clic sulla tabella **DimUserSecurity** e selezionare **Progetta**. Selezionare quindi **Progettazione tabelle -> Relazioni**. Al termine, salvare la tabella.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_keys.png)

3. Aggiungere gli utenti alla tabella. Fare clic con il pulsante destro del mouse sulla tabella **DimUserSecurity** e selezionare **Modifica le prime 200 righe**. Dopo aver aggiunto gli utenti, la tabella **DimUserSecurity** avrà l'aspetto seguente con i propri utenti:
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_users.png)
   
   Si tornerà a questi utenti nelle attività successive.

4. A questo punto viene eseguito un *inner join* con la tabella **DimSalesTerritory** che contiene i dettagli dell'area associati all'utente. Il codice SQL esegue l'*inner join*. L'immagine illustra la visualizzazione della tabella.
   
       select b.SalesTerritoryCountry, b.SalesTerritoryRegion, a.EmployeeID, a.FirstName, a.LastName, a.UserName from [dbo].[DimUserSecurity] as a join  [dbo].[DimSalesTerritory] as b on a.[SalesTerritoryID] = b.[SalesTerritoryKey]
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_join_users.png)

   L'immagine illustra chi è il responsabile di ogni area di vendita, grazie alla relazione creata nel **passaggio 2**. Si può ad esempio notare che **Jon Doe** è il responsabile per l'**Australia**. 

## <a name="task-2-create-the-tabular-model-with-facts-and-dimension-tables"></a>Attività 2: Compilare il modello tabulare con tabelle dei fatti e delle dimensioni

1. Dopo aver creato il data warehouse relazionale, è necessario definire il modello tabulare. Il modello può essere creato usando [**SQL Server Data Tools (SSDT)** ](https://docs.microsoft.com/sql/ssdt/sql-server-data-tools). Per altre informazioni, vedere [Creare un nuovo progetto di modello tabulare](https://msdn.microsoft.com/library/hh231689.aspx).

2. Importare tutte le tabelle necessarie nel modello come illustrato di seguito.
   
    ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/ssdt_model.png)

3. Dopo aver importato le tabelle necessarie, occorre definire un ruolo denominato **SalesTerritoryUsers** con autorizzazione di **lettura**. Selezionare il menu **Modello** in SQL Server Data Tools, quindi selezionare **Ruoli**. Nella finestra di dialogo **Gestione ruoli** selezionare **Nuovo**.

4. Nella scheda **Membri** della finestra di dialogo **Gestione ruoli** aggiungere gli utenti definiti nella tabella **DimUserSecurity** al **passaggio 3 dell'attività 1**.
   
    ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/rolemanager.png)

5. Successivamente, aggiungere le funzioni appropriate per le tabelle **DimSalesTerritory** e **DimUserSecurity**, come illustrato di seguito nella scheda **Filtri di riga**.
   
    ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/rolemanager_complete.png)

6. In questo passaggio viene usata la funzione **LOOKUPVALUE** per restituire i valori per una colonna in cui il nome utente di Windows è uguale a quello restituito dalla funzione **USERNAME**. È quindi possibile limitare le query al punto in cui i valori restituiti dalla funzione **LOOKUPVALUE** sono uguali a quelli presenti nella stessa tabella o in quella correlata. Nella colonna **Filtro DAX** digitare la formula seguente:
   
       =DimSalesTerritory[SalesTerritoryKey]=LOOKUPVALUE(DimUserSecurity[SalesTerritoryID], DimUserSecurity[UserName], USERNAME(), DimUserSecurity[SalesTerritoryID], DimSalesTerritory[SalesTerritoryKey])

    In questa formula la funzione **LOOKUPVALUE** restituisce tutti i valori per la colonna **DimUserSecurity [SalesTerritoryID]** , dove **DimUserSecurity [UserName]** è uguale al nome utente di Windows connesso e **DimUserSecurity [SalesTerritoryID]** è uguale a **DimSalesTerritory [SalesTerritoryKey]** .
   
    > [!IMPORTANT]
    > Quando si usa la sicurezza a livello di riga, la funzione DAX [USERELATIONSHIP](https://msdn.microsoft.com/query-bi/dax/userelationship-function-dax) non è supportata.

   Il set di Sales SalesTerritoryKey restituito da **LOOKUPVALUE** viene quindi usato per limitare le righe visualizzate in **DimSalesTerritory**. Vengono visualizzate solo le righe in cui il valore **SalesTerritoryKey** si trova nel set di ID restituiti dalla funzione **LOOKUPVALUE**.

7. Per la tabella **DimUserSecurity**, aggiungere la formula seguente nella colonna **Filtro DAX**:
   
       =FALSE()

    Questa formula specifica che tutte le colonne vengono risolte in `false`, quindi non è possibile eseguire query nelle colonne della tabella **DimUserSecurity**.

8. A questo punto è necessario elaborare e distribuire il modello. Per altre informazioni, vedere l'[articolo Distribuire](https://msdn.microsoft.com/library/hh231693.aspx).

## <a name="task-3-add-data-sources-within-your-on-premises-data-gateway"></a>Attività 3: Aggiungere origini dati all'interno del gateway dati locale

Quando il modello tabulare è stato distribuito ed è pronto per l'uso, è necessario aggiungere una connessione origine dati al server tabulare di Analysis Services locale.

1. Per consentire al **servizio Power BI** di accedere all'istanza di Analysis Services locale, è necessario che nell'ambiente sia installato e configurato un **[gateway dati locale](service-gateway-onprem.md)** .

2. Dopo aver configurato correttamente il gateway, è necessario creare una connessione all'origine dati per l'istanza tabulare di **Analysis Services**. Per altre informazioni, vedere [Gestire l'origine dati - Analysis Services](service-gateway-enterprise-manage-ssas.md).
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/pbi_gateway.png)

  Dopo aver completato il passaggio precedente, il gateway è configurato e pronto per interagire con l'origine dati di **Analysis Services** locale.

## <a name="task-4-create-report-based-on-analysis-services-tabular-model-using-power-bi-desktop"></a>Attività 4: Creare un report basato sul modello tabulare di Analysis Services usando Power BI Desktop

1. Avviare **Power BI Desktop** e selezionare **Recupera dati > Database**.

2. Dall'elenco delle origini dati selezionare **Database di SQL Server Analysis Services**, quindi **Connetti**.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata.png)

3. Inserire i dettagli dell'istanza tabulare di **Analysis Services** e selezionare **Connessione in tempo reale**. Selezionare quindi **OK**. In **Power BI** la sicurezza dinamica funziona solo se si seleziona l'opzione **Connessione dinamica**.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata_connectlive.png)

4. È possibile notare che il modello distribuito si trova nell'istanza di **Analysis Services**. Selezionare il modello corrispondente, quindi selezionare **OK**.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata_connectlive.png)

   In **Power BI Desktop** ora sono visualizzati tutti i campi disponibili, a destra dell'area di disegno nel riquadro **Campi**.

5. Nel riquadro **Campi** a destra selezionare la misura **SalesAmount** dalla tabella **FactInternetSales** e la dimensione **SalesTerritoryRegion** dalla tabella **SalesTerritory**.

6. Per mantenere la semplicità del report, al momento non verranno aggiunte altre colonne. Perché la rappresentazione dei dati sia più significativa, cambiare la visualizzazione in **Grafico ad anello**.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/donut_chart.png)

7. Quando il report è pronto, è possibile pubblicarlo direttamente nel portale di Power BI. Dalla barra multifunzione **Home** in **Power BI Desktop** selezionare **Pubblica**.

## <a name="task-5-create-and-share-a-dashboard"></a>Attività 5: Creare e condividere un dashboard

1. Il report è stato creato e pubblicato nel servizio **Power BI**. A questo punto è possibile usare l'esempio creato nei passaggi precedenti per illustrare lo scenario di sicurezza del modello.
   
   Nel ruolo di **Responsabile vendite** l'utente Sumit può visualizzare i dati di tutte le varie aree di vendita. Sumit crea il report, vale a dire quello creato nei precedenti passaggi delle attività, e lo pubblica nel servizio Power BI.
   
   Dopo aver pubblicato il report, Sumit crea un dashboard nel servizio Power BI denominato **TabularDynamicSec**, basato su tale report. Nell'immagine seguente si può notare che Sumit può visualizzare i dati corrispondenti all'intera area di vendita.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/donut_chart_1.png)

2. Ora Sumit condivide il dashboard con un collega, Jon Doe, responsabile delle vendite nell'area Australia.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/user_jon_doe.png)
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/pbi_dashboard.png)

3. Quando Jon Doe accede al servizio **Power BI** e visualizza il dashboard condiviso che Sumit ha creato, vedrà **solo** le vendite della sua regione. 
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/dashboard_jon_doe.png)

    Congratulazioni. Il **servizio Power BI** illustra la sicurezza dinamica a livello di riga definita nel modello tabulare di **Analysis Services** locale. Power BI usa la proprietà **EffectiveUserName** per inviare le credenziali dell'utente di Power BI corrente all'origine dati locale per eseguire le query.

## <a name="task-6-understand-what-happens-behind-the-scenes"></a>Attività 6: Conoscere ciò che accade dietro le quinte

Questa attività presuppone che si abbia familiarità con [SQL Profiler](https://docs.microsoft.com/sql/tools/sql-server-profiler/sql-server-profiler) perché è necessario acquisire una traccia di SQL Server Profiler nell'istanza tabulare di SSAS locale.

1. La sessione verrà inizializzata non appena l'utente (in questo caso Jon Doe) eseguirà l'accesso al dashboard nel servizio Power BI. È possibile notare che il ruolo **salesterritoryusers** avrà effetto immediato con il nome utente effettivo **<EffectiveUserName>jondoe@moonneo.com</EffectiveUserName>**
   
       <PropertyList><Catalog>DefinedSalesTabular</Catalog><Timeout>600</Timeout><Content>SchemaData</Content><Format>Tabular</Format><AxisFormat>TupleFormat</AxisFormat><BeginRange>-1</BeginRange><EndRange>-1</EndRange><ShowHiddenCubes>false</ShowHiddenCubes><VisualMode>0</VisualMode><DbpropMsmdFlattened2>true</DbpropMsmdFlattened2><SspropInitAppName>PowerBI</SspropInitAppName><SecuredCellValue>0</SecuredCellValue><ImpactAnalysis>false</ImpactAnalysis><SQLQueryMode>Calculated</SQLQueryMode><ClientProcessID>6408</ClientProcessID><Cube>Model</Cube><ReturnCellProperties>true</ReturnCellProperties><CommitTimeout>0</CommitTimeout><ForceCommitTimeout>0</ForceCommitTimeout><ExecutionMode>Execute</ExecutionMode><RealTimeOlap>false</RealTimeOlap><MdxMissingMemberMode>Default</MdxMissingMemberMode><DisablePrefetchFacts>false</DisablePrefetchFacts><UpdateIsolationLevel>2</UpdateIsolationLevel><DbpropMsmdOptimizeResponse>0</DbpropMsmdOptimizeResponse><ResponseEncoding>Default</ResponseEncoding><DirectQueryMode>Default</DirectQueryMode><DbpropMsmdActivityID>4ea2a372-dd2f-4edd-a8ca-1b909b4165b5</DbpropMsmdActivityID><DbpropMsmdRequestID>2313cf77-b881-015d-e6da-eda9846d42db</DbpropMsmdRequestID><LocaleIdentifier>1033</LocaleIdentifier><EffectiveUserName>jondoe@moonneo.com</EffectiveUserName></PropertyList>

2. In base alla richiesta del nome utente effettivo, Analysis Services converte la richiesta nelle credenziali moonneo/jondoe effettive dopo l'esecuzione di query all'istanza di Active Directory locale. Dopo aver ottenuto le credenziali, **Analysis Services** restituisce i dati per i quali l'utente ha autorizzazione di visualizzazione e accesso.

3. Se si verificano altre attività con il dashboard, ad esempio se Jon Doe passa dal dashboard al report sottostante, in SQL Profiler si noterà una query specifica che viene nuovamente inviata al modello tabulare di Analysis Services come query DAX.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/profiler1.png)

4. È anche possibile vedere di seguito la query DAX, eseguita per popolare i dati del report.
   
   ```
   EVALUATE
     ROW(
       "SumEmployeeKey", CALCULATE(SUM(Employee[EmployeeKey]))
     )
   
   <PropertyList xmlns="urn:schemas-microsoft-com:xml-analysis">``
             <Catalog>DefinedSalesTabular</Catalog>
             <Cube>Model</Cube>
             <SspropInitAppName>PowerBI</SspropInitAppName>
             <EffectiveUserName>jondoe@moonneo.com</EffectiveUserName>
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

* Le eventuali modifiche apportate ai dati dopo l'elaborazione del modello saranno immediatamente disponibili per gli utenti che eseguiranno l'accesso tramite **connessione dinamica** dal servizio Power BI.

