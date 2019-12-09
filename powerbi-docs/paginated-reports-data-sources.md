---
title: Origini dati supportate per i report impaginati di Power BI
description: In questo articolo sono descritte le origini dati supportate per i report impaginati del servizio Power BI ed è illustrato come connettersi alle origini dati del database SQL di Azure.
author: onegoodsausage
ms.author: andremi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 12/03/2019
ms.openlocfilehash: f7662cbd2fb0085ad2e6fda6a33577d1cc29ddfb
ms.sourcegitcommit: e492895259aa39960063f9b337a144a60c20125a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74831284"
---
# <a name="supported-data-sources-for-power-bi-paginated-reports"></a>Origini dati supportate per i report impaginati di Power BI

In questo articolo sono elencate le origini dati supportate per i report impaginati del servizio Power BI ed è illustrato come connettersi alle origini dati del database SQL di Azure. Alcune origini dati sono supportate in modalità nativa. È possibile connettersi ad altre origini dati tramite gateway dati.

## <a name="natively-supported-data-sources"></a>Origini dati supportate in modalità nativa

I report impaginati supportano in modalità nativa l'elenco di origini dati seguente:

| Origine dati | Autenticazione | Note |
| --- | --- | --- |
| Database SQL di Azure <br>Azure SQL Data Warehouse | Di base, Single Sign-On (SSO), OAuth2 |   |
| Istanza gestita di SQL di Azure | Di base | tramite l'endpoint pubblico con l'estensione per il database SQL di Azure  |
| Azure Analysis Services | SSO, OAuth2 |   |
| Set di dati di Power BI | SSO | Set di dati di Power BI Premium e non Premium |
| Set di dati di Power BI Premium (XMLA) | SSO |   |
| Immetti i dati | N/D | I dati sono incorporati nel report. |

Ad eccezione del database SQL di Azure, tutte le origini dati sono pronte per l'uso dopo il caricamento del report nel servizio Power BI. Per impostazione predefinita, le origini dati usano Single Sign-on (SSO), dove applicabile. Per Azure Analysis Services, è possibile modificare il tipo di autenticazione in OAuth2.

Per le origini dati del database SQL di Azure, è necessario specificare altre informazioni, come descritto nella sezione [Autenticazione del database SQL di Azure](#azure-sql-database-authentication).

## <a name="other-data-sources"></a>Altre origini dati

Oltre alle origini dati supportate in modalità nativa, è possibile accedere alle origini dati seguenti tramite un [gateway dati di Power BI](service-gateway-onprem.md):

- SQL Server
- SQL Server Analysis Services
- Oracle
- Teradata

Per i report impaginati, il database SQL di Azure e Azure Analysis Services non sono attualmente accessibili tramite un gateway dati di Power BI.

## <a name="azure-sql-database-authentication"></a>Autenticazione del database SQL di Azure

Per le origini dati del database SQL di Azure, è necessario impostare un tipo di autenticazione prima di eseguire il report. Questa opzione si applica solo quando si usa un'origine dati per la prima volta in un'area di lavoro. La prima volta viene visualizzato il messaggio seguente:

![Pubblicazione in Power BI](media/paginated-reports-data-sources/power-bi-paginated-publishing.png)

Se non si specificano le credenziali, si verifica un errore durante l'esecuzione del report. Selezionare **Continua** per passare alla pagina **Credenziali dell'origine dati** del report appena caricato:

![Impostazioni per il database SQL di Azure](media/paginated-reports-data-sources/power-bi-paginated-settings-azure-sql.png)

Selezionare il collegamento **Modifica credenziali** per una determinata origine dati per visualizzare la finestra di dialogo **Configura**:

![Configurare il database SQL di Azure](media/paginated-reports-data-sources/power-bi-paginated-configure-azure-sql.png)

Per le origini dati del database SQL di Azure, sono supportati i tipi di autenticazione seguenti:

- Di base (nome utente e password)
- SSO (Single Sign-On)
- OAuth2 (token AAD archiviato)

Per il corretto funzionamento di SSO e OAuth2, il server del database SQL di Azure a cui è connessa l'origine dati deve avere [il supporto per l'autenticazione di AAD abilitato](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure). Per il metodo di autenticazione OAuth2, AAD genera un token e lo archivia per l'accesso futuro all'origine dati. Per usare invece [il metodo di autenticazione SSO](https://docs.microsoft.com/power-bi/service-azure-sql-database-with-direct-connect#single-sign-on), selezionare l'opzione SSO **Quando accedono a questa origine dati tramite DirectQuery, gli utenti finali usano le proprie credenziali OAuth2** visualizzata nella parte sottostante.
  
## <a name="next-steps"></a>Passaggi successivi

[Visualizzare un report impaginato nel servizio Power BI](consumer/paginated-reports-view-power-bi-service.md)

Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)
