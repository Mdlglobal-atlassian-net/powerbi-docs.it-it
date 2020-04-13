---
title: Proteggere i dati di Power BI con l'identificazione nativa dei dispositivi
description: Informazioni su come configurare le app iOS e Android in modo che richiedano un'identificazione aggiuntiva prima che sia possibile accedere ai dati di Power BI
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 04/07/2020
ms.author: painbar
ms.openlocfilehash: ce7b3c3bc667023ef36650d8c551caaceab04c02
ms.sourcegitcommit: 9b806dfe62c2dee82d971bb4f89d983b97931b43
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/07/2020
ms.locfileid: "80802802"
---
# <a name="protect-power-bi-app-with-face-id-touch-id-passcode-or-biometric-data"></a>Proteggere l'app Power BI con Face ID, Touch ID, passcode o dati biometrici 

In molti casi, i dati gestiti in Power BI sono riservati e devono essere protetti e accessibili ai soli utenti autorizzati. 

Le app Power BI per iOS e Android consentono di proteggere i dati configurando un'identificazione aggiuntiva. In questo modo verrà richiesta l'identificazione ogni volta che l'app viene avviata o portata in primo piano. In iOS questo significa fornire Face ID, Touch ID o passcode. In Android significa fornire dati biometrici (ID impronta digitale).

Si applica a:

| ![iPhone](./media/mobile-native-secure-access/ios-logo-40-px.png) | ![iPad](./media/mobile-native-secure-access/ios-logo-40-px.png) | ![Telefono Android](././media/mobile-native-secure-access/android-logo-40-px.png) | ![Tablet Android](././media/mobile-native-secure-access/android-logo-40-px.png) |
|:--- |:--- |:--- |:--- |
|iPhone |iPad |Telefoni Android |Tablet Android |

## <a name="turn-on-face-id-touch-id-or-passcode-on-ios"></a>Attivare Face ID, Touch ID o passcode in iOS

Per usare un'identificazione aggiuntiva nell'app Power BI per dispositivi mobili per iOS, passare alle impostazioni dell'app in **Privacy e sicurezza**. Verrà visualizzata l'opzione per attivare Face ID, Touch ID o passcode. Le opzioni visualizzate dipendono dalle funzionalità del dispositivo.

![Pagina di impostazione dell'app Power BI per iOS](./media/mobile-native-secure-access/mobile-ios-native-secured-setting.png)

Quando questa impostazione è attiva, ogni volta che si avvia l'app o la si porta in primo piano verrà richiesto di specificare il proprio ID prima di poter accedere all'app.

Il tipo di ID che verrà richiesto dipende dalle funzionalità del dispositivo. Se il dispositivo supporta Face ID, è necessario usare Face ID. Se supporta Touch ID, è necessario usare Touch ID. Se non supporta nessuno dei due, è necessario specificare un passcode. L'immagine seguente mostra la schermata di autenticazione con Face ID.

![Face ID di Power BI per iOS](./media/mobile-native-secure-access/mobile-ios-native-secured-faceid.png)

## <a name="turn-on-biometric-data-fingerprint-id-on-android"></a>Attivare i dati biometrici (ID impronta digitale) in Android

Per usare un'identificazione aggiuntiva nell'app Power BI per dispositivi mobili per Android, vedere l'impostazione dell'app in **Privacy e sicurezza**. Verrà visualizzata l'opzione per attivare i dati biometrici.

![Pagina delle impostazioni dell'app Power BI per Android](./media/mobile-native-secure-access/mobile-android-native-secured-setting.png)

Quando questa impostazione è attiva, ogni volta che si avvia l'app o la si porta in primo piano verrà richiesto di specificare i propri dati biometrici (ID impronta digitale) prima di poter accedere all'app.

L'immagine seguente mostra la schermata di autenticazione con impronta digitale.

![Face ID di Power BI per iOS](./media/mobile-native-secure-access/mobile-android-native-secured-fingerprint-id.png)

>[!NOTE]
>Per poter usare l'impostazione Require Biometric Authentification (Richiedi autenticazione biometrica) dell'app per dispositivi mobili, è prima necessario configurare la biometria nel dispositivo Android. Se il dispositivo non supporta la biometria, non sarà possibile proteggere l'accesso ai dati di Power BI usando questa impostazione dell'app per dispositivi mobili.
>
>Se l'amministratore ha [attivato l'accesso sicuro da remoto](#mdm-enforcement-of-secure-access-to-your-power-bi-mobile-app) per l'app per dispositivi mobili, è necessario configurare la biometria nel dispositivo per accedere all'app, se non è già stato fatto. Se il dispositivo non supporta la biometria, l'impostazione remota non avrà alcun effetto. L'accesso all'app per dispositivi mobili rimarrà non sicuro.

## <a name="mdm-enforcement-of-secure-access-to-your-power-bi-mobile-app"></a>Imposizione MDM dell'accesso sicuro all'app Power BI per dispositivi mobili.

Alcune organizzazioni hanno requisiti di conformità e criteri di sicurezza che richiedono un'identificazione aggiuntiva prima di consentire l'accesso a dati aziendali sensibili.

Per supportare queste esigenze, l'app Power BI per dispositivi mobili consente agli amministratori di controllare l'impostazione di accesso sicuro all'app eseguendo il push delle impostazioni di configurazione dell'app da Microsoft Intune e altre soluzioni di gestione dei dispositivi mobili (MDM). Gli amministratori possono usare i criteri di protezione delle app per attivare questa impostazione per tutti gli utenti o per un gruppo di utenti. Per informazioni dettagliate, vedere [Usare MDM per configurare in remoto l'app Power BI per dispositivi mobili](mobile-app-configuration.md#data-protection-settings-ios-and-android).

## <a name="next-steps"></a>Passaggi successivi
* [Usare MDM per configurare in remoto l'app Power BI per dispositivi mobili](mobile-app-configuration.md)
