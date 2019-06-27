---
title: Risoluzione del problema dei valori annidati restituiti come testo nel servizio Power BI
description: Informazioni su come correggere i valori annidati che vengono convertiti in una stringa quando si usano impostazioni della privacy dell'origine dati non corrette
author: cpopell
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 6/4/2019
ms.author: gepopell
LocalizationGroup: Reports
ms.openlocfilehash: e30a79796fd4d5538406a85a3297a23b2c09a61a
ms.sourcegitcommit: 81ba3572531cbe95ea0b887b94e91f94050f3129
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2019
ms.locfileid: "66751410"
---
# <a name="troubleshooting-nested-values-returned-as-text-in-power-bi-service"></a>Risoluzione del problema dei valori annidati restituiti come testo nel servizio Power BI

## <a name="cause"></a>Causa

In passato si sono verificati casi in cui l'aggiornamento di un report di Power BI è stato eseguito correttamente nel Desktop, ma non è riuscito nel servizio Power BI e ha generato un errore, ad esempio "Non è possibile convertire il valore"[Table]"nel tipo Table". Una delle cause di questo errore è che quando il firewall di privacy dei dati (collegamento qui?) memorizza nel buffer un'origine dati, i valori annidati non scalari, come ad esempio tabelle, record, elenchi e funzioni, vengono convertiti automaticamente in valori di testo (ad esempio "[Table]" o "[Record]").

Ora che il servizio Power BI supporta l'impostazione dei livelli di privacy (o la disattivazione completa del firewall), tali errori possono essere evitati [configurando le impostazioni sulla privacy dell'origine dati](https://powerbi.microsoft.com/en-us/blog/privacy-levels-for-cloud-data-sources/) nel servizio Power BI in modo che non siano private.

A partire dalla versione di Power BI di giugno, quando il firewall memorizza nel buffer tabelle,record,elenchi e altri oggetti annidati, invece di convertire tali valori in testo, genera l'errore seguente: 

`We cannot return a value of type Table in this context`

## <a name="effect-on-loadrefresh"></a>Effetto su caricamento/aggiornamento

Anche se questa modifica è motivata dalla memorizzare nel buffer del firewall, ha degli effetti anche su caricamento e aggiornamento. Per risolvere il problema del comportamento di memorizzazione nel buffer del firewall, è stato necessario anche modificare il comportamento del caricamento di tabelle, record e altri oggetti annidati nel modello di Power BI e nel modello di dati di Excel in Power Query per Excel. In precedenza le tabelle, i record e gli altri oggetti annidati sarebbero stati caricati come valori di testo (ad esempio "[Table]" o "[Record]"). Ora vengono trattati come errori che producono un valore Null nella tabella caricata e un incremento del numero di errori nei risultati di caricamento.

Poiché questi errori si verificano solo durante il caricamento/aggiornamento, non vengono visualizzati nell'Editor di Power Query.

### <a name="before"></a>Prima

- Caricamento/aggiornamento senza errori
- Tabella caricata contenente "[Table]", "[Record]", e così via.
 

### <a name="after"></a>Dopo

- Caricamento/aggiornamento con errori
- Tabella caricata contenente valori NULL, invece di "[Table]", "[Record]" e così via.
 

## <a name="resolution"></a>Soluzione

Se si sta caricando una colonna che contiene valori non scalari, come ad esempio tabelle, elenchi, record e così via,
è possibile eliminare gli errori rimuovendo la colonna.
Se non è possibile rimuovere la colonna, dovrebbe essere possibile replicare il comportamento precedente aggiungendo una colonna personalizzata e usando una logica come quella dell'esempio seguente:

`if [MyColumn] is table then "[Table]" else if [MyColumn] is record then "[Record]" else if [MyColumn] is list then "[List]" else if [MyColumn] is function then "[Function]" else [MyColumn]`

Se il problema si ripresenta in Power BI Desktop se si impostano tutte le impostazioni di privacy dell'origine dati in modo che siano private,
l'errore dovrebbe essere risolvibile [configurando le impostazioni sulla privacy dell'origine dati](https://powerbi.microsoft.com/en-us/blog/privacy-levels-for-cloud-data-sources/) nel servizio Power BI in modo che non siano private.
