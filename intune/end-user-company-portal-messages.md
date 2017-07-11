---
title: Messaggi dell'app Portale aziendale visualizzati dagli utenti in Android
description: Descrive i messaggi dell'app Portale aziendale che possono essere visualizzati dagli utenti finali di Intune.
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 03/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3df993aa-48c5-4799-b68d-c85fe4f7b02c
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: ae0bd848413fc82f68f2ce6e6ac55fe92b9cb989
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="help-end-users-understand-company-portal-app-messages"></a>Consentire agli utenti finali di comprendere i messaggi dell'app Portale aziendale

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

> [!NOTE]
> Le informazioni seguenti si applicano solo ai dispositivi Android 6.0 e versioni successive.

In diverse fasi del processo di registrazione vengono visualizzati due messaggi che possono essere motivo di preoccupazione per gli utenti.

- __Allow Company Portal to make and manage phone calls? (Consentire a Portale aziendale di effettuare e gestire chiamate telefoniche?)__
- __Allow Company Portal to access photos, media, and files on your device?__ (Consentire a Portale aziendale di accedere a foto, elementi multimediali e file nel dispositivo?)

## <a name="allow-company-portal-to-make-and-manage-phone-calls"></a>Consentire a Portale aziendale di effettuare e gestire chiamate telefoniche?

### <a name="where-it-appears"></a>Dove viene visualizzato
Il testo del messaggio **Allow Company Portal to make and manage phone calls?** (Consentire a Portale aziendale di effettuare e gestire chiamate telefoniche?) viene visualizzato quando gli utenti toccano **Registra** nell'app Portale aziendale durante la registrazione del dispositivo.

### <a name="what-it-means"></a>Che cosa significa
Accettando questa richiesta, gli utenti acconsentono all'invio del numero di telefono e del codice IMEI del proprio dispositivo al servizio Intune. Questi valori verranno visualizzati nella pagina __Hardware__ della console di amministrazione.

