---
title: Informazioni sul mapping di viste dati in oggetti visivi di Power BI
description: Questo articolo descrive il modo in cui Power BI trasforma i dati prima di passarli negli oggetti visivi.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: ad63a1b97c744e8614e584874c4d896a85598e48
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2020
ms.locfileid: "76819124"
---
# <a name="add-the-locale-in-power-bi-for-custom-visuals"></a>Aggiungere le impostazioni locali in Power BI per gli oggetti visivi personalizzati

Gli oggetti visivi possono recuperare le impostazioni locali di Power BI per localizzare il contenuto nella lingua pertinente.

Per altre informazioni, vedere [Lingue e paesi/aree geografiche supportate per Power BI](./../../supported-languages-countries-regions.md)

È ad esempio possibile recuperare le impostazioni locali nell'oggetto visivo grafico a barre di esempio.

![Localizzazione in un oggetto visivo grafico a barre di esempio](media/locale-in-samplebarchart.png)

Ognuno di questi grafici a barre è stato creato con impostazioni locali diverse (inglese, basco e hindi), visualizzate nella descrizione comando.

> [!NOTE]
> La gestione della localizzazione nel codice dell'oggetto visivo è supportata a partire dall'API 1.10.0.

## <a name="get-the-locale"></a>Ottenere le impostazioni locali

L'elemento `locale` viene passato come stringa durante l'inizializzazione dell'oggetto visivo. Se le impostazioni locali vengono modificate in Power BI, l'oggetto visivo verrà generato nuovamente con le nuove impostazioni locali. Il codice di esempio completo è disponibile in SampleBarChart con le impostazioni locali

Il costruttore BarChart include ora un membro per le impostazioni locali, di cui viene creata un'istanza nel costruttore con l'istanza delle impostazioni locali host.

```typescript
private locale: string;
...
this.locale = options.host.locale;
```

Impostazioni locali supportate:

Stringa delle impostazioni locali | Lingua
--------------|----------------------
ar-SA | العربية (arabo)
bg-BG | български (bulgaro)
ca-ES | català (catalano)
cs-CZ | čeština (ceco)
da-DK | dansk (danese)
de-DE | Deutsche (tedesco)
el-GR | ελληνικά (greco)
en-US | English (inglese)
es-ES | español (spagnolo)
et-EE | eesti (estone)
eU-ES | Euskal (basco)
fi-FI | suomi (finlandese)
fr-FR | français (francese)
gl-ES | galego (galiziano)
he-IL | עברית (ebraico)
hi-IN | हिन्दी (hindi)
hr-HR | hrvatski (croato)
hu-HU | magyar (ungherese)
id-ID | Bahasa Indonesia (indonesiano)
it-IT | italiano (italiano)
ja-JP | 日本の (giapponese)
kk-KZ | Қазақ (kazako)
ko-KR | 한국의 (coreano)
lt-LT | Lietuvos (lituano)
lv-LV | Latvijas (lettone)
ms-MY | Bahasa Melayu (malese)
nb-NO | norsk (norvegese)
nl-NL | Nederlands (olandese)
pl-PL | polski (polacco)
pt-BR | português (portoghese)
pt-PT | português (portoghese)
ro-RO | românesc (rumeno)
ru-RU | русский (russo)
sk-SK | slovenský (slovacco)
sl-SI | slovenski (sloveno)
sr-Cyrl-RS | српски (serbo)
sr-Latn-RS | srpski (serbo)
sv-SE | svenska (svedese)
th-TH | ไทย (thai)
tr-TR | Türk (turco)
uk-UA | український (ucraino)
vi-VN | tiếng Việt (vietnamita)
zh-CN | 中国 (cinese semplificato)
zh-TW | 中國 (cinese tradizionale)

> [!NOTE]
> In Power BI Desktop la proprietà locale conterrà la lingua della versione di Power BI Desktop installata.

## <a name="localizing-the-property-pane-for-custom-visuals"></a>Localizzazione del riquadro delle proprietà per gli oggetti visivi personalizzati

È possibile localizzare i campi nel riquadro delle proprietà per offrire un'esperienza più integrata e coerente, in cui gli oggetti visivi personalizzati si comportano come qualsiasi altro oggetto visivo di base di Power BI.

Ad esempio, un oggetto visivo personalizzato non localizzato creato usando il comando `pbiviz new` mostrerà i campi seguenti nel riquadro delle proprietà:

