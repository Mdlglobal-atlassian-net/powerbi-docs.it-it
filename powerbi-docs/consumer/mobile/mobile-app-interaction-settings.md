---
title: Configurare le impostazioni di interazione con i report
description: Informazioni su come modificare le impostazioni di interazione predefinite per i report.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 01/21/2020
ms.author: painbar
ms.openlocfilehash: fee89c65328b70e1f312b39fbad75d7148bd92f2
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2020
ms.locfileid: "76542290"
---
# <a name="configure-report-interaction-settings"></a>Configurare le impostazioni di interazione con i report

## <a name="overview"></a>Panoramica

L'app per dispositivi mobili Power BI include varie impostazioni di "interazione" configurabili che consentono di controllare la modalità di interazione con i dati e di definire il comportamento di alcuni elementi nell'app per dispositivi mobili Power BI. Attualmente sono disponibili impostazioni per
* [Interazione con tocco singolo o doppio sugli oggetti visivi del report](#single-tap)
* [Piè di pagina del report ancorato o dinamico](#docked-report-footer-android-phones) (Android)
* [Aggiornamento del report con pulsante o con trascinamento verso il basso](#report-refresh-android-phones) (Android)

Per accedere alle impostazioni di interazione, toccare l'immagine del profilo personale per aprire il [pannello laterale](./mobile-apps-home-page.md#header), scegliere **Impostazioni** e individuare la sezione **Interazione**.

![Impostazioni di interazione](./media/mobile-app-interaction-settings/powerbi-mobile-app-interactions-section.png)

>[!NOTE]
>Le impostazioni di interazione per il pulsante di aggiornamento e per l'ancoraggio del piè di pagina del report non vengono applicate attualmente ai report del server di report. Questo comportamento cambierà nella versione del server di report di gennaio 2020.

## <a name="interaction-settings"></a>Impostazioni di interazione

### <a name="single-tap"></a>Tocco singolo
Quando si scarica l'app per dispositivi mobili Power BI, è impostata per l'interazione con tocco singolo. Questo significa che quando si tocca un oggetto visivo per eseguire un'azione, ad esempio la selezione di un elemento del filtro dei dati, l'evidenziazione incrociata, il clic su un collegamento o un pulsante e così via, il tocco seleziona l'oggetto visivo ed esegue l'azione desiderata.

Se si preferisce, è possibile disattivare l'interazione con tocco singolo. Si avrà quindi un'interazione con doppio tocco. Con l'interazione con doppio tocco è prima necessario toccare un oggetto visivo per selezionarlo e poi toccare di nuovo l'oggetto visivo per eseguire l'azione desiderata.

### <a name="docked-report-footer-android-phones"></a>Piè di pagina del report ancorato (telefoni Android)

L'impostazione del piè di pagina del report ancorato determina se il piè di pagina del report rimane ancorato (ovvero fisso e sempre visibile) nella parte inferiore del report oppure se viene nascosto e visualizzato nuovamente in base alle azioni eseguite nel report, ad esempio lo scorrimento.

Nei telefoni Android l'impostazione del piè di pagina del report ancorato è **attiva** per impostazione predefinita e questo significa che il piè di pagina del report è ancorato e sempre visibile nella parte inferiore del report. Impostare l'opzione su **disattivato** se si preferisce un piè di pagina dinamico nei report, che viene visualizzato e scompare a seconda delle azioni eseguite nel report.

### <a name="report-refresh-android-phones"></a>Aggiornamento del report (telefoni Android)

L'impostazione di aggiornamento dei report consente di definire la modalità di avvio degli aggiornamenti dei report. È possibile scegliere di aggiungere un pulsante di aggiornamento in tutte le intestazioni dei report oppure di usare l'azione di trascinamento verso il basso per aggiornare (trascinando leggermente dall'alto verso il basso) nella pagina del report. Nella figura seguente sono illustrate le due alternative. 

![Pulsante di aggiornamento o trascinamento verso il basso](./media/mobile-app-interaction-settings/powerbi-mobile-app-interactions-refresh-button-versus-pull.png)

Per impostazione predefinita, nei telefoni Android viene aggiunto un pulsante di aggiornamento.

Per modificare l'impostazione di aggiornamento del report, passare all'opzione per l'aggiornamento del report nelle impostazioni di interazione. Viene visualizzata l'impostazione corrente. Toccare il valore per aprire un popup in cui è possibile scegliere un nuovo valore.

![Impostare l'aggiornamento](./media/mobile-app-interaction-settings/powerbi-mobile-app-interactions-set-refresh.png)

## <a name="remote-configuration"></a>Configurazione remota

Le interazioni possono anche essere configurate in modalità remota da un amministratore usando uno strumento MDM con un file di configurazione dell'app. In questo modo è possibile standardizzare l'esperienza di interazione con i report per l'intera organizzazione o per gruppi specifici di utenti nell'organizzazione. Per informazioni dettagliate, vedere [Configurare l'interazione usando la gestione dei dispositivi mobili](./mobile-app-configuration.md).


## <a name="next-steps"></a>Passaggi successivi
* [Interazione con i report](./mobile-reports-in-the-mobile-apps.md#interact-with-reports)
* [Configurare l'interazione usando la gestione dei dispositivi mobili](./mobile-app-configuration.md)
