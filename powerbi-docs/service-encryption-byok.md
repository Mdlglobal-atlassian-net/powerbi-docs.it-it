---
title: Usare chiavi di crittografia personalizzate per Power BI (anteprima)
description: Informazioni su come usare chiavi di crittografia personalizzate in Power BI Premium.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 06/10/2019
LocalizationGroup: Premium
ms.openlocfilehash: 7adcfeec771796aa9fe322512f8ca8584559cea0
ms.sourcegitcommit: c122c1a8c9f502a78ccecd32d2708ab2342409f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829389"
---
# <a name="bring-your-own-encryption-keys-for-power-bi-preview"></a>Usare chiavi di crittografia personalizzate per Power BI (anteprima)

Power BI consente di crittografare i dati _inattivi_ e _in elaborazione_. Per impostazione predefinita, Power BI usa chiavi gestite da Microsoft per crittografare i dati. In Power BI Premium è anche possibile usare chiavi personalizzate per i dati inattivi che vengono importati in un set di dati. Per altre informazioni, vedere [Considerazioni su origine e archiviazione dei dati](#data-source-and-storage-considerations). Questo approccio viene spesso descritto come _BYOK (Bring Your Own Key)_ .

## <a name="why-use-byok"></a>Vantaggi derivanti dall'uso di BYOK

BYOK semplifica le procedure necessarie per soddisfare i requisiti di conformità che specificano le disposizioni in merito alle chiavi da concordare con il provider di servizi cloud (in questo caso Microsoft). Con BYOK, le chiavi di crittografia per i dati inattivi di Power BI vengono specificate e controllate a livello di applicazione. Di conseguenza, è possibile esercitare un controllo e, nel caso in cui si decida di uscire dal servizio, revocare le chiavi dell'organizzazione. Se si revocano le chiavi, i dati diventano illeggibili per il servizio.

## <a name="data-source-and-storage-considerations"></a>Considerazioni su origine e archiviazione dei dati

Per usare la crittografia BYOK, è necessario caricare i dati nel servizio Power BI da un file di Power BI Desktop con estensione pbix. Quando ci si connette alle origini dati in Power BI Desktop, è necessario specificare una modalità di archiviazione dell'importazione. Non è possibile usare la crittografia BYOK negli scenari seguenti:

- DirectQuery
- Connessione dinamica ad Analysis Services
- Cartelle di lavoro di Excel, a meno che i dati vengano prima importati in Power BI Desktop
- Set di dati di push

Nella sezione successiva viene illustrato come configurare Azure Key Vault, in cui vengono archiviate le chiavi di crittografia per BYOK.

## <a name="configure-azure-key-vault"></a>Configurare Azure Key Vault

Azure Key Vault è uno strumento per l'archiviazione e l'accesso sicuri ai segreti, come le chiavi di crittografia. È possibile usare un insieme di credenziali delle chiavi esistente per archiviare le chiavi di crittografia oppure è possibile crearne uno nuovo da usare con Power BI.

Le istruzioni riportate in questa sezione presuppongono la conoscenza di base di Azure Key Vault. Per altre informazioni, vedere [Azure Key Vault](/azure/key-vault/key-vault-whatis). Configurare l'insieme di credenziali delle chiavi nel modo seguente:

1. Aggiungere il servizio Power BI come un'entità servizio per l'insieme di credenziali delle chiavi, con autorizzazioni per eseguire e annullare il wrapping.

1. Creare una chiave RSA con una lunghezza di 4096 bit (o usare una chiave esistente di questo tipo), con autorizzazioni per eseguire e annullare il wrapping.

1. Consigliato: verificare che l'opzione di _eliminazione temporanea_ sia abilitata per l'insieme di credenziali delle chiavi.

### <a name="add-the-service-principal"></a>Aggiungere l'entità servizio

1. Nel portale di Azure nell'insieme di credenziali delle chiavi, sotto **Criteri di accesso**, selezionare **Aggiungi nuovo**.

1. In **Selezionare un'entità** cercare e selezionare Microsoft.Azure.AnalysisServices.

1. In **Autorizzazioni chiave** selezionare **Annulla il wrapping della chiave** e **Esegui il wrapping della chiave**.

    ![Componenti file PBIX](media/service-encryption-byok/service-principal.png)

1. Selezionare **OK** e quindi **Salva**.

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

È consigliabile abilitare l'[eliminazione temporanea](/azure/key-vault/key-vault-ovw-soft-delete) nell'insieme di credenziali delle chiavi, per evitare perdite di dati in caso di eliminazione accidentale della chiave o dell'insieme di credenziali delle chiavi. È necessario usare [PowerShell per abilitare la proprietà "eliminazione temporanea"](/azure/key-vault/key-vault-soft-delete-powershell) per un insieme di credenziali delle chiavi, perché questa opzione non è ancora disponibile nel portale di Azure.

Una volta configurato Azure Key Vault correttamente, è possibile abilitare la crittografia BYOK nel tenant.

## <a name="enable-byok-on-your-tenant"></a>Abilitare la crittografia BYOK nel tenant

La crittografia BYOK viene abilitata nel tenant tramite PowerShell, inserendo per prima cosa nel tenant di Power BI le chiavi di crittografia create e archiviate in Azure Key Vault. In seguito queste chiavi di crittografia vengono assegnate ad ogni livello capacità Premium per crittografare il contenuto della capacità.

### <a name="important-considerations"></a>Considerazioni importanti

Prima di abilitare la crittografia BYOK, tenere presente le considerazioni seguenti:

- In questa fase non è possibile disabilitare la crittografia BYOK dopo averla abilitata. A seconda di come vengono specificati i parametri per `Add-PowerBIEncryptionKey`, è possibile controllare la modalità con cui viene usata la crittografia BYOK per una o più capacità. Tuttavia, non è possibile annullare l'introduzione delle chiavi nel tenant. Per altre informazioni, vedere [Abilitare la crittografia BYOK](#enable-byok).

- Non è possibile spostare _direttamente_ un'area di lavoro che usa BYOK da una capacità dedicata in Power BI Premium a una capacità condivisa. È necessario prima spostare l'area di lavoro in una capacità dedicata in cui la crittografia BYOK non è abilitata.

### <a name="enable-byok"></a>Abilitare la crittografia BYOK

Per abilitare la crittografia BYOK, è necessario essere un amministratore del tenant del servizio Power BI e aver eseguito l'accesso usando il cmdlet `Connect-PowerBIServiceAccount`. Usare quindi `Add-PowerBIEncryptionKey` per abilitare la crittografia BYOK, come illustrato nell'esempio seguente:

```powershell
Add-PowerBIEncryptionKey -Name'Contoso Sales' -KeyVaultKeyUri'https://contoso-vault2.vault.azure.net/keys/ContosoKeyVault/b2ab4ba1c7b341eea5ecaaa2wb54c4d2'
```

Il cmdlet accetta tre parametri opzionali che influiscono sulla crittografia per le capacità correnti e future. Nessuno dei parametri opzionali è impostato in modo predefinito:

- `-Activate`: indica che la chiave verrà usata per tutte le capacità esistenti nel tenant.

- `-Default`: indica che la chiave è ora il valore predefinito per l'intero tenant. Quando si crea una nuova capacità, la capacità eredita questa chiave.

- `-DefaultAndActivate`: indica che la chiave verrà usata per tutte le capacità esistenti e per tutte quelle che verranno create.

Se si specifica `-Default` o `-DefaultAndActivate`, tutte le capacità create in questo tenant da questo momento verranno crittografate con la chiave specificata (o con una chiave predefinita aggiornata). Non è possibile annullare l'operazione predefinita, quindi non è possibile creare una capacità Premium che non usi BYOK nel tenant.

È possibile controllare la modalità di uso della crittografia BYOK in tutto il tenant. Ad esempio, per crittografare una capacità singola, chiamare `Add-PowerBIEncryptionKey` senza `-Activate`, `-Default`, o `-DefaultAndActivate`. Chiamare quindi `Set-PowerBICapacityEncryptionKey` per la capacità in cui si vuole abilitare la crittografia BYOK.

## <a name="manage-byok"></a>Gestire BYOK

Power BI offre altri cmdlet per gestire la crittografia BYOK nel tenant:

- Usare `Get-PowerBIEncryptionKey` per ottenere la chiave attualmente in uso nel tenant:

    ```powershell
    Get-PowerBIEncryptionKey
    ```

- Usare `Get-PowerBIWorkspaceEncryptionStatus` per vedere se i set di dati in un'area di lavoro vengono crittografati e se il relativo stato di crittografia è sincronizzato con l'area di lavoro:

    ```powershell
    Get-PowerBIWorkspaceEncryptionStatus -Name'Contoso Sales'
    ```

    Si noti che la crittografia è abilitata a livello di capacità, ma lo stato della crittografia viene ottenuto a livello di set di dati per l'area di lavoro specificata.

- Usare `Set-PowerBICapacityEncryptionKey` per aggiornare la chiave di crittografia per la capacità di Power BI:

    ```powershell
    Set-PowerBICapacityEncryptionKey-CapacityId 08d57fce-9e79-49ac-afac-d61765f97f6f -KeyName 'Contoso Sales'
    ```

- `Use Switch-PowerBIEncryptionKey` per cambiare (o _ruotare_) la chiave attualmente usata per la crittografia. Il cmdlet aggiorna semplicemente l'elemento `-KeyVaultKeyUri` per una chiave `-Name`:

    ```powershell
    Switch-PowerBIEncryptionKey -Name'Contoso Sales' -KeyVaultKeyUri'https://contoso-vault2.vault.azure.net/keys/ContosoKeyVault/b2ab4ba1c7b341eea5ecaaa2wb54c4d2'
    ```