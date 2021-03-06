---
title: Reduzieren und Erweitern von Codebereichen in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- outlining
- Visual Studio, expand/collapse code
- Visual Studio, outlining
- expand/collapse code
- code [Visual Studio], outlining
- code [Visual Studio], hiding
- outlining code
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 64fd40d78b31c4791c699c2602528b33a36f4245
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="outlining"></a>Gliedern

Sie können festlegen, dass bestimmter Code in der Ansicht ausgeblendet wird, indem Sie einen Codebereich reduzieren, der dann unterhalb eines Pluszeichens (+) angezeigt wird. Sie erweitern einen reduzierten Bereich, indem Sie auf das Pluszeichen klicken. Wenn Sie eine Tastatur verwenden, können Sie **STRG** + **M** + **M** drücken, um Bereiche zu reduzieren bzw. zu erweitern. Sie können einen Gliederungsbereich auch reduzieren, indem Sie am Gliederungsrand auf eine beliebige Zeile im Bereich doppelklicken, der direkt auf der linken Seite des Codes angezeigt. Sie können den Inhalt eines reduzierten Bereichs als QuickInfo sehen, wenn Sie auf den reduzierten Bereich zeigen.

Bereiche am Gliederungsrand werden auch hervorgehoben, wenn Sie mit der Maus auf den Rand zeigen. Die standardmäßige Hervorhebungsfarbe wird möglicherweise in einigen Farbkonfigurationen etwas schwach angezeigt. Sie können sie unter **Extras** > **Optionen** > **Umgebung** > **Schriftarten und Farben** > **Reduzierbarer Bereich** ändern.

Wenn Sie mit Code mit Rand arbeiten, können Sie die Bereiche erweitern, an denen Sie arbeiten, sie reduzieren, wenn Sie fertig sind, und dann mit anderen Bereichen fortfahren. Wenn Sie die Gliederung nicht anzeigen möchten, können Sie mit dem Befehl **Gliederung entfernen** die Gliederungsinformationen entfernen, ohne damit zugrunde liegenden Code zu beeinträchtigen.

Diese Aktionen werden durch die Befehle **Rückgängig** und **Wiederholen** im Menü **Bearbeiten** beeinflusst. Bei den Befehlen **Kopieren**, **Ausschneiden** und **Einfügen** sowie bei Drag & Drop-Vorgängen werden Gliederungsinformationen beibehalten, der Zustand des zuklappbaren Bereichs jedoch nicht. Wenn Sie beispielsweise einen zugeklappten Bereich kopieren, wird der kopierte Text beim Vorgang **Einfügen** als aufgeklappter Bereich eingefügt.

> [!CAUTION]
> Wenn Sie einen gegliederten Bereich ändern, geht die Gliederung möglicherweise verloren. Beispielsweise wird durch Löschvorgänge oder Suchen und Ersetzen das Ende des Bereichs möglicherweise gelöscht.

Die folgenden Befehle sind im Untermenü **Bearbeiten** > **Gliedern** zu finden.

|||
|-|-|
|Aktuelles Element umschalten|(STRG+M, STRG+H) – Reduziert einen ausgewählten Codeblock, der normalerweise nicht für eine Gliederung verfügbar wäre, beispielsweise einen `if`-Block. Um den benutzerdefinierten Bereich zu entfernen, verwenden Sie **Gliederung in aktuellem Element entfernen** (oder STRG+M, STRG+U). Nicht in Visual Basic verfügbar.|  
|Gliederungserweiterung umschalten|- Kehrt den aktuellen Zustand (ausgeblendet oder erweitert) des innersten Gliederungsbereichs um, wenn sich der Cursor in einem verschachtelten reduzierten Bereich befindet.|  
|Alle Gliederungen umschalten|(STRG+M, STRG+L) – Legt alle Bereiche auf denselben reduzierten oder erweiterten Zustand fest. Wenn einige Bereiche erweitert und andere reduziert sind, werden die reduzierten Bereiche erweitert.|  
|Gliederung entfernen|(STRG+M, STRG+P) – Entfernt alle Gliederungsinformationen für das gesamte Dokument.|  
|Gliederung in aktuellem Element entfernen|(STRG+M, STRG+U) – Entfernt die Gliederungsinformationen für den aktuell ausgewählten benutzerdefinierten Bereich. Nicht in Visual Basic verfügbar.|  
|Nur Definitionen anzeigen|(STRG+M, STRG+O) – Reduziert die Member aller Typen.|  
|Block zuklappen:\<logische Begrenzung>|(Visual C++) Reduziert einen Bereich in der Funktion mit der Einfügemarke. Wenn beispielsweise die Einfügemarke innerhalb einer Schleife platziert ist, wird die Schleife ausgeblendet.|  
|Alle zuklappen in: \<logische Strukturen>|(Visual C++) Reduziert alle Strukturen innerhalb der Funktion.|  

Sie können auch das Visual Studio SDK verwenden, um die Textbereiche zu definieren, die Sie erweitern oder reduzieren möchten. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Gliedern](../extensibility/walkthrough-outlining.md).

## <a name="see-also"></a>Siehe auch

[Writing code in the editor (Schreiben von Code im Code-Editor)](../ide/writing-code-in-the-code-and-text-editor.md)