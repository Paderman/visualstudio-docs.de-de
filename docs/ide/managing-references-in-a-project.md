---
title: Verwalten von Verweisen in einem Projekt | Microsoft-Dokumentation
ms.custom: 
ms.date: 10/26/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.ProjectPropertiesReferencePaths
- cs.ProjectPropertiesReferencePaths
helpviewer_keywords:
- C# projects, references
- referencing objects, project references
- external component references
- referencing namespaces
- Visual Basic projects, references
- referencing components, external components
- Web references, types of project references
- namespaces [Visual Studio], referencing
- COM components, referencing
- objects [Visual Studio], referencing
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b7fbb9ddfd53210f460b5035f1f83159e46b5aa1
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2018
---
# <a name="managing-references-in-a-project"></a>Verwalten von Verweisen in einem Projekt

Bevor Sie Code schreiben können, der sich auf eine externe Komponente oder einen verbundenen Dienst bezieht, müssen Sie zunächst einen Verweis auf diese Komponente im Projekt einrichten. Ein Verweis ist im Prinzip ein Eintrag in einer Projektdatei, der Informationen beinhaltet, die von Visual Studio zum Auffinden der Komponente oder des Diensts benötigt.

Um einen Verweis hinzuzufügen, klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Knoten „Verweise“, und klicken Sie dann auf **Verweis hinzufügen**. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen und Entfernen von Verweisen mit dem Verweis-Manager](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).