> [!NOTE]
> **The Company Portal app never makes or manages phone calls!** (L'app Portale aziendale non effettua o gestisce mai chiamate telefoniche.) Il testo del messaggio è controllato da Google e non può essere modificato.

Per visualizzare la pagina **Hardware**, accedere a **Gruppi** > **Tutti i dispositivi mobili** > **Dispositivi**. Selezionare il dispositivo dell'utente e passare a **Visualizza proprietà** > **Hardware**.

### <a name="what-happens-if-users-deny-access"></a>Cosa accade se gli utenti negano l'accesso
Se gli utenti negano l'accesso, possono continuare a usare l'app Portale aziendale e registrare il proprio dispositivo. Tuttavia, il numero di telefono e il codice IMEI del dispositivo non verranno visualizzati nella pagina __Hardware__ della console di amministrazione. La seconda volta che gli utenti accedono all'app Portale aziendale dopo aver negato l'accesso, nel messaggio viene visualizzata la casella di controllo **Non visualizzare più questo messaggio** che è possibile selezionare per evitare di visualizzare di nuovo il messaggio.

Se gli utenti consentono l'accesso e in seguito lo negano, il messaggio verrà visualizzato all'accesso successivo all'app Portale aziendale dopo la registrazione.

Se gli utenti decidono di consentire l'accesso in un secondo momento, passare a **Impostazioni** > **App** > **Portale aziendale** > **Autorizzazioni** > **Telefono** e quindi attivare l'autorizzazione.

### <a name="how-to-explain-this-to-your-users"></a>Come spiegare questo agli utenti
Suggerire agli utenti di consultare l'articolo [Registrare il dispositivo Android in Intune](/intune-user-help/enroll-your-device-in-intune-android) per ottenere altre informazioni.

## <a name="allow-company-portal-to-access-your-contacts"></a>Consentire a Portale aziendale di accedere ai contatti?

### <a name="where-it-appears"></a>Dove viene visualizzato
Il messaggio **Allow Company Portal to access your contacts?** (Consentire a Portale aziendale di accedere ai contatti?) viene visualizzato quando l'utente tocca **Registra** nell'app Portale aziendale durante la registrazione del dispositivo.

### <a name="what-it-means"></a>Che cosa significa
Accettando questa richiesta, gli utenti consentono a Intune di creare il proprio account aziendale e gestire l'identità di Azure Active Directory registrata per l'utente nel dispositivo.

> [!NOTE]
> **Microsoft never accesses your contacts!** (Microsoft non accede mai ai contatti dell'utente.) Il testo del messaggio è controllato da Google e non può essere modificato.

### <a name="what-happens-if-users-deny-access"></a>Cosa accade se gli utenti negano l'accesso
Se gli utenti negano l'accesso, il dispositivo non verrà registrato in Intune e non può essere gestito. La seconda volta che gli utenti accedono all'app Portale aziendale dopo aver negato l'accesso, nel messaggio viene visualizzata la casella di controllo **Non visualizzare più questo messaggio** che è possibile selezionare per evitare di visualizzare di nuovo il messaggio.

Se gli utenti consentono l'accesso e in seguito lo negano, il messaggio verrà visualizzato all'accesso successivo all'app Portale aziendale dopo la registrazione.

Se gli utenti decidono di consentire l'accesso in un secondo momento, passare a **Impostazioni** > **App** > **Portale aziendale** > **Autorizzazioni** > **Telefono** e quindi attivare l'autorizzazione.

### <a name="how-to-explain-this-to-your-users"></a>Come spiegare questo agli utenti
Suggerire agli utenti di consultare l'articolo [Registrare il dispositivo Android in Intune](/intune-user-help/enroll-your-device-in-intune-android) per ottenere altre informazioni.

## <a name="allow-company-portal-to-access-photos-media-and-files-on-your-device"></a>Consentire a Portale aziendale di accedere a foto, elementi multimediali e file nel dispositivo?

### <a name="where-it-appears"></a>Dove viene visualizzato
Il messaggio **Allow Company Portal to access photos, media, and files on your device?** (Consentire a Portale aziendale di accedere a foto, elementi multimediali e file nel dispositivo?) viene visualizzato quando gli utenti toccano **Invia dati** per inviare i log all'amministratore IT.

### <a name="what-it-means"></a>Che cosa significa
Accettando questa richiesta, gli utenti consentono al dispositivo di scrivere i log di dati nella scheda SD e abilitare lo spostamento dei log tramite un cavo USB.   

> [!NOTE]
> **The Company Portal app never accesses users' photos, media, and files!** (L'app Portale aziendale non accede mai a foto, elementi multimediali e file degli utenti.) Il testo del messaggio è controllato da Google e non può essere modificato.

### <a name="what-happens-if-users-deny-access"></a>Cosa accade se gli utenti negano l'accesso
Se gli utenti negano l'accesso, possono comunque inviare i log di dati tramite posta elettronica, ma questi non vengono copiati nella scheda SD del dispositivo.

Al secondo accesso all'app Portale aziendale dopo aver negato l'accesso, nel messaggio sarà visualizzata la casella di controllo **Non visualizzare più questo messaggio** che gli utenti potranno selezionare per evitare di visualizzare di nuovo il messaggio. Se gli utenti consentono l'accesso e in seguito lo negano, il messaggio verrà visualizzato al successivo tentativo di invio dei log. Se si decide di consentire l'accesso in un secondo momento, passare a **Impostazioni** > **App** > **Portale aziendale** > **Autorizzazioni** > **Archiviazione** e quindi attivare l'autorizzazione.


### <a name="how-to-explain-this-to-your-users"></a>Come spiegare questo agli utenti
Suggerire agli utenti di consultare l'articolo [Inviare i log all'amministratore IT tramite posta elettronica](/intune-user-help/send-logs-to-your-it-admin-by-email-android) e anche l'articolo [Send logs to your IT admin by cable](/intune-user-help/send-logs-to-your-it-admin-by-cable-android) (Inviare i log all'amministratore IT tramite cavo), se si vuole che confrontino i due metodi.


### <a name="see-also"></a>Vedere anche
[Informazioni sull'uso di Intune per gli utenti finali](/intune-classic/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)