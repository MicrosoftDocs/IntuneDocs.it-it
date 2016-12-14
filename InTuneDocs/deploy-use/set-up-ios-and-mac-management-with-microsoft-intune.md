---
title: Configurare la gestione dei dispositivi iOS e Mac con Microsoft Intune
description: Abilitare la gestione di dispositivi mobili (MDM) per dispositivi iOS, inclusi iPad e iPhone, e dispositivi Mac OS X con Microsoft Intune.
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 11/17/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc451224-1372-4b84-b641-cfa67cb3849b
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6adfb7375f9747f64e7037164f48918789bd7ee0
ms.openlocfilehash: 641d2db2bfb49ce6c4f88d823188a714e61f683c


---

# <a name="set-up-ios-and-mac-device-management"></a>Configurare la gestione dei dispositivi iOS e Mac
Intune consente la gestione dei dispositivi mobili (MDM) iPad, iPhone e Mac OS X e offre agli utenti accesso alla posta elettronica e alle app aziendali. Affinché Intune gestisca i dispositivi iOS e Mac, è necessario un dispositivo Apple Push Notification Service. Dopo aver aggiunto il certificato a Intune, gli utenti possono installare l'app Portale aziendale per registrare i propri dispositivi. In alternativa, l'amministratore può configurare la [gestione dei dispositivi iOS di proprietà dell'azienda](enroll-corporate-owned-ios-devices-in-microsoft-intune.md).

1.  **Configurare Intune**<br>
    Se non è stato già fatto, preparare la gestione di dispositivi mobili (MDM) [impostando l'autorità di gestione di dispositivi mobili](prerequisites-for-enrollment.md#step-2-set-mdm-authority), ad esempio **Microsoft Intune**, e configurando MDM.

2.  **Ottenere una richiesta di firma del certificato**<br>
    Gli utenti amministratori possono aprire la [console di amministrazione di Microsoft Intune](http://manage.microsoft.com), fare clic su **Amministrazione** &gt; ** Gestione dei dispositivi mobili** &gt; **iOS e Mac OS X** &gt; **Carica un certificato APNs** e quindi scegliere **Scarica richiesta di certificato APN**. Salvare il file della richiesta di firma del certificato (estensione csr) in locale. Questo file viene usato per richiedere un certificato di relazione di trust al portale Apple Push Certificates.

    ![Caricare la finestra di dialogo del certificato APN](../media/Intune-iOS-enrollment-with-apns.png)

3.  **Ottenere un certificato di Apple Push Notification Service**<br>
    Visitare il [portale Apple Push Certificates](http://go.microsoft.com/fwlink/?LinkId=269844) e accedere con il proprio ID Apple per creare il certificato APN usando il file con estensione csr. Dopo aver scelto **Upload** (Carica) nel portale Apple Push Certificates si riceverà un file con estensione json che non può essere usato per il servizio APN. Completare il download e tornare al portale Apple Push Certificates per **Certificates for Third-Party Servers** (Certificati per server di terze parti) e fare clic su **Download** (Scarica).

    Scaricare il certificato APN (con estensione pem) e salvare il file in locale.

    > [!NOTE]
    > Questo certificato APN dovrà essere rinnovato (non sostituito) ogni anno. Usare lo stesso ID Apple per accedere al portale Apple Push Certificates per rinnovare il certificato e quindi usare le stesse istruzioni in questo argomento per scaricare il certificato e caricarlo in Intune.

4.  **Aggiungere il certificato APN a Intune**<br>
    Nella [console di amministrazione di Microsoft Intune](http://manage.microsoft.com), fare clic su **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **iOS e Mac OS X** &gt; **Carica un certificato APNs** e quindi scegliere **Carica il certificato APNs**. Passare al file (con estensione pem) del certificato, scegliere **Apri** e quindi immettere l'**ID Apple**. Con il certificato APN Intune può registrare e gestire i dispositivi iOS effettuando il push dei criteri nei dispositivi mobili registrati.

5.  **Indicare agli utenti come registrare i propri dispositivi per accedere alle risorse aziendali.**

    Per istruzioni sulla registrazione da parte degli utenti finali, vedere [Registrare il dispositivo iOS in Intune](../enduser/enroll-your-device-in-intune-ios.md) e [Registrare il dispositivo Mac OS X in Intune](../enduser/enroll-your-device-in-intune-macos.md). Il processo di registrazione indica agli utenti cosa possono aspettarsi e i dati visibili o meno agli amministratori IT nei propri dispositivi.

    Per informazioni su altre attività dell'utente finale, vedere gli articoli seguenti:
    - [Informazioni sull'uso di Microsoft Intune per gli utenti finali](what-to-tell-your-end-users-about-using-microsoft-intune.md)
    - [Uso del dispositivo iOS o Mac OS con Intune](../enduser/using-your-ios-or-mac-os-x-device-with-intune.md)

Se l'azienda o l'organizzazione acquista dispositivi iOS per gli utenti, i dispositivi possono anche essere registrati per la gestione come [dispositivi iOS di proprietà dell'azienda](enroll-corporate-owned-ios-devices-in-microsoft-intune.md).

### <a name="see-also"></a>Vedere anche
[Prerequisiti per la registrazione in Microsoft Intune](prerequisites-for-enrollment.md)



<!--HONumber=Dec16_HO2-->

