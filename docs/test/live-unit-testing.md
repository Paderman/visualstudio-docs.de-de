---
title: Live Unit Testing in Visual Studio| Microsoft-Dokumentation
ms.date: 2017-03-07
ms.technology: vs-ide-test
ms.topic: article
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: 7ab19350529e4bd1c7edf914a8a8ca049ace6054
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2018
---
# <a name="live-unit-testing-with-visual-studio-2017"></a>Live Unit Testing mit Visual Studio 2017

Live Unit Testing führt automatisch alle betroffenen Komponententests im Hintergrund aus, und zeigt die Ergebnisse und Code Coverage in der Visual Studio-IDE in Echtzeit an, während Sie eine Anwendung entwickeln. Wenn Sie Ihren Code ändern, bietet Live Unit Testing Feedback dazu, welche Auswirkungen Ihre Änderungen auf vorhandene Tests haben und ob der neue von Ihnen hinzugefügte Code von einem oder mehreren vorhandenen Tests abgedeckt wird. So werden Sie daran erinnert, Komponententests zu schreiben, während Sie Fehler beheben oder neue Funktionen hinzufügen.

> [!NOTE]
> Live Unit Testing steht für C#- und Visual Basic-Projekte zur Verfügung, die auf .NET Core und .NET Framework in der Enterprise-Edition von Visual Studio 2017 ausgerichtet sind.

Wenn Sie Live Unit Testing für Ihre Tests verwenden, werden Daten zum Status Ihrer Tests beibehalten. Da bei Live Unit Testing persistente Daten verwendet werden können, bietet es eine überragende Leistung bei der dynamischen Ausführung Ihrer Tests in Bezug auf Codeänderungen.
 
## <a name="supported-test-frameworks"></a>Unterstützte Testframeworks
Live Unit Testing kann mit den drei gängigen Frameworks für Komponententests verwendet werden, die in der folgenden Tabelle aufgeführt sind. Die unterstützte Mindestversion der Adapter und Frameworks ist ebenfalls in der Tabelle aufgeführt. Die Frameworks für Komponententests sind auf „NuGet.org“ verfügbar.
 
<table> 
<tr>
   <th>Testframework</th>
   <th>Mindestversion des Visual Studio-Adapters</th>
   <th>Mindestversion des Frameworks</th>
</tr>
<tr>
   <td>xUnit.net</td>
   <td> xunit.runner.visualstudio, Version 2.2.0-beta3-build1187</td>
   <td>xUnit 1.9.2</td> 
</tr>
<tr>
   <td>NUnit</td>
   <td>NUnit3TestAdapter, Version 3.5.1</td>  
   <td>NUnit, Version 3.5.0</td>
</tr>
<tr>
   <td>MSTest</td>
   <td>MSTest.TestAdapter 1.1.4-preview</td>
   <td>MSTest.TestFramework 1.0.5-preview</td>
</tr>
</table>

Wenn Sie über ältere, auf MSTest-basierende Testprojekte verfügen, die sich auf `Microsoft.VisualStudio.QualityTools.UnitTestFramework` beziehen, und Sie nicht auf die neueren MSTest-NuGet-Pakete umsteigen möchten, sollten Sie auf Visual Studio 2017 Version 15.4 upgraden. 

In einigen Fällen müssen Sie explizit die NuGet-Pakete wiederherstellen, auf die die Projekte in der Projektmappe verweisen, damit Live Unit Testing funktioniert. Hierzu können Sie entweder die Projektmappe explizit erstellen (wählen Sie im obersten Visual Studio-Menü **Erstellen** und dann **Projektmappe neu erstellen** aus) oder Pakete in der Projektmappe wiederherstellen (klicken Sie mit der rechten Maustaste auf die Projektmappe, und wählen Sie **NuGet-Pakete wiederherstellen** aus), bevor Sie Living Unit Testing aktivieren. 

#   <a name="configuring-live-unit-testing"></a>Konfigurieren von Live Unit Testing

Sie können Live Unit Testing konfigurieren, indem Sie im obersten Visual Studio-Menü **Extras**, **Optionen** und dann im Dialogfeld **Optionen** im linken Bereich **Live Unit Testing** auswählen. Die folgende Abbildung zeigt die verfügbaren Konfigurationsoptionen für Live Unit Testing in dem Dialogfeld.

  ![Bild](./media/lut-options.png)

Die konfigurierbaren Optionen umfassen Folgendes:

