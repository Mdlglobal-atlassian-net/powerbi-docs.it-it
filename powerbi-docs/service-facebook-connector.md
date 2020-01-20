---
title: 'Servizio di terze parti: Connettore Facebook per Power BI Desktop'
description: 'Servizio di terze parti: Connettore Facebook per Power BI Desktop'
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: dcfc695d0371cce21a827ddfe71b3b4b05863935
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2020
ms.locfileid: "75762417"
---
# <a name="use-the-facebook-connector-for-power-bi-desktop"></a>Usare il connettore Facebook per Power BI Desktop
Il connettore Facebook in **Power BI Desktop** si basa sull'API Facebook Graph. e di conseguenza le funzionalità e la disponibilità potrebbero variare nel tempo.

È disponibile un'[esercitazione sul connettore Facebook per Power BI Desktop](desktop-tutorial-facebook-analytics.md).

Il 30 aprile 2015 è scaduta la versione 1.0 dell'API Graph di Facebook. Power BI usa l'API Graph in background per il connettore Facebook, che consente di connettersi ai dati e di analizzarli.

Le query create prima del 30 aprile 2015 potrebbero non funzionare più o restituire un volume di dati inferiore al precedente. Dal 30 aprile 2015 Power BI usa la versione 2.8 in tutte le chiamate all'API Facebook. Se la query è stata creata prima del 30 aprile 2015, e da allora non è più stata utilizzata, è probabile che si debba ripetere l'autenticazione per approvare il nuovo set di autorizzazioni richieste.

Anche se abbiamo tentato di rilasciare aggiornamenti in funzione di tutte le modifiche apportate, è possibile che le modifiche all'API incidano sui risultati delle query generate. In alcuni casi, alcune query potrebbero non essere più supportate. A causa di questa dipendenza non è possibile garantire i risultati delle query quando si usa questo connettore.

Altre informazioni sulla modifica dell'API Facebook sono disponibili [qui](https://developers.facebook.com/docs/apps/changelog#v2_0).

