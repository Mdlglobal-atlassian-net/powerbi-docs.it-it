---
title: Metriche di utilizzo per dashboard e report
description: Documentazione su come visualizzare le metriche di utilizzo per i dashboard e i report di Power BI. Misurare e massimizzare l'impatto con le metriche di utilizzo per gli autori di contenuti.
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/27/2017
ms.author: mihart
ms.openlocfilehash: 04709b76b8e3e464b5384fa2bf137cd79b0749a7
ms.sourcegitcommit: 7517c068db806f12bb0b953e9a1bd4249ca12da5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2018
---
# <a name="usage-metrics-for-dashboards-and-reports"></a>Metriche di utilizzo per dashboard e report
Se si creano dashboard e report, le metriche di utilizzo aiutano a comprenderne l'impatto. L'esecuzione di metriche di utilizzo per dashboard o report permette di scoprire come vengono usati questi elementi all'interno dell'organizzazione, cosa viene usato, chi usa che cosa e per quale motivo lo usa.  

> [!NOTE]
> Le metriche di utilizzo tengono traccia dei report incorporati in SharePoint Online. Tengono anche traccia dell'incorporamento di dashboard e report tramite il flusso di lavoro di tipo "le credenziali sono di proprietà dell'utente" e "le credenziali sono di proprietà dell'app". Le metriche di utilizzo non tengono traccia dell'incorporamento dei report tramite [Pubblica sul Web](service-publish-to-web.md).
> 
> 

Questi report sulle metriche di utilizzo sono di sola lettura. Tuttavia, è possibile personalizzare un report sulle metriche di utilizzo selezionando "Salva con nome". Questa operazione crea un nuovo set di dati e converte il report di sola lettura in un report Power BI modificabile con funzionalità complete. Il report personalizzato non solo contiene metriche per il dashboard o il report selezionato, ma consente anche di accedere alle metriche di utilizzo per tutti i dashboard o i report nell'area di lavoro selezionata, se si rimuove il filtro predefinito.

![](media/service-usage-metrics/power-bi-dashboard-usage-metrics-update-3.png)

## <a name="why-are-usage-metrics-important-to-me"></a>Perché le metriche di utilizzo sono importanti per me?
 Sapere come viene usato il contenuto consente di dimostrare l'impatto e assegnare priorità agli interventi. Le metriche di utilizzo possono mostrare che uno dei report viene utilizzato ogni giorno da un importante segmento dell'organizzazione e potrebbe mostrare che un dashboard creato dall'utente non viene affatto visualizzato. Questo tipo di commenti e suggerimenti è estremamente utile nel guidare gli interventi.

È possibile eseguire report sulle metriche di utilizzo solo nel servizio Power BI.  Tuttavia, se si salva un report sulle metriche di utilizzo o lo si aggiunge a un dashboard, è possibile aprire e interagire con questo report sui dispositivi mobili.

> **NOTA**: la funzionalità Metriche di utilizzo acquisisce le informazioni sull'utilizzo di tutti gli utenti, con account gratuito e Pro. Tuttavia, per eseguire ed accedere ai dati delle metriche di utilizzo è necessaria una licenza Pro.
> 
> 

## <a name="about-the-usage-metrics-report"></a>Informazioni sul report Metriche di utilizzo
Le metriche di utilizzo vengono offerte per i dashboard o i report presenti nell'area di lavoro selezionata. Per accedere ai dati delle metriche di utilizzo per un determinato dashboard o report, è necessario:    
•   Avere accesso in modifica al dashboard o al report specifico   
•   Avere una licenza Pro

Quando si seleziona **Metriche di utilizzo** o l'icona ![](media/service-usage-metrics/power-bi-usage-metrics-report-icon.png), Power BI genera un report predefinito con le metriche di utilizzo per tale contenuto relative agli ultimi 90 giorni.  L'aspetto del report è simile a quello dei tradizionali report di Power BI, ma è progettato per essere informale, non interattivo. È possibile suddividerlo in sezioni a seconda della modalità di accesso degli utenti finali, ossia a seconda del fatto che accedano tramite un'app Web o per dispositivi portatili, ecc. Man mano che i dashboard e i report si evolvono, si evolve anche il report sulle metriche di utilizzo, che viene aggiornato quotidianamente con i nuovi dati.  

