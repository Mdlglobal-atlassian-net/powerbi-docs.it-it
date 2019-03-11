---
title: Usare SAML per l'accesso Single Sign-On (SSO) alle origini dati locali
description: Configurare il gateway con SAML (Security Assertion Markup Language) per abilitare Single Sign-On (SSO) da Power BI alle origini dati locali.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 03/05/2019
LocalizationGroup: Gateways
ms.openlocfilehash: c1ca797efa2e40bf74384a1e9f2362acd26c6f8f
ms.sourcegitcommit: 883a58f63e4978770db8bb1cc4630e7ff9caea9a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/07/2019
ms.locfileid: "57555652"
---
# <a name="use-security-assertion-markup-language-saml-for-single-sign-on-sso-from-power-bi-to-on-premises-data-sources"></a>Usare SAML (Security Assertion Markup Language) per abilitare Single Sign-On (SSO) da Power BI alle origini dati locali

Usare [SAML (Security Assertion Markup Language)](https://www.onelogin.com/pages/saml) per abilitare la connettività Single Sign-On. L'abilitazione di SSO rende più semplice per i report e i dashboard di Power BI aggiornare i dati delle origini locali.

## <a name="supported-data-sources"></a>Origini dati supportate

Attualmente sono supportate le origini dati SAP HANA con SAML. Per altre informazioni sull'impostazione e la configurazione di Single Sign-On per SAP HANA tramite SAML, vedere l'argomento [SAML SSO for BI Platform to HANA](https://wiki.scn.sap.com/wiki/display/SAPHANA/SAML+SSO+for+BI+Platform+to+HANA) (SSO SAML per la piattaforma BI per HANA) nella documentazione di SAP HANA.

Sono supportate ulteriori origini dati con [Kerberos](service-gateway-sso-kerberos.md).

## <a name="configuring-the-gateway-and-data-source"></a>Configurazione del gateway e dell'origine dati

Per usare SAML, generare innanzitutto un certificato per il provider di identità SAML, quindi eseguire il mapping di un utente di Power BI all'identità.

1. Generare un certificato. Assicurarsi di usare il nome di dominio completo del server SAP HANA quando si specifica il *nome comune*. Il certificato scade tra 365 giorni.

    ```
    openssl req -newkey rsa:2048 -nodes -keyout samltest.key -x509 -days 365 -out samltest.crt
    ```

1. In SAP HANA Studio fare clic con il pulsante destro del mouse sul server SAP HANA, quindi passare a **Security** (Sicurezza)  > **Open Security Console** (Apri console sicurezza)  > **SAML Identity Provider** (Provider identità SAML)  > **OpenSSL Cryptographic Library** (Libreria di crittografia OpenSSL).

    È anche possibile usare la libreria di crittografia SAP (nota anche come CommonCryptoLib o sapcrypto) invece di OpenSSL per completare questa procedura di configurazione. Consultare la documentazione ufficiale di SAP per altre informazioni.

1. Selezionare **Import** (Importa), passare a samltest.crt e importare il file.

    ![Provider di identità](media/service-gateway-sso-saml/identity-providers.png)

1. In SAP HANA Studio selezionare la cartella **Security** (Sicurezza).

    ![Cartella Security (Sicurezza)](media/service-gateway-sso-saml/security-folder.png)

1. Espandere **Users** (Utenti) quindi selezionare l'utente a cui si vuole eseguire il mapping dell'utente di Power BI.

1. Selezionare **SAML**, quindi **Configure** (Configura).

    ![Configurare SAML](media/service-gateway-sso-saml/configure-saml.png)

1. Selezionare il provider di identità creato nel passaggio 2. Per **External Identity** (Identità esterna), immettere l'UPN dell'utente di Power BI, quindi selezionare **Add** (Aggiungi).

    ![Selezionare il provider di identità](media/service-gateway-sso-saml/select-identity-provider.png)

Dopo aver configurato il certificato e l'identità, convertire il certificato in formato pfx e configurare il computer gateway per l'uso del certificato.

1. Convertire il certificato in formato pfx eseguendo il comando seguente.

    ```
    openssl pkcs12 -inkey samltest.key -in samltest.crt -export -out samltest.pfx
    ```

1. Copiare il file pfx nel computer gateway:

    1. Fare doppio clic su samltest.pfx, quindi selezionare **Local Machine** (Computer locale)  > **Next** (Avanti).

    1. Immettere la password e quindi selezionare **Next** (Avanti).

    1. Selezionare **Place all certificates in the following store** (Inserire tutti i certificati nell'archivio seguente), quindi **Browse** (Sfoglia)  > **Personal** (Personale)  > **OK**.

    1. Selezionare **Next** (Avanti), quindi **Finish** (Fine).

    ![Importare il certificato](media/service-gateway-sso-saml/import-certificate.png)

1. Concedere all'account di servizio gateway l'accesso alla chiave privata del certificato:

    1. Nel computer gateway eseguire Microsoft Management Console (MMC).

        ![Eseguire MMC](media/service-gateway-sso-saml/run-mmc.png)

    1. In **File** selezionare **Add/Remove Snap-in** (Aggiungi/Rimuovi snap-in).

        ![Aggiungere lo snap-in](media/service-gateway-sso-saml/add-snap-in.png)

    1. Selezionare **Certificates** (Certificati)  > **Add** (Aggiungi), quindi **Computer account** (Account computer)  > **Next** (Avanti).

    1. Selezionare **Local Computer** (Computer locale)  > **Finish** (Fine)  > **OK**.

    1. Espandere **Certificates** (Certificati)  > **Personal** (Personale)  > **Certificates** (Certificati) e individuare il certificato.

    1. Fare clic con il pulsante destro del mouse sul certificato e passare a **All Tasks** (Tutte le attività)  > **Manage Private Keys** (Gestisci chiavi private).

        ![Gestire le chiavi private](media/service-gateway-sso-saml/manage-private-keys.png)

    1. Aggiungere l'account di servizio gateway all'elenco. Per impostazione predefinita, l'account è **NT SERVICE\PBIEgwService**. È possibile individuare l'account in cui è in esecuzione il servizio gateway eseguendo **services.msc** e trovando il **servizio gateway dati locale**.

        ![Servizio gateway](media/service-gateway-sso-saml/gateway-service.png)

Infine, seguire questa procedura per aggiungere l'identificazione personale del certificato alla configurazione del gateway.

1. Eseguire il comando PowerShell per visualizzare l'elenco dei certificati nel computer.

    ```powershell
    Get-ChildItem -path cert:\LocalMachine\My
    ```
1. Copiare l'identificazione personale per il certificato creato.

1. Passare alla directory del gateway il cui percorso predefinito è C:\Programmi\gateway dati locale.

1. Aprire PowerBI.DataMovement.Pipeline.GatewayCore.dll.config e trovare la sezione \*SapHanaSAMLCertThumbprint\*. Incollare l'identificazione personale copiata.

1. Riavviare il servizio gateway.

## <a name="running-a-power-bi-report"></a>Esecuzione di un report di Power BI

È ora possibile usare la pagina **Gestisci gateway** in Power BI per configurare l'origine dati e abilitare SSO in **Impostazioni avanzate**. È quindi possibile pubblicare report e set di dati associati all'origine dati.

![Impostazioni avanzate](media/service-gateway-sso-saml/advanced-settings.png)

## <a name="troubleshooting"></a>Risoluzione dei problemi

Dopo aver configurato l'accesso SSO, potrebbe essere visualizzato l'errore seguente nel portale di Power BI: "Le credenziali specificate non possono essere usate per l'origine SapHana." Questo errore indica che la credenziale SAML è stata rifiutata da SAP HANA.

Le tracce di autenticazione forniscono informazioni dettagliate per la risoluzione dei problemi relativi alle credenziali in SAP HANA. Seguire questi passaggi per configurare la traccia per il server SAP HANA.

1. Nel server di SAP HANA, attivare la traccia di autenticazione eseguendo la query seguente.

    ```
    ALTER SYSTEM ALTER CONFIGURATION ('indexserver.ini', 'SYSTEM') set ('trace', 'authentication') = 'debug' with reconfigure 
    ```

1. Riprodurre il problema che si è riscontrato.

1. In HANA Studio, aprire la console di amministrazione e passare alla scheda **Diagnosis Files** (File di diagnosi).

1. Aprire la traccia indexserver più recente e cercare SAMLAuthenticator.cpp.

    È necessario trovare un messaggio di errore dettagliato che indica la causa principale, come nell'esempio seguente.

    ```
    [3957]{-1}[-1/-1] 2018-09-11 21:40:23.815797 d Authentication   SAMLAuthenticator.cpp(00091) : Element '{urn:oasis:names:tc:SAML:2.0:assertion}Assertion', attribute 'ID': '123123123123123' is not a valid value of the atomic type 'xs:ID'.
    [3957]{-1}[-1/-1] 2018-09-11 21:40:23.815914 i Authentication   SAMLAuthenticator.cpp(00403) : No valid SAML Assertion or SAML Protocol detected
    ```

1. Dopo aver completato la risoluzione dei problemi, disattivare la traccia di autenticazione eseguendo la query seguente.

    ```
    ALTER SYSTEM ALTER CONFIGURATION ('indexserver.ini', 'SYSTEM') UNSET ('trace', 'authentication');
    ```

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su **Gateway dati locale** e su **DirectQuery**, vedere le risorse seguenti:

* [Gateway dati locale](service-gateway-onprem.md)
* [DirectQuery in Power BI](desktop-directquery-about.md)
* [Data sources supported by DirectQuery](desktop-directquery-data-sources.md) (Origini dati supportate da DirectQuery)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery and SAP HANA](desktop-directquery-sap-hana.md) (DirectQuery e SAP HANA)
