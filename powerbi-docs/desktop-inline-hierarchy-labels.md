---
title: Usare le etichette di gerarchia inline in Power BI Desktop
description: Usare le etichette di gerarchia inline in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 8762be72353aa779281d721ac8038b6e3dd16aa2
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65454244"
---
# <a name="use-inline-hierarchy-labels-in-power-bi-desktop"></a>Usare le etichette di gerarchia inline in Power BI Desktop
**Power BI Desktop** supporta l'uso di **etichette di gerarchia inline**, ovvero la prima di due funzionalità che consentono di ottimizzare l'esplorazione gerarchica. La seconda funzionalità, che è attualmente in fase di sviluppo, è la possibilità di usare le etichette di gerarchia annidate (a breve disponibile: gli aggiornamenti avvengono di frequente).   

## <a name="how-inline-hierarchy-labels-work"></a>Funzionamento delle etichette di gerarchia inline
Le etichette di gerarchia inline permettono di visualizzare le etichette di gerarchia quando si espandono gli oggetti visivi usando la funzionalità **Espandi tutto**. Un grande vantaggio offerto dalla visualizzazione di queste etichette di gerarchia è che è anche possibile scegliere di eseguire l'**ordinamento** in base alle diverse etichette di gerarchia quando si espandono i dati gerarchici.

### <a name="using-the-built-in-expand-feature-without-sorting-by-hierarchy-labels"></a>Uso della funzionalità Espandi predefinita (senza l'ordinamento in base alle etichette di gerarchia)
Prima di passare al funzionamento delle etichette di gerarchia inline verrà preso in esame il comportamento della funzionalità **Espandi al livello successivo** predefinita. In tal modo sarà possibile comprendere (e apprezzare) quanto siano utili le etichette di gerarchia inline.

L'immagine seguente mostra un grafico a barre per le vendite annuali. Quando si fa clic con il pulsante destro del mouse su una barra, è possibile scegliere **Espandi al livello successivo**.

![Menu di scelta rapida Espandi](media/desktop-inline-hierarchy-labels/desktop-inline-hierarchy-labels-menu.png)

> [!NOTE]
> In alternativa al clic con il pulsante destro del mouse su una barra, è possibile selezionare il pulsante *Espandi* nella parte superiore sinistra della visualizzazione.

  ![Pulsante Espandi](media/desktop-inline-hierarchy-labels/desktop-inline-hierarchy-labels-expand-button-finger.png)


Quando si seleziona **Espandi al livello successivo** l'oggetto visivo espande la gerarchia di date da *Anno* a *Trimestre*, come illustrato nella figura seguente.

![Oggetto visivo espanso per anno e trimestre](media/desktop-inline-hierarchy-labels/desktop-inline-hierarchy-labels-qty-year-quarter.png)

Come si può notare, le etichette *Anno* e *Trimestre* sono visualizzate inline insieme. Questo schema di etichettatura continua mentre si **espande tutto** fino al termine della gerarchia.

![Oggetto visivo espanso per anno, trimestre e mese](media/desktop-inline-hierarchy-labels/desktop-inline-hierarchy-labels-qty-year-quarter-month.png)

Questo è il comportamento della gerarchia *Data* predefinita, che è associata ai campi con un tipo di dati *Data/ora*. Passando alla sezione successiva verranno prese in esame le differenze della nuova funzionalità di etichette di gerarchia inline.

### <a name="using-inline-hierarchy-labels"></a>Uso delle etichette di gerarchia inline
Prima di tutto verrà preso in esame un grafico differente, che usa dati con gerarchia informali. Nella figura seguente è rappresentato un grafico a barre con il valore **Quantity**, che usa *ProductName* come asse. In questi dati *ProductName* e *ShipCountry* formano una gerarchia informale. A questo punto è possibile selezionare nuovamente *Espandi al livello successivo* per eseguire il drill-down nella gerarchia.

![Grafico con gerarchia informale](media/desktop-inline-hierarchy-labels/desktop-inline-hierarchy-labels-informal-top-expand.png)

Se si seleziona **Espandi al livello successivo**, viene visualizzato il livello successivo con la visualizzazione inline delle etichette di gerarchia. Per impostazione predefinita, le gerarchie inline vengono ordinate in base il valore della misura, in questo caso, **Quantity**. Con le etichette di gerarchia inline abilitate, è possibile scegliere di ordinare i dati anche in base alla gerarchia, selezionando i puntini di sospensione nell'angolo superiore destro ( **...** ), quindi selezionando **Ordina per ProductName ShipCountry**, come illustrato nella figura seguente.

![Grafico con gerarchia informale ordinata in base all'impostazione predefinita](media/desktop-inline-hierarchy-labels/desktop-inline-hierarchy-labels-informal-sort-quantity.png)

Dopo la selezione di **ShipCountry**, i dati vengono ordinati in base alla selezione della gerarchia informale, come illustrato nella figura seguente.

![Grafico con gerarchia informale ordinata in base alla gerarchia informale](media/desktop-inline-hierarchy-labels/desktop-inline-hierarchy-labels-informal-sorted.png)

> [!NOTE]
> La funzionalità di etichetta gerarchia inline non consente ancora di ordinare la gerarchia temporale predefinita in base al valore, ma solo in ordine gerarchico.
> 
> 

## <a name="troubleshooting"></a>Risoluzione dei problemi
Gli oggetti visivi potrebbero rimanere bloccati in uno stato espanso al livello di gerarchia inline. In alcuni casi, alcuni oggetti visivi potrebbero rimanere bloccati nella modalità in cui sono stati espansi, nel qual caso il drill-up non funziona. Questa situazione può verificarsi se è stata eseguita la procedura seguente (la soluzione per questo problema è indicata *dopo* questi passaggi):

Passaggi che potrebbero determinare il blocco degli oggetti visivi in uno stato espanso:

1. Si abilita la funzionalità di **etichetta di gerarchia inline**.
2. Si creano alcuni oggetti visivi con gerarchie.
3. Si seleziona **Espandi tutto** e si salva il file.
4. Si *disabilita* quindi la funzionalità di **etichetta di gerarchia inline** e si riavvia Power BI Desktop.
5. A questo punto, si riapre il file.

Se per caso sono stati eseguiti questi passaggi e gli oggetti visivi restano bloccati in modalità espansa, seguire questa procedura per risolvere il problema:

1. Abilitare nuovamente la funzionalità di **etichetta di gerarchia inline**, quindi riavviare Power BI Desktop.
2. Aprire nuovamente il file ed eseguire il drill-up fino all'oggetto visivo interessato.
3. Salvare il file.
4. Disabilitare la funzionalità di **etichetta di gerarchia inline**, quindi riavviare Power BI Desktop.
5. Aprire di nuovo il file.

In alternativa, è sufficiente eliminare l'oggetto visivo e ricrearlo.