Le metriche di utilizzo non vengono visualizzate in **Recenti**, **Aree di lavoro**, **Preferiti** o in altri elenchi di contenuti. Non possono essere aggiunte a un'app. Se si aggiunge un titolo di un rapporto sulle metriche di utilizzo a un dashboard, non è possibile aggiungere il dashboard a un pacchetto di app o contenuti.

Per esaminare in dettaglio i dati del report o creare report personali basati sul set di dati, usare **Salva con nome** (vedere [Salvare il report Metriche di utilizzo come un report Power BI con tutte le funzionalità)](#save-the-usage-metrics-report-as-a-full-featured-power-bi-report).

## <a name="open-a-usage-metrics-report-for-a-dashboard-or-report"></a>Aprire un report Metriche di utilizzo per un dashboard o report
1. Iniziare nell'area di lavoro che contiene il dashboard o report.
2. Dall'elenco del contenuto dell'area di lavoro o dallo stesso dashboard o report, selezionare l'icona di **Metriche di utilizzo**  ![](media/service-usage-metrics/power-bi-usage-metrics-report-icon.png).
   
    ![](media/service-usage-metrics/power-bi-run-usage-metrics-report.png)
   
    ![](media/service-usage-metrics/power-bi-run-usage-metrics-report2.png)
3. La prima volta che si esegue questa operazione, Power BI crea un report sulle metriche di utilizzo e avvisa l'utente appena è pronto.
   
    ![](media/service-usage-metrics/power-bi-usage-metrics-ready.png)    
4. Per aprire i risultati, selezionare **Visualizza metriche di utilizzo**.
   
    Le metriche di utilizzo possono essere un potente alleato quando si distribuiscono e si aggiornano dashboard e report Power BI. Come scegliere quali pagine del report è utile mantenere e quali eliminare? Dividere il report in sezioni per pagina per scoprirlo. Come determinare se è opportuno creare un layout mobile per il dashboard? Il report sulle metriche di utilizzo contiene informazioni sul numero di utenti che accedono al contenuto tramite le app per dispositivi mobili o il Web browser.
5. In alternativa, è possibile aggiungere visualizzazioni a un dashboard per poterle controllare più facilmente o condividerle con altri utenti.
   
   > **NOTA**: se si aggiunge un riquadro di un report sulle metriche di utilizzo a un dashboard, non è possibile aggiungere questo dashboard a un gruppo di app o contenuti.
   > 
   > 

<br><br>

## <a name="what-metrics-are-reported"></a>Quali metriche vengono inserite nel report?
| Metrica | Dashboard | Report | Descrizione |
| --- | --- | --- | --- |
| Filtro dei dati del metodo di distribuzione |sì |sì |Il modo in cui gli utenti hanno ottenuto l'accesso al contenuto. Sono disponibili 3 metodi: gli utenti possono accedere al dashboard o al report se sono membri di un'[area di lavoro appl.](service-the-new-power-bi-experience.md), consentendo la [condivisione del loro contenuto](service-share-dashboards.md) o installando un pacchetto/un'app di contenuto.  Si noti che le visualizzazioni tramite app sono conteggiate come "pacchetto di contenuto". |
| Filtro dei dati delle piattaforme |sì |sì |L'accesso al dashboard o al report è stato eseguito attraverso il servizio Power BI (PowerBI.com) o un dispositivo mobile? I dispositivi mobili includono tutte le app per iOS, Android e Windows. |
| Filtro dei dati pagine del report |no |sì |Se il report contiene più di una pagina filtrarlo in base alla pagina (o alle pagine) visualizzata. Se viene visualizzata un'opzione di elenco per "Vuoto", significa che la pagina del report è stata aggiunta di recente (entro 24 ore il nome effettivo della nuova pagina verrà visualizzato nell'elenco del filtro dei dati) e/o che le pagine del report sono state eliminate. "Vuoto" acquisisce questo tipo di situazioni. |
| Visualizzazioni al giorno |sì |sì |Numero totale delle visualizzazioni al giorno: per visualizzazione si intende il caricamento di una pagina del report o del dashboard da parte di un utente. |
| Visualizzatori unici al giorno |sì |sì |Numero di utenti *diversi* che hanno visualizzato il dashboard o il report (in base all'account utente AAD). |
| Visualizzazioni per utente |sì |sì |Numero di visualizzazioni negli ultimi 90 giorni, suddivise per i singoli utenti. |
| Condivisioni al giorno |sì |no |Numero di volte in cui il dashboard è stato condiviso con un altro utente o gruppo. |
| Visualizzazioni totali |sì |sì |Numero di visualizzazioni negli ultimi 90 giorni. |
| Visualizzatori totali |sì |sì |Numero di visualizzatori unici negli ultimi 90 giorni. |
| Condivisioni totali |sì |no |Numero di volte in cui il dashboard o il report è stato condiviso negli ultimi 90 giorni. |
| Totale nell'organizzazione |sì |sì |Conteggio di tutti i dashboard o report in tutta l'organizzazione che sono stati visualizzati almeno una volta negli ultimi 90 giorni.  Usato per calcolare la classificazione. |
| Classificazione: visualizzazioni totali |sì |sì |Per le visualizzazioni totali di tutti i dashboard o i report nell'organizzazione negli ultimi 90 giorni, dove si classifica questo dashboard o report. |
| Classificazione: condivisioni totali |sì |no |Per le condivisioni totali di tutti i dashboard nell'organizzazione negli ultimi 90 giorni, dove si classifica questo dashboard o report. |

### <a name="dashboard-usage-metrics-report"></a>Report Metriche di utilizzo del dashboard
![](media/service-usage-metrics/power-bi-dashboard-usage-metrics-update-3.png)

### <a name="report-usage-metrics-report"></a>Report Metriche di utilizzo del report
![](media/service-usage-metrics/power-bi-report-usage-metrics-update.png)

## <a name="save-the-usage-metrics-report-as-a-full-featured-power-bi-report-personalize"></a>Salvataggio del report Metriche di utilizzo come report Power BI con funzionalità complete (personalizzato)
Scegliere **Salva con nome** per convertire il report Metriche di utilizzo in un report di Power BI completo che può essere personalizzato e condiviso. Dopo aver creato una copia personalizzata, si avrà accesso completo al set di dati sottostante e sarà possibile personalizzare tutto il report sulle metriche di utilizzo in base alle proprie esigenze specifiche. È possibile anche usare Power BI Desktop per creare report sulle metriche di utilizzo personalizzati usando la funzionalità di [connessione dinamica al servizio Power BI](https://powerbi.microsoft.com/blog/connecting-to-datasets-in-the-power-bi-service-from-desktop).

In più, il set di dati sottostante include i dettagli di utilizzo per tutti i dashboard o report nell'area di lavoro. Ciò dà vita a tutta un'altra serie di possibilità. È possibile ad esempio creare un report che confronti tutti i dashboard nell'area di lavoro in base all'utilizzo. Oppure, è possibile creare un dashboard sulle metriche di utilizzo per l'app Power BI aggregando l'utilizzo di tutti i contenuti distribuiti all'interno dell'app.  Vedere la sezione [Remove the Page level filter (Rimuovere il filtro a livello di pagina) ](#remove-the-filter-to-see-all-the-usage-metrics-data-in-the-workspace)riportata di seguito.

### <a name="what-is-created-when-using-save-as"></a>Cosa viene creato quando si usa "Salva con nome"?
Quando Power BI crea il report con tutte le funzionalità, crea anche un nuovo set di dati **costituito da tutti i dashboard e report contenuti nell'area di lavoro corrente** a cui gli utenti hanno avuto accesso negli ultimi 90 giorni. Si supponga ad esempio di avere un'area di lavoro denominata "Sales" (Vendite) che contiene tre dashboard e due report, e che si crei un report sulle metriche di utilizzo nel dashboard "Northeast" (Nordest). Si supponga quindi di usare **Salva con nome** per personalizzarlo e convertirlo in un report con tutte le funzionalità. I set di dati per questo nuovo report contengono le metriche di utilizzo *non solo del dashboard denominato "Northeast" (Nordest)* ma anche di tutti e tre i dashboard nell'area di lavoro "Sales" (Vendite). Per impostazione predefinita, il report visualizzerà i dati per il dashboard "Northeast" (Nordest) e sarà necessario [rimuovere un filtro](#remove-the-filter-to-see-all-the-usage-metrics-data-in-the-workspace) (con un solo clic del mouse) per visualizzare i dati per tutti e tre i dashboard.

### <a name="create-a-copy-of-the-usage-report-using-save-as"></a>Creare una copia del report di utilizzo usando "Salva con nome"
Quando si crea una copia usando "Salva con nome" (copia personalizzata), Power BI converte il report pre-compilato di sola lettura in un report con tutte le funzionalità.  A prima vista non c'è alcuna differenza. Tuttavia, dopo questa operazione è possibile aprire il report nella visualizzazione di modifica, aggiungere nuove visualizzazioni, filtri e pagine, modificare o eliminare le visualizzazioni esistenti e molto altro ancora. Power BI crea anche un set di dati completamente nuovo che contiene le metriche di utilizzo per tutti i dashboard o i report presenti nell'area di lavoro specificata.

> **SUGGERIMENTO**: per consentire a Power BI di accedere alle metriche di utilizzo per tutti i dashboard o report nell'area di lavoro, [rimuovere il filtro a livello di livello di pagina](#remove-the-filter-to-see-all-the-usage-metrics-data-in-the-workspace).
> 
> 

1. Nel report sulle metriche di utilizzo pre-compilato, selezionare **File > Salva con nome**. Power BI converte il report Metriche di utilizzo in un report di Power BI completo. Questo report viene definito un report sulle metriche di utilizzo *personalizzato*.
   
    ![](media/service-usage-metrics/power-bi-save-as.png)
2. Aprire il report nella Visualizzazione di modifica e [interagire con esso come si farebbe con qualsiasi altro report di Power BI](service-interact-with-a-report-in-editing-view.md). Ad esempio, aggiungere nuove pagine e creare nuove visualizzazioni, aggiungere filtri, formattare i tipi di carattere e i colori, e così via.
   
    ![](media/service-usage-metrics/power-vi-editing-view.png)
3. In alternativa, aprire il nuovo set di dati e creare un nuovo report.
   
    ![](media/service-usage-metrics/power-bi-new-dataset.png)
4. Il nuovo report viene salvato nell'area di lavoro corrente e anche aggiunto all'elenco contenuto **Recenti**.
   
    ![](media/service-usage-metrics/power-bi-new-report.png)

### <a name="remove-the-filter-to-see-all-the-usage-metrics-data-in-the-workspace"></a>Rimuovere il filtro per visualizzare tutti i dati sulle metriche di utilizzo nell'area di lavoro.
Per visualizzare le metriche di tutti i dashboard o di tutti i report nell'area di lavoro, è necessario rimuovere un filtro. Per impostazione predefinita, il report personalizzato viene filtrato per visualizzare le metriche solo per il dashboard o report usato per la creazione.

Ad esempio, se è stato usato il dashboard denominato "European sales" (Vendite europee) per creare il nuovo report personalizzato, verranno visualizzati solo i dati di utilizzo del dashboard "European sales" (Vendite europee). Per rimuovere il filtro e abilitare i dati di tutti i dashboard in quell'area di lavoro:

1. Aprire il report personalizzato nella visualizzazione di modifica.
   
    ![](media/service-usage-metrics/power-bi-editing-view.png)
2. Nel riquadro Filtri, ricercare il bucket **Filtri a livello di report** e rimuovere il filtro selezionando la "x".
   
    ![](media/service-usage-metrics/power-bi-report-level-filter2.png)
   
    A questo punto il report personalizzato visualizza le metriche per tutta l'area di lavoro.

## <a name="admin-controls-for-usage-metrics---for-power-bi-administrators"></a>Comandi dell'amministratore per le metriche di utilizzo - Per gli amministratori di Power BI
I report sulle metriche di utilizzo sono una funzionalità che l'amministratore di Power BI o Office 365 può attivare o disattivare. Gli amministratori hanno un controllo granulare sugli utenti autorizzati ad accedere alle metriche di utilizzo. L'accesso alle metriche è attivato per impostazione predefinita per tutti gli utenti dell'organizzazione.

1. Aprire il Portale di amministrazione selezionando l'icona dell'ingranaggio nell'angolo in alto a destra del servizio Power BI e scegliendo **Portale di amministrazione**.
   
    ![](media/service-usage-metrics/power-bi-admin-portal-new.png)
2. Dal portale di amministrazione, selezionare **Impostazioni tenant** e scegliere **Metriche di utilizzo per i creatori di contenuti**.
   
    ![](media/service-usage-metrics/power-bi-usage-settings.png)
3. Abilitare (o disabilitare) le metriche di utilizzo e selezionare **Applica**.
   
    ![](media/service-usage-metrics/power-bi-tenant-settings-updated.png)

Quando disabilitano le metriche di utilizzo per l'intera organizzazione, gli amministratori possono usare l'opzione **Elimina tutto il contenuto della metrica di utilizzo esistente** per eliminare tutti i report esistenti e i riquadri del dashboard creati usando i report e i set di dati delle metriche di utilizzo. Questa opzione rimuove completamente l'accesso ai dati delle metriche di utilizzo per tutti gli utenti dell'organizzazione che le usano. Occorre prestare attenzione, perché l'eliminazione del contenuto delle metriche di utilizzo è irreversibile.

## <a name="considerations-and-limitations"></a>Considerazioni e limitazioni
D:   Non è possibile eseguire le metriche di utilizzo per un dashboard o un report.    
R:    È possibile visualizzare solo le metriche di utilizzo di cui si è proprietari o che si è autorizzati a modificare.

D: Le metriche di utilizzo acquisiscono viste da dashboard e report incorporati?     
R:    Le metriche di utilizzo attualmente non supportano l'acquisizione dell'utilizzo per dashboard e report incorporati, inclusi il flusso [i dati sono di proprietà dell'utente](developer/integrate-report.md), il flusso [i dati sono di proprietà dell'app](developer/embed-sample-for-customers.md) e il flusso [pubblicazione sul Web](service-publish-to-web.md). In questi casi, è consigliabile usare le piattaforme di analisi Web esistenti per tenere traccia dell'utilizzo dell'app o del portale di hosting.

D:    Non è possibile eseguire le metriche di utilizzo in nessun contenuto.    
R1:   Gli amministratori possono disabilitare questa funzione per la loro organizzazione.  Contattare l'amministratore per verificare se è questo il caso.    
R2:    Le Metriche di utilizzo sono una funzionalità di Power BI Pro.

D:    I dati non sembrano essere aggiornati. Ad esempio, i metodi di distribuzione non vengono visualizzati, mancano le pagine del report e così via.   
R:    L'aggiornamento dei dati può richiedere fino a 24 ore.

D:    Ci sono quattro report nell'area di lavoro, ma il report sulle metriche di utilizzo ne visualizza solo 3.    
R:    Il report sulle metriche di utilizzo include solo i report (o i dashboard) a cui gli utenti hanno avuto accesso negli ultimi 90 giorni.  Se un report (o dashboard) non viene visualizzato, è probabile che non sia stato usato per oltre 90 giorni.

## <a name="next-steps"></a>Passaggi successivi
[Aggiungere un dashboard ai Preferiti](service-dashboard-favorite.md)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

