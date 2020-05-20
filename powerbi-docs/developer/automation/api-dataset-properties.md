---
title: Proprietà dei set di dati di Power BI
description: Informazioni sulle proprietà delle API dei set di dati di Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 7dad7071fbf887c36443cacdb9be83d83e0b89be
ms.sourcegitcommit: a72567f26c1653c25f7730fab6210cd011343707
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2020
ms.locfileid: "83561502"
---
# <a name="dataset-properties"></a>Proprietà dei set di dati

La versione 1 corrente dell'API dei set di dati consente la creazione di un solo set di dati con un nome e una raccolta di tabelle. Ogni tabella può avere un nome e una raccolta di colonne. Ogni colonna ha un nome e un tipo di dati. Queste proprietà vengono notevolmente estese, in particolare con il supporto per le misure e le relazioni tra tabelle. L'elenco completo delle proprietà supportate per questa versione è il seguente:

> [!IMPORTANT]
> È possibile accedervi dalla pagina [Datasets Operation Groups](https://docs.microsoft.com/rest/api/power-bi/datasets) (Gruppi di operazioni di set di dati).

## <a name="dataset"></a>Set di dati

Name  |Type  |Description  |Sola lettura  |Obbligatorio
---------|---------|---------|---------|---------
ID     |  Guid       | Identificatore univoco a livello di sistema per il set di dati.        | True        | False        
name     | String        | Nome del set di dati definito dall'utente.        | False        | True        
tables     | Table[]        | Raccolta di tabelle.        |  False       | False        
relationships     | Relationship[]        | Raccolta di relazioni tra tabelle.        | False        |  False  
defaultMode     | String        | Determina se il set di dati è sottoposto a push, trasmesso in streaming o entrambi, con valori di "Push" e "Streaming".         | False        |  False

## <a name="table"></a>Table

Name  |Type  |Description  |Sola lettura  |Obbligatorio
---------|---------|---------|---------|---------
name     | String        |  Nome della tabella definito dall'utente. Viene inoltre usato come identificatore della tabella.       | False        |  True       
columns     |  column[]       |  Raccolta di colonne.       | False        |  True       
measures     | measure[]        |  Raccolta di misure.       | False        |  False       
isHidden     | Boolean        | Se true, la tabella verrà nascosta dagli strumenti client.        | False        | False        

## <a name="column"></a>colonna

Name  |Type  |Description  |Sola lettura  |Obbligatorio
---------|---------|---------|---------|---------
name     |  String        | Nome della colonna definito dall'utente.        |  False       | True       
dataType     |  String       |  [Tipi di dati EDM](/dotnet/framework/data/adonet/entity-data-model-primitive-data-types) e restrizioni supportati. Vedere [Restrizioni del tipo di dati](#data-type-restrictions).      |  False       | True        
formatString     | String        | Stringa che descrive come deve essere formattato il valore quando viene visualizzato. Per altre informazioni sulla formattazione delle stringhe, vedere [Contenuto di FORMAT_STRING](/analysis-services/multidimensional-models/mdx/mdx-cell-properties-format-string-contents).      | False        | False        
sortByColumn    | String        |   Nome stringa di una colonna nella stessa tabella da usare per ordinare la colonna corrente.     | False        | False       
dataCategory     | String        |  Valore stringa da usare per la categoria di dati che descrive i dati all'interno della colonna. Alcuni valori comuni includono: Address, City, Continent, Country, Image, ImageUrl, Latitude, Longitude, Organization, Place, PostalCode, StateOrProvince, WebUrl       |  False       | False        
isHidden    |  Boolean       |  Proprietà che indica se la visualizzazione della colonna è nascosta. L'impostazione predefinita è false.       | False        | False        
summarizeBy     | String        |  Metodo di aggregazione predefinito per la colonna. I valori includono: default, none, sum, min, max, count, average, distinctCount     |  False       | False

## <a name="measure"></a>Misura

Name  |Type  |Description  |Sola lettura  |Obbligatorio
---------|---------|---------|---------|---------
name     | String        |  Nome della misura definito dall'utente.       |  False       | True        
expression     | String        | Espressione DAX valida.        | False        |  True       
formatString     | String        |  Stringa che descrive come deve essere formattato il valore quando viene visualizzato. Per altre informazioni sulla formattazione delle stringhe, vedere [Contenuto di FORMAT_STRING](/analysis-services/multidimensional-models/mdx/mdx-cell-properties-format-string-contents).       | False        | False        
isHidden     | String        |  Se true, la tabella verrà nascosta dagli strumenti client.       |  False       | False       

## <a name="relationship"></a>Relazione

Name  |Type  |Description  |Sola lettura  |Obbligatorio 
---------|---------|---------|---------|---------
name     | String        | Nome della relazione definito dall'utente. Viene inoltre usato come identificatore della relazione.        | False       | True        
crossFilteringBehavior     | String        |    Direzione del filtro della relazione: OneDirection (impostazione predefinita), BothDirections, Automatic       | False        | False        
fromTable     | String        | Nome della tabella di chiave esterna.        | False        | True         
fromColumn    | String        | Nome della colonna di chiave esterna.        | False        | True         
toTable    | String        | Nome della tabella di chiave primaria.        | False        | True         
toColumn     | String        | Nome della colonna di chiave primaria.        | False        | True        

## <a name="data-type-restrictions"></a>Restrizioni del tipo di dati

Queste restrizioni si applicano alla proprietà dataType.

Tipo di dati  |Restrizioni  
---------|---------
Int64     |   Int64.MaxValue e Int64.MinValue non sono consentiti.      
Double     |  Double.MaxValue e Double.MinValue non sono consentiti. NaN non supportato. +Infinity e -Infinity non supportati in alcune funzioni, ad esempio Min, Max.       
Boolean     |   True o False.
DateTime    |   Durante il caricamento dei dati, i valori vengono quantizzati con frazioni giornaliere fino a multipli interi di 1/300 secondi (3,33 ms).      
String     |  Attualmente consente fino a 4000 caratteri per valore di stringa.
Decimal|precisione=28, scalabilità=4

## <a name="example"></a>Esempio
L'esempio di codice seguente include alcune di queste proprietà:

```json
{

  "name": "PushAdvanced",

  "tables": [

    {

      "name": "Date",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        }

      ]

    },

    {

      "name": "sales",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "Sales",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ],

      "measures": [

        {

          "name": "percent to forecast",

          "expression": "SUM(sales[Sales])/SUM(forecast[forecast])",

          "formatString": "0.00 %;-0.00 %;0.00 %"

        }

      ]

    },

    {

      "name": "forecast",

      "columns": [

        {

          "name": "date",

          "dataType": "dateTime",

          "formatString": "m/d/yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "forecast",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ]

    }

  ],

  "relationships": [

    {

      "name": "2ea345ce-b147-436e-8ac2-9d3c4d82af8d",

      "fromTable": "sales",

      "fromColumn": "Date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    },

    {

      "name": "5d95f419-e589-4345-9581-6e70670b1bba",

      "fromTable": "forecast",

      "fromColumn": "date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    }

  ]

}
```