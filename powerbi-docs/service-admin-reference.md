---
title: Cmdlet di PowerShell, API REST e .NET SDK per gli amministratori
description: Informazioni su come amministrare Power BI tramite gli script e le API di programmazione.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: overview
ms.date: 06/25/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: f4455fef5a2ed0e7ee23ff8ca3a0b626cd695838
ms.sourcegitcommit: a1b7ca499f4ca7e90421511e9dfa61a33333de35
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2018
ms.locfileid: "51507992"
---
# <a name="powershell-cmdlets-rest-apis-and-net-sdk-for-power-bi-administration"></a>Cmdlet di PowerShell, API REST e .NET SDK per l'amministrazione di Power BI
Power BI consente agli amministratori di creare script per le attività comuni tramite i cmdlet di PowerShell. Inoltre, espone le API REST e mette a disposizione .NET SDK per lo sviluppo di soluzioni di amministrazione. In questo argomento viene presentato un elenco di cmdlet con il metodo SDK e l'endpoint API REST corrispondenti. Per altre informazioni, vedere:

  - [Download](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt/) e [documentazione](https://docs.microsoft.com/powershell/power-bi/overview?view=powerbi-ps) di PowerShell
  - [Documentazione](https://docs.microsoft.com/rest/api/power-bi/admin) relativa alle API REST
  - [Download](https://www.nuget.org/packages/Microsoft.PowerBI.Api/) di .NET SDK 


| **Nome del cmdlet** | **Metodo SDK** | **Endpoint API REST** | **Descrizione** |
| --- | --- | --- | --- |
| **Get-PowerBIDatasource** | Datasets\_GetDataSourcesAsAdmin | /v1.0/myorg/admin/datasets/{datasetkey}/datasources | Recupera le origini dati per un determinato set di dati. |
| **Get-PowerBIDataset** | Datasets\_GetDatasetsAsAdmin | /v1.0/myorg/admin/datasets | Recupera l'elenco completo dei set di dati in un tenant di Power BI. |
| **Get-PowerBIWorkspace** | Groups\_GetGroupsAsAdmin | /v1.0/myorg/admin/groups | Recupera l'elenco completo delle aree di lavoro in un tenant di Power BI. |
| **Add-PowerBIWorkspaceUser** | Groups\_AddUserAsAdmin | /v1.0/myorg/admin/groups/{groupId}/users | Aggiunge un utente come membro a un'area di lavoro. |
| **Remove-PowerBIWorkspaceUser** | Groups\_DeleteUserAsAdmin | /v1.0/myorg/admin/groups/{groupId}/users/{user} | Rimuove un utente dall'elenco di appartenenza di un'area di lavoro. |
| **Restore-PowerBIWorkspace** | Groups\_RestoreDeletedGroupAsAdmin | /v1.0/myorg/admin/groups/{groupId}/restore | Ripristina un'area di lavoro eliminata. |
| **Set-PowerBIWorkspace** | Groups\_UpdateGroupAsAdmin | /v1.0/myorg/admin/groups/{groupId} | Aggiorna le proprietà di un'area di lavoro. |
| **Get-PowerBIDataset -WorkspaceId** | Groups\_GetDatasetsAsAdmin | /v1.0/myorg/admin/groups/{group\_id}/datasets | Recupera i set di dati all'interno di un'area di lavoro. |
| **Export-PowerBIReport** | Reports\_ExportReportAsAdmin | N/D | Esporta un report specifico in un file locale. |
| **Get-PowerBIReport** | Reports\_GetReportsAsAdmin | /v1.0/myorg/admin/reports | Recupera l'elenco completo dei report in un tenant di Power BI. |
| **Get-PowerBIDashboard** | Dashboards\_GetDashboardsAsAdmin | /v1.0/myorg/admin/dashboards | Recupera l'elenco completo dei dashboard in un tenant di Power BI. |
| **Get-PowerBIDashboard -WorkspaceId** | Groups\_GetDashboardsAsAdmin | /v1.0/myorg/admin/groups/{group\_id}/dashboards | Recupera i dashboard all'interno di un'area di lavoro. |
| **Get-PowerBITile -DashboardId** | Dashboards\_GetTilesAsAdmin | /v1.0/myorg/admin/dashboards/{dashboard\_id}/tiles | Recupera i riquadri di un dashboard specifico. |
| **Get-PowerBIReport -WorkspaceId** | Groups\_GetReportsAsAdmin | /v1.0/myorg/admin/groups/{group\_id}/reports | Recupera i report all'interno di un'area di lavoro. |
| **Get-PowerBIImport** | Imports\_GetImportsAsAdmin | /v1.0/myorg/admin/imports | Recupera l'elenco completo delle importazioni in un tenant di Power BI. |
| **Connect-PowerBIServiceAccount** | N/D | N/D | Accesso a Power BI e avvio di una sessione. |
| **Disconnect-PowerBIServiceAccount** | N/D | N/D | Disconnessione da Power BI e chiusura della sessione esistente. |
| **Invoke-PowerBIRestMethod** | N/D | N/D | Inviare chiamate arbitrarie all'API REST di Power BI. |
| **Get-PowerBIAccessToken** | N/D | N/D | Recuperare il token di accesso di Power BI in una sessione. |
| **Resolve-PowerBIError** | N/D | N/D | Recupera informazioni dettagliate sugli errori per le chiamate non riuscite ai cmdlet. |