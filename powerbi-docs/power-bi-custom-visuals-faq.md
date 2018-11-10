---
title: Domande frequenti sugli oggetti visivi personalizzati di Power BI
description: Esplorare un elenco di domande frequenti e risposte relative agli oggetti visivi personalizzati di Power BI
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 10/29/2018
LocalizationGroup: Visualizations
ms.openlocfilehash: 064d32944f52f6e391d4a7ec4df41ecbf09b7e3f
ms.sourcegitcommit: 02f918a4f27625b6f4e47473193ebc8219db40e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2018
ms.locfileid: "51223077"
---
# <a name="frequently-asked-questions-about-power-bi-custom-visuals"></a>Domande frequenti sugli oggetti visivi personalizzati di Power BI

## <a name="organizational-custom-visuals"></a>Oggetti visivi personalizzati dell'organizzazione

**In quale modo l'amministratore può gestire gli oggetti visivi personalizzati dell'organizzazione?**

Nel portale di amministrazione, nella scheda "Oggetti visivi dell'organizzazione" l'amministratore può visualizzare e [gestire tutti oggetti visivi personalizzati dell'organizzazione](https://docs.microsoft.com/power-bi/service-admin-portal#organization-visuals): aggiungere, disabilitare, abilitare ed eliminare.
Non è più necessario condividere questi oggetti visivi tramite messaggi di posta elettronica o cartelle condivise. Dopo la distribuzione nel repository dell'organizzazione, gli utenti dell'organizzazione possono facilmente individuarli e importarli nei loro report direttamente da Power BI Desktop o dal servizio Power BI. Gli oggetti visivi personalizzati dell'organizzazione sono disponibili dall'archivio predefinito (nella versione desktop e nel servizio) nella scheda "ORGANIZZAZIONE PERSONALE". Quando l'amministratore carica una nuova versione di un oggetto visivo personalizzato dell'organizzazione, chiunque nell'organizzazione ottiene la stessa versione aggiornata. Gli autori di report non devono eliminare l'oggetto visivo nei report per ottenere la nuova versione di questi oggetti visivi, perché tutti i report con questi oggetti visivi vengono aggiornati automaticamente. Il meccanismo di aggiornamento è simile per gli oggetti visivi del marketplace.

**Se un amministratore carica un oggetto visivo personalizzato dal marketplace pubblico nell'archivio dell'organizzazione, viene aggiornato automaticamente quando un fornitore aggiorna l'oggetto visivo nel marketplace pubblico?**

No, non è disponibile l'aggiornamento automatico dal marketplace pubblico.
È responsabilità dell'amministratore aggiornare la versione degli oggetti visivi personalizzati se lo desidera.

**È possibile disabilitare l'archivio dell'organizzazione?**

No, gli utenti vedono sempre la scheda "ORGANIZZAZIONE PERSONALE" in Power BI Desktop e nel servizio Power BI. L'amministratore può disabilitare o eliminare tutti gli oggetti visivi personalizzati dell'organizzazione dal portale di amministrazione e l'archivio dell'organizzazione risulterà vuoto.
  
**Se l'amministratore disabilita gli oggetti visivi personalizzati dal portale di amministrazione (impostazioni del tenant), gli utenti avranno ancora accesso agli oggetti visivi personalizzati dell'organizzazione?**

Sì, se l'amministratore disabilita gli oggetti visivi personalizzati dal portale di amministrazione, tale operazione non influisce sull'archivio dell'organizzazione. Alcune organizzazioni disabilitano gli oggetti visivi personalizzati e abilitano solo quelli selezionati manualmente, importati e caricati dall'amministratore di Power BI nell'archivio dell'organizzazione. La disabilitazione degli oggetti visivi personalizzati dal portale di amministrazione non è disponibile in Power BI Desktop. Gli utenti desktop possono essere ancora in grado di aggiungere e usare oggetti visivi personalizzati dal marketplace pubblico nei propri report. Tuttavia, tali oggetti visivi personalizzati pubblici non vengono più inclusi nel rendering dopo la pubblicazione nel servizio Power BI e generano un errore appropriato. Quando si usa il servizio Power BI, non è possibile importare gli oggetti visivi personalizzati dal marketplace pubblico. È possibile importare solo gli oggetti visivi dall'archivio dell'organizzazione perché l'impostazione per gli oggetti visivi personalizzati nel portale di amministrazione è disponibile nel servizio Power BI.

**Per quale motivo l'archivio dell'organizzazione e gli oggetti visivi personalizzati dell'organizzazione rappresentano un valida soluzione aziendale?**

* Tutti gli utenti ottengono la stessa versione degli oggetti visivi, controllata dall'amministratore di Power BI. Quando l'amministratore aggiorna la versione dell'oggetto visivo nel portale di amministrazione, tutti gli utenti nell'organizzazione di ottengono automaticamente la versione aggiornata.

* Non è più necessario condividere i file degli oggetti visivi tramite posta elettronica o cartelle condivise. Un'unica posizione visibile per tutti i membri connessi.

* Sicurezza e facilità di supporto. Le nuove versioni degli oggetti visivi personalizzati dell'organizzazione vengono aggiornate automaticamente in tutti i report, come per gli oggetti visivi del marketplace.

* Gli utenti dell'organizzazione che usano gli oggetti visivi personalizzati dell'organizzazione devono essere connessi per poter visualizzare e usare gli oggetti visivi dell'organizzazione personalizzati e ciò rappresenta una misura di sicurezza per l'organizzazione.

* Gli amministratori possono controllare quali oggetti visivi personalizzati sono disponibili nell'organizzazione.

* Gli amministratori possono abilitare o disabilitare gli oggetti visivi per attività di test dal portale di amministrazione. Maggiore sicurezza perché questi oggetti visivi saranno consentiti solo per i membri dell'organizzazione.

## <a name="certified-custom-visuals"></a>Oggetti visivi personalizzati certificati

**Che cosa sono gli oggetti visivi personalizzati certificati?**

Gli oggetti visivi personalizzati certificati sono gli oggetti visivi nel [marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) che soddisfano determinati requisiti del codice e di test [specificati](power-bi-custom-visuals-certified.md) dal team di Power BI.  I test eseguiti sono progettati per controllare che l'oggetto visivo non acceda a servizi o risorse esterne. Microsoft non è tuttavia l'autore di oggetti visivi personalizzati di terze parti e si consiglia ai clienti di contattare l'autore direttamente per verificare la funzionalità di tali oggetti visivi.

## <a name="next-steps"></a>Passaggi successivi

Per informazioni sulla risoluzione dei problemi, consultare la pagina [Troubleshooting your Power BI custom visuals](power-bi-custom-visuals-troubleshoot.md) (Risoluzione dei problemi degli oggetti visivi personalizzati di Power BI).
