---
title: Inviare un oggetto visivo di Power BI ad AppSource usando il Dashboard venditori
description: Inviare un oggetto visivo di Power BI ad AppSource usando il Dashboard venditori
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 12/03/2019
ms.openlocfilehash: 73a6a3d16ae2515af41a3232a37579e18876f38b
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/04/2020
ms.locfileid: "75223679"
---
# <a name="submit-a-power-bi-visual-to-appsource-using-seller-dashboard"></a>Inviare un oggetto visivo di Power BI ad AppSource usando il Dashboard venditori

È necessario inviare un messaggio di posta elettronica con allegati il file con estensione **pbiviz** e il file con estensione **pbix** al team di Power BI prima dell'invio ad AppSource. Ciò consente al team di Power BI di caricare i file nel server di condivisione pubblico. In caso contrario, lo Store non potrà recuperare i file. È necessario inviare i file con i nuovi invii di oggetti visivi Power BI, gli aggiornamenti degli oggetti Power BI esistenti e le correzioni degli invii rifiutati.

>[!NOTE]
>Il [Dashboard venditori](https://docs.microsoft.com/office/dev/store/use-the-seller-dashboard-to-submit-to-the-office-store) verrà gradualmente sostituito. Il programma sostitutivo è il [Centro per i partner](https://docs.microsoft.com/partner-center/). Usare il Dashboard venditori solo se è già in corso l'invio di un oggetto visivo di Power BI. Se si sta inviando ad AppSource un nuovo oggetto visivo di Power BI, usare il [metodo Centro per i partner](office-store.md#submitting-to-appsource).

### <a name="seller-dashboard-submission-process"></a>Processo di invio Dashboard venditori

Per accedere al [centro per sviluppatori Office](https://dev.office.com/) è necessario avere un account sviluppatore di Office valido, che deve essere un account Microsoft Live ID, ad esempio hotmail.com o outlook.com.

1. Passare al [centro per sviluppatori](https://sellerdashboard.microsoft.com/Application/Summary).

2. Selezionare **Aggiungi una nuova app**.

    ![Aggiungi un'app](media/office-store/powerbi-custom-visual-add-an-app.png)

3. Selezionare **Oggetto visivo personalizzato di Microsoft Power BI** e quindi **Avanti**.

4. Selezionare il segno **+** sotto **Pacchetto dell'app** e selezionare il file XML del pacchetto dell'app ricevuto dal team di Power BI dalla finestra di dialogo Apri file.

    ![Pacchetto app](media/office-store/powerbi-custom-visual-apppackage.png)

5. Si dovrebbe ricevere la conferma della validità del pacchetto dell'app di Power BI.

    ![Manifesto approvato](media/office-store/powerbi-custom-visual-manifest-approved.png)

6. Compilare i dettagli in **Informazioni generiche**.

   * *Titolo invio:* il modo in cui verrà denominato l'invio nel centro sviluppatori.
   * *Versione:* il numero di versione viene compilato automaticamente dal pacchetto dell'app del componente aggiuntivo.
   * *Data di rilascio (UTC):* selezionare una data per il rilascio dell'app nello store. Se si sceglie una data futura, l'app non sarà disponibile nello store fino al raggiungimento di tale data.
   * *Categoria:* la prima categoria verrà automaticamente compilata come "Visualizzazione dati + BI". Tutti gli oggetti visivi di Power BI vengono contrassegnati in questo modo. Per aiutare gli utenti a trovare facilmente l'oggetto visivo è possibile specificare fino a due categorie aggiuntive.
   * *Note per i test:* facoltativo, se si vogliono fornire istruzioni per i tester di Microsoft
   * *L'app chiama, supporta, contiene o usa la crittografia:* lasciare deselezionato
   * *Rendi disponibile questo componente aggiuntivo nel catalogo dei componenti aggiuntivi per Office per iPad:* lasciare deselezionato
7. Caricare il logo dell'oggetto visivo selezionando il segno **+** sotto **Logo dell'app**. Selezionare quindi il file dell'icona nella finestra di dialogo Apri file. Il file deve essere in formato PNG, JPG, JPEG o GIF. Le dimensioni devono essere esattamente pari a 300 px (larghezza) x 300 px (altezza) e il file deve avere dimensioni massime di 512 KB.

    ![Logo dell'app](media/office-store/powerbi-custom-visual-app-logo.png)

8. Compilare i dettagli in **Documenti di supporto**.

   * Collegamento al documento di supporto
   * Collegamento al documento sulla privacy
   * Collegamento video
   * Contratto di licenza con l'utente finale (EULA)

       È necessario caricare un file del contratto di licenza. Può essere il proprio contratto di licenza oppure si può usare il contratto di licenza predefinito in Office Store per gli oggetti visivi di Power BI. Per usare il contratto di licenza predefinito, incollare l'URL seguente nella finestra di dialogo di caricamento del file "Contratto di licenza con l'utente finale" del dashboard del venditore: [https://visuals.azureedge.net/app-store/Power BI - Default Custom Visual EULA.pdf](https://visuals.azureedge.net/app-store/Power%20BI%20-%20Default%20Custom%20Visual%20EULA.pdf).

9. Selezionare **Avanti** e proseguire alla pagina **Dettagli**.

10. Selezionare **Lingua** e scegliere una lingua dall'elenco.

    ![Lingua](media/office-store/powerbi-custom-visual-language.png)

11. Immettere le informazioni necessarie in "Descrizione".

    * *Nome app (per questa lingua):* immettere il titolo dell'app così come dovrebbe apparire nella pagina principale dello store.
    * *Descrizione breve:* immettere una breve descrizione dell'app, fino a 100 caratteri, così come dovrebbe apparire nella pagina principale dello store. Questa descrizione verrà visualizzata nelle pagine di livello superiore insieme al logo. È possibile usare la descrizione del pacchetto PBIVIZ.
    * *Descrizione lunga:* fornire una descrizione più dettagliata dell'app che i clienti vedranno nella pagina dei dettagli dell'app. Per chiedere alla community di migliorare il proprio oggetto visivo rendendolo open source, fornire qui il collegamento all'archivio pubblico, ad esempio GitHub.

12. Caricare almeno una schermata. Il formato può essere PNG, JPG, JPEG o GIF. Deve avere dimensioni pari esattamente a 1366 px (larghezza) x 768 px (altezza). Le dimensioni del file non possono essere maggiori di 1024 KB. *Per un migliore utilizzo, aggiungere fumetti di testo per descrivere la proposta di valore delle caratteristiche basilari in ogni schermata.*

12. Per aggiungere altre lingue, selezionare **Aggiungi una lingua** e ripetere i passaggi 10 e 11. L'aggiunta di altre lingue consentirà agli utenti di visualizzare i dettagli dell'oggetto visivo personalizzato nella propria lingua. Per impostazione predefinita, per le lingue non elencate verrà configurata la prima lingua selezionata.

13. Dopo aver aggiunto le lingue, selezionare **Avanti** per proseguire alla pagina **Blocca accesso**.

14. Se si vuole impedire a clienti in paesi specifici di usare o acquistare l'app, selezionare la casella di controllo e selezionare dall'elenco.

15. Selezionare **Avanti** e proseguire alla pagina **Prezzi**.

16. Attualmente, sono supportati solo oggetti visivi *gratuiti* e gli acquisti aggiuntivi all'interno dell'oggetto visivo (acquisto in-app) non sono consentiti. Selezionare **Questa app è gratuita**.

    > [!NOTE]
    > Se si seleziona un'altra opzione diversa da gratuita o se è presente del contenuto acquistato in-app nell'oggetto visivo inviato, l'invio verrà rifiutato.

17. È ora possibile selezionare **Salva come bozza** e inviare in seguito oppure selezionare **Invia per approvazione** per inviare l'oggetto visivo personalizzato a Office Store.

## <a name="seller-dashboard-certification-submission-process"></a>Processo di invio della certificazione del Dashboard venditori

Seguire le istruzioni riportate in questa sezione per inviare un oggetto visivo di Power BI per la certificazione nel Dashboard venditori. Usare questo metodo se in precedenza è già stato inviato un oggetto visivo di Power BI ad AppSource usando il Dashboard venditori.

1. Inviare un messaggio di posta elettronica al team del supporto tecnico degli oggetti visivi di Power BI (pbicvsupport@microsoft.com). Nel messaggio di posta elettronica, includere le seguenti informazioni:
    * Titolo: Richiesta di certificazione oggetto visivo
    * Collegamento al repository GitHub in cui è ospitato il codice sorgente leggibile dell'oggetto visivo
    * [Adesione ai requisiti](power-bi-custom-visuals-certified.md#certification-requirements)
    * Revisione del codice superata

2. Il team degli oggetti visivi di Microsoft Power BI invia una notifica quando l'oggetto visivo di Power BI viene certificato e aggiunto all'elenco degli [oggetti visivi certificati di Power BI](power-bi-custom-visuals-certified.md#certified-power-bi-visuals) o rifiutato con un report dei problemi che devono essere corretti. È responsabilità dello sviluppatore mantenere una linea di comunicazione aperta con Microsoft e aggiornare gli oggetti visivi certificati in base alle esigenze.

## <a name="tracking-submission-status-and-usage"></a>Rilevamento dello stato e dell'utilizzo dell'invio

È possibile esaminare il [criteri di convalida](https://dev.office.com/officestore/docs/validation-policies#13-power-bi-custom-visuals).

Dopo l'invio, sarà possibile visualizzare lo stato di invio nel [dashboard dell'app](https://sellerdashboard.microsoft.com/Application/Summary/).

## <a name="certify-your-visual"></a>Certificare l'oggetto visivo

Dopo aver creato l'oggetto visivo è possibile ottenere la [certificazione](../developer/power-bi-custom-visuals-certified.md) per l'oggetto.

## <a name="next-steps"></a>Passaggi successivi

[Developing a Power BI custom visual](visuals/custom-visual-develop-tutorial.md) (Sviluppo di un oggetto visivo personalizzato di Power BI)  
[Visualizzazioni in Power BI](../visuals/power-bi-report-visualizations.md)  
[Visualizzazioni personalizzate in Power BI](../developer/power-bi-custom-visuals.md)  
[Ottenere la certificazione di un oggetto visivo di Power BI](../developer/power-bi-custom-visuals-certified.md)

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
