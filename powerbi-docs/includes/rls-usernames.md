## <a name="using-the-username-or-userprincipalname-dax-function"></a>Uso della funzione DAX username() o userprincipalname()
È possibile sfruttare la funzione DAX *username()* o *userprincipalname()* all'interno del set di dati. Queste funzioni possono essere usate all'interno di espressioni in Power BI Desktop. Quando si pubblica il modello, verrà usata all'interno del servizio Power BI.

All'interno di Power BI Desktop, *username()* restituirà un utente nel formato *DOMINIO\utente*, mentre *userprincipalname()* restituirà un utente nel formato <em>user@contoso.com</em>.

All'interno del servizio Power BI, *username()* e *userprincipalname()* restituiranno il nome dell'entità utente (UPN, User Principal Name). simile a un indirizzo di posta elettronica.

