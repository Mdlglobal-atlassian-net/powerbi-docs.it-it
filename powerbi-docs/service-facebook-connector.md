---
title: 'Servizio di terze parti: Connettore Facebook per Power BI Desktop'
description: 'Servizio di terze parti: Connettore Facebook per Power BI Desktop'
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 6b02717c49a1207dfec39ebb1529e7e9b222fa62
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65512866"
---
# <a name="facebook-connector-for-power-bi-desktop"></a>Connettore Facebook per Power BI Desktop
Il connettore Facebook in **Power BI Desktop** si basa sull'API Facebook Graph. Le funzionalità e la disponibilità possono quindi variare nel tempo.

È disponibile un'[esercitazione sul connettore Facebook per Power BI Desktop](desktop-tutorial-facebook-analytics.md).

Facebook scaduta la versione 1.0 dell'API Graph aprile 2015 30. Power BI usa l'API Graph in background per il connettore Facebook, che consente di connettersi ai dati e di analizzarli.

Le query create prima del mese di aprile 2015 30 potrebbero non funzionare più o restituire meno dati. Dopo il 30 aprile 2015 Power BI Usa la versione 2.8 in tutte le chiamate all'API Facebook. Se la query è stata creata prima del 30 aprile 2015, e da allora non è più stata utilizzata, è probabile che si debba ripetere l'autenticazione per approvare il nuovo set di autorizzazioni richieste.

Anche se abbiamo tentato di rilasciare aggiornamenti in funzione di tutte le modifiche apportate, è possibile che le modifiche all'API incidano sui risultati delle query generate. In alcuni casi, alcune query potrebbero non essere più supportate. A causa di questa dipendenza, è possibile garantire i risultati delle query quando si usa questo connettore.

Altre informazioni sulla modifica dell'API Facebook sono disponibili [qui](https://developers.facebook.com/docs/apps/changelog#v2_0).

