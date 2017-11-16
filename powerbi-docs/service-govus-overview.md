---
title: Power Bi per i clienti del Governo degli Stati Uniti - Panoramica
description: "I I clienti governativi troveranno informazioni sulle funzionalità e sulle limitazioni per il servizio Power BI per il Governo degli Stati Uniti"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: 9c8e2b44c128db283bef65198204e4aee1bfdd7a
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2017
---
# <a name="power-bi-for-us-government-customers"></a>Power BI per i clienti del Governo degli Stati Uniti
Il **servizio Power BI** ha una versione disponibile per i clienti del Governo degli Stati Uniti come parte delle sottoscrizioni al **piano Office 365 US Government Community**. La versione del **servizio Power BI** descritta in questo articolo è progettata specificamente per i clienti del Governo degli Stati Uniti ed è separato e diverso dalla versione commerciale del **servizio Power BI**.

![](media/service-govus-overview/service_usgov_overview-1.png)

Le sezioni seguenti descrivono le *funzionalità* disponibili per la versione del **servizio Power BI** per il Governo degli Stati Uniti, illustrano alcune delle *limitazioni*, contengono le **domande frequenti** e le risposte (compresa la modalità di iscrizione) e forniscono i collegamenti ad altre informazioni.

## <a name="features-of-power-bi-us-government"></a>Funzionalità di Power BI per il Governo degli Stati Uniti
È importante notare che **Power BI per il Governo degli Stati Uniti** è disponibile solo come **licenza Pro** e non come licenza gratuita. Alcune funzionalità del servizio Power BI sono disponibili nella versione **Power BI per il Governo degli Stati Uniti**.

Le funzionalità seguenti sono disponibili in **Power BI per il Governo degli Stati Uniti**, dal momento che sono previste nella licenza **Pro**:

* Creare e visualizzare dashboard e report
* [Limiti per la capacità dei dati](service-admin-manage-your-data-storage-in-power-bi.md)
* [Aggiornamento pianificato dei dati](refresh-data.md)
* Dashboard del team aggiornabili
* Gruppi di Active Directory per la condivisione e la gestione del controllo di accesso
* [Importare dati](service-get-data.md) e report da file di Excel, CSV e di Power BI Desktop
* Gateway di gestione dati
* Tutti i dati sono crittografati in Azure SQL e nell'archiviazione BLOB per Power BI
* Connettersi ai servizi con i [pacchetti di contenuto](service-connect-to-services.md)

## <a name="limitations-of-power-bi-us-government"></a>Limitazioni di Power BI per il Governo degli Stati Uniti
Alcune delle funzionalità disponibili nella versione commerciale del **servizio Power BI** *non* sono disponibili nel **servizio Power BI** per i clienti del Governo degli Stati Uniti. Il team di Power BI è attivamente impegnato a rendere disponibili queste funzionalità ai clienti del Governo degli Stati Uniti e ad aggiornare questo articolo di conseguenza.

* **Power BI per il Governo degli Stati Uniti** è disponibile solo come licenza **Pro**. Tutti i riferimenti alle licenze gratuite di Power BI in un portale di amministrazione (o come utenti) vengono eseguiti in un cloud del servizio Power BI a pagamento.
* **Controllo**: il controllo non è disponibile attraverso il portale del Centro sicurezza e conformità di Office 365.

Se agli account sono assegnate licenze gratuite di **Power BI**, questi vengono eseguiti in una versione a pagamento del servizio **Power BI** e non sono incluse nell'offerta di **Power BI per il Governo degli Stati Uniti**. Con gli account delle licenze gratuite è possibile riscontrare i problemi seguenti:

* Non è possibile eseguire l'autenticazione di gateway, dispositivo mobile e desktop
* Non è possibile accedere alle origini dati commerciali di Azure
* I file PBIX devono essere caricati manualmente dal commerciale
* Le app Power BI per dispositivi mobili non sono disponibili

Per risolvere i problemi, contattare il proprio rappresentante.

## <a name="frequently-asked-questions-faq-for-the-us-government-version-of-the-power-bi-service"></a>Domande frequenti per la versione del servizio Power BI per il Governo degli Stati Uniti
Le seguenti domande (e risposte) hanno l'obiettivo di aiutare a ottenere rapidamente le informazioni necessarie sul servizio.

**Domanda:** come eseguire la migrazione dei dati commerciali di **Power BI** al **servizio Power BI** per il Governo degli Stati Uniti?

**Risposta:** l'amministratore deve creare una nuova istanza di **Power BI** in una sottoscrizione separata, specifica del Governo degli Stati Uniti. Sarà quindi possibile replicare i dati commerciali nel **servizio Power BI** per il Governo degli Stati Uniti, rimuovere la licenza commerciale e associare il dominio esistente al nuovo servizio specifico del Governo degli Stati Uniti.

**Domanda:** perché non è possibile connettersi a un pacchetto di contenuto specifico?

**Risposta:** è necessario verificare che la sottoscrizione sia abilitata prima di connettersi a tale pacchetto di contenuto.

**Domanda:** vorrei ottenere **Power BI** per la mia organizzazione del Governo degli Stati Uniti. Per iniziare

**Risposta:** la registrazione (spesso chiamata *onboarding*) potrebbe differire in base alla licenza e alla sottoscrizione esistenti. Per altre informazioni, vedere l'articolo [Iscrizione a Power BI per il Governo degli Stati Uniti](service-govus-signup.md).

**Domanda:** l'URL per la connessione a **Power BI** per il Governo degli Stati Uniti è diverso dall'URL della versione commerciale di **Power BI**?

**Risposta:** sì, gli URL sono diversi. La tabella seguente illustra ciascun URL:

| URL versione commerciale | URL versione Governo degli Stati Uniti |
| --- | --- |
| https://app.powerbi.com/ |[https://app.powerbigov.us](https://app.powerbigov.us) |

## <a name="next-steps"></a>Passaggi successivi
Power BI offre infinite possibilità. Per altre informazioni e per la formazione, tra cui un articolo che illustra come effettuare l'iscrizione al servizio, vedere le risorse seguenti:

* [Iscrizione a Power BI per il Governo degli Stati Uniti](service-govus-signup.md)
* <a href="https://channel9.msdn.com/Blogs/Azure/Cognitive-Services-HDInsight-and-Power-BI-on-Azure-Government">Demo di Power BI per il Governo degli Stati Uniti</a>
* [Apprendimento guidato per Power BI](guided-learning/gettingstarted.yml#step-1)
* [Introduzione al servizio Power BI](service-get-started.md)
* [Introduzione a Power BI Desktop](desktop-getting-started.md)

