---
title: Impostare gli avvisi per i dati nelle app Power BI per dispositivi mobili
description: Informazioni su come impostare avvisi nelle app Power BI per dispositivi mobili in modo da ricevere una notifica quando i dati in un dashboard superano i limiti impostati.
services: powerbi
documentationcenter: 
author: maggiesMSFT
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/18/2017
ms.author: maggies
ms.openlocfilehash: c6406a6d1ad4269352ce8421b91f4304fd35c78f
ms.sourcegitcommit: ea247cb3cfc1cac076d4b076c1ad8e2fc37e15a1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/19/2017
---
# <a name="set-data-alerts-in-the-power-bi-mobile-apps"></a>Impostare gli avvisi per i dati nelle app Power BI per dispositivi mobili
Si applica a:

| ![iPhone](media/mobile-set-data-alerts-in-the-mobile-apps/iphone-logo-50-px.png) | ![iPad](media/mobile-set-data-alerts-in-the-mobile-apps/ipad-logo-50-px.png) | ![Telefono Android](media/mobile-set-data-alerts-in-the-mobile-apps/android-phone-logo-50-px.png) | ![Tablet Android](media/mobile-set-data-alerts-in-the-mobile-apps/android-tablet-logo-50-px.png) | ![Tablet Android](media/mobile-set-data-alerts-in-the-mobile-apps/win-10-logo-50-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhone |iPad |Telefoni Android |Tablet Android |Dispositivi Windows 10 |

È possibile impostare gli avvisi sui dashboard nell'app Power BI per dispositivi mobili e nel servizio Power BI. Gli avvisi segnalano eventuali modifiche apportate ai dati in un riquadro che superano i limiti impostati. Gli avvisi possono essere usati con i riquadri in cui è presente un singolo numero, ad esempio le schede e i misuratori, ma non con i dati di streaming. Gli avvisi per i dati possono essere impostati in un dispositivo mobile e visualizzati nel servizio Power BI e viceversa. Gli avvisi per i dati sono visibili solo all'utente che li ha impostati, anche se si condivide un dashboard o uno snapshot di un riquadro.

È possibile impostare avvisi sui riquadri se si ha una licenza di Power BI Pro oppure se si ha una licenza gratuita di Power BI e il dashboard condiviso è disponibile in una capacità Premium. 

> [!WARNING]
> Le notifiche di avviso basate sui dati forniscono informazioni sui dati. Se il dispositivo viene rubato, è consigliabile disattivare tutte le regole di avviso basate sui dati usando il servizio Power BI. 
> 
> Altre informazioni sulla [gestione degli avvisi per i dati nel servizio Power BI](service-set-data-alerts.md).
> 
> 

## <a name="data-alerts-on-an-iphone-or-ipad"></a>Avvisi per i dati in un iPhone o iPad
### <a name="set-an-alert-on-an-iphone-or-ipad"></a>Impostare un avviso in un iPhone o iPad
1. Toccare il riquadro con un numero o un misuratore nel dashboard per aprirlo in modalità messa a fuoco.  
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-card-visual.png)
2. Toccare l'icona a forma di campanello ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-alert-icon.png) per aggiungere un avviso.  
3. Toccare **Aggiungi regola di avviso**.
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-add-alert-rule.png)
4. Impostare il valore al di sopra o al di sotto del quale si vogliono ricevere gli avvisi.
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-set-alert-threshold.png)
5. Decidere se ricevere avvisi ogni ora o ogni giorno e se si vuole ricevere anche un messaggio di posta elettronica quando viene generato l'avviso.
   
   > [!NOTE]
   > Gli avvisi non vengono ricevuti con la cadenza oraria o giornaliera specificata se i dati non vengono effettivamente aggiornati in quel momento.
   > 
   > 
6. È anche possibile modificare il titolo dell'avviso.
7. Toccare **Salva**.
8. Un singolo riquadro può includere avvisi per i valori sia superiori che inferiori alla soglia specificata. In **Gestisci avvisi** toccare **Aggiungi regola di avviso**.
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-add-another-alert-rule.png)

### <a name="manage-alerts-on-your-iphone-or-ipad"></a>Gestire gli avvisi nell'iPhone o iPad
È possibile gestire i singoli avvisi nel dispositivo mobile o [tutti gli avvisi nel servizio Power BI](service-set-data-alerts.md).

1. In un dashboard toccare il riquadro di tipo numero o misuratore che contiene un avviso.  
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-card-visual.png)
2. Toccare l'icona a forma di campanello ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-has-alert-icon.png).  
3. Toccare il nome dell'avviso per modificarlo, toccare il dispositivo di scorrimento per disattivare gli avvisi di posta elettronica o toccare l'icona a forma di bidone della spazzatura per eliminare l'avviso.
   
    ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-edit-delete-alert.png)

## <a name="data-alerts-on-an-android-device"></a>Avvisi per i dati in un dispositivo Android
### <a name="set-an-alert-on-an-android-device"></a>Impostare un avviso in un dispositivo Android
1. In un dashboard di Power BI toccare un numero o un misuratore per aprirlo.  
2. Toccare l'icona a forma di campanello ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-alert-icon.png) per aggiungere un avviso.  
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-tap-alert.png)
3. Toccare l'icona più (+).
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-plus-alert.png)
4. Digitare il valore al di sopra o al di sotto del quale si vogliono ricevere gli avvisi.
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-tablet-set-alert-condition.png)
5. Toccare **Fatto**.
6. Decidere se ricevere avvisi ogni ora o ogni giorno e se si vuole ricevere anche un messaggio di posta elettronica quando viene generato l'avviso.
   
   > [!NOTE]
   > Gli avvisi non vengono ricevuti con la cadenza oraria o giornaliera specificata se i dati non vengono effettivamente aggiornati in quel momento.
   > 
   > 
