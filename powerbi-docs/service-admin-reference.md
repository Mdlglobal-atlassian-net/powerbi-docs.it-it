---
title: Cmdlet di PowerShell, API REST e .NET SDK per gli amministratori
description: Informazioni su come amministrare Power BI tramite gli script e le API di programmazione.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: b4f4227a53a87cd831962bc5c944a569531b8232
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/02/2019
ms.locfileid: "74699867"
---
# <a name="powershell-cmdlets-rest-apis-and-net-sdk-for-power-bi-administration"></a>Cmdlet di PowerShell, API REST e .NET SDK per l'amministrazione di Power BI
Power BI consente agli amministratori di creare script per le attività comuni tramite i cmdlet di PowerShell. Inoltre, espone le API REST e mette a disposizione .NET SDK per lo sviluppo di soluzioni di amministrazione. In questo argomento viene presentato un elenco di cmdlet con il metodo SDK e l'endpoint API REST corrispondenti. Per altre informazioni, vedere:

- [Download](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt/) e [documentazione](https://docs.microsoft.com/powershell/power-bi/overview?view=powerbi-ps) di PowerShell
- [Documentazione](https://docs.microsoft.com/rest/api/power-bi/admin) relativa alle API REST
- [Download](https://www.nuget.org/packages/Microsoft.PowerBI.Api/) di .NET SDK

> I cmdlet riportati di seguito devono essere chiamati con `-Scope Organization` per agire sul tenant per l'amministrazione.

| **Nome del cmdlet** | **Alias** | **Metodo SDK** | **Endpoint API REST** | **Descrizione** |
| --- | --- | --- | --- | --- |
| `Get-PowerBIDatasource` | N/D | `Datasets_GetDataSourcesAsAdmin` | /v1.0/myorg/admin/datasets/{datasetkey}/datasources | Recupera le origini dati per un determinato set di dati. |
| `Get-PowerBIDataset` | N/D | `Datasets_GetDatasetsAsAdmin` | /v1.0/myorg/admin/datasets | Recupera l'elenco completo dei set di dati in un tenant di Power BI. |
| `Get-PowerBIWorkspace` | `Get-PowerBIGroup` | `Groups_GetGroupsAsAdmin` | /v1.0/myorg/admin/groups | Recupera l'elenco completo delle aree di lavoro in un tenant di Power BI. |
| `Add-PowerBIWorkspaceUser` | `Add-PowerBIGroupUser` | `Groups_AddUserAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/users | Aggiunge un utente come membro a un'area di lavoro. |
| `Remove-PowerBIWorkspaceUser` | `Remove-PowerBIGroupUser` | `Groups_DeleteUserAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/users/{user} | Rimuove un utente dall'elenco di appartenenza di un'area di lavoro. |
| `Restore-PowerBIWorkspace` |`Restore-PowerBIGroup` | `Groups_RestoreDeletedGroupAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/restore | Ripristina un'area di lavoro eliminata. |
| `Set-PowerBIWorkspace` |`Set-PowerBIGroup` | `Groups_UpdateGroupAsAdmin` | /v1.0/myorg/admin/groups/{groupId} | Aggiorna le proprietà di un'area di lavoro. |
| `Get-PowerBIDataset -WorkspaceId` | N/D | `Groups_GetDatasetsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/datasets | Recupera i set di dati all'interno di un'area di lavoro. |
| `Get-PowerBIReport` | N/D | `Reports_GetReportsAsAdmin` | /v1.0/myorg/admin/reports | Recupera l'elenco completo dei report in un tenant di Power BI. |
| `Get-PowerBIDashboard` | N/D | `Dashboards_GetDashboardsAsAdmin` | /v1.0/myorg/admin/dashboards | Recupera l'elenco completo dei dashboard in un tenant di Power BI. |
| `Get-PowerBIDashboard -WorkspaceId` | N/D | `Groups_GetDashboardsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/dashboards | Recupera i dashboard all'interno di un'area di lavoro. |
| `Get-PowerBITile` | `Get-PowerBIDashboardTile` | `Dashboards_GetTilesAsAdmin` | /v1.0/myorg/admin/dashboards/{dashboard\_id}/tiles | Recupera i riquadri di un dashboard specifico. |
| `Get-PowerBIReport` | N/D | `Groups_GetReportsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/reports | Recupera i report all'interno di un'area di lavoro. |
| `Get-PowerBIImport` | N/D | `Imports_GetImportsAsAdmin` | /v1.0/myorg/admin/imports | Recupera l'elenco completo delle importazioni in un tenant di Power BI. |
| `Connect-PowerBIServiceAccount` | `Login-PowerBI` &  `Login-PowerBIServiceAccount` | N/D | N/D | Accesso a Power BI e avvio di una sessione. |
| `Disconnect-PowerBIServiceAccount` | `Logout-PowerBI` & `Logout-PowerBIServiceAccount` | N/D | N/D | Disconnessione da Power BI e chiusura della sessione esistente. |
| `Invoke-PowerBIRestMethod`| N/D | N/D | N/D | Inviare chiamate arbitrarie all'API REST di Power BI. |
| `Get-PowerBIAccessToken`| N/D | N/D | N/D | Recuperare il token di accesso di Power BI in una sessione. |
| `Resolve-PowerBIError`| N/D | N/D | N/D | Recupera informazioni dettagliate sugli errori per le chiamate non riuscite ai cmdlet. |