![Hinzufügen eines Verweises in Visual C&#43;&#43;](../ide/media/vs2015_cpp_add_reference.png "vs2015_cpp_add_reference")

Sie können einen Verweis auf die folgenden Komponenten- und Diensttypen herstellen:

- .NET Framework-Klassenbibliotheken oder -Assemblys

- UWP-Apps

- COM-Komponenten

- Sonstige Assemblys oder Klassenbibliotheken von Projekten in derselben Projektmappe

- XML-Webdienste

## <a name="uwp-app-references"></a>Verweise von UWP-Apps

### <a name="project-references"></a>Projektverweise

Projekte von Universellen Windows-Plattform (UWP), können Verweise auf andere UWP-Projekte in der Projektmappe oder auf Windows 8.1-Projekte oder Binärdateien erstellen. Die Voraussetzung hierfür ist, dass diese Projekte keine APIs verwenden, die in Windows 10 nicht mehr unterstützt werden. Weitere Informationen finden Sie unter [Move from Windows Runtime 8 to UWP](/windows/uwp/porting/w8x-to-uwp-root)(Von Windows-Laufzeit zu UWP) (möglicherweise in englischer Sprache).

Informationen zur Neuausrichtung von Windows 8.1-Projekten auf Windows 10 finden Sie unter [Übertragung, Migration und Upgrade der Visual Studio-Projekte](../porting/port-migrate-and-upgrade-visual-studio-projects.md).

### <a name="extension-sdk-references"></a>Verweise auf Erweiterungs-SDKs

In Visual Basic, C#, C++ und JavaScript für die universelle Windows-Plattform (UWP) geschriebene Apps können auf Erweiterungs-SDKs verweisen, die auf Windows 8.1 ausgerichtet sind, sofern diese Erweiterungs-SDKs keine APIs verwenden, die in Windows 10 nicht mehr unterstützt werden. Besuchen Sie die Website des Anbieters des Erweiterungs-SDKs, um festzustellen, ob UWP-Apps darauf verweisen können.

Wenn Sie feststellen, dass das Erweiterungs-SDK, auf das von Ihrer Anwendung verwiesen wird, nicht unterstützt wird, müssen Sie folgende Schritte ausführen:

1. Schauen Sie sich den Namen des Projekts an, das den Fehler verursacht. Die Plattform, auf die Ihr Projekt abzielt, steht in Klammern neben dem Projektnamen. Beispielsweise bedeutet **MyProjectName (Windows 8.1)** dass das Projekt **MyProjectName** auf die Plattformversion Windows 8.1 abzielt.

1. Wechseln Sie zur Website des Anbieters des nicht unterstützten Erweiterungs-SDKs, und installieren Sie die SDK-Version, deren Abhängigkeiten mit der Version der Plattform kompatibel sind, auf die Ihr Projekt ausgelegt ist.

    > [!NOTE]
    > Um herauszufinden, ob ein Erweiterungs-SDK von einem anderen abhängt, können Sie im **Verweis-Manager** nachsehen. Starten Sie Visual Studio neu, erstellen Sie ein neues C#-UWP-App-Projekt, klicken Sie dann mit der rechten Maustaste auf das Projekt, und wählen Sie **Verweis hinzufügen** aus. Wechseln Sie zur Registerkarte **Fenster** und dann zur Unterregisterkarte **Erweiterungen**, und wählen Sie das Erweiterungs-SDK aus. Sehen Sie sich den **Verweis-Manager** im rechten Bereich an. Wenn Abhängigkeiten bestehen, werden sie dort aufgeführt.

    > [!IMPORTANT]
    > Wenn Ihr Projekt auf Windows 10 ausgerichtet ist und das im vorherigen Schritt installierte Erweiterungs-SDK von Microsoft Visual C++ Runtime Package abhängt, lautet die mit Windows 10 kompatible Version von Microsoft Visual C++ Runtime Package 14.0 und wird mit Visual Studio installiert.

1. Wenn das im vorherigen Schritt installierte Erweiterungs-SDK von anderen Erweiterungs-SDKs abhängt, rufen Sie die Websites der entsprechenden Anbieter auf, und installieren Sie die Versionen der Abhängigkeiten, die mit der Version der Plattform kompatibel sind, auf die Ihr Projekt ausgelegt ist.

1. Starten Sie Visual Studio neu, und öffnen Sie Ihre App.

1. Klicken Sie im Projekt, das den Fehler verursacht hat, mit der rechten Maustaste auf den Knoten **Verweise** und anschließend auf **Verweis hinzufügen**.

1. Klicken Sie auf die Registerkarte **Fenster** und anschließend auf die Unterregisterkarte **Erweiterungen**. Deaktivieren Sie dann die Kontrollkästchen für die alten Erweiterungs-SDKs, und aktivieren Sie die Kontrollkästchen für die neuen. Klicken Sie auf **OK**.

## <a name="adding-a-reference-at-design-time"></a>Hinzufügen von Verweisen zur Entwurfszeit

Wenn Sie im Projekt einen Verweis auf eine Assembly erstellen, sucht Visual Studio die Assembly an den folgenden Speicherorten:

- Das aktuelle Projektverzeichnis. (Sie können die Assemblys über die Registerkarte **Durchsuchen** suchen.)

- Andere Projektverzeichnisse in der gleichen Projektmappe. (Sie finden diese Assemblys auf der Registerkarte **Projekte** .)

> [!NOTE]
> Alle Projekte enthalten einen impliziten Verweis auf "mscorlib". Visual Basic-Projekte enthalten einen impliziten Verweis auf `Microsoft.VisualBasic`. Alle Projekte enthalten einen impliziten Verweis auf `System.Core`. Dies gilt auch, wenn `System.Core` aus der Liste der Verweise entfernt wird.

## <a name="references-to-shared-components-at-run-time"></a>Verweise auf freigegebene Komponenten zur Laufzeit

Zur Laufzeit müssen sich Komponenten entweder im Ausgabepfad des Projekts oder im Globalen Assemblycache (GAC) befinden. Wenn das Projekt einen Verweis auf ein Objekt enthält, der sich nicht an einem dieser Orte befindet, müssen Sie den Verweis beim Erstellen des Projekts in den Ausgabepfad des Projekts kopieren. Die <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> -Eigenschaft gibt an, ob diese Kopie erstellt werden muss. Wenn der Wert **True**lautet, wird der Verweis beim Erstellen des Projekts in das Projektverzeichnis kopiert. Wenn der Wert **False**ist, wird der Verweis nicht kopiert.

Wenn Sie eine Anwendung bereitstellen, die einen Verweis auf eine im GAC registrierte benutzerdefinierte Komponente enthält, wird die Komponente unabhängig von der <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> -Einstellung nicht mit der Anwendung bereitgestellt. In früheren Versionen von Visual Studio konnten Sie die <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A>-Eigenschaft für einen Verweis festlegen, um sicherzustellen, dass die Assembly bereitgestellt wird. Jetzt müssen Sie die Assembly manuell dem Ordner \Bin hinzufügen. Dadurch wird der gesamte benutzerdefinierte Code einer Prüfung unterzogen, und das Risiko der Veröffentlichung von unbekanntem benutzerdefinierten Code wird vermindert.

Wenn sich die Assembly bzw. Komponente im globalen Assemblycache befindet oder eine .NET Framework-Komponente ist, wird die <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> -Eigenschaft standardmäßig auf **False** festgelegt. Andernfalls wird der Wert auf **True**festgelegt. Verweise zwischen Projekten werden immer auf **True**festgelegt.

## <a name="referencing-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Verweisen auf ein Projekt oder eine Assembly, die auf eine andere Version von .NET Framework ausgerichtet ist

Sie können Anwendungen erstellen, die auf Projekte oder Assemblys verweisen, die auf eine andere Version von .NET Framework abzielen. Sie können z.B. eine Anwendung für [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] erstellen, die auf eine Assembly verweist, die wiederum auf [!INCLUDE[dnprdnext](../ide/includes/dnprdnext_md.md)] ausgelegt ist. Wenn Sie ein Projekt für eine frühere Version von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] erstellen, können Sie in diesem Projekt nicht auf Projekte oder Assemblys verweisen, die auf eine neuere Version ausgerichtet sind.

