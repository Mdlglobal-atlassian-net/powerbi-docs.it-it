---
title: Prerequisiti per le origini dati di Power BI
description: Prerequisiti per le origini dati di Power BI
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: d118cae8cd4b6fbd95066b15819b1e798c8bbe0f
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2020
ms.locfileid: "75761319"
---
# <a name="power-bi-data-source-prerequisites"></a>Prerequisiti per le origini dati di Power BI
Per ogni provider di dati, Power BI supporta una versione di provider specifica per gli oggetti. Per altre informazioni sulle origini dati disponibili in Power BI, vedere [Origini dati](desktop-data-sources.md). La tabella seguente descrive questi requisiti.

| Origine dati | Provider | Versione minima del provider | Versione minima dell'origine dati | Oggetti origine dati supportati | Collegamento per il download |
| --- | --- | --- | --- | --- | --- |
| SQL Server |ADO.NET (integrato in .NET Framework) |.NET Framework 3.5 (esclusivamente) |SQL Server 2005+ |Tabelle/viste, funzioni scalari, funzioni di tabella |Incluso in .NET Framework 3.5 o versione successiva |
| Accesso |Motore di database di Microsoft Access |Motore di database di Microsoft Access 2010 SP1 |Nessuna restrizione |Tabelle/viste |[Collegamento per il download](https://go.microsoft.com/fwlink/?linkid=285987&clcid=0x409) |
| Excel (solo file con estensione xls) (vedere la nota 1) |Motore di database di Microsoft Access |Motore di database di Microsoft Access 2010 SP1 |Nessuna restrizione |Tabelle, fogli |[Collegamento per il download](https://go.microsoft.com/fwlink/?linkid=285987&clcid=0x409) |
| Oracle (vedere la nota 2) |ODP.NET |ODAC 11.2 versione 5 (11.2.0.3.20) |9.x+ |Tabelle/viste |[Collegamento per il download](https://go.microsoft.com/fwlink/?linkid=272376&clcid=0x409) |
| | System.Data.OracleClient (integrato in .NET Framework) |.NET Framework 3.5 |9.x+ |Tabelle/viste |Incluso in .NET Framework 3.5 o versione successiva |
| IBM DB2 |Client ADO.Net di IBM (parte del pacchetto di driver del server dati IBM) |10.1 |9.1+ |Tabelle/viste |[Collegamento per il download](https://go.microsoft.com/fwlink/?linkid=274911&clcid=0x409) |
| MySQL |Connector/Net |6.6.5 |5.1 |Tabelle/viste, funzioni scalari |[Collegamento per il download](https://go.microsoft.com/fwlink/?linkid=278885&clcid=0x409) |
| PostgreSQL |Provider NPGSQL ADO.NET |2.0.12 |7.4 |Tabelle/viste |[Collegamento per il download](https://go.microsoft.com/fwlink/?linkid=282716&clcid=0x409) |
| Teradata |Provider di dati .NET per Teradata |14+ |12+ |Tabelle/viste |[Collegamento per il download](https://go.microsoft.com/fwlink/?linkid=278886&clcid=0x409) |
| SAP Sybase SQL Anywhere |iAnywhere.Data.SQLAnywhere per .NET 3.5 |16+ |16+ |Tabelle/viste |[Collegamento per il download](https://go.microsoft.com/fwlink/?linkid=324846) |

>[!NOTE]
>I file di Excel con estensione xlsx non richiedono un'installazione del provider separata.

>[!NOTE]
>I provider Oracle richiedono anche il software client Oracle (versione 8.1.7+).
> 
> 

