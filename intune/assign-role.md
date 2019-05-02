---
title: Assegnare un ruolo a un utente di Intune
description: Informazioni su come assegnare un ruolo predefinito o personalizzato a un utente in Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: a59c413fcc11dfce76152a7325517703a71785d2
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61508180"
---
# <a name="assign-a-role-to-an-intune-user"></a>Assegnare un ruolo a un utente di Intune

È possibile assegnare un ruolo [predefinito](role-based-access-control.md#built-in-roles) o [personalizzato](create-custom-role.md) a un utente di Intune.

Per creare, modificare o assegnare ruoli, l'account deve disporre di una delle seguenti autorizzazioni in Azure AD:
- **Amministratore globale**
- **Amministratore del servizio Intune**

Per un elenco completo delle autorizzazioni per ogni ruolo predefinito, vedere [Intune RBAC Table](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a) (Tabella di controllo degli accessi in base al ruolo di Intune).

1. Accedere al [portale Azure](https://portal.azure.com).

2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.

3. Nel pannello **Intune** scegliere **Ruoli** > **Tutti i ruoli**.

4. Nel pannello **Ruoli di Intune - Tutti i ruoli** scegliere il ruolo predefinito da assegnare.

5. Nel pannello <*nome ruolo*> - **Panoramica** scegliere **Gestisci** > **Assegnazioni**.

6. Nel pannello del ruolo personalizzato scegliere **Assegna**.

7. Nel pannello **Assegnazioni di ruolo** immettere un **Nome dell'assegnazione** e una **Descrizione dell'assegnazione** facoltativa per l'assegnazione.

8. Per **Membri (gruppi)** scegliere un gruppo contenente l'utente a cui si vogliono assegnare le autorizzazioni.

9. Per **Ambito (gruppi)** scegliere un gruppo contenente gli utenti/dispositivi che il membro indicato in precedenza è autorizzato a gestire.

10. Per **Ambito (tag)** scegliere i tag in cui verrà applicata questa assegnazione di ruolo.

11. Al termine, scegliere **OK**. La nuova assegnazione viene visualizzata nell'elenco di assegnazioni.


## <a name="next-steps"></a>Passaggi successivi
- [Informazioni sul controllo degli accessi in base al ruolo in Intune](role-based-access-control.md)
- [Creare un ruolo personalizzato](create-custom-role.md)