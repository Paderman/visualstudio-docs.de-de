---
title: Sicherheit in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code access security, coding errors
- security [.NET Framework], about security
ms.assetid: 318c34ce-f643-468c-83a1-843196f5d845
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c9d546d4020cb9a8e73efdea77fdb85d77d6146d
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2018
---
# <a name="security-in-visual-studio"></a>Sicherheit in Visual Studio

Sicherheitsüberlegungen sollten vom Entwurf bis zur Bereitstellung in alle Aspekte der Anwendungsentwicklung einfließen. Beginnen Sie damit, Visual Studio so sicher wie möglich auszuführen. Weitere Informationen finden Sie unter [Benutzerberechtigungen](../ide/user-permissions-and-visual-studio.md).  
  
 Damit Sie sichere Anwendungen effektiv entwickeln können, benötigen Sie grundlegende Kenntnisse über die Sicherheitskonzepte und Sicherheitsfunktionen der Plattformen, für die Anwendungen entwickelt werden. Außerdem sollten Kenntnisse im Bereich sicherer Codierungstechniken vorhanden sein.  
  
## <a name="understanding-security"></a>Sicherheit  
 [Sicherheit](/dotnet/standard/security/index)  
 Beschreibt Codezugriffssicherheit, rollenbasierte Sicherheit, Sicherheitsrichtlinien und Sicherheitstools in .NET Framework.  
  
 [Defend Your Code with Top Ten Security Tips Every Developer Must Know (Die zehn wichtigsten Tipps zum Schützen des Codes, die jeder Entwickler kennen sollte)](http://go.microsoft.com/fwlink/?LinkId=72877)  
 Beschreibt die wichtigsten Punkte, die Sie in Betracht ziehen sollten, damit Ihre Daten im System nicht gefährdet sind.  
  
## <a name="coding-for-security"></a>Richtige Codierung zur Gewährleistung der Sicherheit  
 Die meisten Codierungsfehler, die Sicherheitsmängel verursachen, entstehen, weil Entwickler bei Benutzereingaben von falschen Voraussetzungen ausgehen oder nicht vollständig mit der Plattform vertraut sind, für welche die Anwendung entwickelt wird.  
  
 [Richtlinien für das Schreiben von sicherem Code](/dotnet/standard/security/secure-coding-guidelines)  
 Stellt Richtlinien zum Klassifizieren der Komponenten in Bezug auf die Sicherheitsprobleme bereit.  
  
 [Empfohlene Vorgehensweisen bezüglich der Sicherheit](/cpp/top/security-best-practices-for-cpp)  
 Behandelt Pufferüberläufe und beschreibt ausführlich das über das Kompilierzeitkennzeichen /GS bereitgestellte Sicherheitsüberprüfungsfeature von Microsoft Visual C++.

## <a name="building-for-security"></a>Programmieren für die Sicherheit  
 Die Sicherheit ist im Buildprozess auch ein wichtiger Aspekt.  Einige zusätzliche Schritte können die Sicherheit einer bereitgestellten App verbessern und nicht autorisiertes Reverse Engineering, Spoofing oder andere Angriffe verhindern.

 [Dotfuscator Community Edition (CE)](dotfuscator/index.md)  
 Erläutert das Einrichten und Starten mithilfe des kostenlosen Programms PreEmptive Protection – Dotfuscator Community Edition zum Schutz von .NET-Assemblys vor Reverse Engineering und unautorisiertem Gebrauch (z.B. unautorisiertem Debuggen).
  
 [Verwalten der Signierung von Assemblys und Manifesten](managing-assembly-and-manifest-signing.md)  
 Beschreibt das Signieren mit starkem Namen, was zum eindeutigen Identifizieren von Softwarekomponenten verwendet werden kann und das Vortäuschen von Namen verhindert.