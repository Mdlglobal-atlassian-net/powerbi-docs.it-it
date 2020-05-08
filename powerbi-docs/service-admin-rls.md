---
title: Sicurezza a livello di riga con Power BI
description: Come configurare la sicurezza a livello di riga per i set di dati importati e DirectQuery nel servizio Power BI.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.author: kfollis
ms.date: 12/05/2019
ms.custom: seodec18
LocalizationGroup: Administration
ms.openlocfilehash: 70f10620932708dd178b635f966a55f8139cde65
ms.sourcegitcommit: 220910f0b68cb1e265ccd5ac0cee4ee9c6080b26
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82841159"
---
# <a name="row-level-security-rls-with-power-bi"></a>Sicurezza a livello di riga con Power BI

La sicurezza a livello di riga con Power BI può essere usata per limitare l'accesso ai dati per determinati utenti. I filtri limitano l'accesso ai dati a livello di riga ed è possibile definirli all'interno dei ruoli. Tenere presente che nel servizio Power BI i membri di un'area di lavoro hanno accesso ai set di dati presenti nell'area di lavoro. La sicurezza a livello di riga non limita l'accesso a questi dati.

È possibile configurare la sicurezza a livello di riga per i modelli di dati importati in Power BI con Power BI Desktop. È anche possibile configurare la sicurezza a livello di riga nei set di dati che usano DirectQuery, ad esempio SQL Server. In precedenza, era possibile implementare la sicurezza a livello di riga solo nei modelli di Analysis Services all'esterno di Power BI. Per le connessioni dinamiche di Analysis Services o Azure Analysis Services, è possibile configurare la sicurezza a livello di riga nel modello, non in Power BI Desktop. L'opzione di sicurezza non verrà visualizzata per i set di dati di connessione dinamica.

[!INCLUDE [include-short-name](./includes/rls-desktop-define-roles.md)]

Per impostazione predefinita, i filtri per la sicurezza a livello di riga usano i filtri unidirezionali, indipendentemente dal fatto che le relazioni siano impostate su unidirezionali o bidirezionali. È possibile abilitare manualmente il filtro incrociato bidirezionale con la sicurezza a livello di riga selezionando la selezione e selezionando la casella di controllo **Applica filtro di sicurezza in entrambe le direzioni**. È consigliabile selezionare questa casella quando è stata implementata anche la sicurezza a livello di riga dinamica a livello di server, in cui la sicurezza a livello di riga si basa sul nome utente o sull'ID di accesso.

Per altre informazioni, vedere [Filtro incrociato bidirezionale con DirectQuery in Power BI Desktop](desktop-bidirectional-filtering.md) e l'articolo tecnico [Securing the Tabular BI Semantic Model](https://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/Securing%20the%20Tabular%20BI%20Semantic%20Model.docx) (Protezione del modello semantico tabulare di BI).

![Applicare il filtro di sicurezza](media/service-admin-rls/rls-apply-security-filter.png)


[!INCLUDE [include-short-name](./includes/rls-desktop-view-as-roles.md)]

## <a name="manage-security-on-your-model"></a>Gestire la sicurezza nel modello

Per gestire la sicurezza nel modello di dati, si dovranno eseguire le operazioni seguenti.

1. Selezionare i **puntini di sospensione (…)** accanto a un set di dati.
2. Scegliere **Sicurezza**.
   
   ![Applica filtro di sicurezza in entrambe le direzioni](media/service-admin-rls/rls-security.png)

Verrà visualizzata la pagina della sicurezza a livello di riga per aggiungere membri a un ruolo che è stato creato in Power BI Desktop. Solo i proprietari del set di dati potranno visualizzare l'opzione Sicurezza. Se il set di dati è in un gruppo, l'opzione di sicurezza sarà visibile solo per gli amministratori del gruppo. 

È possibile creare o modificare i ruoli solo all'interno di Power BI Desktop.

## <a name="working-with-members"></a>Utilizzo dei membri

### <a name="add-members"></a>Aggiungere membri

È possibile aggiungere un membro al ruolo digitando l'indirizzo di posta elettronica, o il nome, dell'utente, del gruppo di sicurezza o della lista di distribuzione da aggiungere. Non è possibile aggiungere gruppi creati all'interno di Power BI. È possibile aggiungere membri [esterni all'organizzazione](guidance/whitepaper-azure-b2b-power-bi.md#data-security-for-external-partners).

![Aggiungere un membro](media/service-admin-rls/rls-add-member.png)

È anche possibile stabilire il numero di membri che fanno parte del ruolo in base al numero indicato tra parentesi accanto al nome del ruolo o accanto a Membri.

![Membri nel ruolo](media/service-admin-rls/rls-member-count.png)

### <a name="remove-members"></a>Rimuovere membri

È possibile rimuovere i membri selezionando l'icona X accanto al nome. 

![Rimuovere un membro](media/service-admin-rls/rls-remove-member.png)

## <a name="validating-the-role-within-the-power-bi-service"></a>Convalida del ruolo all'interno del servizio Power BI

È possibile convalidare il corretto funzionamento del ruolo definito testandolo. 

1. Selezionare **Altre opzioni** (...) accanto al ruolo.
2. Selezionare **Test dei dati come ruolo**

![Test come ruolo](media/service-admin-rls/rls-test-role.png)

Verranno visualizzati i report disponibili per questo ruolo. I dashboard non vengono presentati in questa visualizzazione. La barra blu sopra indica cosa viene applicato.

![Visualizzazione come <ruolo>](media/service-admin-rls/rls-test-role2.png)

È possibile testare altri ruoli, o combinazioni di ruoli, selezionando **Visualizzazione attuale come**.

![Testare altri ruoli](media/service-admin-rls/rls-test-role3.png)

È possibile scegliere di visualizzare i dati come un utente specifico oppure è possibile selezionare una combinazione dei ruoli disponibili per convalidarne il funzionamento. 

Per tornare alla visualizzazione normale, selezionare **Torna alla sicurezza a livello di riga**.

[!INCLUDE [include-short-name](./includes/rls-usernames.md)]

## <a name="using-rls-with-workspaces-in-power-bi"></a>Usare la sicurezza a livello di riga con le aree di lavoro in Power BI

Se si pubblica il report di Power BI Desktop in un'area di lavoro all'interno del servizio Power BI, i ruoli verranno applicati ai membri di sola lettura. Sarà necessario indicare che i membri possono visualizzare il contenuto di Power BI solo entro le impostazioni dell'area di lavoro.

> [!WARNING]
> Se l'area di lavoro è stata configurata in modo da assegnare le autorizzazioni di modifica ai membri, i ruoli di sicurezza a livello di riga non verranno applicati. Gli utenti riusciranno a visualizzare tutti i dati.

![Impostazioni dei gruppi](media/service-admin-rls/rls-group-settings.png)

[!INCLUDE [include-short-name](./includes/rls-limitations.md)]

[!INCLUDE [include-short-name](./includes/rls-faq.md)]

## <a name="next-steps"></a>Passaggi successivi
[Sicurezza a livello di riga con Power BI Desktop](desktop-rls.md)  

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
