---
title: 'Pacchetti di contenuto aziendali: Accedere e copiare'
description: Scoprire come creare copie e risolvere i problemi di accesso nei pacchetti di contenuto aziendali in Power BI
author: maggiesMSFT
manager: kfile
ms.reviewer: ajayan
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 06/08/2018
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: c2d7a878189542d8a477933f6c54390b2636787e
ms.sourcegitcommit: b7839f2aa68c3626f55ee7e49c8392169d1ec67e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2018
ms.locfileid: "34852234"
---
# <a name="organizational-content-packs-copy-refresh-and-get-access"></a>Pacchetti di contenuto aziendali: Copiare, aggiornare e ottenere l'accesso
> [!NOTE]
> Le nuove *app* costituiscono la soluzione ideale per la distribuzione di contenuto a un vasto pubblico in Power BI. I pacchetti di contenuto aziendale verranno presto deprecati. Al loro posto, si consiglia quindi di usare le app. Altre informazioni sulle [app](service-install-use-apps.md).
> 
> 

Quando viene pubblicato un pacchetto di contenuto aziendale, tutti i destinatari visualizzano lo stesso dashboard, gli stessi report, le stesse cartelle di lavoro di Excel, gli stessi set di dati e gli stessi dati, a meno che non sia un'origine dati SQL Server Analysis Services (SSAS).  [Solo il creatore può modificare e ripubblicare](service-organizational-content-pack-manage-update-delete.md) il pacchetto di contenuto.  Tuttavia, tutti i destinatari possono salvare una copia del pacchetto di contenuto che può esistere insieme all'originale.

La creazione di pacchetti di contenuto è diversa dalla condivisione di dashboard o dalla collaborazione negli stessi in un gruppo. Per scegliere la soluzione migliore in base alla situazione specifica, leggere [Come si condividono i dashboard e i report e in che modo ci si collabora?](service-how-to-collaborate-distribute-dashboards-reports.md).

## <a name="create-a-copy-of-an-organizational-content-pack"></a>Creare una copia di un pacchetto di contenuto aziendale
Creare la propria copia del pacchetto di contenuto, non visibile ad altri utenti.

1. Selezionare i puntini di sospensione (...) accanto al dashboard del pacchetto di contenuto > Crea una copia.
   
    ![](media/service-organizational-content-pack-copy-refresh-access/power-bi-create-copy-organizational-content-pack.png)
2. Selezionare **Salva**.  

A questo punto si ha una copia che è possibile modificare. Nessun altro potrà vedere le modifiche apportate.

## <a name="help--i-can-no-longer-access-the-content-pack"></a>Come fare  se il pacchetto di contenuto non è più accessibile
Questo problema può verificarsi per diversi motivi:

* **Modifiche all'appartenenza:** i pacchetti di contenuto vengono pubblicati per i gruppi di distribuzione di posta elettronica, i gruppi di sicurezza e i [gruppi di Power BI basati su Office 365](https://support.office.com/article/Create-a-group-in-Office-365-7124dc4c-1de9-40d4-b096-e8add19209e9).  Se si viene rimossi dal gruppo, non sarà più possibile accedere al pacchetto di contenuto.
* **Modifiche alla distribuzione:** il creatore del pacchetto di contenuto cambia la distribuzione. Ad esempio, se il pacchetto di contenuto è stato pubblicato in origine per l'intera organizzazione, ma il creatore lo ha ripubblicato per un gruppo di destinatari ristretto, l'utente potrebbe non essere più incluso.
* **Modifiche alle impostazioni di sicurezza:** se il dashboard e i report si connettono a origini dati SSAS locali e vengono apportate modifiche alle impostazioni di sicurezza, le autorizzazioni per il server potrebbero essere revocate.

## <a name="how-are-organizational-content-packs-refreshed"></a>Aggiornamento dei pacchetti di contenuto aziendali
Quando si crea il pacchetto di contenuto, le impostazioni di aggiornamento vengono ereditate con il set di dati.  Quando si crea una copia del pacchetto di contenuto, la nuova versione manterrà il collegamento al set di dati originale e la relativa pianificazione dell'aggiornamento. 

Vedere [Gestire, aggiornare ed eliminare pacchetti di contenuto aziendali](service-organizational-content-pack-manage-update-delete.md).

## <a name="next-steps"></a>Passaggi successivi
* [Introduzione ai pacchetti di contenuto aziendali](service-organizational-content-pack-introduction.md)
* [Creare un gruppo in Power BI](service-create-distribute-apps.md)
* Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

