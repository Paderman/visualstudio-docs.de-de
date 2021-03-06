---
title: Bereitstellen eine ebenenmodellerweiterung | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, deploying extensions
- layer models, deploying extensions
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 311add860016c914aab232ffad6e3a4efadb15c9
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="deploy-a-layer-model-extension"></a>Bereitstellen einer Ebenenmodellerweiterung
Andere Benutzer von Visual Studio können Ebenenmodellierungserweiterungen installieren, die Sie mithilfe von Visual Studio erstellt haben.  
  
## <a name="installing-your-extension"></a>Installieren der Erweiterung  
 Die Erweiterung wird zu einer VSIX-Datei kompiliert, die Sie auf anderen Computern installieren können. Sie können sie auch auf dem Entwicklungscomputer installieren, um die Erweiterung in der Hauptinstanz von Visual Studio verfügbar zu machen.  
  
#### <a name="to-install-the-extension"></a>So installieren Sie die Erweiterung  
  
1.  In das Projekt mit **source.vsix.manifest**öffnen **"bin"\\ \***  im Datei-Explorer.  
  
2.  Kopieren der  **\*VSIX** -Datei auf den Computer, auf dem Sie die Erweiterung installieren möchten.  
  
3.  Doppelklicken Sie auf dem Zielcomputer auf die VSIX-Datei in Windows-Explorer.  
  
     Das VSIX-Installationsprogramm wird geöffnet.  
  
#### <a name="to-uninstall-the-extension"></a>So deinstallieren Sie die Erweiterung  
  
1.  In Visual Studio auf die **Tools** Menü klicken Sie auf **Erweiterungen und Updates**.  
  
2.  Klicken Sie auf den Namen der Erweiterung, und klicken Sie dann auf **Deinstallieren**.  
  
## <a name="installing-an-extension-on-a-team-foundation-build-server"></a>Installieren einer Erweiterung auf einem Team Foundation Build-Server  
 [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] Server müssen normalerweise keine Visual Studio installiert, und Sie können nicht so VSIX-Pakete installieren, indem Sie darauf doppelklicken. Die Installation von [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] schließt einige Komponenten ein, die das Ausführen einer VSIX-Erweiterung ermöglichen, Sie müssen die Erweiterung jedoch manuell installieren.  
  
#### <a name="to-install-your-layer-extension-on-a-includeesprbuildmiscincludesesprbuildmdmd-server"></a>So installieren Sie die Ebenenerweiterung auf einem [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)]-Server  
  
1.  Kopieren der **VSIX** Dateien vom Entwicklungscomputer auf den [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] Computer.  
  
     Speichern Sie die VSIX-Datei in einem der folgenden Speicherorte:  
  
    -   So führen Sie die Installation für alle Benutzer und Dienste aus:  
  
         %ProgramFiles%\Microsoft Visual Studio [Version]\Common7\IDE\Extensions\Microsoft  
  
    -   So führen Sie die Installation nur für den Netzwerkdienst aus, der [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] ausführt:  
  
         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\[version]\Extensions\Microsoft  
  
    -   Wenn Sie [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] zur Ausführung im interaktiven Modus für einen bestimmten Benutzer konfiguriert haben, können Sie die Installation nur für diesen Benutzer ausführen:  
  
         %LocalAppData%\Microsoft\VisualStudio\\[version]\Extensions\Microsoft  
  
        > [!NOTE]
        >  %LocalAppData% ist in der Regel *DriveName*: Benutzer*Benutzername*AppDataLocal.  
  
2.  Erweitern Sie jede VSIX-Datei in einen Ordner am gleichen Speicherort:  
  
    1.  Ändern Sie die Dateinamenerweiterung von **VSIX** auf **ZIP**.  
  
    2.  Extrahieren Sie den Inhalt der ZIP-Datei in einen Ordner.  
  
    3.  Löschen Sie die ZIP-Datei.  
  
3.  Starten Sie [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] neu.
