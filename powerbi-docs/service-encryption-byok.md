---
title: Usare chiavi di crittografia personalizzate per Power BI (anteprima)
description: Informazioni su come usare chiavi di crittografia personalizzate in Power BI Premium.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/08/2020
LocalizationGroup: Premium
ms.openlocfilehash: c4b4d706f56d9ebc91b17194c9b2fa631aeb8497
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/04/2020
ms.locfileid: "75762118"
---
# <a name="bring-your-own-encryption-keys-for-power-bi-preview"></a>Usare chiavi di crittografia personalizzate per Power BI (anteprima)

Power BI consente di crittografare i dati _inattivi_ e _in elaborazione_. Per impostazione predefinita, Power BI usa chiavi gestite da Microsoft per crittografare i dati. In Power BI Premium è anche possibile usare chiavi personalizzate per i dati inattivi che vengono importati in un set di dati. Per altre informazioni, vedere [Considerazioni su origine e archiviazione dei dati](#data-source-and-storage-considerations). Questo approccio viene spesso descritto come _BYOK (Bring Your Own Key)_ .

## <a name="why-use-byok"></a>Vantaggi derivanti dall'uso di BYOK

BYOK semplifica le procedure necessarie per soddisfare i requisiti di conformità che specificano le disposizioni in merito alle chiavi da concordare con il provider di servizi cloud (in questo caso Microsoft). Con BYOK, le chiavi di crittografia per i dati inattivi di Power BI vengono specificate e controllate a livello di applicazione. Di conseguenza, è possibile esercitare un controllo e, nel caso in cui si decida di uscire dal servizio, revocare le chiavi dell'organizzazione. Se si revocano le chiavi, i dati diventano illeggibili per il servizio.

## <a name="data-source-and-storage-considerations"></a>Considerazioni su origine e archiviazione dei dati

Per usare la crittografia BYOK, è necessario caricare i dati nel servizio Power BI da un file di Power BI Desktop con estensione pbix. Non è possibile usare la crittografia BYOK negli scenari seguenti:

- Connessione dinamica ad Analysis Services
- Cartelle di lavoro di Excel, a meno che i dati vengano prima importati in Power BI Desktop
- [Set di dati di push](/rest/api/power-bi/pushdatasets)
- [Set di dati in streaming](service-real-time-streaming.md#set-up-your-real-time-streaming-dataset-in-power-bi)
- [Modelli di grandi dimensioni](service-premium-large-models.md)

La crittografia BYOK si applica solo al set di dati associato al file PBIX e non alle cache dei risultati di query per riquadri e oggetti visivi.

## <a name="configure-azure-key-vault"></a>Configurare Azure Key Vault

In questa sezione si vedrà come configurare Azure Key Vault, uno strumento per l'archiviazione e l'accesso sicuri ai segreti, come le chiavi di crittografia. È possibile usare un insieme di credenziali delle chiavi esistente per archiviare le chiavi di crittografia oppure è possibile crearne uno nuovo da usare con Power BI.

Le istruzioni riportate in questa sezione presuppongono la conoscenza di base di Azure Key Vault. Per altre informazioni, vedere [Azure Key Vault](/azure/key-vault/key-vault-whatis). Configurare l'insieme di credenziali delle chiavi nel modo seguente:

1. Aggiungere il servizio Power BI come un'entità servizio per l'insieme di credenziali delle chiavi, con autorizzazioni per eseguire e annullare il wrapping.

1. Creare una chiave RSA con una lunghezza di 4096 bit (o usare una chiave esistente di questo tipo), con autorizzazioni per eseguire e annullare il wrapping.

    > [!IMPORTANT]
    > BYOK in Power BI supporta solo le chiavi RSA con una lunghezza di 4096 bit.

1. Consigliato: verificare che l'opzione di _eliminazione temporanea_ sia abilitata per l'insieme di credenziali delle chiavi.

### <a name="add-the-service-principal"></a>Aggiungere l'entità servizio

1. Nel portale di Azure nell'insieme di credenziali delle chiavi, sotto **Criteri di accesso**, selezionare **Aggiungi nuovo**.

1. In **Selezionare un'entità** cercare e selezionare Microsoft.Azure.AnalysisServices.

    > [!NOTE]
    > Se non si riesce a trovare "Microsoft.Azure.AnalysisServices", è probabile che alla sottoscrizione di Azure associata ad Azure Key Vault non sia mai stata associata una risorsa Power BI. Provare invece a cercare la stringa seguente: 00000009-0000-0000-c000-000000000000.

1. In **Autorizzazioni chiave** selezionare **Annulla il wrapping della chiave** e **Esegui il wrapping della chiave**.

    ![Componenti file PBIX](media/service-encryption-byok/service-principal.png)

1. Selezionare **OK** e quindi **Salva**.

> [!NOTE]
> Per revocare l'accesso di Power BI ai dati in futuro, rimuovere i diritti di accesso a questa entità servizio da Azure Key Vault.

### <a name="create-an-rsa-key"></a>Creare una chiave RSA

1. Nell'insieme di credenziali delle chiavi sotto **Chiavi**, selezionare **Genera/Importa**.

1. Selezionare un **Tipo di chiave** RSA e un valore di **Dimensioni della chiave RSA** pari a 4096.

    ![Componenti file PBIX](media/service-encryption-byok/create-rsa-key.png)

1. Selezionare **Crea**.

1. In **Chiavi** selezionare la chiave creata.

1. Selezionare il GUID per la **Versione corrente** della chiave.

1. Verificare che le opzioni **Esegui il wrapping della chiave** e **Annulla il wrapping della chiave** siano entrambe selezionate. Copiare l'**Identificatore chiave** da usare quando si abilita la crittografia BYOK in Power BI.

    ![Componenti file PBIX](media/service-encryption-byok/key-properties.png)

### <a name="soft-delete-option"></a>Opzione di eliminazione temporanea

È consigliabile abilitare l'[eliminazione temporanea](/azure/key-vault/key-vault-ovw-soft-delete) nell'insieme di credenziali delle chiavi, per evitare perdite di dati in caso di eliminazione accidentale della chiave o dell'insieme di credenziali delle chiavi. È necessario usare [PowerShell per abilitare la proprietà "eliminazione temporanea"](/azure/key-vault/key-vault-soft-delete-powershell) per l'insieme di credenziali delle chiavi, perché questa opzione non è ancora disponibile nel portale di Azure.

Una volta configurato Azure Key Vault correttamente, è possibile abilitare la crittografia BYOK nel tenant.

## <a name="enable-byok-on-your-tenant"></a>Abilitare la crittografia BYOK nel tenant

La crittografia BYOK viene abilitata nel tenant tramite [PowerShell](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt.Admin), inserendo per prima cosa nel tenant di Power BI le chiavi di crittografia create e archiviate in Azure Key Vault. In seguito queste chiavi di crittografia vengono assegnate ad ogni livello capacità Premium per crittografare il contenuto della capacità.

### <a name="important-considerations"></a>Considerazioni importanti

Prima di abilitare la crittografia BYOK, tenere presente le considerazioni seguenti:

- In questa fase non è possibile disabilitare la crittografia BYOK dopo averla abilitata. A seconda di come vengono specificati i parametri per `Add-PowerBIEncryptionKey`, è possibile controllare la modalità con cui viene usata la crittografia BYOK per una o più capacità. Tuttavia, non è possibile annullare l'introduzione delle chiavi nel tenant. Per altre informazioni, vedere [Abilitare la crittografia BYOK](#enable-byok).

- Non è possibile spostare _direttamente_ un'area di lavoro che usa BYOK da una capacità dedicata in Power BI Premium a una capacità condivisa. È necessario prima spostare l'area di lavoro in una capacità dedicata in cui la crittografia BYOK non è abilitata.

- Se si sposta un'area di lavoro che usa BYOK da una capacità dedicata in Power BI Premium a una capacità condivisa, report e set di dati diventano inaccessibili, in quanto sono crittografati con la chiave. Per evitare che ciò accada, è necessario prima spostare l'area di lavoro in una capacità dedicata in cui la crittografia BYOK non è abilitata.

### <a name="enable-byok"></a>Abilitare la crittografia BYOK

Per abilitare la crittografia BYOK, è necessario essere un amministratore del tenant del servizio Power BI e aver eseguito l'accesso usando il cmdlet `Connect-PowerBIServiceAccount`. Usare quindi [`Add-PowerBIEncryptionKey`](/powershell/module/microsoftpowerbimgmt.admin/Add-PowerBIEncryptionKey) per abilitare la crittografia BYOK, come illustrato nell'esempio seguente:

```powershell
Add-PowerBIEncryptionKey -Name'Contoso Sales' -KeyVaultKeyUri'https://contoso-vault2.vault.azure.net/keys/ContosoKeyVault/b2ab4ba1c7b341eea5ecaaa2wb54c4d2'
```

Per aggiungere più chiavi, eseguire `Add-PowerBIEncryptionKey` con valori diversi per `-Name` e `-KeyVaultKeyUri`. 

Il cmdlet accetta due parametri opzionali che influiscono sulla crittografia per le capacità correnti e future. Per impostazione predefinita, nessuna delle due opzioni è impostata:

- `-Activate`: indica che la chiave verrà usata per tutte le capacità esistenti nel tenant non ancora crittografate.

- `-Default`: indica che la chiave è ora il valore predefinito per l'intero tenant. Quando si crea una nuova capacità, la capacità eredita questa chiave.

> [!IMPORTANT]
> Se si specifica `-Default`, tutte le capacità create nel tenant da questo momento verranno crittografate con la chiave specificata (o con una chiave predefinita aggiornata). Non è possibile annullare l'operazione predefinita, quindi non è possibile creare nel tenant una capacità Premium che non usi la funzionalità BYOK (Bring Your Own Key).

Dopo aver abilitato la funzionalità BYOK nel tenant, impostare la chiave di crittografia per una o più capacità di Power BI:

1. Usare [`Get-PowerBICapacity`](/powershell/module/microsoftpowerbimgmt.capacities/get-powerbicapacity) per ottenere l'ID capacità necessario per il passaggio successivo.

    ```powershell
    Get-PowerBICapacity -Scope Individual
    ```

    Il cmdlet restituisce un output simile all'output seguente:

    ```
    Id              : xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
    DisplayName     : Test Capacity
    Admins          : adam@sometestdomain.com
    Sku             : P1
    State           : Active
    UserAccessRight : Admin
    Region          : North Central US
    ```

1. Usare [`Set-PowerBICapacityEncryptionKey`](/powershell/module/microsoftpowerbimgmt.admin/set-powerbicapacityencryptionkey) per impostare la chiave di crittografia:

    ```powershell
    Set-PowerBICapacityEncryptionKey-CapacityId xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx -KeyName 'Contoso Sales'
    ```

È possibile controllare la modalità di uso della crittografia BYOK in tutto il tenant. Ad esempio, per crittografare una capacità singola, chiamare `Add-PowerBIEncryptionKey` senza `-Activate`, o `-Default`. Chiamare quindi `Set-PowerBICapacityEncryptionKey` per la capacità in cui si vuole abilitare la crittografia BYOK.

## <a name="manage-byok"></a>Gestire BYOK

Power BI offre altri cmdlet per gestire la crittografia BYOK nel tenant:

- Usare [`Get-PowerBICapacity`](/powershell/module/microsoftpowerbimgmt.capacities/get-powerbicapacity) per ottenere la chiave attualmente usata da una capacità:

    ```powershell
    Get-PowerBICapacity -Scope Organization -ShowEncryptionKey
    ```

- Usare [`Get-PowerBIEncryptionKey`](/powershell/module/microsoftpowerbimgmt.admin/get-powerbiencryptionkey) per ottenere la chiave attualmente in uso nel tenant:

    ```powershell
    Get-PowerBIEncryptionKey
    ```

- Usare [`Get-PowerBIWorkspaceEncryptionStatus`](/powershell/module/microsoftpowerbimgmt.admin/get-powerbiworkspaceencryptionstatus) per vedere se i set di dati in un'area di lavoro vengono crittografati e se il relativo stato di crittografia è sincronizzato con l'area di lavoro:

    ```powershell
    Get-PowerBIWorkspaceEncryptionStatus -Name'Contoso Sales'
    ```

    Si noti che la crittografia è abilitata a livello di capacità, ma lo stato della crittografia viene ottenuto a livello di set di dati per l'area di lavoro specificata.

- Usare [`Switch-PowerBIEncryptionKey`](/powershell/module/microsoftpowerbimgmt.admin/switch-powerbiencryptionkey) per cambiare (o _ruotare_) la versione della chiave usata per la crittografia. Il cmdlet aggiorna semplicemente l'elemento `-KeyVaultKeyUri` per una chiave `-Name`:

    ```powershell
    Switch-PowerBIEncryptionKey -Name'Contoso Sales' -KeyVaultKeyUri'https://contoso-vault2.vault.azure.net/keys/ContosoKeyVault/b2ab4ba1c7b341eea5ecaaa2wb54c4d2'
    ```
