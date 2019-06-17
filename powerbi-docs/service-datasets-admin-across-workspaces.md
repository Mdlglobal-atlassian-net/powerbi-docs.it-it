---
title: Controllare l'uso di set di dati in aree di lavoro diverse (anteprima) - Power BI
description: Informazioni su come limitare il flusso di informazioni nel tenant Power BI.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/31/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 363bf9b107722b3993ed7ac43138c73da03f410a
ms.sourcegitcommit: 7c426a5209d4fdd1360fc3d0442d57991be1984d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/03/2019
ms.locfileid: "66461788"
---
# <a name="control-the-use-of-datasets-across-workspaces-preview"></a>Controllare l'uso di set di dati in aree di lavoro diverse (anteprima)

Usare set di dati in aree di lavoro diverse è un'ottima soluzione per offrire cultura e democratizzazione di dati all'interno di un'organizzazione. Può tuttavia succedere talvolta che un amministratore Power BI voglia limitare il flusso di informazioni nel tenant Power BI. Con l'impostazione del tenant **Usa i set di dati in tutte le aree di lavoro**, è possibile limitare il riutilizzo di set di dati completamente o parzialmente a seconda dei gruppi di sicurezza.

![Impostazioni dell'area di lavoro dell'amministratore Power BI](media/service-datasets-admin-across-workspaces/power-bi-admin-workspace-settings.png)

Se si disattiva questa impostazione, gli effetti sugli autori di report sono i seguenti:

- Il pulsante per copiare i report in aree di lavoro diverse non è disponibile. 
- In un report basato su un set di dati condiviso il pulsante **Modifica report** non è disponibile.
- Nel servizio Power BI l'esperienza di individuazione visualizza solo i set di dati nell'area di lavoro corrente.
- In Power BI Desktop l'esperienza di individuazione visualizza solo i set di dati delle aree di lavoro di cui si è membro.
- In Power BI Desktop, se gli utenti aprono un file con estensione pbix con una connessione dinamica a un set di dati esterno a tutte le aree di lavoro di cui si è membro, viene visualizzato un messaggio di errore in cui si richiede la connessione a un set di dati diverso.

## <a name="provide-a-link-for-the-certification-process"></a>Specificare un collegamento per il processo di certificazione

L'amministratore tenant può specificare un URL per il collegamento **Altre informazioni** nella pagina delle impostazioni **Approvazione**.  Questo collegamento apre la documentazione sul processo di certificazione. Se l'amministratore non specifica una destinazione per il collegamento **Altre informazioni**, per impostazione predefinita si aprirà l'articolo [Certificare set di dati](service-datasets-certify.md).

![Altre informazioni sulla certificazione del set di dati](media/service-datasets-certify-promote/power-bi-dataset-learn-more-certification.png)

## <a name="next-steps"></a>Passaggi successivi

- [Usare set di dati in aree di lavoro diverse (anteprima)](service-datasets-across-workspaces.md)
- Domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)
