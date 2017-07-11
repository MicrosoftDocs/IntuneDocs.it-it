---
title: Stabilire come preparare le app per la gestione delle applicazioni mobili con Microsoft Intune
description: "Le informazioni contenute in questo argomento consentono di stabilire quando è necessario usare lo strumento di wrapping delle app e App SDK per abilitare le app line-of-business personalizzate per l'uso dei criteri di gestione delle app mobili."
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 29e22121-8268-48b5-a671-f940a6be1d24
ms.reviewer: oldang
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e8b218ce38a7e76135a62b1155dbf9060ba511cc
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="prepare-line-of-business-apps-for-mam"></a>Preparare le app linea di business per MAM

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

È possibile consentire alle app di usare i criteri di gestione delle applicazioni mobili (MAM, Mobile Application Management) tramite lo strumento di wrapping delle app di Intune o Intune App SDK. In questo articolo vengono fornite informazioni su questi due metodi e su quando usarli.

## <a name="intune-app-wrapping-tool"></a>Strumento di wrapping delle app di Intune
Lo strumento di wrapping delle app viene usato principalmente per le app line-of-business (LOB) interne. Lo strumento è un'applicazione della riga di comando che crea un wrapper per l'app, consentendo quindi all'app di essere gestita dai criteri MAM di Intune.

Non è necessario il codice sorgente per usare lo strumento, ma sono necessarie le credenziali di firma.  Per altre informazioni sulle credenziali di firma, vedere il [blog di Intune](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/). Per la documentazione dello strumento di wrapping delle app, vedere [Prepare Android apps for mobile application management with the Intune App Wrapping Tool](app-wrapper-prepare-android.md) (Preparare le app per Android per la gestione di applicazioni per dispositivi mobili con lo strumento di wrapping delle app di Intune) e [Prepare iOS apps for mobile application management with the Intune App Wrapping Tool](app-wrapper-prepare-ios.md) (Preparare le app per iOS per la gestione di applicazioni per dispositivi mobili con lo strumento per di wrapping delle app di Intune).

Lo strumento di wrapping delle app **non** supporta le app nell'App Store Apple o in Google Play Store, né alcune funzionalità che richiedono un'integrazione dello sviluppatore (vedere la tabella di confronto delle funzionalità seguente).


Per altre informazioni sullo strumento di wrapping delle app per la gestione delle applicazioni mobili sui dispositivi non registrati in Intune, vedere [Proteggere app e dati line-of-business su dispositivi non registrati in Microsoft Intune](/intune-classic/deploy-use/protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune).

### <a name="reasons-to-use-the-app-wrapping-tool"></a>Motivi per usare lo strumento di wrapping delle app:
* L'app non dispone di funzionalità per la protezione dei dati incorporate.
* L'app è semplice.
* L'app è distribuita internamente.
* Non si ha accesso al codice sorgente dell'app.
* Non si è lo sviluppatore dell'app.
* L'app offre esperienze minime di autenticazione utente.


### <a name="supported-app-development-platforms"></a>Piattaforme di sviluppo delle app supportate

|**Strumento di wrapping delle app** | **Xamarin** |**Cordova** |
|------|----|----|
|**iOS** |sì|sì|
|**Android**| No |sì|

## <a name="intune-app-sdk"></a>Intune App SDK
App SDK è progettato principalmente per i clienti che hanno le app nell'App Store Apple o in Google Play Store e che vogliono poter gestire le app con Intune. Tuttavia, qualsiasi app può sfruttare l'integrazione dell'SDK, anche se si tratta di un'app line-of-business.

Per altre informazioni sull'SDK, vedere la [panoramica](app-sdk.md). Per un'introduzione all'SDK, vedere [Introduzione a Microsoft Intune App SDK](app-sdk-get-started.md)

### <a name="reasons-to-use-the-sdk"></a>Motivi per usare l'SDK
* L'app non dispone di funzionalità per la protezione dei dati incorporate.
* L'app è complessa e contiene numerose esperienze.
* L'app è distribuita a un app store pubblico, ad esempio Google Play o l'App Store Apple.
* Si è uno sviluppatore di app e si dispone del background tecnico per l'uso dell'SDK.
* L'app ha altre integrazioni dell'SDK.
* L'app viene aggiornata di frequente.

### <a name="supported-app-development-platforms"></a>Piattaforme di sviluppo delle app supportate

|**Intune App SDK** |**Xamarin** |**Cordova**
|------|----|----|
|**iOS**|Sì: usare il [componente Xamarin per Intune App SDK](app-sdk-xamarin.md).|Sì: usare il [plug-in Cordova per Intune App SDK](app-sdk-cordova.md).|
|**Android**| Sì: usare il [componente Xamarin per Intune App SDK](app-sdk-xamarin.md).|Sì: usare il [plug-in Cordova per Intune App SDK](app-sdk-cordova.md).|

## <a name="feature-comparison"></a>Confronto delle funzionalità
Questa tabella elenca le impostazioni che è possibile usare per App SDK e per lo strumento di wrapping delle app.

> [!NOTE]
> Lo strumento di wrapping delle app può essere usato con la versione autonoma di Intune o con Intune con Configuration Manager.

|Funzionalità|App SDK|Strumento di wrapping delle app|
|-----------|---------------------|-----------|
|Limitare il contenuto Web per la visualizzazione in Managed Browser dell'azienda|X|X|
|Impedire backup in Android, iTunes o iCloud|X|X|
|Consenti all'app di trasferire i dati ad altre app|X|X|
|Consenti all'app di ricevere i dati da altre app|X|X|
|Limita le operazioni taglia, copia e incolla con le altre app|X|X|
|Richiedi PIN semplice per l'accesso|X|X|
|Sostituire il PIN dell'app predefinita con il PIN di Intune|X||
|Specificare il numero di tentativi prima della reimpostazione del PIN|X|X|
|Consenti impronta digitale anziché PIN |X|X|
|Richiedi credenziali aziendali per l'accesso|X|X|
|Blocca l'esecuzione delle app gestite nei dispositivi jailbroken o rooted|X|X|
|Crittografa dati app|X|X|
|Ricontrollare i requisiti di accesso dopo un numero di minuti specificato|X|X|
|Specificare il periodo di prova offline|X|X|
|Bloccare l'acquisizione schermo (solo Android)|X|X|
|Supportare la gestione delle applicazioni mobili senza registrazione del dispositivo|X|X|
|Cancellazione completa|X|X|
|Cancellazione selettiva <br></br>**Nota:** per iOS, quando viene rimosso il profilo di gestione, viene rimossa anche l'app.|X||
|Impedire "Salva con nome" |X||
|Configurazione dell'applicazione di destinazione |X||
|Supportare più identità|X||
|Stile personalizzabile |X|||
### <a name="see-also"></a>Vedere anche

[Strumento di wrapping delle app per Android](app-wrapper-prepare-android.md)</br>
[Strumento di wrapping delle app per iOS](app-wrapper-prepare-ios.md)</br>
[Usare l'SDK per abilitare le app per la gestione delle applicazioni per dispositivi mobili](/intune-classic/deploy-use/use-the-sdk-to-enable-apps-for-mobile-application-management)