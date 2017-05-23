---
title: Tools zum Erkennen und Verwalten von Visual Studio-Instanzen | Microsoft-Dokumentation
description: '{{PLATZHALTER}}'
ms.date: 04/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
author: timsneath
ms.author: tims
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: a6c3aa65a2c0198c856f09f6f16f58bf16945d58
ms.contentlocale: de-de
ms.lasthandoff: 05/09/2017

---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Tools zum Erkennen und Verwalten von Visual Studio-Instanzen

## <a name="detecting-existing-visual-studio-instances"></a>Erkennen vorhandener Visual Studio-Instanzen
Wir haben mehrere Tools zur Verfügung gestellt, mit denen Sie installierte Instanzen von Visual Studio auf Clientcomputern erkennen und verwalten können:

* [VSWhere](https://github.com/microsoft/vswhere): eine ausführbare C++-Datei, die Ihnen hilft, den Speicherort der wichtigsten Tools für Visual Studio in einer installierten Instanz von Visual Studio zu finden.
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell): PowerShell-Skripts, die die Setupkonfigurations-API zum Identifizieren der installierten Instanzen von Visual Studio verwenden.
* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples): C#- und C++-Beispiele, die veranschaulichen, wie Sie die Setupkonfigurations-API zum Abfragen einer vorhandene Installation verwenden.

Darüber hinaus stellt die [Setupkonfigurations-API](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.setup.configuration.aspx) Schnittstellen für Entwickler bereit, die eigene Hilfsprogramme zum Abfragen von Visual Studio-Instanzen erstellen möchten.

>[!TIP]
>Weitere Informationen zur Installation von Visual Studio 2017 finden in den [Blogbeiträgen von Heath Stewart](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/).


## <a name="editing-the-registry-for-a-visual-studio-instance"></a>Bearbeiten der Registrierung einer Visual Studio-Instanz
In Visual Studio 2017 werden Registrierungseinträge in einem privaten Speicherort gespeichert, was ermöglicht, dass sich mehrere Instanzen derselben Version von Visual Studio auf demselben Computer befinden.

Da diese Einträge nicht in der globalen Registrierung gespeichert werden, gibt es spezielle Anweisungen zum Verwenden des Registrierungseditors, um Registrierungseinträge zu ändern:

1. Wenn Sie eine Instanz Visual Studio-2017 geöffnet haben, schließen Sie sie.
2. Starten Sie `regedit.exe`.
3. Wählen Sie den Knoten `HKEY_LOCAL_MACHINE` aus.
4. Wählen Sie im Hauptmenü des Registrierungs-Editors **Datei -> Struktur laden...** und dann die private Registrierungsdatei aus, die im Ordner **AppData\Local** gespeichert ist. Zum Beispiel:
   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

> [!NOTE]
> `<config>` entspricht der Instanz von Visual Studio, die Sie durchsuchen möchten.

Sie werden aufgefordert, einen Strukturnamen anzugeben, der zum Namen Ihrer isolierten Struktur wird. Anschließend sollten Sie in der Lage sein, die Registrierung unter der von Ihnen erstellten isolierten Struktur zu durchsuchen.

> [!IMPORTANT]
> Bevor Sie Visual Studio erneut starten, müssen Sie die isolierte Struktur entladen, die Sie erstellt haben. Zu diesem Zweck wählen Sie im Hauptmenü des Registrierungs-Editors „Datei -> Struktur entladen“ aus. (Wenn Sie dies nicht tun, bleibt die Datei gesperrt, und Visual Studio kann nicht gestartet werden.)
