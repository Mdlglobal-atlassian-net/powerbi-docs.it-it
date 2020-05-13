---
title: 'Servizio di terze parti: Connettore Facebook per Power BI Desktop'
description: 'Servizio di terze parti: Connettore Facebook per Power BI Desktop'
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/20/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 882cddf7728a27e78056a35c14fde20f00678e33
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83309545"
---
# <a name="use-the-facebook-connector-for-power-bi-desktop"></a>Usare il connettore Facebook per Power BI Desktop
Il connettore Facebook in **Power BI Desktop** si basa sull'API Facebook Graph. e di conseguenza le funzionalità e la disponibilità potrebbero variare nel tempo.

È disponibile un'[esercitazione sul connettore Facebook per Power BI Desktop](desktop-tutorial-facebook-analytics.md).

> [!IMPORTANT]
> **Avviso di deprecazione del connettore dati per Facebook:** L'importazione e l'aggiornamento dei dati da Facebook in Excel non funzioneranno più correttamente da aprile 2020. Fino a tale data sarà possibile usare il connettore *Recupera e trasforma (Power Query)* per Facebook. Dopo tale data, non sarà possibile connettersi a Facebook e verrà visualizzato un messaggio di errore. È consigliabile correggere o rimuovere al più presto eventuali query di *Recupera e trasforma (Power Query)* che usano il connettore per Facebook per evitare risultati imprevisti.


Il 30 aprile 2015 è scaduta la versione 1.0 dell'API Graph di Facebook. Power BI usa l'API Graph in background per il connettore Facebook, che consente di connettersi ai dati e di analizzarli.

Le query create prima del 30 aprile 2015 potrebbero non funzionare più o restituire un volume di dati inferiore al precedente. Dal 30 aprile 2015 Power BI usa la versione 2.8 in tutte le chiamate all'API Facebook. Se la query è stata creata prima del 30 aprile 2015, e da allora non è più stata utilizzata, è probabile che si debba ripetere l'autenticazione per approvare il nuovo set di autorizzazioni richieste.

Anche se abbiamo tentato di rilasciare aggiornamenti in funzione di tutte le modifiche apportate, è possibile che le modifiche all'API incidano sui risultati delle query generate. In alcuni casi, alcune query potrebbero non essere più supportate. A causa di questa dipendenza non è possibile garantire i risultati delle query quando si usa questo connettore.

Altre informazioni sulla modifica dell'API Facebook sono disponibili [qui](https://developers.facebook.com/docs/apps/changelog#v2_0).

