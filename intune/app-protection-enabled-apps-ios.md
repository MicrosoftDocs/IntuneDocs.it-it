---
title: App iOS con i criteri di protezione delle app | Anteprima di Intune in Azure
titleSuffix: Intune Azure preview
description: "Anteprima di Intune in Azure: questo argomento descrive cosa accade quando l&quot;app iOS è gestita da criteri di protezione delle app."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 586d9440-3813-4dec-b865-8bd319befde0
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 5e172b940dfae32213c870b29f05f56573192704
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>Aspettative dalla gestione dell'app per iOS con criteri di protezione delle app
[!INCLUDE[azure_preview](./includes/azure_preview.md)]Questo argomento descrive l'esperienza dell'utente finale con le app con criteri di protezione delle app. I criteri di protezione delle app vengono applicati solo quando le app sono usate nel contesto di lavoro, ad esempio nei casi di accesso alle app con l'account aziendale o di accesso ai file archiviati nel percorso OneDrive aziendale.
##  <a name="accessing-apps"></a>Accesso alle app

Se il dispositivo **non è registrato in Intune**, all'utente finale verrà chiesto di riavviare l'app la prima volta che la usa.  Il riavvio è necessario per consentire l'applicazione dei criteri di protezione delle app all'app. Lo screenshot seguente illustra questo aspetto tramite l'app Skype:


![screenshot di un dispositivo iOS con la richiesta del PIN](./media/ios-pin-prompt.png)

Per i dispositivi **registrati per la gestione in Intune**, l'utente finale riceverà il messaggio che l'app è ora gestita dalla società:

![schermata del dispositivo iOS con il messaggio relativo alla gestione da parte della società e la richiesta del PIN](./media/ios-managed-devices-pin-prompt.png)

##  <a name="using-apps-with-multi-identity-support"></a>Uso di app con supporto di più identità

I criteri di protezione delle app vengono applicati solo al contesto di lavoro quando si usa l'app. Il comportamento delle diverse app quindi può essere diverso a seconda del contesto, di lavoro o personale.  

Per le app che supportano più identità, Intune applica i criteri di protezione delle app solo quando l'utente finale usa l'app nel contesto di lavoro.  Ad esempio, l'utente finale riceverà la richiesta di inserimento del PIN al momento di accedere ai dati di lavoro.  Per l'**app Outlook**, all'utente finale viene richiesto il PIN all'avvio dell'app. Per l'**app OneDrive** ciò si verifica quando l'utente finale digita l'account aziendale.  Per Microsoft **Word**, **PowerPoint* ed **Excel**, ciò si verifica quando l'utente finale accede ai documenti archiviati nel percorso aziendale di OneDrive for Business.
##  <a name="managing-user-accounts-on-the-device"></a>Gestione degli account utente nel dispositivo

Intune supporta solo la distribuzione di criteri di protezione delle app a un unico account utente per dispositivo.

* A seconda dell'applicazione che si usa, è possibile scegliere di bloccare o meno il secondo utente del dispositivo. In ogni caso, sarà tuttavia interessato dai criteri di protezione delle app solo il primo utente che ottiene i criteri.
  * **Microsoft Word**, **Excel** e **PowerPoint** non bloccano un secondo account utente. Questo account utente non sarà tuttavia interessato dai criteri di protezione delle app.  

  * Per le app **OneDrive e Outlook**, è possibile usare un solo account aziendale.  L'aggiunta di più account aziendali è bloccata in queste app.  È tuttavia possibile rimuovere un utente e aggiungere un altro utente sul dispositivo.

* Se prima della distribuzione dei criteri di protezione delle app, un dispositivo ha più di un account utente, il primo account che riceve la distribuzione dei criteri di protezione delle app sarà gestito dai criteri di protezione delle app di Intune.


Per capire meglio come vengono gestiti gli account utente multipli, leggere lo scenario di esempio riportato sotto.

L'utente A lavora per due aziende, l'**Azienda X** e l'**Azienda Y**. L'utente A ha un account aziendale per ognuna delle aziende per cui lavora e, in entrambi i casi, viene usato Intune per la distribuzione dei criteri di protezione delle app. L'**Azienda X** distribuisce i criteri di protezione delle app **prima dell'****Azienda Y**. L'account associato all'**Azienda X** otterrà i criteri di protezione delle app, a differenza dell'account associato all'Azienda Y. Se si vuole che l'account utente associato all'Azienda Y sia gestito con i criteri di protezione delle app, è necessario rimuovere l'utente associato all'Azienda X.
### <a name="adding-a-second-account"></a>Aggiunta di un secondo account

Se si usa un dispositivo iOS, quando si prova ad aggiungere un secondo account aziendale nello stesso dispositivo potrebbe essere visualizzato un messaggio di blocco.  Verranno visualizzati gli account e sarà possibile scegliere l'account da rimuovere.

![Schermata della finestra di dialogo con il messaggio di blocco e le opzioni Sì e No](./media/ios-switch-user.PNG)

## <a name="next-steps"></a>Passaggi successivi
[Aspettative dalla gestione dell'app per Android con criteri di protezione delle app](app-protection-enabled-apps-android.md)
### <a name="see-also"></a>Vedere anche
[Creare e distribuire i criteri di protezione delle app con Microsoft Intune](app-protection-policies.md)
