---
title: Always Encrypted in Server di report di Power BI
description: Questo articolo illustra il supporto di Always Encrypted in Server di report di Power BI quando si usano i tipi di origini dati Microsoft SQL Server e database SQL di Microsoft Azure.
author: maggiesMSFT
ms.reviewer: cfinlan
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/22/2020
ms.author: maggies
ms.openlocfilehash: f8d711bba8dc7570f2d470554fd1d971639bbb7b
ms.sourcegitcommit: a1409030a1616027b138128695b80f6843258168
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2020
ms.locfileid: "76710207"
---
# <a name="always-encrypted-in-power-bi-report-server"></a>Always Encrypted in Server di report di Power BI

Questo articolo illustra il supporto di Always Encrypted in Server di report di Power BI quando si usano i tipi di origini dati Microsoft SQL Server e database SQL di Microsoft Azure. Per altre informazioni sulle funzionalità di Always Encrypted in SQL Server, vedere l'articolo [Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine).

## <a name="always-encrypted-user-isolation"></a>Isolamento dell'utente in Always Encrypted

Server di report di Power BI attualmente non limita l'accesso alle colonne Always Encrypted nei report se un utente ha accesso al report.  Se quindi al server è stato concesso l'accesso alle chiavi di crittografia delle colonne tramite la chiave master di colonna, gli utenti hanno accesso a tutte le colonne dei report a cui possono accedere.

## <a name="always-encrypted-column-usage"></a>Utilizzo delle colonne Always Encrypted

### <a name="key-storage-strategies"></a>Strategia di archiviazione delle chiavi

|Archiviazione  |Supportato  |
|---------|---------|
|Archivio certificati Windows | Sì |
|Insieme di credenziali chiave di Azure | No |
| Cryptography Next Generation (CNG) | No |

### <a name="certificate-storage-and-access"></a>Archiviazione e accesso ai certificati

L'account che deve avere accesso al certificato è l'account del servizio. Il certificato dovrebbe essere archiviato nell'archivio certificati del computer locale. Per altre informazioni, vedere:

- [Configurare l'account del servizio del server di report](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager) (Configuration Manager)
- Sezione [Rendere disponibili i certificati a utenti e applicazioni](https://docs.microsoft.com/sql/relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted#making-certificates-available-to-applications-and-users) dell'articolo su SQL Server "Creare e archiviare chiavi master di colonna per Always Encrypted".

### <a name="column-encryption-strategy"></a>Strategia di crittografia delle colonne

In Server di report di Power BI Report la strategia di crittografia delle colonne può essere *deterministica* o *casuale*. La tabella seguente illustra le differenze a seconda della strategia usata.

|Uso  |Deterministico  |Casuale  |
|---------|---------|---------|
|Può essere letta così com'è nei risultati di una query, ad esempio nelle istruzioni SELECT. | Sì  | Sì  |
|Può essere usata come entità di raggruppamento all'interno di una query. | Sì | No |
|Può essere usata come campo di aggregazione, a eccezione di COUNT e DISTINCT. | No, a eccezione di COUNT e DISTINCT | No |
|Può essere usata come parametro di report | Sì | No |

Per altre informazioni, vedere [Selezione della crittografia deterministica o casuale](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine#selecting--deterministic-or-randomized-encryption).

### <a name="parameter-usage"></a>Utilizzo dei parametri

L'utilizzo dei parametri si applica solo alla crittografia deterministica.

**Parametro a valore singolo**.  È possibile usare un parametro a valore singolo su una colonna Always Encrypted.

**Parametro multivalore**. Non è possibile usare un parametro multivalore con più di un valore su una colonna Always Encrypted.

**Parametri a cascata**. È possibile usare i parametri a cascata con Always Encrypted se si verificano *tutte* le condizioni seguenti:

- Tutte le colonne Always Encrypted devono essere Always Encrypted con strategia deterministica.
- Tutti i parametri usati sulle colonne Always Encrypted sono parametri a valore singolo.
- Tutti i confronti SQL usano l'operatore Uguale a (=).

## <a name="datatype-support"></a>Supporto dei tipi di dati

| Tipo di dati SQL | Supporto della lettura del campo | Supporto dell'uso come elemento di raggruppamento | Aggregazioni supportate (COUNT, DISTINCT, MAX, MIN, SUM e così via) | Supporto di filtri tramite uguaglianza con parametri | Note |
| --- | --- | --- | --- | --- | --- |
| INT | Sì | Sì | COUNT, DISTINCT | Sì, come Integer |   |
| float | Sì | Sì | COUNT, DISTINCT | Sì, come Float |   |
| NVARCHAR | Sì | Sì | COUNT, DISTINCT | Sì, come Text | La crittografia deterministica deve usare regole di confronto a livello di colonna con un ordinamento binario2 per colonne di tipo carattere. Per informazioni dettagliate, vedere l'articolo su SQL Server [Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine#selecting--deterministic-or-randomized-encryption).  |
| varchar | Sì | Sì | COUNT, DISTINCT | No |   |
| decimal | Sì | Sì | COUNT, DISTINCT | No |   |
| NUMERIC | Sì | Sì | COUNT, DISTINCT | No |   |
| Datetime | Sì | Sì | COUNT, DISTINCT | No |   |
| datetime2 | Sì | Sì | COUNT, DISTINCT | Sì, come Date/Time | Supportato se la colonna non ha una precisione in millisecondi, in altre parole nessun datetime2(0) |

## <a name="aggregation-alternatives"></a>Alternative di aggregazione

Le uniche aggregazioni supportate per le colonne Always Encrypted deterministiche sono attualmente quelle che usano direttamente l'operatore Uguale a (=). Questa limitazione di SQL Server è dovuta alla natura delle colonne Always Encrypted. Gli utenti devono essere aggregati all'interno del report invece che nel database.

## <a name="always-encrypted-in-connection-strings"></a>Always Encrypted nelle stringhe di connessione

È necessario abilitare Always Encrypted nella stringa di connessione per un'origine dati di SQL Server. Per altre informazioni, vedere [Abilitazione di Always Encrypted per le query dell'applicazione](https://docs.microsoft.com/sql/relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider#enabling-always-encrypted-for-application-queries).

## <a name="next-steps"></a>Passaggi successivi

[Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine) in SQL Server e nel database SQL di Azure

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)

