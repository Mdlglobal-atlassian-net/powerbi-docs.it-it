---
title: Eseguire il push dei dati in un set di dati
description: Eseguire il push dei dati in un set di dati di Power BI
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 05/22/2019
ms.openlocfilehash: 9eb81610044f795b6f9dc5c58aeefad13de06542
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222148"
---
# <a name="push-data-into-a-power-bi-dataset"></a>Eseguire il push dei dati in un set di dati di Power BI

L'API Power BI consente di eseguire il push dei dati in un set di dati di Power BI. In questo articolo viene illustrato come eseguire il push di un set di dati Sales Marketing che contiene una tabella Product in un set di dati.

Prima di iniziare, è necessario un Azure Active Directory (Azure AD) e un [account di Power BI](create-an-azure-active-directory-tenant.md).

## <a name="steps-to-push-data-into-a-dataset"></a>Procedura per eseguire il push dei dati in un set di dati

* Passaggio 1: [Registrare un'app in Azure AD](walkthrough-push-data-register-app-with-azure-ad.md)
* Passaggio 2: [Ottenere un token di accesso per l'autenticazione](walkthrough-push-data-get-token.md)
* Passaggio 3: [Creare un set di dati in Power BI](walkthrough-push-data-create-dataset.md)
* Passaggio 4: [Ottenere un set di dati per aggiungere righe in una tabella di Power BI](walkthrough-push-data-get-datasets.md)
* Passaggio 5: [Aggiungere righe a una tabella di Power BI](walkthrough-push-data-add-rows.md)

La sezione successiva fornisce una descrizione generale delle operazioni dell'API di Power BI che seguono il push dei dati.

## <a name="power-bi-api-operations-to-push-data"></a>Operazioni dell'API di Power BI per eseguire il push dei dati

Con l'API REST di Power BI è possibile eseguire il push di origini dati in Power BI. Quando un'app aggiunge righe a un set di dati, l'aggiornamento automaticamente con i nuovi dati riquadri del dashboard. Per eseguire il push dei dati, usare il [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdataset) e [PostRows](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postrows) operazioni. Per trovare un set di dati, usare il [Get Datasets](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets) operazione. È possibile passare un ID di gruppo per lavorare con un gruppo per queste operazioni. Per ottenere un elenco di ID di gruppo, usare il [Get Groups](https://docs.microsoft.com/rest/api/power-bi/groups/getgroups) operazione.

Ecco le operazioni per eseguire il push dei dati in un set di dati:

* [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdataset)
* [Recupera set di dati](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets)
* [PostRows](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postrows)
* [Recupera gruppi](https://docs.microsoft.com/rest/api/power-bi/groups/getgroups)

Viene creato un set di dati in Power BI passando una stringa JSON (JavaScript Object Notation) al servizio Power BI. Per altre informazioni su JSON, vedere l'[introduzione a JSON](http://json.org/).

La stringa JSON per un set di dati ha il formato seguente:

**Oggetto JSON del set di dati di Power BI**

    {"name": "dataset_name", "tables":
        [{"name": "", "columns":
            [{ "name": "column_name1", "dataType": "data_type"},
             { "name": "column_name2", "dataType": "data_type"},
             { ... }
            ]
          }
        ]
    }

Per questo esempio di set di dati Sales Marketing, si passa una stringa JSON come illustrato di seguito. In questo esempio **SalesMarketing** è il nome del set di dati e **prodotto** è il nome della tabella. Dopo aver definito la tabella, definire lo schema di tabella. Lo schema di tabella del set di dati **SalesMarketing** contiene queste colonne: ProductID, Manufacturer, Category, Segment, Product e IsCompete.

**Esempio JSON per l'oggetto set di dati**

    {
        "name": "SalesMarketing",
        "tables": [
            {
                "name": "Product",
                "columns": [
                {
                    "name": "ProductID",
                    "dataType": "int"
                },
                {
                    "name": "Manufacturer",
                    "dataType": "string"
                },
                {
                    "name": "Category",
                    "dataType": "string"
                },
                {
                    "name": "Segment",
                    "dataType": "string"
                },
                {
                    "name": "Product",
                    "dataType": "string"
                },
                {
                    "name": "IsCompete",
                    "dataType": "bool"
                }
                ]
            }
        ]
    }

Per uno schema di tabella di Power BI, è possibile usare i tipi di dati seguenti.

## <a name="power-bi-table-data-types"></a>Tipi di dati per una tabella di Power BI

| **Tipo di dati** | **Restrizioni** |
| --- | --- |
| Int64 |Int64.MaxValue e Int64.MinValue non sono consentiti. |
| Double |Double.MaxValue e Double.MinValue non sono consentiti. NaN non supportato. + Infinity e - Infinity non supportati in alcune funzioni (ad esempio, Min, Max). |
| Boolean |Nessuno |
| DateTime |Durante il caricamento dei dati, vengono quantizzati con frazioni giornaliere fino a multipli interi di 1/300 secondi (3,33 ms) i valori. |
| Stringa |Attualmente consente fino a 128 caratteri. |

## <a name="learn-more-about-pushing-data-into-power-bi"></a>Altre informazioni sul push dei dati in Power BI

Per iniziare il push dei dati in un set di dati, vedere [Passaggio 1: Registrare un'app in Azure AD](walkthrough-push-data-register-app-with-azure-ad.md) nel riquadro di spostamento a sinistra.

[Passaggio successivo >](walkthrough-push-data-register-app-with-azure-ad.md)

## <a name="next-steps"></a>Passaggi successivi

[Iscriversi a Power BI](create-an-azure-active-directory-tenant.md)  
[Introduzione a JSON](http://json.org/)  
[Panoramica dell'API REST di Power BI](overview-of-power-bi-rest-api.md)  
Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)