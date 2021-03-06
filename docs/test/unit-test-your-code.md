---
title: "Komponententest für Code | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: bafabb6755a5d3c8cf8f2b60b67a9dc0d7af9792
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2018
---
# <a name="unit-test-your-code"></a>Komponententest für Code
Mit Komponententests können Entwickler und Tester die Methoden der Klassen in [!INCLUDE[csharp_current_short](../misc/includes/csharp_current_short_md.md)]-, [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)]- und [!INCLUDE[cpp_current_short](../misc/includes/cpp_current_short_md.md)]-Projekten schnell auf logische Fehler überprüfen.  
  
 Zu den Komponententest-Tools gehören:  
  
1.  **Test-Explorer** Mit dem Test-Explorer können Sie Komponententests ausführen und deren Ergebnisse anzeigen. Der Test-Explorer erlaubt die Verwendung jedes Komponententest-Frameworks, auch Frameworks von Drittanbietern, die über einen Adapter für den Explorer verfügen.  
  
2.  **Microsoft-Komponententest-Framework für verwalteten Code.** Das Microsoft-Komponententest-Framework für verwalteten Code wird mit Visual Studio installiert und stellt ein Framework zum Testen von .NET-Code bereit.  
  
3.  **Microsoft-Komponententest-Framework für C++.** Das Microsoft-Komponententest-Framework für C++ wird mit Visual Studio installiert und stellt ein Framework zum Testen von nativem Code bereit.  Google Test-, Boost.Test- und CTest-Frameworks sind ebenfalls in Visual Studio integriert, und Adapter von Drittanbietern sind für zusätzliche Testframeworks verfügbar. Weitere Informationen finden Sie unter [Schreiben von Komponententests für C/C++ ](writing-unit-tests-for-c-cpp.md). 
  
4.  **Codeabdeckungstools.** Sie können die Menge an Produktcode bestimmen, die Ihre Komponententests nach der Eingabe eines Befehls im Test-Explorer prüfen.  
  
5.  **Microsoft Fakes-Isolationsframework.** Das Microsoft Fakes-Isolationsframework kann Ersatzklassen und Methoden für Produktions- und Systemcode erstellen, der Abhängigkeiten im getesteten Code erstellt. Durch die Implementierung von Fakedelegaten für eine Funktion können Sie das Verhalten und die Ausgabe des Abhängigkeitsobjekts steuern.  
  
 Sie können auch [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) verwenden, um Ihren .NET-Code zum Generieren von Testdaten und einer Sammlung von Komponententests zu untersuchen. Für jede Anweisung im Code wird eine Testeingabe generiert, die die betreffende Anweisung ausführt. Für jede bedingte Verzweigung im Code wird eine Fallanalyse ausgeführt.  
  
## <a name="key-tasks"></a>Hauptaufgaben  
 Lesen Sie folgende Themen, um Komponententests besser zu verstehen und sie zu erstellen:  
  
