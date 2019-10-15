---
title: Aggiungere app di sistema Android Enterprise a Microsoft Intune
titleSuffix: ''
description: Informazioni su come aggiungere app di sistema Enterprise a Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c07ce82bbc056e1d76abeb5d31bf57e0973fad6e
ms.sourcegitcommit: bdf948be824cf5390d5166a277f389f3785c81f9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71960889"
---
# <a name="add-android-enterprise-system-apps-to-microsoft-intune"></a>Aggiungere app di sistema Android Enterprise a Microsoft Intune

Prima di assegnare un'app a un dispositivo o a un gruppo di utenti, è necessario aggiungere l'app a Microsoft Intune. Le app di sistema sono supportate nei dispositivi Android Enterprise. È possibile abilitare un'app di sistema per [dispositivi completamente gestiti](../enrollment/android-kiosk-enroll.md) o [dispositivi dedicati Android Enterprise](../enrollment/android-fully-managed-enroll.md).

## <a name="add-the-app"></a>Aggiungere l'app

Seguire questa procedura per aggiungere un'app di sistema Android Enterprise a Intune dal portale di Azure:

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Nel riquadro **Intune** selezionare **App client** > **App** > **Aggiungi**.
3. Nel riquadro **Aggiungi app** selezionare **App di sistema Android Enterprise** nell'elenco degli **altri tipi** disponibili.
4. Per configurare le informazioni sull'app, selezionare **Configura** e specificare le informazioni seguenti:
    - **Nome app**: Immettere il nome dell'app.
    - **Autore**: Immettere il nome dell'autore dell'app.  
    - **Nome pacchetto**: Immettere un nome di pacchetto. Intune convaliderà la validità del nome del pacchetto.
5. Selezionare **OK**.
6. Selezionare **Aggiungi**.

> [!NOTE]
> Sarà necessario collaborare con l'OEM del dispositivo per trovare il nome del pacchetto dell'app che si vuole abilitare o disabilitare.

L'app creata viene visualizzata nell'elenco di app, in cui è possibile assegnarla ai gruppi selezionati. 

Le app di sistema Android Enterprise abilitano o disabilitano le app che fanno già parte della piattaforma. Per abilitare un'app, assegnare l'app di sistema come **obbligatoria**. Per disabilitare un'app, assegnare l'app di sistema come **disinstallazione**. Non è possibile assegnare le app di sistema come disponibili per un utente.


## <a name="next-steps"></a>Passaggi successivi

- [Assegnare app ai gruppi](apps-deploy.md)