---
title: Arbeiten mit Subversion | Microsoft-Dokumentation
description: "Verwenden Subversion in Visual Studio für Mac"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 2400ED9C-6236-4C0A-A3AB-9D7CBE1F0CF4
ms.openlocfilehash: 39f7407854b2ff74552209762565236adb403d84
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="working-with-subversion"></a>Arbeiten mit Subversion

Subversion ist das zentralisierte Versionskontrollsystem, mit dem Sie eine einzelne Masterkopie zentraler Daten auschecken können. Im Gegensatz zu Git wird beim Auschecken eines Subversion-Repositorys nicht das gesamte Repository geklont, sondern es wird nur eine Momentaufnahme gemacht.

Subversion verwendet ein Modell, das auf den Vorgängen Kopieren, Ändern und Zusammenführen aufbaut, damit Benutzer die Möglichkeit haben, gleichzeitig am selben Repository zu arbeiten. Dies bedeutet, dass die Benutzer eine lokale, d.h. Arbeitskopie der zentralisierten Daten erstellen, an der sie dann unabhängig voneinander arbeiten. Die Änderungen an den Arbeitskopien der Benutzer werden chronologisch zusammengeführt.

Angenommen, Benutzer A und Benutzer B checken eine Kopie aus dem Remoterepositorys aus und ändern die Datei jeweils. Benutzer A schließt die Änderungen ab und committet sie remote. Bevor Benutzer B seine Arbeit committet, muss seine Arbeitskopie mit den Änderungen aus dem Remoterepository aktualisiert, also mit den Änderungen von Benutzer A zusammengeführt werden.

In den folgenden Abschnitten wird erläutert, wie Subversion für die Versionskontrolle in Visual Studio für Mac verwendet werden kann.

Die folgende Abbildung veranschaulicht die Optionen, die in Visual Studio für Mac vom Menüelement für die Versionskontrolle bereitgestellt werden:

![Menüelemente für die Versionskontrolle](media/version-control-svnVersionControlMenu.png)

## <a name="checkout"></a>Auschecken…

Bevor Sie ein Remoterepository von Subversion verwenden können, checken Sie es aus, um eine Arbeitskopie dieses Verzeichnisses auf dem lokalen Computer zu erstellen.

Weitere Informationen zur Funtkion **Auschecken** in Visual Studio für Mac finden Sie im Abschnitt [Einrichten eines Subversion-Repositorys](~/set-up-subversion-repository.md).

## <a name="update-solution"></a>Aktualisieren von Projektmappen

Bei Remoterepositorys sollten Sie immer im Hinterkopf behalten, dass andere Benutzer Dateien ändern können und Ihre Arbeitskopie daher möglicherweise veraltet ist. Um Konflikte zu vermeiden, sollten Sie etwaige Änderungen immer aus dem Repository in die Projektmappe pullen, bevor Sie mit der Arbeit beginnen und committen. Um Änderungen zu pullen, wählen Sie das Menüelement **Versionskontrolle > Projektmappe aktualisieren** aus.

## <a name="review-solution-and-commit"></a>Überprüfen und Committen der Projektmappe

Um Änderungen an Dateien zu überprüfen, verwenden Sie die Registerkarten „Änderungen“, „Verantwortung zuweisen“, „Protokoll“ und „Zusammenführen“ für jedes Dokument, wie in der folgenden Abbildung dargestellt:

![Registerkarten für die Versionskontrolle](media/version-control-vcTabs.png)

Überprüfen Sie alle Änderungen an einem Projekt, indem Sie zum Menüelement **Versionskontrolle > Review Solution and Commit** (Lösung und Commit überprüfen) wechseln:

![Überprüfen der Projektmappe](media/version-control-vcStatus.png)

Damit können Sie alle Änderungen in jeder Projektdatei mit den Optionen „Revert“ (Wiederherstellen), „Create Patch“ (Patch erstellen) oder „Commit“ (Commit ausführen) anzeigen.

Um eine Datei für ein Remoterepository zu committen, klicken Sie auf „Commit...“, geben Sie eine Commitnachricht ein, und bestätigen Sie mit „Commit“:


![Committen einer Datei](media/version-control-svnCommit.png)

Damit werden die Änderungen an das Repository gesendet, in dem die neue Revision mit allen Änderungen erstellt wird.
