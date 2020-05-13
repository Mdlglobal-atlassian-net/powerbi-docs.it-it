---
title: Connettersi a Snowflake con Power BI
description: Snowflake con SSO per Power BI
author: cpopell
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/20/2019
ms.author: gepopell
LocalizationGroup: Connect to services
ms.openlocfilehash: 5e5519e30be30d6367791d1b6822196b407a21b1
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83300322"
---
#  <a name="connecting-to-snowflake-in-power-bi-service"></a>Connessione a Snowflake nel servizio Power BI

## <a name="introduction"></a>Introduzione

La connessione a Snowflake nel servizio Power BI differisce da altri connettori per il solo fatto che offre anche una funzionalità per AAD (con un'opzione per l'accesso SSO). Le varie parti dell'integrazione richiedono ruoli amministrativi diversi in Snowflake, Power BI e Azure. È anche possibile scegliere di abilitare l'autenticazione AAD senza usare SSO. L'autenticazione di base funziona in modo analogo ad altri connettori del servizio.

Se si è interessati a configurare l'integrazione di AAD e, facoltativamente, abilitare SSO:
* Se si è un amministratore di Snowflake, leggere l'articolo [Power BI SSO to Snowflake - Getting Started](https://docs.snowflake.net/manuals/LIMITEDACCESS/oauth-powerbi.html) (Accesso SSO di Power BI a Snowflake - Introduzione) nella documentazione di Snowflake.
* (SSO) Se si è un amministratore di Power BI, vedere la sezione "Configurazione del servizio Power BI - Portale di amministrazione".
* (SSO) Se si è un autore di set di dati di Power BI, vedere la sezione "Configurazione del servizio Power BI - Abilitazione di un set di dati".

## <a name="power-bi-service-configuration"></a>Configurazione del servizio Power BI

### <a name="admin-portal"></a>Portale di amministrazione

Per abilitare l'accesso SSO, l'amministratore del tenant deve accedere al portale di amministrazione e approvare l'invio di credenziali AAD di Power BI a Snowflake.

![Impostazione di amministrazione del tenant per l'accesso SSO a Snowflake](media/service-connect-snowflake/snowflakessotenant.png)

Passare al portale di amministrazione, selezionare "Impostazioni del tenant" sulla barra laterale e scorrere verso il basso fino a "Impostazioni di integrazione". Verrà visualizzata un'opzione "SSO Snowflake".

Come indicato, è necessario abilitare questa opzione manualmente per acconsentire all'invio del token AAD ai server di Snowflake. Per abilitarla, fare clic sull'interruttore "Disabilitato", scegliere Applica e attendere che la modifica delle impostazioni diventi effettiva. La propagazione della configurazione potrebbe richiedere fino a un'ora.

Al termine dell'operazione, sarà possibile usare i report con SSO.

### <a name="configuring-a-dataset-with-aad"></a>Configurazione di un set di dati con AAD

Dopo la pubblicazione sul Web di un report basato sul connettore Snowflake, nel servizio Web di Power BI l'autore del set di dati deve passare all'area di lavoro appropriata, selezionare "Set di dati" e quindi "Impostazioni", nel menu con i tre puntini di sospensione (...) accanto al set di dati pertinente da cui è possibile eseguire altre azioni.

A causa della modalità di funzionamento di Power BI, l'accesso SSO è possibile solo quando non vengono eseguite origini dati tramite il gateway dati locale.

* Se nel modello di dati si usa solo un'origine Snowflake, è possibile usare SSO se si sceglie di non usare il gateway dati locale
* Se si usa un'origine Snowflake insieme a un'altra origine, è possibile usare SSO se nessuna delle origini usa il gateway dati locale
* Se si usa un'origine Snowflake tramite il gateway dati locale, le credenziali AAD non sono attualmente supportate. Questo può essere importante nel caso in cui si stia tentando di accedere a una rete virtuale da un singolo IP con il gateway installato, anziché dall'intero intervallo IP di Power BI.
* Se si usa un'origine Snowflake insieme a un'altra origine che richiede un gateway, anche in questo caso sarà necessario usare Snowflake tramite il gateway dati locale e non sarà possibile usare SSO.

Per altre informazioni su come usare il gateway dati locale, vedere l'articolo [Informazioni sul gateway dati locale](https://docs.microsoft.com/power-bi/service-gateway-onprem).

Se non si usa il gateway, è tutto pronto. Se nel gateway dati locale sono configurate le credenziali di Snowflake, ma tale origine dati viene usata solo nel proprio modello, è possibile fare clic sull'interruttore nella pagina Impostazioni set di dati per disattivare il gateway per tale modello di dati.

![Impostazione del set di dati per disattivare il gateway](media/service-connect-snowflake/snowflake_gateway_toggle_off.png)

L'autore del set di dati deve selezionare "Credenziali origine dati" ed eseguire l'accesso. Il set di dati può essere connesso a Snowflake con credenziali di base o OAuth2 (AAD). Se si sceglie di usare AAD, il set di dati può essere abilitato per l'uso di SSO. Quando il primo utente accede a Snowflake per il set di dati, deve selezionare l'opzione in base alla quale le credenziali OAuth2 di altri utenti verranno usate per recuperare i dati. In questo modo verrà abilitato l'accesso SSO con credenziali AAD. Indipendentemente dal fatto che l'utente iniziale esegua l'accesso con l'autenticazione di base o OAuth2 (AAD), sono le credenziali AAD a essere inviate per SSO. 

![Impostazione del set di dati per l'accesso SSO a Snowflake](media/service-connect-snowflake/snowflakessocredui.png)

Quando la configurazione è completata, gli altri utenti devono usare automaticamente l'autenticazione AAD per connettersi ai dati dal set di dati di Snowflake.

Se si sceglie di non abilitare SSO, gli utenti che aggiornano il report useranno le credenziali dell'utente che ha eseguito l'accesso, come per la maggior parte degli altri report di Power BI.

### <a name="troubleshooting"></a>Risoluzione dei problemi

In caso di problemi con l'integrazione, vedere la [guida alla risoluzione dei problemi](https://docs.snowflake.net/manuals/LIMITEDACCESS/oauth-powerbi.html#troubleshooting) di Snowflake.

