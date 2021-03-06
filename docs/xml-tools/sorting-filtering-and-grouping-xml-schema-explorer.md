---
title: Sortieren, Filtern und gruppieren (XML-Schema-Explorer) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b8fe3daa1c95169623a908307d4d6c81044d378f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>Sortieren, Filtern und Gruppieren (XML-Schema-Explorer)
In diesem Thema wird beschrieben, die über die verfügbaren Optionen die **sortieren, Filtern und Gruppierungsoptionen** Menü auf der Symbolleiste des XML-Schema-Explorer.  
  
## <a name="filter-options"></a>Filteroptionen  
 Die folgenden Filteroptionen sind verfügbar. Wird standardmäßig die **Namespaces anzeigen** und **Schemadateien anzeigen** Optionen ausgewählt werden.  
  
-   **Namespaces anzeigen**.  
  
-   **Schemadateien anzeigen**.  
  
-   **Anzeigen von Compositors (Sequence/Choice/All)**.  
  
## <a name="sorting-options"></a>Sortierungsoptionen  
 Die folgenden Sortierungsoptionen sind verfügbar. Die Standardeinstellung ist **nach Sortiertyp**. Die "Sortieren nach"-Optionen gelten nicht für Dateien und Namespaces.  
  
-   **Nach Typ sortieren**.  
  
-   **Nach Namen sortieren**.  
  
-   **Nach Dokumentreihenfolge**.  
  
### <a name="sort-by-type"></a>Nach Typ sortieren  
 Wenn die **nach Sortiertyp** ausgewählt ist, werden globale Knoten in der folgenden Reihenfolge sortiert. Knoten sind innerhalb jeder Gruppe alphabetisch sortiert.  
  
1.  `import`-Knoten  
  
2.  `include`-Knoten  
  
3.  `redefine`-Knoten  
  
4.  `attribute`-Knoten  
  
5.  `attributeGroup`-Knoten  
  
6.  `complexType`-Knoten  
  
7.  `simpleType`-Knoten  
  
8.  `element`-Knoten  
  
9. `group`-Knoten  
  
### <a name="sort-by-name"></a>Nach Namen sortieren  
 Wenn die **nach Namen sortieren** ausgewählt ist, werden globale Knoten in der folgenden Reihenfolge sortiert:  
  
1.  `import`-Knoten (in alphabetischer Reihenfolge der Namespaces)  
  
2.  `include`-Knoten (in alphabetischer Reihenfolge der `schemaLocation`-Attribute)  
  
3.  `redefine`-Knoten (in alphabetischer Reihenfolge der `schemaLocation`-Attribute)  
  
4.  Andere globale Knoten in alphabetischer Reihenfolge  
  
### <a name="document-order"></a>Dokumentreihenfolge  
 Die **Dokumentreihenfolge** Option ist verfügbar, wenn die **Schemadateien anzeigen** ausgewählt ist. Wenn **Dokumentreihenfolge** ausgewählt ist, werden globale Knoten in der Reihenfolge, in der sie in der Schemadatei erscheinen, angezeigt.  
  
## <a name="persisting-sortfilter-options"></a>Speichern von Sortierungs-/Filteroptionen  
 Die Sortierungs-, Filter- und Gruppierungsoptionen werden in der Registrierung für jeden Benutzer gespeichert, unabhängig davon, welche Projektmappe oder welche Dateien beim Ändern der Einstellungen geöffnet waren.