- Ob Live Unit Testing angehalten wird, wenn eine Projektmappe erstellt und ein Debugging durchgeführt wird
 
- Ob Live Unit Testing angehalten wird, wenn die Akkuleistung des Systems unter einen bestimmten Schwellenwert sinkt.
- Ob Live Unit Testing automatisch ausgeführt wird, wenn eine Projektmappe geöffnet wird.
- Das Verzeichnis, in dem persistente Daten gespeichert werden sollen.   
   Mit der Schaltfläche **Persistente Daten löschen** können alle persistente Daten gelöscht werden. Dies ist hilfreich, wenn sich Live Unit Testing auf unvorhersehbare oder unerwartete Weise verhält, was darauf hinweist, dass die persistenten Daten beschädigt wurden.   
- Das Intervall, nach dem eine Zeitüberschreitung für einen Testfall auftritt. Der Standardwert ist 30 Sekunden. 
- Die maximale Anzahl der Testläufe, die Live Unit Testing erstellt. 
- Die maximale Arbeitsspeichermenge, die Live Unit Testing-Prozesse belegen können.
- Den Umfang an Informationen, der in das Live Unit Testing-Fenster **Ausgabe** geschrieben wird.   
   Mögliche Optionen sind: Keine Protokollierung (**Keine**), nur Fehlermeldungen (**Fehler**), Fehler- und Informationsmeldungen (**Info**, die Standardeinstellung) oder alle Details (**Ausführlich**).

Sie können auch eine ausführlichen Ausgabe im Live Unit Testing-Fenster **Ausgabe** anzeigen, indem Sie einer Umgebungsvariablen auf Benutzerebene mit dem Namen `VS_UTE_DIAGNOSTICS` den Wert „1“ zuweisen und Visual Studio neu starten. 

Um detaillierte MSBuild-Protokollmeldungen von Live Unit Testing in einer Datei aufzuzeichnen, legen Sie die `LiveUnitTesting_BuildLog`-Umgebungsvariable auf Benutzerebene auf den Namen der Datei fest, die das Protokoll enthalten soll.

