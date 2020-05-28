---
title: Riepiloghi degli aggiornamenti per Power BI
description: Informazioni su come usare i riepiloghi di aggiornamento in Power BI
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/18/2020
ms.author: davidi
LocalizationGroup: Data refresh
ms.openlocfilehash: 854b3500fa985a464130e505a889bb9981cd4151
ms.sourcegitcommit: 250242fd6346b60b0eda7a314944363c0bacaca8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/20/2020
ms.locfileid: "83694390"
---
# <a name="refresh-summaries-for-power-bi"></a>Riepiloghi degli aggiornamenti per Power BI

La pagina dei **riepiloghi degli aggiornamenti** di Power BI, disponibile nel portale di amministrazione di Power BI, offre controllo e informazioni cognitive dettagliate su pianificazioni degli aggiornamenti, capacità e potenziali sovrapposizioni delle pianificazioni degli aggiornamenti. È possibile usare la pagina dei riepiloghi degli aggiornamenti per determinare se è necessario modificare le pianificazioni degli aggiornamenti, ottenere i codici errore associati ai problemi di aggiornamento e gestire correttamente la pianificazione dell'aggiornamento dei dati. 

La pagina riepiloghi degli aggiornamenti presenta due visualizzazioni:

* **Cronologia**: visualizza la cronologia del riepilogo degli aggiornamenti per le capacità di Power BI Premium di cui si è amministratore.

* **Pianificazione**: mostra la visualizzazione della pianificazione per l'aggiornamento pianificato, che può anche rivelare eventuali problemi con le fasce orarie per cui è stata superata la sottoscrizione.

È anche possibile esportare informazioni su un evento di aggiornamento in un file CSV, che può fornire informazioni significative e informazioni cognitive dettagliate sugli eventi o sugli errori di aggiornamento che possono influire sulle prestazioni o sul completamento degli eventi di aggiornamento pianificati.

Le sezioni seguenti esaminano ognuna di queste visualizzazioni. 

## <a name="refresh-history"></a>Cronologia aggiornamenti

È possibile selezionare la visualizzazione **Cronologia** facendo clic su **Cronologia** nella pagina dei riepiloghi degli aggiornamenti.

![Visualizzazione Cronologia nei riepiloghi degli aggiornamenti](media/refresh-summaries/refresh-summaries-01a.jpg)

La cronologia offre una panoramica dei risultati degli aggiornamenti pianificati di recente nelle capacità per cui si ha il privilegio di amministratore. È possibile ordinare la visualizzazione in base a qualsiasi colonna facendo clic sulla colonna. È possibile scegliere di ordinare la visualizzazione in base alla colonna selezionata in ordine crescente, decrescente o usando filtri di testo.

![Ordinare la visualizzazione Cronologia](media/refresh-summaries/refresh-summaries-01b.jpg)

Nella visualizzazione Cronologia i dati associati a un determinato aggiornamento sono basati su un massimo di 60 record più recenti per ogni aggiornamento pianificato.

È anche possibile esportare informazioni per qualsiasi aggiornamento pianificato in un file CSV, che include informazioni dettagliate, tra cui i messaggi di errore per ogni evento di aggiornamento. L'esportazione in un file CSV consente di ordinare il file in base a una delle colonne, cercare parole, ordinare in base ai codici errore o ai proprietari e così via. L'immagine seguente mostra un esempio di file CSV esportato. 

![Esportare le informazioni relative a un aggiornamento](media/refresh-summaries/refresh-summaries-05.jpg)

Con le informazioni contenute nel file esportato, è possibile esaminare la capacità, la durata e gli eventuali messaggi di errore registrati per l'istanza dell'aggiornamento. 


## <a name="refresh-schedule"></a>Pianificare gli aggiornamenti

È possibile selezionare la visualizzazione **Pianificazione** facendo clic su **Pianificazione** nei riepiloghi degli aggiornamenti. La visualizzazione Pianificazione visualizza le informazioni sulla pianificazione della settimana, suddivisa in fasce orarie di 30 minuti. 

![Visualizzazione Pianificazione](media/refresh-summaries/refresh-summaries-02a.jpg)

La visualizzazione Pianificazione è molto utile per determinare se gli eventi di aggiornamento pianificati sono correttamente distanziati nel tempo, consentendo il completamento di tutti gli aggiornamenti senza sovrapposizioni, o se sono stati pianificati eventi di aggiornamento che richiedono troppo tempo e creano conflitti di risorse. Se si riscontrano tali conflitti di risorse, è necessario modificare le pianificazioni degli aggiornamenti per evitare i conflitti o le sovrapposizioni, in modo che gli aggiornamenti pianificati possano essere completati correttamente. 

![Visualizzazione Pianificazione](media/refresh-summaries/refresh-summaries-02.jpg)

La colonna *Periodo di aggiornamento prenotato (minuti)* è un calcolo della media di un massimo di 60 record per ogni set di dati associato. Il valore numerico per ogni fascia oraria di 30 minuti corrisponde alla somma dei minuti calcolata per tutti gli aggiornamenti pianificati che devono iniziare in una determinata fascia oraria **e** degli aggiornamenti pianificati impostati per iniziare nella fascia oraria *precedente*, ma la cui durata media si estende alla fascia oraria selezionata.

È possibile selezionare una fascia oraria e quindi selezionare il pulsante dei **dettagli** associato per visualizzare gli eventi di aggiornamento pianificati che contribuiscono al periodo di aggiornamento prenotato, i proprietari e il tempo necessario per il completamento.

L'esempio seguente ne illustra il funzionamento. La finestra di dialogo seguente viene visualizzata quando si seleziona la fascia oraria delle 20:30 della domenica e si fa clic su **dettagli**.

![Visualizzazione Pianificazione](media/refresh-summaries/refresh-summaries-04.jpg)

In questa fascia oraria si verificano tre eventi di aggiornamento pianificati. 

Gli aggiornamenti pianificati 1 e 3 sono entrambi pianificati per questa fascia oraria delle 20:30, come si può determinare esaminando il valore nella colonna **Fascia oraria pianificata**. Le durate medie sono rispettivamente di 4:39 e sei secondi (0:06). Fino a questo punto non si riscontrano problemi.

L'aggiornamento 2 è tuttavia pianificato per la fascia oraria delle 20:00, ma poiché il completamento richiede una media di oltre 48 minuti (come indicato nella colonna **Durata media**), tale evento di aggiornamento si estende alla successiva fascia oraria da 30 minuti. 

Questo costituisce un problema. In questo caso, l'amministratore deve contattare i proprietari dell'istanza di aggiornamento pianificato e suggerire di trovare una fascia oraria diversa per l'aggiornamento pianificato o di ripianificare gli altri aggiornamenti in modo da evitare sovrapposizioni oppure trovare altre soluzioni per evitare tale sovrapposizione. 


## <a name="next-steps"></a>Passaggi successivi

- [Aggiornamento dei dati in Power BI](refresh-data.md)  
- [Power BI Gateway - Personale](service-gateway-personal-mode.md)  
- [Gateway dati locale (modalità personale)](service-gateway-onprem.md)  
- [Risoluzione dei problemi del gateway dati locale](service-gateway-onprem-tshoot.md)  
- [Risoluzione dei problemi di Gateway di Power BI - Personale](service-admin-troubleshooting-power-bi-personal-gateway.md)  

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)