![Localizzazione nel riquadro delle proprietà](media/property-pane.png)

Sia Category Data che Measure Data sono definiti nel file capabilities.json come `displayName`.

## <a name="how-to-localize-capabilities"></a>Come localizzare le funzionalità

Prima di tutto aggiungere una chiave a ogni nome visualizzato che si vuole localizzare nelle funzionalità. In questo esempio:

```json
{
    "dataRoles": [
        {
            "displayName": "Category Data",
            "displayNameKey": "VisualCategoryDataNameKey1",
            "name": "category",
            "kind": "Grouping"
        },
        {
            "displayName": "Measure Data",
            "displayNameKey": "VisualMeasureDataNameKey2",
            "name": "measure",
            "kind": "Measure"
        }
    ]
}
```

Aggiungere quindi una directory chiamata stringResources. La directory conterrà tutti i diversi file di risorse stringa in base alle impostazioni locali che l'oggetto visivo deve supportare. Sotto questa directory sarà necessario aggiungere un file JSON per ognuna delle impostazioni locali che si vuole supportare. Tali file contengono le informazioni sulle impostazioni locali e i valori delle stringhe localizzate per ogni displayNameKey che si vuole sostituire.

Si supponga, ad esempio, di dover supportare l'arabo e l'ebraico. Sarà necessario aggiungere due file JSON nel modo seguente:

![Stringhe per le localizzazioni nella cartella delle risorse stringa](media/stringresources-files.png)

Ogni file JSON definisce una singola impostazione locale (questo file deve essere una delle impostazioni locali supportate elencate sopra), con i valori delle stringhe per le chiavi dei nomi visualizzati desiderate. Nell'esempio il file di risorse stringa per l'ebraico sarà simile al seguente:

```json
{
    "locale": "he-IL",
    "values": {
        "VisualCategoryDataNameKey1": "קטגוריה",
        "VisualMeasureDataNameKey2": "יחידות מידה"
    }
}
```

Tutti i passaggi necessari per usare l'utilità di gestione della localizzazione sono descritti sotto.

> [!NOTE]
> La localizzazione non è attualmente supportata per il debug dell'oggetto visivo di sviluppo

## <a name="setup-environment"></a>Configurare l'ambiente

### <a name="desktop"></a>Desktop

Per l'utilizzo del desktop, scaricare la versione localizzata di Power BI Desktop da https://powerbi.microsoft.com.

### <a name="web-service"></a>Servizio Web

Se si usa il client Web (browser) nel servizio, cambiare la lingua nelle impostazioni:

![Localizzazione nel servizio Web](media/webservice-settings.png)

## <a name="resource-file"></a>File di risorse

All'interno della cartella stringResources aggiungere un file resources.resjson a una cartella con il nome corrispondente alle impostazioni locali da usare. Nell'esempio si tratta delle cartelle en-US e ru-RU.

![Nuovo file con estensione resjson](media/new-resjson.png)

Nel file resources.resjson aggiunto nel passaggio precedente aggiungere tutte le stringhe di localizzazione da usare.

```json
{
    ...
    "Role_Legend": "Обозначения",
    "Role_task": "Задача",
    "Role_StartDate": "Дата начала",
    "Role_Duration": "Длительность"
    ...
}
```

Questo esempio corrisponde alla versione en-US del file resources.resjson:

```json
{
    ...
    "Role_Legend": "Legend",
    "Role_task": "Task",
    "Role_StartDate": "Start date",
    "Role_Duration": "Duration"
    ...
}
```

Creare una nuova istanza di localizationManager nel codice dell'oggetto visivo, come segue

```typescript
private localizationManager: ILocalizationManager;

constructor(options: VisualConstructorOptions) {
    this.localizationManager = options.host.createLocalizationManager();
}
```

## <a name="localizationmanager-usage-sample"></a>Esempio di utilizzo di localizationManager

È ora possibile chiamare la funzione getDisplayName dell'utilità di gestione della localizzazione con l'argomento della chiave della stringa definito in resources.resjson per ottenere la stringa necessaria in qualsiasi punto del codice:

```typescript
let legend: string = this.localization.getDisplayName("Role_Legend");
```

Restituisce "Legend" per en-US e "Обозначения" per ru-RU

## <a name="next-steps"></a>Passaggi successivi

* [Informazioni su come usare le utilità per la formattazione per fornire i formati localizzati](utils-formatting.md)