Nach der Aktivierung von Live Unit Testing (siehe nächster Abschnitt [Starten, Anhalten und Beenden von Live Unit Testing](#starting-pausing-and-stopping-live-unit-testing)) können Sie auch das Dialogfeld **Optionen** öffnen, indem Sie **Test**, **Live Unit Testing**, **Optionen** wählen.

## <a name="starting-pausing-and-stopping-live-unit-testing"></a>Starten, Anhalten und Beenden von Live Unit Testing

Sie aktivieren Live Unit Testing, indem Sie im obersten Visual Studio-Menü **Test**, **Live Unit Testing** und dann **Starten** auswählen. Wenn Live Unit Testing aktiviert ist, ändern sich die verfügbaren Optionen im **Live Unit Testing**-Menü von dem einzelnen Element **Starten** zu **Anhalten**, **Beenden** und **Zurücksetzen und bereinigen**.

> [!NOTE]
> Wenn Sie Live Unit Testing in einer Projektmappe starten, die kein Komponententestprojekt enthält, erscheinen zwar die Optionen **Pause**, **Beenden**, und **Bereinigt zurücksetzen** im **Live Unit Testing**-Menü, Live Unit Testing wird jedoch nicht gestartet. Das **Ausgabe**-Fenster zeigt eine Nachricht, die mit „No supported test adapters are referenced by this solution...“(Diese Projektmappe bezieht sich auf keine unterstützten Testadapter...) beginnt.  

Sie können Live Unit Testing jederzeit vorübergehend anhalten oder vollständig beenden. Sie könnten sich beispielsweise dann dazu entschließen, wenn Sie gerade ein Refactoring ausführen und wissen, dass die Tests für eine Weile gestört sind. Die drei Menüoptionen sind:

- **Anhalten**: Unterbricht Live Unit Testing vorübergehend. 
 
    Wenn Live Unit Testing angehalten wird, wird die Abdeckungsvisualisierung nicht im Editor dargestellt, aber alle gesammelten Daten bleiben erhalten. Um Live Unit Testing fortzusetzen, wählen Sie im Live Unit Testing-Menü **Weiter** aus. Live Unit Testing führt die notwendigen Schritte aus, um alle Änderungen nachzuholen, die vorgenommen wurden, während Live Unit Testing angehalten war, und aktualisiert die Glyphen entsprechend. 

- **Beenden**: Beendet Live Unit Testing vollständig. Live Unit Testing verwirft alle Daten, die gesammelt wurden.

- **Zurücksetzen und bereinigen**: Beendet Live Unit Testing, löscht persistente Daten und startet Live Unit Testing neu.

- **Optionen**: Öffnet das Dialogfeld **Optionen**, das im Abschnitt [Konfigurieren von Live Unit Testing](#configuring-live-unit-testing) beschrieben wird.
 
##  <a name="viewing-coverage-visualization-in-the-editor-as-you-type"></a>Anzeigen der Abdeckungsvisualisierung im Editor während der Eingabe

Nach der Aktivierung aktualisiert Live Unit Testing alle Codezeilen im Visual Studio-Editor, um Ihnen zu zeigen, ob der Code, den Sie schreiben, von Komponententests abgedeckt ist, und ob die Tests, die ihn abdecken, erfolgreich sind.  Die folgende Abbildung zeigt Codezeilen mit erfolgreichen und fehlgeschlagenen Tests sowie Codezeilen, die nicht durch Tests abgedeckt sind. Zeilen mit einem grünen „✓“ werden nur durch bestandene Tests abgedeckt, Zeilen mit einem roten „x“ werden von einem oder mehreren nicht bestandenen Tests abgedeckt, und Zeilen mit einem blauen „➖“ werden von keinem Test abgedeckt.

  ![Bild](./media/lut-codewindow.png)

Die Abdeckungsvisualisierung von Live Unit Testing wird sofort aktualisiert, wenn Sie Code im Code-Editor ändern. Während der Verarbeitung der Änderungen wird die Visualisierung geändert, um anzugeben, dass die Daten nicht auf dem neuesten Stand sind. Dazu wird ein rundes Uhrensymbol unterhalb der Symbole für erfolgreiche, fehlgeschlagene und nicht abgedeckte Test angezeigt, wie in der folgenden Abbildung dargestellt.

  ![Bild](./media/lut-codeupdating.png)
 
## <a name="getting-information-on-successful-or-failed-tests"></a>Abrufen von Informationen zu erfolgreichen oder fehlgeschlagenen Tests

Wenn Sie den Mauszeiger im Codefenster über das Symbol für erfolgreiche oder fehlgeschlagene Tests bewegen, können Sie sehen, wie viele Tests diese Zeile betreffen. Wenn Sie auf das Symbol klicken, können Sie den Status der einzelnen Tests sehen, wie in der folgenden Abbildung dargestellt wird:
 
  ![Bild](./media/lut-failedinfo.png) 

Neben der Angabe der Namen und Testergebnisse können Sie mithilfe der QuickInfo die Gruppe von Tests erneut ausführen sowie mit dem Debugger ausführen. Wenn Sie einen oder mehrere Tests in der QuickInfo auswählen, können Sie diese Tests auch ausführen oder debuggen. Auf diese Weise können Sie Ihre Tests debuggen, ohne das Codefenster verlassen zu müssen. Wenn der Debugger eine [`Assert`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert)-Methode ausführt, die ein unerwartetes Ergebnis zurückgibt, wird die Programmausführung bei der Überwachung aller eventuell festgelegten Haltepunkte und zusätzlich beim Debuggen angehalten. 

Wenn Sie den Mauszeiger über einen nicht bestandenen Test in der QuickInfo bewegen, wird sie erweitert, und es werden zusätzliche Informationen zum jeweiligen Fehler bereitgestellt, wie in der folgenden Abbildung dargestellt wird. Wenn Sie in der QuickInfo auf den nicht bestandenen Test doppelklicken, können Sie direkt zum Test navigieren.

  ![Bild](./media/lut-failedmsg.png) 

Wenn Sie zum nicht bestandenen Test navigieren, kennzeichnet Live Unit Testing in der Methodensignatur auch die Tests visuell, die bestanden wurden (angezeigt durch ein halbvolles Becherglas mit einem grünen „✓“), die nicht bestanden wurden (ein halbvolles Becherglas mit einem roten „🞩“) oder die nicht von Live Unit Testing abgedeckt wurden (ein halbvolles Becherglas mit einem blauen „➖“). Methoden, die keine Testmethoden darstellen, sind nicht mit einem Symbol versehen. Die folgende Abbildung zeigt alle vier Arten von Methoden.
 
  ![Bild](media/lut-testsource.png)
 
## <a name="diagnosing-and-correcting-test-failures"></a>Diagnose und Korrektur von fehlgeschlagenen Tests

Über den fehlgeschlagenen Test können Sie problemlos den Produktcode debuggen, ihn bearbeiten und die Entwicklung Ihrer Anwendung fortsetzen. Da Live Unit Testing im Hintergrund ausgeführt wird, müssen Sie Live Unit Testing beim Debuggen, Bearbeiten und Fortsetzen des Zyklus nicht beenden und neu starten.

Beispiel: Der in der obigen Abbildung dargestellte nicht bestandene Test wurde durch die falsche Annahme in der Testmethode verursacht, dass nicht alphabetische Zeichen `true` zurückgeben, wenn sie an die <xref:System.Char.IsLower%2A?displayProperty=fullName>-Methode übergeben werden. Nachdem wir die Testmethode korrigiert haben, stellen wir fest, dass alle Tests bestanden wurden. Währenddessen müssen wir Live Unit Testing nicht anhalten oder beenden.

## <a name="live-unit-testing-and-test-explorer"></a>Live Unit Testing und Test-Explorer

Normalerweise stellt der **Test-Explorer** die Schnittstelle bereit, mit der Sie Tests ausführen und debuggen und Testergebnisse analysieren können. Live Unit Testing ist in den **Test-Explorer** integriert. Wenn Live Unit Testing nicht aktiviert ist oder beendet wurde, zeigt der **Test-Explorer** den Status von Komponententests an, als zuletzt ein Test ausgeführt wurde. Änderungen am Quellcode erfordern, dass Sie die Tests erneut ausführen. Wenn Live Unit Testing dagegen aktiviert ist, wird der Status der Komponententests im **Test-Explorer** sofort aktualisiert. Sie müssen Komponententests nicht mehr explizit ausführen. 

> [!NOTE]
> Öffnen Sie **Test-Explorer** in der obersten Ebene des Visual Studio-Menüs durch Auswahl von **Test**, **Windows**, **Test-Explorer**.  

Möglicherweise ist Ihnen ausgefallen, dass im **Test-Explorer**-Fenster einige Tests als verblasst angezeigt werden. Beispiel: Wenn Sie Live Unit Testing aktivieren, nachdem Sie ein zuvor gespeichertes Projekt geöffnet haben, ist das **Test-Explorer**-Fenster mit Ausnahme des nicht bestandenen Test verblasst, wie in der folgenden Abbildung gezeigt wird. In diesem Fall hat Live Unit Testing den nicht bestandenen Test erneut ausgeführt, jedoch nicht die erfolgreichen Tests, da die persistenten Daten von Live Unit Testing darauf hinweisen, dass keine Änderungen festgestellt wurden, seitdem die Tests zuletzt erfolgreich ausgeführt wurden.

  ![Bild](media/lut-test-explorer.png)

Sie können alle Tests, die verblasst angezeigt werden, erneut ausführen. Wählen Sie hierfür im **Test-Explorer**-Menü die Option **Alle ausführen** oder **Ausführen**, oder wählen Sie im **Test-Explorer**-Menü einen oder mehrere Tests aus, klicken Sie mit der rechten Maustaste darauf, und wählen Sie im Popupmenü **Ausgewählte Tests ausführen** oder **Ausgewählte Tests debuggen** aus. Tests, die ausgeführt werden, werden oben angezeigt.

Es gibt einige Unterschiede zwischen dem automatischen Ausführen und Aktualisieren der Testergebnisse durch Live Unit Testing und dem expliziten Ausführen von Tests im **Test-Explorer**. Zu diesen Unterschieden zählen Folgende:

- Beim Ausführen oder Debuggen von Tests im Test-Explorer-Fenster werden reguläre Binärdateien ausgeführt. Live Unit Testing führt dagegen instrumentierte Binärdateien aus. 
- Live Unit Testing erstellt keine neue Anwendungsdomäne zum Ausführen von Tests, sondern führt Tests mit der Standarddomäne aus. Tests, die über das **Test-Explorer**-Fenster ausgeführt werden, erstellen eine neue Anwendungsdomäne.
- Live Unit Testing führt Tests in allen Testassemblys nacheinander aus. Wenn Sie mehrere Tests im **Test-Explorer**-Fenster ausführen und die Schaltfläche **Tests parallel ausführen** ausgewählt ist, werden Tests parallel ausgeführt.

## <a name="live-unit-testing-and-large-solutions"></a>Live Unit Testing und große Projektmappen

Wenn Ihre Projektmappe 10 oder mehr Projekte enthält, zeigt Visual Studio das folgende Dialogfeld an, um Sie zu warnen, dass die dynamische Ausführung einer großen Anzahl von Tests in großen Projekten die Leistung schwerwiegend beeinträchtigen kann, wenn Sie Live Unit Testing starten, und keine persistenten Daten vorhanden sind, oder wenn Sie die Option **Test**, **Live Unit Testing**, **Bereinigt zurücksetzen** in der obersten Ebene des Visual Studio-Menüs auswählen. Bei Auswahl von **OK** führt Live Unit Testing alle Tests in der Projektmappe aus. Bei Auswahl von **Abbrechen** können Sie wählen, welche Tests ausgeführt werden. Informationen hierzu finden Sie im folgenden Abschnitt, [Einschließen und Ausschließen von Testprojekten und Testmethoden](#including-and-excluding-test-projects-and-test-methods).  

 ![Live Unit Testing-Dialogfeld für große Projekte](media/lut-large-project.png)

## <a name="including-and-excluding-test-projects-and-test-methods"></a>Einschließen und Ausschließen von Testprojekten und Testmethoden

Bei Projektmappen mit vielen Testprojekten können Sie steuern, welche Projekte und welche einzelnen Methoden in einem Projekt von Live Unit Testing berücksichtigt werden. Wenn Sie z.B. eine Projektmappe mit Hunderten von Testprojekten haben, können Sie eine bestimmte Reihe von Testprojekten für Live Unit Testing auswählen. Hierfür stehen eine Reihe von Möglichkeiten zur Verfügung, je nachdem, ob Sie alle Tests im Projekt oder in der Projektmappe ausschließen, einen Großteil der Tests ein- oder ausschließen oder einzelne Tests ausschließen möchten. Live Unit Testing speichert den Status für das Einschließen/Ausschließen als Benutzereinstellung, wenn eine Projektmappe geschlossen und erneut geöffnet wird. 

**Ausschließen aller Tests in einem Projekt oder einer Projektmappe**

Um die einzelnen Projekte in Komponententests auszuwählen, gehen Sie nach dem Start von Live Unit Testing wie folgt vor:

1.  Klicken Sie mit der rechten Maustaste im Projektmappen-Explorer auf die Projektmappe, und wählen Sie **Livetests** und dann **Ausschließen** aus, um die gesamte Projektmappe auszuschließen.
1.  Klicken Sie mit der rechten Maustaste auf jedes Testprojekt, das Sie in die Tests einschließen möchten, und wählen Sie **Livetests** und dann **Einschließen** aus.

**Ausschließen von einzelnen Tests im Code-Editor-Fenster**

Im Code-Editor-Fenster können Sie einzelne Testmethoden ein- oder ausschließen. Klicken Sie im Code-Editor-Fenster mit der rechten Maustaste auf die Signatur der Testmethode. Wählen Sie dann **Live Tests**, **[die ausgewählte Methode] einschließen**, **Live Tests**, **[die ausgewählte Methode] ausschließen** oder **Live Tests**, **Alle außer [die ausgewählte Methode] ausschließen**, wobei „die ausgewählte Methode“ für den Namen der im Codefenster ausgewählten Methode steht. 

**Programmgesteuertes Ausschließen von Tests** 

Sie können auch das <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute>-Attribut anwenden, damit Methoden, Klassen oder Strukturen ihre Abdeckung nicht programmgesteuert in Live Unit Testing ausgeschlossen werden.

Mithilfe der folgenden Attribute können Sie ebenfalls einzelne Methoden von Live Unit Testing ausschließen:

- Für xUnit: `[Trait("Category", "SkipWhenLiveUnitTesting")]`
- Für NUnit: `[Category("SkipWhenLiveUnitTesting")]`
- Für MSTest: `[TestCategory("SkipWhenLiveUnitTesting")]` 
 
## <a name="see-also"></a>Siehe auch

[Tools zum Testen von Codes](https://www.visualstudio.com/vs/testing-tools/)   
[Live Unit Testing-Blog](https://go.microsoft.com/fwlink/?linkid=842514)   
[Live Unit Testing – häufig gestellte Fragen](live-unit-testing-faq.md)    
[Channel 9 Video: Live Unit Testing in Visual Studio 2017](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)