|Aufgaben|Verwandte Themen|  
|-----------|-----------------------|  
|**Schnellstarts und exemplarische Vorgehensweisen:** Erfahren Sie in den folgenden Themen ausgehend von Codebeispielen, wie Komponententests in Visual Studio durchgeführt werden.|-   [Exemplarische Vorgehensweise: Erstellen und Ausführen von Komponententests für verwalteten Code](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />-   [Schnellstart: Testgesteuerte Entwicklung mit dem Test-Explorer](../test/quick-start-test-driven-development-with-test-explorer.md)<br />-   [Hinzufügen von Komponententests zu vorhandenen C++-Anwendungen](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)|  
|**Komponententest mit Test-Explorer:** Erfahren Sie, wie Sie Test-Explorer unterstützen kann, produktivere und effizientere Komponententests zu erstellen.|-   [Grundlagen zum Komponententest](../test/unit-test-basics.md)<br />-   [Ein Komponententestprojekt erstellen](../test/create-a-unit-test-project.md)<br />-   [Ausführen von Komponententests mit dem Test-Explorer](../test/run-unit-tests-with-test-explorer.md)<br />-   [Installieren von Frameworks für Komponententests von Drittanbietern](../test/install-third-party-unit-test-frameworks.md)<br />-   [Upgrade der Tests der programmierten UI von Visual Studio 2010](../test/upgrading-coded-ui-tests-from-visual-studio-2010.md)|  
|**Komponententests von verwaltetem Code:**|-   [Schreiben von Komponententests für .NET Framework mit dem Microsoft-Komponententestframework für verwalteten Code](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)|  
|**Komponententests von C++-Code**|-   [Schreiben von Komponententests für C-C++ mit dem Microsoft-Komponententestframework für C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)|  
|**Isolation von Komponententests**|-   [Isolieren von getestetem Code mithilfe von Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)|  
|**Verwenden Sie die Codeabdeckung, um zu identifizieren, welcher Teil des Projektcodes mit Komponententests getestet wird:** Erfahren Sie mehr über die Codeabdeckungsfunktion der [!INCLUDE[vsprvsts](../code-quality/includes/vsprvsts_md.md)]-Testtools.|-   [Bestimmen des Umfangs des zu testenden Codes mithilfe von Code Coverage](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|  
|**Führen Sie die Belastungs- und Leistungsanalyse mithilfe von Auslastungstests für die Komponententests aus:** Sie können einen Auslastungstest erstellen und diesem die Komponententests hinzufügen, um die Leistungs- und Auslastungsprobleme in der Anwendung isolieren zu können.|-   [Auslastungstest (VSTS und TFS)](/vsts/load-test/)|  
|**Festlegen und Erzwingen von Quality Gates**: Sie können Quality Gates erstellen, um zu erzwingen, dass vor dem Einchecken von Code Tests ausgeführt werden. Auf diese Weise können Sie die Qualität des Codes sicherstellen.|-   [Festlegen und Erzwingen von Quality Gates](http://msdn.microsoft.com/Library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|  
|**Erweitern Sie den Komponententesttyp:** Sie können den Tests Funktionen hinzufügen, die im Komponententest-Framework möglicherweise nicht enthalten sind. Sie können z. B. eine Testeigenschaft hinzufügen, die angibt, ob ein Test als normaler Benutzer ausgeführt werden soll. Sie können das Framework auch erweitern, indem Sie einer Methode Zeilenattribute hinzufügen und die Daten in dieser Zeile im Test verwenden.|Beispielcode zum Erweitern des Komponententestframeworks finden Sie auf der [Microsoft-Website](http://go.microsoft.com/fwlink/?LinkId=185591).|  
|**Festlegen von Testoptionen:** Sie können beispielsweise angeben, an welchem Ort die Testergebnisse gespeichert werden.|[Konfigurieren von Komponententests mithilfe einer .runsettings-Datei](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|  
  
## <a name="reference"></a>Verweis  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>  
 Beschreibt den UnitTesting-Namespace, der Attribute, Ausnahmen, Asserts und andere Klassen bereitstellt, die Komponententests unterstützen.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web>  
 Beschreibt den UnitTesting.Web-Namespace, der den UnitTesting-Namespace durch die Unterstützung für [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] und Webdienst-Komponententests erweitert.  
  
## <a name="external-resources"></a>Externe Ressourcen  
  
### <a name="videos"></a>Videos  
 [Channel 9: Unit testing your UWP apps built using XAML (Channel 9: Durchführen von Komponententests für Ihre mit XAML erstellten UWP-Apps)](http://go.microsoft.com/fwlink/?LinkId=226285)  
  
### <a name="forums"></a>Foren  
 [Visual Studio-Komponententest](http://go.microsoft.com/fwlink/?LinkId=224477)  
  
### <a name="guidance"></a>Empfehlungen  
 [Testing for Continuous Delivery with Visual Studio 2012 - Chapter 2: Unit Testing: Testing the Inside (Tests für fortlaufende Übermittlung mit Visual Studio 2012 – Kapitel 2: Komponententests – Interne Tests)](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
### <a name="reference"></a>Verweis  
 [Inhaltsverzeichnis für Komponententests](http://go.microsoft.com/fwlink/?LinkID=254719)  
  
## <a name="see-also"></a>Siehe auch

[Verbessern der Codequalität](/visualstudio/test/improve-code-quality)
