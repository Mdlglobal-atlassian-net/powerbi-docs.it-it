---
title: Risoluzione degli errori del riquadro
description: Errori più comuni che possono essere rilevati durante un tentativo di aggiornamento di un riquadro
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: powerbi
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: f7d89fd6d6969c584fc016761bde6e9eb3a76028
ms.sourcegitcommit: f679c05d029ad0765976d530effde744eac23af5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33083530"
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

L'accesso ai dati non è riuscito perché l'origine dati non era raggiungibile. Questo errore può verificarsi se l'origine dati è stata rimossa, rinominata, spostata, disconnessa o se le autorizzazioni sono state modificate. Verificare che l'origine si trovi ancora nel percorso a cui viene fatto riferimento e di avere le autorizzazioni necessarie per l'accesso. Se il problema persiste, l'origine potrebbe essere rallentata. Riprovare in un secondo momento, quando il carico sull'origine è minore. Se si tratta di un'origine locale, il proprietario dell'origine dati potrebbe riuscire a fornire altre informazioni.

**Non si è autorizzati a visualizzare questo riquadro o ad aprire la cartella di lavoro.**

Contattare il proprietario del dashboard per verificare che le origini dati e il modello esistano e siano accessibili all’account.

**Le forme dati devono contenere almeno un gruppo o un calcolo che esegua l'output dei dati. Contattare il proprietario del dashboard.**

Non ci sono dati da visualizzare perché la query è vuota. Provare ad aggiungere alcuni campi all'oggetto visivo dall'elenco di campi e ad aggiungere di nuovo l'oggetto.

**Non è possibile visualizzare i dati perché Power BI non può determinare la relazione tra uno o più campi.**

Si sta provando a usare due o più campi da tabelle non correlate. Rimuovere i campi non correlati dall'oggetto visivo e creare una relazione tra le tabelle. Dopo aver eseguito questa procedura, sarà possibile aggiungere di nuovo i campi all'oggetto visivo. Questa operazione può essere eseguita in Power BI Desktop o Power Pivot per Excel. [Altre informazioni](desktop-create-and-manage-relationships.md)

**I gruppi nell'asse primario e nell'asse secondario si sovrappongono. I gruppi nell'asse primario non possono avere le stesse chiavi dei gruppi nell'asse secondario.**

In genere, si tratta di un problema temporaneo, che si verifica quando si spostano i gruppi dalle righe alle colonne. In questo caso, l'errore dovrebbe scomparire una volta spostati tutti i gruppi. Se il messaggio viene ancora visualizzato, provare a scambiare i campi tra righe e colonne o la legenda dell'asse oppure a rimuovere i campi dall'oggetto visivo.  

**L'elemento visivo ha superato il numero di risorse disponibili. Provare ad applicare un filtro per ridurre la quantità di dati visualizzati.**

L'oggetto visivo ha provato a eseguire query su una quantità di dati eccessiva per poter ottenere il risultato con le risorse disponibili. Provare a filtrare l'oggetto visivo per ridurre la quantità di dati nel risultato.

**Non è possibile identificare i campi seguenti: {0}. Aggiornare l'oggetto visivo con i campi esistenti nel set di dati.**

Il campo probabilmente è stato eliminato o rinominato. È possibile rimuovere il campo interrotto dall'oggetto visivo, aggiungere un campo diverso e aggiungerlo di nuovo.

**Non è stato possibile recuperare i dati per questo elemento visivo. Riprovare più tardi.**

In genere, si tratta di un problema temporaneo. Se il messaggio viene visualizzato di nuovo durante un tentativo successivo, contattare il supporto tecnico.

## <a name="contact-support"></a>Contattare il supporto tecnico
Se il problema riscontrato persiste, [contattare il supporto tecnico](https://support.powerbi.com) per ulteriori verifiche.

## <a name="next-steps"></a>Passaggi successivi
[Risoluzione dei problemi del gateway dati locale](service-gateway-onprem-tshoot.md)  
[Risoluzione dei problemi relativi a Power BI Personal Gateway](service-admin-troubleshooting-power-bi-personal-gateway.md)  
Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

