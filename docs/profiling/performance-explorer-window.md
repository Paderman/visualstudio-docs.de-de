---
title: "Das Fenster „Leistungs-Explorer“ | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performanceexplorer
- vs.performance.explorer
helpviewer_keywords:
- performance tools, Performance Explorer
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 16b3c7111ddda71d070456c409b95f53c04f0063
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2018
---
# <a name="performance-explorer-window"></a>Das Fenster "Leistungs-Explorer"

Im Fenster **Leistungs-Explorer** in der integrierten Visual Studio-Entwicklungsumgebung (IDE) können Sie mit den Visual Studio-Profilerstellungstools Leistungssitzungen konfigurieren und starten.

## <a name="performance-explorer-toolbar"></a>Die Symbolleiste „Leistungs-Explorer“

Die folgenden Optionen sind auf der Symbolleiste **Leistungs-Explorer** verfügbar:

- **Leistung-Assistenten starten**: Zeigt die Leistung-Assistenten an, um eine neue Leistungssitzung zum Leistungs-Explorer-Fenster hinzuzufügen.

- **New Performance Session**: Fügt dem Leistungs-Explorer-Fenster eine leere Leistungssitzung hinzu.

- **Start**: Mit der **Start** Befehlsschaltfläche können Sie die Anwendung starten, die die Profilerstellung sofort aktiviert (**Mit Profilerstellung starten**) oder sie anhält (**Mit angehaltener Profilerstellung starten**).

- **Methode**: Gibt an, ob die Profilerstellungsmethode der Sitzung Eine Beispiel- oder Instrumentierungsmethode ist.

- **Beenden Sie**: Beendet die Anwendung und den Profiler sofort.

- **Anfügen/Trennen**: Zeigt das Dialogfeld **Profiler an Prozess anfügen** an, damit Sie einen laufenden Prozess auswählen können, an den Sie den Profiler anfügen.

## <a name="performance-explorer-window"></a>Das Fenster "Leistungs-Explorer"

Das Fenster **Leistungs-Explorer** enthält eine Strukturansicht, in dem die Binärdateien und Berichtsatendateien von einer oder mehreren Leistungssitzungen angezeigt werden.

- **Der Sitzungsname**: Der Stamm der Strukturansicht enthält den Namen der Sitzung. Mit der rechten Maustaste auf den Sitzungsnamen klicken, um die Sitzungseigenschaften einzurichten, oder die Zielanwendung und den Profiler zu starten.

- **Ziele**: Zeigt die Namen der Binärdateien an, für die in der Sitzung ein Profil erstellt werden. Klicken Sie mit der rechten Maustaste auf **Ziele**, um eine Binärdatei, ein [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Projekt oder eine Website hinzufügen oder entfernen. Klicken Sie mit der rechten Maustaste auf einen Zielnamen, um Eigenschaften für die jeweilige Binärdatei festzulegen.

- **Berichte**: Zeigt die Namen von Profilerstellungsdatendateien an, die für die Sitzung generiert werden. Klicken Sie mit der rechten Maustaste auf **Berichte**, um einen vorhandenen Bericht hinzuzufügen oder zwei Profiler-Datendateien zu vergleichen. Klicken Sie mit der rechten Maustaste auf einen Berichtsnamen, um eine Profilerstellungsdatendatei zu öffnen, entfernen oder exportieren.

## <a name="see-also"></a>Siehe auch

[Übersichten](../profiling/overviews-performance-tools.md)  
[Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)  
[Steuern der Datenauflistung](../profiling/controlling-data-collection.md)