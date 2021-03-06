---
title: Filtrare un report usando i parametri della stringa di query nell'URL
description: Filtrare un report usando i parametri della stringa di query dell'URL, filtrando anche in base a più campi.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/04/2020
LocalizationGroup: Reports
ms.openlocfilehash: 6ca52601526568668ef3de25df69159a74033e50
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83273593"
---
# <a name="filter-a-report-using-query-string-parameters-in-the-url"></a>Filtrare un report usando i parametri della stringa di query nell'URL

Quando si apre un report nel servizio Power BI, ogni pagina del report ha un proprio URL univoco. Per filtrare tale pagina del report, è possibile usare il riquadro Filtri nell'area di disegno report.  In alternativa, è possibile aggiungere i parametri della stringa di query all'URL per prefiltrare il report. Se, ad esempio, si vuole mostrare un report ai colleghi applicando un filtro preliminare, basta iniziare dall'URL predefinito del report, aggiungere i parametri di filtro all'URL e quindi inviare l'intero nuovo URL tramite posta elettronica.

![Report di Power BI nel servizio](media/service-url-filters/power-bi-report2.png)

## <a name="uses-for-query-string-parameters"></a>Usi dei parametri della stringa di query

Si supponga di usare Power BI Desktop. Si vuole creare un report che include collegamenti ad altri report di Power BI, ma è necessario visualizzare solo alcune delle informazioni negli altri report. In primo luogo, filtrare i report usando i parametri della stringa di query e salvare gli URL. Successivamente, creare una tabella in Power BI Desktop con questi nuovi URL di report.  Quindi, pubblicare e condividere il report.

I parametri della stringa di query possono essere anche utili per la creazione di una soluzione avanzata di Power BI.  Con DAX è possibile creare un report che genera un URL del report filtrato in modo dinamico in base alla selezione effettuata dal cliente nel report corrente. Quando i clienti selezionano l'URL, vedono solo le informazioni desiderate. 

## <a name="query-string-parameter-syntax-for-filtering"></a>Sintassi dei parametri della stringa di query per i filtri

Con i parametri, è possibile filtrare il report per uno o più valori, anche se tali valori contengono spazi o caratteri speciali. La sintassi di base è molto semplice: iniziare con l'URL del report, aggiungere un punto interrogativo e quindi aggiungere la sintassi del filtro.

*URL*?filter=*Tabella*/*Campo* eq '*valore*'

![URL con filtro](media/service-url-filters/power-bi-filter-urls7b.png)

* Per i nomi **Tabella** e **Campo** viene fatta distinzione tra maiuscole e minuscole, mentre per **valore** la distinzione non è rilevante.
* I campi che sono nascosti dalla visualizzazione Report possono comunque essere filtrati.

### <a name="reports-in-apps"></a>Report nelle app

Se si vuole aggiungere un filtro URL a un report in un'app, la formattazione è leggermente diversa. I collegamenti ai report in un'app hanno un parametro di query (ctid) che viene aggiunto all'URL. Separare i parametri di query con una e commerciale (&). Mantenere "?filter=" e spostare il parametro ctid alla fine dell'URL, preceduto da una e commerciale (&). 

Come in questo esempio:

app.powerbi.com/groups/me/apps/*app-id*/reports/*report-id*/ReportSection?filter=*Table*/*Field* eq '*value*'&ctid=*ctid*

### <a name="field-types"></a>Tipi di campo

Il tipo del campo può essere numerico, datetime o stringa e il tipo usato deve corrispondere al tipo impostato nel set di dati.  Ad esempio, la specifica del tipo "string" per una colonna di tabella non funziona se si sta cercando un valore datetime o numerico in un set di colonne del set di dati impostato come data, ad esempio, Table/StringColumn eq 1.

* Le **stringhe** devono essere racchiuse tra virgolette singole, ad esempio 'nome manager'.
* Per i **numeri** non è richiesta alcuna formattazione speciale. Per informazioni dettagliate, vedere [Tipi di dati numerici](#numeric-data-types) in questo articolo.
* Per le **date e ore** vedere [Tipi di dati di data](#date-data-types) in questo articolo. 

Se è ancora poco chiaro, continuare la lettura per un'analisi approfondita.  

## <a name="filter-on-a-field"></a>Filtrare in base a un campo

Si supponga che l'URL per il report sia il seguente.

![URL iniziale](media/service-url-filters/power-bi-filter-urls6.png)

Nella visualizzazione della mappa (sopra) sono visibili i negozi presenti nella Carolina del Nord.

>[!NOTE]
>Questo esempio si basa sull'[Esempio di analisi delle vendite al dettaglio](../create-reports/sample-datasets.md).
> 

Per filtrare il report in modo da visualizzare solo i dati relativi ai negozi in "NC" (Carolina del Nord), aggiungere all'URL quanto segue:

?filter=Store/Territory eq 'NC'

![URL con filtro](media/service-url-filters/power-bi-filter-urls7.png)

>[!NOTE]
>*NC* è un valore memorizzato nel campo **Territory** (Territorio) della tabella **Store** (Negozio).
> 

Il report viene filtrato in base alla Carolina del Nord; tutte le visualizzazioni nella pagina del report mostrano solo i dati relativi alla Carolina del Nord.

![Report filtrato per la Carolina del Nord](media/service-url-filters/power-bi-report4.png)

## <a name="filter-on-more-than-one-value-in-a-field"></a>Filtrare in base a più di un valore in un campo

Per applicare un filtro in base a più di un valore in un singolo campo, usare l'operatore **in** anziché l'operatore **and**. La sintassi è:

*URL*?filter=*Tabella*/*Campo* **in** ('*valore1*', '*valore2*')

