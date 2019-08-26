---
title: Creare e pubblicare un pacchetto di contenuto aziendale - Power BI
description: In questa esercitazione è possibile creare un pacchetto di contenuto aziendale, limitare l'accesso a un gruppo specifico e pubblicare il pacchetto nella libreria di pacchetti di contenuto dell'organizzazione in Power BI.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/06/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 8d48214cffcc17da9c105f7277b721c03946d5c2
ms.sourcegitcommit: 0e50ebfa8762e19286566432870ef16d242ac78f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2019
ms.locfileid: "68961804"
---
# <a name="tutorial-create-and-publish-a-power-bi-organizational-content-pack"></a>Esercitazione: Creare e pubblicare un pacchetto di contenuto aziendale di Power BI

In questa esercitazione è possibile creare un pacchetto di contenuto aziendale, concedere l'accesso a un gruppo specifico e pubblicare il pacchetto nella libreria di pacchetti di contenuto dell'organizzazione in Power BI.

La creazione di pacchetti di contenuto è diversa dalla condivisione di dashboard o dalla collaborazione negli stessi in un gruppo. Per scegliere l'opzione migliore in base alla situazione specifica, vedere [Modalità per la condivisione del lavoro in Power BI](service-how-to-collaborate-distribute-dashboards-reports.md).

Per creare un pacchetto di contenuto aziendale è necessario che l'utente e i colleghi dispongano di un [account di Power BI Pro](https://powerbi.microsoft.com/pricing).

> [!NOTE]
> Non è possibile creare o installare pacchetti di contenuto aziendali nell'anteprima delle nuove esperienze delle aree di lavoro. Se non si è ancora iniziato, questo è un buon momento per aggiornare i pacchetti di contenuto per le app. [Altre informazioni sulla nuova esperienza dell'area di lavoro](service-create-the-new-workspaces.md).

## <a name="create-and-publish-a-content-pack"></a>Creare e pubblicare un pacchetto di contenuto

Si immagini di essere il responsabile del rilascio presso Contoso e di dover predisporre tutto quanto necessario per il lancio di un nuovo prodotto.  Si è creato un dashboard con i report che si vuole condividere. Anche altri dipendenti che gestiscono il lancio potrebbero trovarli utili. Si immagini di voler creare pacchetti di dashboard e report come soluzione a uso dei colleghi.

