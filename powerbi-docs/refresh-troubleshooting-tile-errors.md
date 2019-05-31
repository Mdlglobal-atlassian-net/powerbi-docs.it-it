---
title: Risoluzione degli errori del riquadro
description: Errori più comuni che possono essere rilevati durante un tentativo di aggiornamento di un riquadro in Power BI
author: mgblythe
manager: kfile
ms.reviewer: kayu
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: c1df7e6293db703922f37c3f28546bb296d1a46a
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051005"
---
# <a name="troubleshooting-tile-errors"></a>Risoluzione degli errori del riquadro
Di seguito sono elencati gli errori comuni che possono verificarsi nei riquadri e la relativa spiegazione.

> [!NOTE]
> Se si verifica un errore diverso da quelli elencati di seguito che causa problemi, è possibile richiedere ulteriore assistenza nel [sito della community](http://community.powerbi.com/) oppure creare un [ticket di supporto](https://powerbi.microsoft.com/support/).
> 
> 

## <a name="errors"></a>Errori
**Power BI ha riscontrato un errore imprevisto durante il caricamento del modello. Riprovare più tardi.**
oppure **Non è stato possibile recuperare il modello di dati. Contattare il proprietario del dashboard per verificare che le origini dati e il modello esistano e siano accessibili.**

L'accesso ai dati non è riuscito perché l'origine dati non era raggiungibile. Questo problema può verificarsi se l'origine dati è stata rimossa, rinominata, spostata, disconnessa o se le autorizzazioni sono state modificate. Verificare che l'origine si trovi ancora nel percorso a cui viene fatto riferimento e di avere le autorizzazioni necessarie per l'accesso. Se il problema persiste, l'origine potrebbe essere rallentata. Riprovare in un secondo momento, quando il carico sull'origine è minore. Se si tratta di un'origine locale, il proprietario dell'origine dati potrebbe riuscire a fornire altre informazioni.

**Non si è autorizzati a visualizzare questo riquadro o ad aprire la cartella di lavoro.**

Contattare il proprietario del dashboard per verificare che le origini dati e il modello esistano e siano accessibili all'account.

**Gli oggetti visivi sono stati disabilitati dall'amministratore.**

L'amministratore di Power BI ha disabilitato l'utilizzo di oggetti visivi personalizzati per l'organizzazione o il gruppo di sicurezza. Non sarà possibile usare oggetti visivi personalizzati da [Microsoft Marketplace](https://appsource.microsoft.com/en-us/marketplace/apps?page=1&product=power-bi-visuals) o importare oggetti visivi privati da un file. Sarà possibile usare solo il set di oggetti visivi già inserito nel pacchetto.


**Le forme dati devono contenere almeno un gruppo o un calcolo che esegua l'output dei dati. Contattare il proprietario del dashboard.**

Non ci sono dati da visualizzare perché la query è vuota. Provare ad aggiungere alcuni campi all'oggetto visivo dall'elenco di campi e ad aggiungere di nuovo l'oggetto.

**Non è possibile visualizzare i dati perché Power BI non può determinare la relazione tra uno o più campi.**

Si sta provando a usare due o più campi da tabelle non correlate. Rimuovere i campi non correlati dall'oggetto visivo e creare una relazione tra le tabelle. Dopo aver eseguito questa modifica, sarà possibile aggiungere di nuovo i campi all'oggetto visivo. Questa operazione può essere eseguita in Power BI Desktop o Power Pivot per Excel. [Altre informazioni](desktop-create-and-manage-relationships.md)

**I gruppi nell'asse primario e nell'asse secondario si sovrappongono. I gruppi nell'asse primario non possono avere le stesse chiavi dei gruppi nell'asse secondario.**

In genere, si tratta di un problema temporaneo che si verifica quando si spostano i gruppi dalle righe alle colonne. In questo caso, l'errore dovrebbe scomparire una volta spostati tutti i gruppi. Se il messaggio viene ancora visualizzato, provare a scambiare i campi tra righe e colonne o la legenda dell'asse oppure a rimuovere i campi dall'oggetto visivo.  

**L'elemento visivo ha superato il numero di risorse disponibili. Provare ad applicare un filtro per ridurre la quantità di dati visualizzati.**

L'oggetto visivo ha provato a eseguire query su una quantità di dati eccessiva per poter ottenere il risultato con le risorse disponibili. Provare a filtrare l'oggetto visivo per ridurre la quantità di dati nel risultato.

**Non è possibile identificare i campi seguenti: {0}. Aggiornare l'oggetto visivo con i campi esistenti nel set di dati.**

Il campo probabilmente è stato eliminato o rinominato. È possibile rimuovere il campo interrotto dall'oggetto visivo, aggiungere un campo diverso e aggiungerlo di nuovo.

**Non è stato possibile recuperare i dati per questo elemento visivo. Riprovare più tardi.**

In genere, si tratta di un problema temporaneo, Se il messaggio viene visualizzato di nuovo durante un tentativo successivo, contattare il supporto tecnico.

**I riquadri continuano a mostrare i dati non filtrati dopo l'abilitazione di single sign-on (SSO).**

Questa situazione può verificarsi se il set di dati sottostante è configurato per usare la modalità DirectQuery o una connessione dinamica ad Analysis Services tramite un gateway dati locale. In questo caso, i riquadri continuano a mostrare i dati non filtrati dopo l'abilitazione di SSO per l'origine dati fino a quando non al successivo aggiornamento della sezione è in scadenza. Al successivo aggiornamento della tessera, Power BI Usa l'accesso SSO in base alla configurazione e i riquadri visualizzati i dati filtrati in base alle identità dell'utente. 

Se si desidera visualizzare immediatamente i dati filtrati, è possibile forzare l'aggiornamento di un riquadro selezionando i puntini di sospensione (...) in alto a destra di un dashboard e selezionando **Aggiorna riquadri del dashboard**.

Il proprietario di un set di dati è anche possibile modificare la frequenza di aggiornamento del riquadro e impostarlo su 15 minuti per accelerare l'aggiornamento del riquadro. Selezionare l'icona a forma di ingranaggio in alto a destra del servizio Power BI, quindi selezionare **impostazioni**. Nel **le impostazioni** pagina, selezionare la **i set di dati** scheda. Espandere **aggiornamento pianificato della cache** e modificare **frequenza di aggiornamento**. Assicurarsi di che reimpostare la configurazione per la frequenza di aggiornamento originale dopo che Power BI ha eseguito l'aggiornamento del riquadro successivo.

> [!NOTE]
> Il **aggiornamento pianificato della cache** sezione è disponibile solo per i set di dati in modalità DirectQuery/LiveConnection. Set di dati in modalità di importazione non richiedono un aggiornamento del riquadro separati perché i riquadri vengono aggiornati automaticamente durante l'aggiornamento dati pianificato successivo.

## <a name="contact-support"></a>Contact support
Se il problema riscontrato persiste, [contattare il supporto tecnico](https://support.powerbi.com) per ulteriori verifiche.

## <a name="next-steps"></a>Passaggi successivi
[Risoluzione dei problemi del gateway dati locale](service-gateway-onprem-tshoot.md)  
[Risoluzione dei problemi relativi a Power BI Personal Gateway](service-admin-troubleshooting-power-bi-personal-gateway.md)  
Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

