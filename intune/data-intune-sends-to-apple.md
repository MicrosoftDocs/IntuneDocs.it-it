---
title: Dati inviati da Intune ad Apple
titleSuffix: Microsoft Intune
description: Elenco di dati inviati da Intune ad Apple.
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b204a956-18ec-11e8-accf-0ed5f89f718b
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c247cfbd715368f65dfb1ba2ce8b5e88a491d302
ms.sourcegitcommit: 54fc806036f84a8667cf8f74086358bccd30aa7d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2018
---
# <a name="data-intune-sends-to-apple"></a>Dati inviati da Intune ad Apple

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Quando in un dispositivo è abilitato uno dei seguenti servizi Apple, Microsoft Intune stabilisce una connessione con Apple e condivide informazioni sull'utente e il dispositivo con Apple: 

- [Programma di registrazione del dispositivo mobile di Apple (DEP)](device-enrollment-program-enroll-ios.md)
- [Certificato per le notifiche push MDM Apple (APNS)](apple-mdm-push-certificate-get.md)
- [Apple School Manager (ASM)](https://docs.microsoft.com/schooldatasync/apple-school-manager-integration-with-intune-for-education-and-school-data-sync)
- [Volume Purchase Program (VPP) di Apple](vpp-apps-ios.md)

Per consentire a Microsoft Intune di stabilire una connessione, è necessario creare un account di Apple per ogni servizio Apple.

La tabella seguente elenca i dati che Microsoft Intune invia da un dispositivo ai servizi Apple abilitati. 

| Servizio | Dati inviati ad Apple | Utilizzato per |
|---|---| ---|
| [APNS](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Token, PushMagic | Se il server accetta il dispositivo, questo trasmette il proprio token di notifica push al server. Il server deve usare questo token per inviare messaggi push al dispositivo. Questo messaggio di accesso contiene anche una stringa PushMagic. Il server deve memorizzare questa stringa e includerla in tutti i messaggi push inviati al dispositivo. |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Token di server | Token di notifica push del dispositivo usato per l'autenticazione al servizio Apple. |
| ASM/DEP | server_name | Nome identificabile per il server MDM. |
| ASM/DEP | server_uuid | Identificatore del server generato dal sistema. |
| ASM/DEP | admin_id | ID Apple della persona che ha generato i token correnti che sono in uso. |
| ASM/DEP | org_name | Nome dell'organizzazione. |
| ASM/DEP | org_email | Indirizzo di posta elettronica dell'organizzazione. |
| ASM/DEP | org_phone | Numero di telefono dell'organizzazione. |
| ASM/DEP | org_address | Indirizzo dell'organizzazione. |
| ASM/DEP | org_ID | ID cliente DEP. Questa chiave è disponibile solo nella versione 3 e versioni successive del protocollo. |
| ASM/DEP | serial_number | Numero di serie del dispositivo (stringa). |
| ASM/DEP | model | Nome del modello (stringa). |
| ASM/DEP | description | Descrizione del modello (stringa). |
| ASM/DEP | asset_tag | Tag risorsa del dispositivo (stringa). |
| ASM/DEP | profile_status | Stato dell'installazione del profilo. Valori possibili: **empty**, **assigned**, **pushed** o **removed**. |
| ASM/DEP | profile_uuid | ID univoco del profilo assegnato. |
| ASM/DEP | device_assigned_by | Indirizzo di posta elettronica della persona che ha assegnato il dispositivo. |
| ASM/DEP | os | Sistema operativo del dispositivo: iOS, OSX, o tvOS. Questa chiave è valida in X-Server-Protocol-Version 2 e versioni successive. |
| ASM/DEP | device_family | Famiglia di prodotti Apple del dispositivo: iPad, iPhone, iPod, Mac o AppleTV. Questa chiave è valida in X-Server-Protocol-Version 2 e versioni successive. |
| ASM/DEP | profile_name | Stringa. Nome leggibile del profilo. |
| ASM/DEP | support_phone_number | Facoltativo. Stringa. Numero di telefono di supporto dell'organizzazione. |
| ASM/DEP | support_email_address | Facoltativo. Stringa. Indirizzo di posta elettronica di supporto dell'organizzazione. Questa chiave è valida in X-Server-Protocol-Version 2 e versioni successive. |
| ASM/DEP | department | Facoltativo. Stringa. Nome del reparto o della posizione definito dall'utente. |
| ASM/DEP | devices | Matrice di stringhe contenente i numeri di serie dei dispositivi. (Può essere vuoto.) |
| VPP | GUID UserId di Intune | GUID generato da Intune. |
| VPP | UPN ID Apple gestito | ID Apple specificato dall'amministratore quando configura la connessione del token VPP ad Apple. |
| VPP | Numero di serie | Numero di serie del dispositivo gestito. |

Per interrompere l'uso di servizi Apple con Microsoft Intune ed eliminare i dati è necessario disabilitare il token Apple di Microsoft Intune ed eliminare anche l'account Apple. Per informazioni sulla gestione account, vedere l'account Apple.