Per iniziare, Nel [servizio Power BI](https://powerbi.com) passare all'**Area di lavoro personale**. Passare quindi a **Recupera dati** > **Esempi** > **Esempio di analisi delle opportunità** > **Connetti** per ottenere una copia personale.

1. Nel riquadro di spostamento a sinistra selezionare **Aree di lavoro** > **Area di lavoro personale**.

1. Nella barra di spostamento superiore selezionare l'icona dell'ingranaggio ![Screenshot dell'icona dell'ingranaggio](media/service-organizational-content-pack-create-and-publish/cog.png) > **Crea pacchetto di contenuto**.

   ![Screenshot dell'interfaccia utente con l'icona dell'ingranaggio e l'opzione Crea pacchetto di contenuto evidenziate.](media/service-organizational-content-pack-create-and-publish/pbi_create_contpk.png)

1. Nella finestra **Crea pacchetto di contenuto** inserire le informazioni seguenti.  

   Tenere presente che la libreria di pacchetti di contenuto dell'organizzazione potrebbe riempirsi rapidamente. La libreria può arrivare a includere centinaia di pacchetti di contenuto pubblicati per l'organizzazione o per i gruppi. Dedicare tempo alla scelta di un nome significativo per il pacchetto, aggiungere una descrizione appropriata e selezionare i destinatari più adatti.  Usare parole per facilitare l'individuazione del pacchetto di contenuto in una ricerca. Sarà più facile trovarlo in futuro.

      ![Screenshot del modulo Crea pacchetto di contenuto completato.](media/service-organizational-content-pack-create-and-publish/cpwindow.png)

    1. Selezionare **Gruppi specifici**.

    1. Immettere gli indirizzi di posta elettronica completi di singoli utenti, [gruppi di Office 365](https://support.office.com/article/Create-a-group-in-Office-365-7124dc4c-1de9-40d4-b096-e8add19209e9), gruppi di distribuzione o gruppi di sicurezza. Ad esempio: salesmgrs@contoso.com, sales@contoso.com

        Per questa esercitazione provare a usare l'indirizzo di posta elettronica del proprio gruppo.

    1. Assegnare al pacchetto di contenuto il nome *Opportunità di vendita*.

        > [!TIP]
        > È consigliabile includere il nome del dashboard nel nome del pacchetto di contenuto. In questo modo, i colleghi possono trovare il dashboard più facilmente dopo essersi connessi al pacchetto di contenuto.

    1. Consigliato: aggiungere una descrizione per consentire ai collaboratori di trovare più facilmente i pacchetti di contenuto di cui hanno bisogno. Oltre a una descrizione, aggiungere parole chiave che i collaboratori possono usare per cercare questo pacchetto di contenuto. Includere le informazioni sul contatto che i collaboratori potranno usare per richiedere chiarimenti o per ricevere assistenza.

    1. Caricare un'immagine o un logo per consentire ai membri del gruppo di trovare più facilmente il pacchetto di contenuto.

        È più veloce cercare un'immagine che un testo. Lo screenshot mostra un'immagine del riquadro dell'istogramma **Opportunity Count** (Numero di opportunità).

    1. Selezionare il dashboard **Esempio di analisi delle opportunità** per aggiungerlo al pacchetto di contenuto.

        Power BI aggiunge automaticamente il report e il set di dati associati. È possibile aggiungerne altri, se si desidera.

       > [!NOTE]
       > Power BI elenca solo i dashboard, i report, i set di dati e le cartelle di lavoro modificabili dall'utente, quindi l'app non visualizza nessuno degli elementi condivisi,

   1. Le cartelle di lavoro di Excel, se presenti, sono visualizzate in **Report**, con un'icona di Excel. Anche queste cartelle di lavoro possono essere aggiunte al pacchetto di contenuto.

      ![Screenshot della sezione Report e report che è possibile selezionare.](media/service-organizational-content-pack-create-and-publish/pbi_orgcontpkexcel.png)

      > [!NOTE]
      > Se i membri del gruppo non possono visualizzare la cartella di lavoro di Excel, potrebbe essere necessario [condividere la cartella di lavoro in OneDrive for Business](https://support.office.com/article/Share-documents-or-folders-in-Office-365-1fe37332-0f9a-4719-970e-d2578da4941c).

1. Selezionare **Pubblica** per aggiungere il pacchetto di contenuto alla libreria dei pacchetti di contenuto aziendale del gruppo.  

   Al completamento della pubblicazione verrà visualizzato un apposito messaggio che indica la riuscita dell'operazione.

1. Quando i membri del gruppo passano a **Recupera dati** > **Pacchetti di contenuto dell'organizzazione**, vedono il pacchetto di contenuto.

   ![Screenshot del pacchetto di contenuto Sales Opportunities (Opportunità di vendita) nella finestra di dialogo AppSource.](media/service-organizational-content-pack-create-and-publish/powerbi-find-content-pack-organization.png)

   > [!TIP]
   > L'URL visualizzato nel browser è l'indirizzo univoco del pacchetto di contenuto.  Per informare i collaboratori che è disponibile un nuovo pacchetto di contenuto,  incollarne l'URL in un messaggio di posta elettronica.

1. Quando i membri del gruppo selezionano **Connetti**, possono [visualizzare e usare il pacchetto di contenuto](service-organizational-content-pack-copy-refresh-access.md).

## <a name="next-steps"></a>Passaggi successivi

* [Introduzione ai pacchetti di contenuto aziendali in Power BI](service-organizational-content-pack-introduction.md).

* [Gestire, aggiornare ed eliminare pacchetti di contenuto aziendali](service-organizational-content-pack-manage-update-delete.md).

* [Pubblicare un'app in Power BI](service-create-distribute-apps.md).

* [OneDrive for Business](https://support.office.com/article/What-is-OneDrive-for-Business-187f90af-056f-47c0-9656-cc0ddca7fdc2)

* Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)