Usando lo stesso esempio, per filtrare il report in modo da visualizzare solo i dati relativi ai negozi in "NC" (Carolina del Nord) o "TN" (Tennessee), aggiungere all'URL quanto segue:

?filter=Store/Territory in ('NC', 'TN')

Vedere la tabella [Operatori](#operators) più avanti nell'articolo per un elenco di altri operatori utili.

## <a name="filter-on-multiple-fields"></a>Filtrare in base a più campi

È possibile anche filtrare in base a più campi aggiungendo parametri aggiuntivi all'URL. Tornare al parametro filtro originale.

```
?filter=Store/Territory eq 'NC'
```

Per filtrare in base a campi aggiuntivi, aggiungere un operatore "**and**" e un altro campo nello stesso formato indicato in precedenza. Ecco un esempio.

```
?filter=Store/Territory eq 'NC' and Store/Chain eq 'Fashions Direct'
```

## <a name="operators"></a>Operatori

Power BI supporta molti operatori oltre a "**and**". La tabella seguente elenca tali operatori insieme al tipo di contenuto supportato.

|Operatore  | Definizione | Stringa  | d'acquisto | Data |  Esempio|
|---------|---------|---------|---------|---------|---------|
|**and**     | e |  sì      | sì |  sì|  prodotto/prezzo le 200 and prezzo gt 3.5 |
|**eq**     | equals |  sì      | sì   |  sì       | Indirizzo/Città eq 'Milano' |
|**ne**     | diverso da |   sì      | sì  | sì        |  Indirizzo/Città ne 'Londra' |
|**ge**     |  maggiore o uguale a       | no | sì |sì |  prodotto/prezzo ge 10
|**gt**     | maggiore di        |no | sì | sì  | prodotto/prezzo gt 20
|**le**     |   minore o uguale a      | no | sì | sì  | prodotto/prezzo le 100
|**lt**     |  minore di       | no | sì | sì |  prodotto/prezzo lt 20
|**in\*\***     |  incluso       | sì | sì |  sì | Studente/Età in (27, 29)


\*\* Quando si usa **in** i valori a destra di **in** possono essere un elenco delimitato da virgole racchiuso tra parentesi o una singola espressione che restituisce una raccolta.

### <a name="numeric-data-types"></a>Tipi di dati numerici

Un filtro URL di Power BI può includere numeri nei formati seguenti.

|Tipo di numero  |Esempio  |
|---------|---------|
|**integer**     |   5      |
|**long**     |   5 L o 5 l      |
|**double**     |   5,5 o 55e-1 o 0,55e+1 o 5D o 5d o 0,5e1D o 0,5e1d o 5,5D o 5,5d o 55e-1D o 55e-1d     |
|**decimal**     |   5 M o 5 m o 5,5 M o 5,5 m      |
|**float**     | 5 F o 5 f o 0,5e1 F o 0,5e-1 d        |

### <a name="date-data-types"></a>Tipi di dati di data

Power BI supporta OData V3 e V4 per i tipi di dati **Date** e **DateTimeOffset**. Per OData V3, le date devono essere racchiuse tra virgolette singole e precedute dalla parola datetime. In OData V4 non è necessario usare le virgolette singole e la parola datetime. 
  
Le date vengono rappresentate usando il formato EDM (2019-02-12T00:00:00). Quando si specifica una data nel formato 'AAAA-MM-GG', Power BI la interpreta come 'AAAA-MM-GGT00:00:00'. Il mese e il giorno devono essere composti da due cifre, MM e GG.

Perché è importante questa distinzione? Si supponga di creare un parametro di stringa di query **Table/Date gt '2018-08-03'** .  I risultati includeranno il 3 agosto 2018 oppure partiranno dal 4 agosto 2018? Power BI converte la query in **Table/Date gt '2018-08-03T00:00:00'** . I risultati includono pertanto tutte le date con una parte dell'ora diversa da zero, perché tali date saranno posteriori a **"2018-08-03T00:00:00"** .

Esistono altre differenze tra V3 e V4. OData v3 non supporta data, solo data e ora. Se quindi si usa il formato V3, è necessario qualificarlo con la data e l'ora complete. I valori letterali di data come "datetime'2019-05-20'"non sono supportati nella notazione V3. È tuttavia possibile scrivere semplicemente "2019-05-20" nella notazione V4. Ecco due query di filtro equivalenti in V3 e V4:

- Formato OData V4: filter=Table/Date gt 2019-05-20
- Formato OData V3: filter=Table/Date gt datetime'2019-05-20T00:00:00'


## <a name="special-characters-in-url-filters"></a>Caratteri speciali nei filtri di URL

### <a name="special-characters-in-table-and-column-names"></a>Caratteri speciali nei nomi di tabelle e colonne

I caratteri speciali e gli spazi nei nomi di tabella e colonna richiedono alcuni elementi di formattazione aggiuntivi. Quando la query contiene spazi, trattini o altri caratteri non ASCII, anteporre a questi caratteri speciali un *codice di escape* costituito da un carattere di sottolineatura e da una X ( **_x**), seguiti dal codice **Unicode** di quattro cifre e da un altro carattere di sottolineatura. Se il codice Unicode è composto da meno di quattro caratteri, è necessario aggiungere zeri. Di seguito sono riportati alcuni esempi.

|Identificatore  |Unicode  | Codice per Power BI  |
|---------|---------|---------|
|**Nome tabella**     | Lo spazio è 0x20        |  Nome_x0020_tabella       |
|**Colonna**@**Numero**     |   @ è 0x40     |  Colonna_x0040_Numero       |
|**[Colonna]**     |  [ è 0x005B ] è 0x005D       |  _x005B_Column_x005D_       |
|**Colonna+Più**     | + è 0x2B        |  Colonna_x002B_Più       |

Tabella_x0020_Nome/Colonna_x002B_Più eq 3 ![oggetto visivo tabella che mostra caratteri speciali](media/service-url-filters/power-bi-special-characters1.png)


Tabella_x0020_Speciale/_x005B_Colonna_x0020_ParentesiQuadre_x005D_ eq '[C]' ![oggetto visivo tabella che mostra caratteri speciali](media/service-url-filters/power-bi-special-characters2.png)

### <a name="special-characters-in-values"></a>Caratteri speciali nei valori

I filtri URL supportano già tutti i caratteri speciali nei valori dei campi, ad eccezione della virgoletta singola ('). Questo è l'unico carattere di cui è necessario eseguire l'escape. Per cercare un carattere virgoletta singola, usare due virgolette singole (''). 

Ad esempio:

- `?filter=Table/Name eq 'O''Brien'` diventa: 

    :::image type="content" source="media/service-url-filters/power-bi-url-filter-obrien.png" alt-text="Name is O'Brien":::

- `?filter=Table/Name eq 'Lee''s Summit'` diventa:

    :::image type="content" source="media/service-url-filters/power-bi-url-filter-lees.png" alt-text="Lee's Summit":::

- Anche l'operatore `in` supporta questa modalità di escape: `?filter=Table/Name in ('Lee''s Summit', 'O''Brien')` diventa:

    :::image type="content" source="media/service-url-filters/power-bi-url-filter-in.png" alt-text="Lee's Summit or O'Brien":::

## <a name="use-dax-to-filter-on-multiple-values"></a>Usare DAX per filtrare in base a più valori

Un altro modo per filtrare in base a più campi consiste nel creare una colonna calcolata che concateni due campi in un unico valore. quindi filtrare in base a tale valore.

Ad esempio, ci sono due campi: Territory e Chain. In Power BI Desktop [creare una nuova colonna calcolata](../transform-model/desktop-tutorial-create-calculated-columns.md) (Campo) denominata TerritoryChain. Tenere presente che il nome **Campo** non può contenere spazi. Ecco la formula DAX per tale colonna.

TerritoryChain = [Territory] & " - " & [Chain]

Pubblicare il report nel servizio Power BI, quindi usare la stringa di query dell'URL per filtrare e visualizzare solo i dati relativi ai negozi Lindseys nella Carolina del Nord.

    https://app.powerbi.com/groups/me/reports/8d6e300b-696f-498e-b611-41ae03366851/ReportSection3?filter=Store/TerritoryChain eq 'NC – Lindseys'

## <a name="pin-a-tile-from-a-filtered-report"></a>Aggiungere un riquadro da un report filtrato

Dopo aver filtrato il report usando i parametri della stringa di query, è possibile aggiungere al dashboard le visualizzazioni da tale report.  Il riquadro nel dashboard contiene i dati filtrati; selezionandolo, viene aperto il report usato per crearlo.  Tuttavia, i filtri applicati usando l'URL non vengono salvati con il report. Quando si seleziona il riquadro del dashboard, il report viene aperto nello stato non filtrato.  I dati visualizzati nel riquadro del dashboard non corrispondono quindi ai dati presenti nella visualizzazione del report.

Questa discrepanza è utile quando si vogliono visualizzare risultati diversi, filtrati nel dashboard e non filtrati nel report.

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi

Ci sono un paio di aspetti da tenere presenti quando si usano i parametri della stringa di query.

* Quando si usa l'operatore *in*, i valori a destra di *in* devono essere un elenco delimitato da virgole racchiuso tra parentesi.    
* Server di report di Power BI supporta anche la possibilità di specificare filtri aggiuntivi tramite il parametro URL "filter". Di seguito è riportato un esempio di come potrebbe apparire l'URL in Server di report di Power BI: `https://reportserver/reports/powerbi/Store Sales?rs:Embed=true&filter= Store/Territory eq 'NC' and Store/Chain eq 'Fashions Direct'`
* I filtri URL dei report hanno un limite di 10 espressioni (10 filtri connessi tramite AND).
* Il tipo di dati long è (2^53-1) a causa di limitazioni di JavaScript.

I filtri URL sono supportati in alcuni scenari di incorporamento e non in altri.

- È supportato l'[incorporamento di un report in un portale o un sito Web sicuro](service-embed-secure.md).
- I filtri URL sono supportati in Power BI Embedded. Per informazioni dettagliate, vedere [Funzionalità avanzate per filtri URL in Power BI Embedded](https://azure.microsoft.com/updates/power-bi-embedded-advanced-url-filtering-capabilities).
- Il filtro della stringa di query non funziona con l'opzione [Pubblica sul Web](service-publish-to-web.md) o [Esporta in PDF](../consumer/end-user-pdf.md).
- La funzione descritta in [Incorporare con web part report in SharePoint Online](service-embed-report-spo.md) non supporta i filtri URL.
- Teams non consente di specificare un URL.

## <a name="next-steps"></a>Passaggi successivi

[Aggiungere una visualizzazione a un dashboard](../create-reports/service-dashboard-pin-tile-from-report.md)  
[Iscriversi per una versione di valutazione gratuita](https://powerbi.microsoft.com/get-started/)

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)



