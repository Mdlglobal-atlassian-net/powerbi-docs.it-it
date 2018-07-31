## <a name="limitations"></a>Limitazioni
Di seguito è riportato un elenco delle limitazioni correnti per la sicurezza a livello di riga nei modelli cloud.

* Se in precedenza sono stati definiti ruoli e regole all'interno del servizio Power BI, sarà necessario crearli di nuovo all'interno di Power BI Desktop.
* È possibile definire la sicurezza a livello di riga solo per i set di dati creati con il client Power BI Desktop. Se si vuole abilitare la sicurezza a livello di riga per i set di dati creati con Excel, sarà necessario convertire prima di tutto i file in file PBIX. [Altre informazioni](../desktop-import-excel-workbooks.md)
* Sono supportate solo le connessioni ETL e DirectQuery. Le connessioni dinamiche ad Analysis Services vengono gestite nel modello locale.
* Al momento le funzionalità Domande e risposte e Cortana non sono supportate con la sicurezza a livello di riga. La casella di input Domande e risposte non verrà visualizzata per i dashboard se è stata configurata la sicurezza a livello di riga per tutti i modelli. È una funzionalità prevista, anche se non è ancora disponibile una data precisa.
* Per un determinato modello, il numero massimo di entità di Azure AD, ovvero i singoli utenti o i gruppi di sicurezza, che possono essere assegnati ai ruoli di sicurezza è 1.000. Per assegnare un numero elevato di utenti ai ruoli, assicurarsi di assegnare i gruppi di sicurezza e non i singoli utenti.

## <a name="known-issues"></a>Problemi noti
Esiste un problema noto quando si riceve un messaggio di errore durante il tentativo di pubblicazione da Power BI Desktop di un set di dati già pubblicato in precedenza. Lo scenario è come indicato di seguito.

1. Anna ha un set di dati che viene pubblicato nel servizio Power BI e per cui è configurata la sicurezza a livello di riga.
2. Anna aggiorna il report in Power BI Desktop e pubblica nuovamente il set di dati.
3. Anna riceve un errore.

**Soluzione alternativa:** pubblicare nuovamente il file di Power BI Desktop dal servizio Power BI finché non viene risolto il problema. A tale scopo, selezionare **Recupera dati** > **File**. 

