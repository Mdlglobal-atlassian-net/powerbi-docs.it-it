---
title: Disconnettersi da un pacchetto di contenuto aziendale - Power BI
description: Leggere le informazioni su come rimuovere la connessione a un pacchetto di contenuto aziendale eliminando il relativo set di dati in Power BI.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/02/2018
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 81406726bacac4d2a59f513473d04a8c083c90bd
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83348023"
---
# <a name="remove-your-connection-to-a-power-bi-organizational-content-pack"></a>Rimuovere la connessione a un pacchetto di contenuto aziendale di Power BI

> [!NOTE]
> Non è possibile creare pacchetti di contenuto aziendali né installarli nelle nuove aree di lavoro. Questo è un buon momento per aggiornare i pacchetti di contenuto per le app, se non è ancora stato fatto. [Altre informazioni sulla nuova esperienza dell'area di lavoro](service-create-the-new-workspaces.md).
> 

Un collaboratore ha creato un pacchetto di contenuto, che è stato individuato in AppSource e aggiunto all'area di lavoro di Power BI. Ora però non è più necessario.  Come fare a rimuoverlo?

Per rimuovere un pacchetto di contenuto, è necessario rimuovere il set di dati associato.  

* Nel riquadro di spostamento selezionare i puntini di sospensione a destra del set di dati e selezionare **Rimuovi \> Sì**.  
  
  ![Rimuovere il pacchetto di contenuto](media/service-organizational-content-pack-disconnect/power-bi-remove-organizational-content-pack-dataset.png)

Quando si rimuove il set di dati, vengono rimossi anche tutti i report e i dashboard associati. Tuttavia, rimuovendo la connessione al pacchetto di contenuto, quest'ultimo non viene eliminato da AppSource dell'organizzazione.  È sempre possibile tornare ad AppSource e aggiungere nuovamente il pacchetto di contenuto all'area di lavoro. Solo l'autore di un pacchetto di contenuto può [eliminarlo da AppSource](service-organizational-content-pack-manage-update-delete.md).

## <a name="next-steps"></a>Passaggi successivi
* [Introduzione ai pacchetti di contenuto aziendali](service-organizational-content-pack-introduction.md) 
* [Creare e distribuire un'app in Power BI](service-create-distribute-apps.md) 
* [Concetti di base sulle finestre di progettazione del servizio Power BI](../fundamentals/service-basic-concepts.md)  
* Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)
