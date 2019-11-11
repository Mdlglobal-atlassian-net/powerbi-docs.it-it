---
title: Sviluppare con le API REST per un server di report di Power BI
description: L'API REST offre l'accesso a livello di codice agli oggetti contenuti in un catalogo del server di report di Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/25/2018
ms.openlocfilehash: 9b8e795c4a55f9efd6fd534d92d95b36c93cf2c0
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73874067"
---
# <a name="develop-with-the-rest-apis-for-power-bi-report-server"></a>Sviluppare con le API REST per un server di report di Power BI

Il server di report di Power BI supporta le API REST (Representational State Transfer, Trasferimento di stato rappresentativo). Le API REST sono endpoint servizio che supportano un set di operazioni HTTP (metodi) che offrono l'accesso per le operazioni di creazione, recupero, aggiornamento o eliminazione per le risorse in un server di report.

L'API REST offre l'accesso a livello di codice agli oggetti contenuti in un catalogo del server di report di Power BI. Gli oggetti sono, ad esempio, cartelle, report, KPI, origini dati, set di dati, piani di aggiornamento, sottoscrizioni e altri ancora. Le API REST consentono di esplorare la gerarchia delle cartelle, individuare il contenuto di una cartella o di scaricare una definizione del report. È anche possibile creare, aggiornare ed eliminare gli oggetti. Le operazioni che si possono eseguire con gli oggetti sono ad esempio caricare un report, eseguire un piano di aggiornamento, eliminare una cartella e così via.

[!INCLUDE [GDPR-related guidance](../includes/gdpr-hybrid-note.md)]

## <a name="components-of-a-rest-api-requestresponse"></a>Componenti di una richiesta/risposta dell'API REST

Una coppia richiesta/risposta dell'API REST può essere suddivisa in cinque componenti:

* **URI della richiesta**, costituito da: `{URI-scheme} :// {URI-host} / {resource-path} ? {query-string}`. Sebbene l'URI della richiesta sia incluso nell'intestazione del messaggio di richiesta, viene evidenziato separatamente perché la maggior parte dei linguaggi o framework richiede di passarlo separatamente dal messaggio di richiesta.
  
  * Schema URI: indica il protocollo usato per trasmettere la richiesta. Ad esempio: `http` o `https`.
  * Host URI: specifica il nome di dominio o l'indirizzo IP del server in cui è ospitato l'endpoint di servizio REST, ad esempio `myserver.contoso.com`.
  * Percorso delle risorse: specifica la risorsa o la raccolta di risorse, che può includere più segmenti usati dal servizio per determinare la selezione di tali risorse. Ad esempio: è possibile usare `CatalogItems(01234567-89ab-cdef-0123-456789abcdef)/Properties` per recuperare le proprietà specificate per CatalogItem.
  * Stringa di query (facoltativa): offre parametri semplici aggiuntivi, ad esempio la versione API o i criteri di selezione delle risorse.
* Campi dell'intestazione del messaggio della richiesta HTTP:
  
  * [Metodo HTTP](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html) obbligatorio (noto anche come operazione o verbo) che comunica al servizio il tipo di operazione richiesta. Le API REST di Reporting Services supportano i metodi DELETE, GET, HEAD, PUT, POST e PATCH.
  * Campi dell'intestazione aggiuntivi facoltativi, come richiesto dal metodo HTTP e dall'URI specificati.
* Campi del **corpo del messaggio di richiesta** HTTP facoltativi, per supportare l'operazione HTTP e l'URI. Ad esempio, le operazioni POST contengono oggetti con codifica MIME passati come parametri complessi. Per le operazioni POST o PUT, è necessario specificare anche il tipo di codifica MIME per il corpo nell'intestazione della richiesta `Content-type`. Alcuni servizi richiedono di usare un tipo MIME specifico, come `application/json`.
* Campi dell'**intestazione del messaggio della risposta** HTTP:
  
  * [Codice di stato HTTP](https://www.w3.org/Protocols/HTTP/HTRESP.html), compreso tra 2xx per le operazioni riuscite e 4xx o 5xx per le operazioni con errori. In alternativa, può essere restituito un codice di stato definito dal servizio, come indicato nella documentazione dell'API.
  * Campi dell'intestazione aggiuntivi facoltativi, per il supporto della risposta della richiesta, ad esempio un'intestazione della risposta `Content-type`.
* Campi del **corpo del messaggio di risposta** HTTP facoltativi:
  
  * Gli oggetti della risposta con codifica MIME sono restituiti nel corpo della risposta HTTP, ad esempio una risposta da un metodo GET che restituisce dati. In genere questi oggetti vengono restituiti in un formato strutturato, come JSON o XML, come indicato dall'intestazione della risposta `Content-type`.

## <a name="api-documentation"></a>Documentazione dell'API

Un'API REST moderna richiede una documentazione API moderna. L'API REST è basata sulla specifica OpenAPI, ovvero la specifica Swagger, e la documentazione è disponibile in [SwaggerHub](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0). Oltre a fornire la documentazione per l'API, SwaggerHub consente di generare una libreria client nel linguaggio scelto, ad esempio JavaScript, TypeScript, C#, Java, Python, Ruby e altri ancora.

## <a name="testing-api-calls"></a>Test delle chiamate API

[Fiddler](https://www.telerik.com/fiddler) è uno strumento che permette di testare i messaggi di richiesta/risposta HTTP. Fiddler è un proxy di debug Web gratuito che intercetta le richieste REST semplificando così la diagnosi dei messaggi di richiesta/risposta HTTP.

## <a name="next-steps"></a>Passaggi successivi

Rivedere le API disponibili in [SwaggerHub](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0).

Gli esempi sono disponibili in [GitHub](https://github.com/Microsoft/Reporting-Services). L'esempio include un'app HTML5 basata su TypeScript, React e webpack, oltre a un esempio PowerShell.

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)