7. È anche possibile modificare il titolo dell'avviso.
8. Toccare **Salva**.

### <a name="manage-alerts-on-an-android-device"></a>Gestire gli avvisi in un dispositivo Android
È possibile gestire i singoli avvisi nell'app Power BI per dispositivi mobili o [tutti gli avvisi nel servizio Power BI](service-set-data-alerts.md).

1. In un dashboard toccare il riquadro di tipo scheda o misuratore che contiene un avviso.  
2. Toccare l'icona a forma di campanello ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-filled-alert-bell.png).  
3. Toccare l'avviso per modificare un valore o per disattivarlo.
   
    ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-manage-alerts.png)
4. Toccare l'icona del segno più (+) per aggiungere un altro avviso allo stesso riquadro.
5. Per eliminare completamente l'avviso, toccare l'icona a forma di bidone della spazzatura ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-delete-alert-icon.png).

## <a name="data-alerts-on-a-windows-device"></a>Avvisi per i dati in un dispositivo Windows
### <a name="set-data-alerts-on-a-windows-device"></a>Impostare avvisi per i dati in un dispositivo Windows
1. Toccare il riquadro con un numero o un misuratore nel dashboard per aprirlo.  
2. Toccare l'icona a forma di campanello ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-alert-bell-off.png) per aggiungere un avviso.  
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-tap-alert.png)
3. Toccare l'icona più (+).
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-no-alerts-yet.png)
4. Digitare il valore al di sopra o al di sotto del quale si vogliono ricevere gli avvisi.
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-set-alert.png)
5. Decidere se ricevere avvisi ogni ora o ogni giorno e se si vuole ricevere anche un messaggio di posta elettronica quando viene generato l'avviso.
   
   > [!NOTE]
   > Gli avvisi non vengono ricevuti con la cadenza oraria o giornaliera specificata se i dati non vengono effettivamente aggiornati in quel momento.
   > 
   > 
6. È anche possibile modificare il titolo dell'avviso.
7. Toccare il segno di spunta.
8. Un singolo riquadro può includere avvisi per i valori sia superiori che inferiori alla soglia specificata. In **Gestisci avvisi** toccare il segno più (+).
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-add-another-alert.png)

### <a name="manage-alerts-on-a-windows-device"></a>Gestire gli avvisi per i dati in un dispositivo Windows
È possibile gestire i singoli avvisi nell'app Power BI per dispositivi mobili o [tutti gli avvisi nel servizio Power BI](service-set-data-alerts.md).

1. In un dashboard toccare il riquadro di tipo scheda o misuratore che contiene un avviso.  
2. Toccare l'icona a forma di campanello ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-alert-bell-on.png).  
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-has-alerts.png)
3. Toccare l'avviso per modificare un valore o per disattivarlo.
   
    ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-add-another-alert.png)
4. Per eliminare completamente l'avviso, fare clic con il pulsante destro del mouse oppure toccare e tenere premuto > **Elimina**.

## <a name="receiving-alerts"></a>Ricezione di avvisi
Gli avvisi vengono ricevuti nel [centro notifiche](mobile-apps-notification-center.md) di Power BI nel dispositivo mobile o nel servizio Power BI, insieme alle notifiche sui nuovi dashboard condivisi da altri utenti.

Le origini dati vengono spesso impostate in modo da essere aggiornate quotidianamente, anche se alcuni utenti scelgono di aggiornarle più di frequente. Quando i dati nel dashboard vengono aggiornati, se i dati rilevati raggiungono una delle soglie impostate, verranno eseguite alcune operazioni.

1. A seconda dell'opzione selezionata, Power BI controlla se è trascorsa più di un'ora o più di 24 ore dall'invio dell'ultimo avviso.
   
   Se i dati superano la soglia, viene visualizzato un avviso ogni ora o ogni 24 ore.
2. Se è stato impostato anche l'invio di un messaggio di posta elettronica, nella posta in arrivo viene visualizzato un messaggio simile al seguente.
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/powerbi-alerts-email.png)
3. Power BI aggiunge un messaggio al **centro notifiche** e una nuova icona di avviso al riquadro ![](media/mobile-set-data-alerts-in-the-mobile-apps/powerbi-alert-tile-notification-icon.png) applicabile.
4. Toccare il pulsante di spostamento ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-alert-global-nav-button.png) per [aprire il **Centro notifiche**](mobile-apps-notification-center.md) e visualizzare i dettagli dell'avviso.
   
     ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-notifications.png) 

> [!NOTE]
> Gli avvisi possono essere usati solo con dati aggiornati. Quando i dati vengono aggiornati, Power BI controlla se è impostato un avviso per tali dati. Se i dati raggiungono una soglia di avviso, viene generato un avviso.
> 
> 

## <a name="tips-and-troubleshooting"></a>Suggerimenti e risoluzione dei problemi
* Gli avvisi non sono attualmente supportati per i riquadri Bing o di tipo scheda con misure di data/ora.
* Gli avvisi possono essere usati solo con dati numerici.
* Gli avvisi possono essere usati solo con dati aggiornati. Non possono essere usati con dati statici.
* Gli avvisi non funzionano con i riquadri contenenti dati di streaming.

## <a name="next-steps"></a>Passaggi successivi
* [Gestire gli avvisi nel servizio Power BI](service-set-data-alerts.md)
* [Centro notifiche di Power BI per dispositivi mobili](mobile-apps-notification-center.md)
* Domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

