---
title: Certificare set di dati (anteprima) - Power BI
description: Informazioni su come indirizzare gli utenti aziendali a set di dati affidabili e di alta qualità.
author: maggiesMSFT
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/03/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: bdce9ec797d00b34f657ed66df6b7a5ce373334d
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73877149"
---
# <a name="certify-datasets-preview"></a>Certificare set di dati (anteprima)

L'organizzazione può certificare set di dati con origine autorevole per informazioni di importanza critica. Questi set di dati vengono messi in evidenza quando i responsabili della progettazione report iniziano a creare un report e cercano dati affidabili. La certificazione può essere un processo estremamente selettivo, tant'è che solo i set di dati più validi ottengono la certificazione. Gli amministratori tenant Power BI possono usare una nuova impostazione per controllare chi può certificare i set di dati. In questo modo gli amministratori possono assicurare che tale processo certifichi set di dati realmente affidabili e autorevoli utilizzabili in tutta l'organizzazione.

Gli utenti di Power BI possono ora accedere a set di dati diversi. È quindi necessario che le aziende indirizzino gli utenti nella scelta di set di dati affidabili e di alta qualità. Power BI offre due modi per *approvare* i set di dati:

- **Promozione**: I proprietari dei set di dati e altri utenti in un'area di lavoro possono promuovere i rispettivi set di dati quando sono pronti per l'utilizzo diffuso. Vedere [Promuovere il set di dati](service-datasets-promote.md) per informazioni dettagliate. 
- **Certificazione**: I proprietari di set di dati possono richiedere la certificazione di un set di dati promosso. Un gruppo selezionato di utenti definito nell'impostazione dell'amministratore tenant **Certificazione del set di dati** decide quali set di dati certificare. Il nome della persona che certifica un set di dati viene visualizzato in una descrizione comando durante l'esperienza di individuazione di set di dati. Per visualizzarlo è sufficiente passare il mouse sull'etichetta **Certificato**.

## <a name="certify-a-dataset"></a>Certificare un set di dati

L'amministratore tenant può specificare un URL per il collegamento **Altre informazioni** nella pagina delle impostazioni **Approvazione**.  Questo collegamento apre la documentazione sul processo di certificazione. Se l'amministratore non specifica una destinazione per il collegamento **Altre informazioni**, per impostazione predefinita si aprirà questo articolo.

![Altre informazioni sulla certificazione del set di dati](media/service-datasets-certify-promote/power-bi-dataset-learn-more-certification.png)

Essere nominati certificatore di set dati è ovviamente un'importante responsabilità. Quando si viene contattati da un autore di set di dati per certificare un set di dati, inizia il processo di verifica. Quando si è certi che un set di dati meriti di essere certificato, gli ultimi passaggi sono i seguenti.

1. Il proprietario del set di dati deve concedere le autorizzazioni di membro per l'area di lavoro in cui si trova il set di dati.
1. Se si è stati nominati dall'amministratore tenant certificatore di set di dati, l'opzione **Certificato** è disponibile nella sezione **Approvazione** di **Impostazioni** per il set di dati. Selezionare **Certificato**.
1. Selezionare **Applica**.

Sono disponibili altre informazioni su come gli amministratori tenant [controllano l'uso di set di dati in aree di lavoro diverse](service-datasets-admin-across-workspaces.md).

## <a name="next-steps"></a>Passaggi successivi

* Leggere [Usare set di dati in aree di lavoro diverse](service-datasets-across-workspaces.md)
* Domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
