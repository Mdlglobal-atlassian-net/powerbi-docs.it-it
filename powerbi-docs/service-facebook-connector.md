---
title: 'Servizio di terze parti: Connettore Facebook per Power BI Desktop'
description: 'Servizio di terze parti: Connettore Facebook per Power BI Desktop'
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: a8b37606b602a24aa4a0995e138a52a86e0f945c
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54295614"
---
# <a name="facebook-connector-for-power-bi-desktop"></a>Connettore Facebook per Power BI Desktop
Il connettore Facebook in **Power BI Desktop** si basa sull'API Facebook Graph. Le funzionalità e la disponibilità possono quindi variare nel tempo.

È disponibile un'[esercitazione sul connettore Facebook per Power BI Desktop](desktop-tutorial-facebook-analytics.md).

Il 30 aprile<sup> </sup>2015 è scaduta la versione 1.0 dell'API Graph di Facebook  Power BI usa l'API Graph in background per il connettore Facebook, che consente di connettersi ai dati e di analizzarli.

Le query create prima del 30<sup> </sup>aprile 2015 potrebbero non funzionare più o restituire un minor numero di dati. Dal 30<sup> </sup>aprile 2015, Power BI usa la versione 2.8 in tutte le chiamate all'API Facebook. Se la query è stata creata prima del 30 aprile 2015, e da allora non è più stata utilizzata, è probabile che si debba ripetere l'autenticazione per approvare il nuovo set di autorizzazioni richieste.

Anche se abbiamo tentato di rilasciare aggiornamenti in funzione di tutte le modifiche apportate, è possibile che le modifiche all'API incidano sui risultati delle query generate. In alcuni casi, alcune query potrebbero non essere più supportate. A causa di questa dipendenza non è possibile garantire i risultati delle query quando si usa questo connettore.

Altre informazioni sulla modifica dell'API Facebook sono disponibili [qui](https://developers.facebook.com/docs/apps/changelog#v2_0).