Weitere Informationen finden Sie unter [Festlegen einer bestimmten .NET-Framework-Zielversion](../ide/targeting-a-specific-dotnet-framework-version.md).

## <a name="project-to-project-references"></a>Projekt-zu-Projekt-Verweise

Verweise zwischen Projekten sind Verweise auf Projekte mit Assemblys, die Sie im Dialogfeld **Projekt** erstellen. Visual Studio kann anhand eines Pfads zum Projekt nach einer Assembly suchen.

Wenn Sie ein Projekt haben, das eine Assembly erstellt, müssen Sie auf das Projekt verweisen und keinen Dateiverweis verwenden (siehe unten). Der Vorteil eines Verweises zwischen Projekten liegt darin, dass eine Abhängigkeit zwischen den Projekten im Buildsystem erzeugt wird. Das abhängige Projekt wird erstellt, wenn es sich seit der letzten Erstellung des verweisenden Projekts geändert hat. Bei Dateiverweisen wird keine Buildabhängigkeit erstellt, d. h., das verweisende Projekt kann ohne Erstellen des abhänigen Projekts erstellt werden, und der Verweis kann veraltet sein. (Das heißt, das Projekt kann auf eine vorher erstellte Version des Projekts verweisen.) Dies kann dazu führen, dass im BIN-Verzeichnis mehrere Versionen einer einzigen DLL erforderlich sind, was jedoch nicht möglich ist. Wenn dieser Konflikt auftritt, wird eine Meldung wie die folgende angezeigt: „Fehler: Die Abhängigkeit ‚Datei‘ in Projekt ‚Projekt‘ kann nicht in das Ausführungsverzeichnis kopiert werden, da sie den Verweis ‚Datei‘ überschreiben würde.“ Weitere Informationen finden Sie unter [Problembehandlung bei fehlerhaften Verweisen](../ide/troubleshooting-broken-references.md) und [Vorgehensweise: Erstellen und Entfernen von Projektabhängigkeiten](../ide/how-to-create-and-remove-project-dependencies.md).

> [!NOTE]
> Anstelle eines Projekt-zu-Projekt-Verweises wird ein Dateiverweis erstellt, wenn die Zielversion von .NET Framework eines Projekts Version 4.5 ist und die Zielversion des anderen Projekts Version 2, 3, 3.5 oder 4.0 ist.

## <a name="file-references"></a>Dateiverweise

Dateiverweise sind direkte Verweise auf Assemblys, die sich außerhalb eines Visual Studio-Projekts befinden. Sie erstellen diese mithilfe der Registerkarte **Durchsuchen** im **Verweis-Manager**. Dateiverweise bieten sich an, wenn Sie nur eine Assembly oder Komponente haben und nicht das Projekt, das sie als Ausgabe erstellt.

## <a name="see-also"></a>Siehe auch

[Problembehandlung bei fehlerhaften Verweisen](../ide/troubleshooting-broken-references.md)  
[Gewusst wie: Hinzufügen und Entfernen von Verweisen mit dem Verweis-Manager](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)
