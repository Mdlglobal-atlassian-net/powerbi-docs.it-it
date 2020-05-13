---
title: 'Project Online: connettersi ai dati con Power BI Desktop'
description: 'Project Online: connettersi ai dati con Power BI Desktop'
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/01/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 0f01a6da3bb0d829d396861814f71d33ba69f22f
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83291927"
---
# <a name="connect-to-project-online-data-through-power-bi-desktop"></a>Connettersi ai dati di Project Online con Power BI Desktop
È possibile connettersi ai dati in Project Online con Power BI Desktop.

## <a name="step-1-download-power-bi-desktop"></a>Passaggio 1: scaricare Power BI Desktop
1. [Scaricare Power BI Desktop](https://go.microsoft.com/fwlink/?LinkID=521662), quindi eseguire il programma di installazione per installare **Power BI Desktop** nel computer.

## <a name="step-2-connect-to-project-online-with-odata"></a>Passaggio 2: connettersi a Project Online con OData
1. Aprire **Power BI Desktop**.
2. Nella schermata *Introduzione* selezionare **Recupera dati**.
3. Scegliere **Feed OData** e selezionare **Connetti**.
4. Immettere l'indirizzo per il feed OData nella casella URL e fare clic su OK.
   
   Se l'indirizzo del sito Project Web App è simile a *https://\<tenantname\>.sharepoint.com/sites/pwa*, l'indirizzo da inserire per il feed OData sarà *https://\<tenantname\>.sharepoint.com/sites/pwa/\_api/Projectdata*.
   
   Per questo esempio, si userà:

    `https://contoso.sharepoint.com/sites/pwa/default.aspx`

5. Power BI Desktop richiederà di eseguire l'autenticazione con l'account Office 365. Selezionare l'account aziendale e quindi immettere le proprie credenziali.
   
   ![](media/desktop-project-online-connect-to-data/image.png)

L'account che si usa per connettersi al feed OData deve poter accedere almeno come Visualizzatore portfolio al sito Project Web App. 

A questo punto, è possibile scegliere a quali tabelle ci si vuole connettere e compilare una query.  Per un'idea di come iniziare,  leggere il post di blog seguente che illustra come creare un grafico burndown partendo dai dati di Project Online.  Il post di blog riguarda l'uso di Power Query per connettersi a Project Online, ma si applica anche a Power BI Desktop.

[Creazione di grafici burn-down per Project Online usando Power Pivot e Power Query](https://blogs.office.com/2014/03/24/creating-burndown-charts-for-project-using-power-pivot-and-power-query/)

