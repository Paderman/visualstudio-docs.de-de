---
title: Inhalts-Modellansicht | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8db7c7d-31cf-479e-9dcc-299759891795
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 582082504b713988039af609d59150715f75ecfe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="content-model-view"></a>Inhaltsmodellansicht
Die Inhaltsmodellansicht bietet eine grafische Darstellung lokaler und globaler Schemaknoten und ihrer Komponenten. Dazu zählen einfache und komplexe Typen, Elemente, Modellgruppen, Attribute und Attributgruppen. XML-Kommentare und -Verarbeitungsanweisungen können nicht in der Inhaltsmodellansicht angezeigt werden. Die Inhaltsmodellansicht enthält zwei Bereiche: einen **Arbeitsbereich** Bereich, der eine Liste der Knoten im enthält die [Arbeitsbereich des XML-Schema-Designers](../xml-tools/xml-schema-designer-workspace.md), und der Entwurfsoberfläche, die Sie, in dem das Inhaltsmodell des Schemas sehen die im ausgewählten Knoten die **Arbeitsbereich** Bereich. Die Inhaltsmodellansicht enthält auch die Symbolleiste des XML-Schema-Designers und die Breadcrumb-Leiste.  
  
 Das folgende Bild zeigt den Arbeitsbereich mit sechs Schemaknoten. Der `purchaseOrder`-Knoten ist im Arbeitsbereich ausgewählt und wird auf der Entwurfsoberfläche angezeigt.  
  
 ![XML-Schema-Designer-Inhaltsmodellansicht](../xml-tools/media/xsddesigner_contentmodelview.gif "XSDDesigner_ContentModelView")  
  
## <a name="workspace-panel"></a>Arbeitsbereich  
 Nachdem Sie dem Arbeitsbereich Knoten hinzugefügt haben, erscheint die Liste der Knoten der **Arbeitsbereich** Bedienungsfeld der Inhaltsmodellansicht. Bei Auswahl von Knoten in der **Arbeitsbereich** Bereich, die sie auf der Entwurfsoberfläche der Inhaltsmodellansicht angezeigt werden. Um Knoten aus dem Arbeitsbereich zu löschen, verwenden Sie die XSD-Designer-Symbolleiste, die **Arbeitsbereich** Kontextmenü oder die ENTF-Taste.  
  
 Informationen zum Hinzufügen von Knoten finden Sie im Abschnitt "Hinzufügen von Knoten zum Arbeitsbereich" [Arbeitsbereich des XML-Schema-Designers](../xml-tools/xml-schema-designer-workspace.md).  
  
## <a name="design-surface"></a>Entwurfsoberfläche  
 Wenn Sie einen Knoten im Arbeitsbereich auswählen, wird er der Entwurfsoberfläche der Inhaltsmodellansicht hinzugefügt, wo Sie die Details des Knotens anzeigen können.  
  
 Das Inhaltsmodell eines Knotens wird durch eine erweiterbare grafische Struktur mit Elementen und Attributen als Strukturknoten dargestellt. Standardmäßig wird nur eine Ebene erweitert. Weitere Informationen wie Compositors, Typnamen, Gruppen und andere Container werden (bei erweiterter Struktur) auf einer vertikalen Leiste neben den zugehörigen Elementen und Attributen angezeigt. Wenn Sie auf einen vertikalen Balken doppelklicken, wird er horizontal dargestellt, und die Struktur wird reduziert. Wenn Sie auf einen horizontalen Balken doppelklicken, wird er vertikal dargestellt, und die Struktur wird erweitert. Durch Auswahl des vertikalen Balkens werden alle Knoten im Container ausgewählt. Rechts neben einem Knoten werden Erweiterungsschaltflächen angezeigt, wenn ein Element erweitert oder reduziert werden kann.  
  
 Wenn die Entwurfsoberfläche leer ist, werden der XML-Editor, der XML-Schema-Explorer und das Wasserzeichen angezeigt. Die *Wasserzeichen* ist eine Liste mit Links zu allen Ansichten des XSD-Designer. Wenn das Schemaset Fehler enthält, wird der folgende Text am Ende der Liste angezeigt: "Verwenden Sie die Fehlerliste, um die Fehler im Schemaset anzuzeigen und zu beheben."  
  
## <a name="breadcrumb-bar"></a>Breadcrumb-Leiste  
 Die Breadcrumb-Leiste am unteren Rand der Inhaltsmodellansicht zeigt an, wo sich der ausgewählte Knoten im Schemaset befindet.  
  
## <a name="context-menus"></a>Kontextmenüs  
 Wenn Sie auf der Entwurfsoberfläche oder im Arbeitsbereich mit der rechten Maustaste auf ein Element klicken, wird ein Kontextmenü angezeigt. In der folgenden Tabelle werden die Optionen beschrieben, die für die Entwurfsoberfläche der Inhaltsmodellansicht verfügbar sind.  
  
|Option|Beschreibung|  
|------------|-----------------|  
|**XML-Schema-Explorer anzeigen**|Legt den Fokus auf den Schema-Explorer und hebt den Schemasetknoten hervor.|  
|**In der Diagrammansicht anzeigen**|Wechselt zur Diagrammansicht.|  
|**Beispiel-XML generieren**|Ist nur für globale Elemente verfügbar. Generiert eine Beispiel-XML-Datei für das globale Element.|  
|**Dokumentation anzeigen**|Blendet den Inhalt von Anmerkungs-/Dokumentationsknoten ein bzw. aus.|  
|**Exportieren Sie Diagramm als Bild...**|Speichert die Entwurfsoberfläche in einer XPS-Datei.|  
|**Code anzeigen**|Öffnet die Datei, die den ausgewählten Knoten enthält, im XML-Editor. Das im XML-Schema-Explorer ausgewählte Element wird auch im XML-Editor ausgewählt.|  
|**Eigenschaftenfenster**|Öffnet die **Eigenschaften** Fenster (wenn es nicht bereits geöffnet ist). In diesem Fenster werden Informationen zum Knoten angezeigt.|  
  
 In der folgenden Tabelle werden die Optionen beschrieben, die für den Arbeitsbereich verfügbar sind.  
  
|Option|Beschreibung|  
|------------|-----------------|  
|**XML-Schema-Explorer anzeigen**|Legt den Fokus auf den Schema-Explorer und hebt den Schemasetknoten hervor.|  
|**In der Diagrammansicht anzeigen**|Wechselt zur Diagrammansicht.|  
|**Arbeitsbereich löschen**|Löscht den Arbeitsbereich und die Entwurfsoberfläche.|  
|**Aus Arbeitsbereich entfernen**|Entfernt ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche.|  
|**Alles außer Auswahl aus Arbeitsbereich entfernen**|Entfernt nicht ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche.|  
|**Beispiel-XML generieren**|Ist nur für globale Elemente verfügbar. Generiert eine Beispiel-XML-Datei für das globale Element.|  
|**Alle auswählen**|Wählt alle Knoten im Arbeitsbereich aus.|  
|**Code anzeigen**|Öffnet die Datei, die den ausgewählten Knoten enthält, im XML-Editor. Das im XML-Schema-Explorer ausgewählte Element wird auch im XML-Editor ausgewählt.|  
|**Eigenschaftenfenster**|Öffnet die **Eigenschaften** Fenster (wenn es nicht bereits geöffnet ist). In diesem Fenster werden Informationen zum Knoten angezeigt.|  
  
## <a name="properties-window"></a>Eigenschaftenfenster  
 Verwenden Sie das Kontextmenü um zu Beginn zu öffnen die **Eigenschaften** Fenster. Wird standardmäßig die **Eigenschaften** Fenster wird in der unteren rechten Ecke von Visual Studio. Wenn Sie einen Knoten, die in der Inhaltsmodellansicht gerendert wird klicken, wird die Eigenschaften dieses Knotens angezeigt der **Eigenschaften** Fenster.  
  
## <a name="xsd-designer-toolbar"></a>XSD-Designer-Symbolleiste  
 Die folgenden XSD-Designer-Symbolleistenschaltflächen sind aktiviert, wenn die Inhaltsmodellansicht aktiv ist.  
  
 ![XML-Schema-Designer-Symbolleiste](../xml-tools/media/xsdcontentmodelviewtoolbar.gif "XSDContentModelViewToolbar")  
  
|Option|Beschreibung|  
|------------|-----------------|  
|**Ausgangsansicht anzeigen**|Wechselt in den [Ausgangsansicht](../xml-tools/start-view.md). In dieser Ansicht kann mit der Tastenkombination zugegriffen werden: **STRG + 1**.|  
|**Inhaltsmodellansicht anzeigen**|Wechselt in den [Inhalte Modellansicht](../xml-tools/content-model-view.md). In dieser Ansicht kann mit der Tastenkombination zugegriffen werden: **STRG + 2**.|  
|**Diagrammansicht anzeigen**|Wechselt in den [Diagrammansicht](../xml-tools/graph-view.md). In dieser Ansicht kann mit der Tastenkombination zugegriffen werden: **STRG + 3**.|  
|**Arbeitsbereich löschen**|Löscht den Arbeitsbereich und die Entwurfsoberfläche.|  
|**Aus Arbeitsbereich entfernen**|Entfernt ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche.|  
|**Alles außer Auswahl aus Arbeitsbereich entfernen**|Entfernt nicht ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche.|  
|**Dokumentation anzeigen**|Blendet den Inhalt von Anmerkungs-/Dokumentationsknoten ein bzw. aus.|  
  
## <a name="panscroll"></a>Schwenken/Bildlauf  
 Sie können die Entwurfsoberfläche mit den Bildlaufleisten oder durch Drücken der STRG-TASTE und gleichzeitiges Klicken und Ziehen der Maus schwenken. Wenn Sie die Entwurfsoberfläche mittels Klicken und Ziehen schwenken, wird der Cursor als vier sich kreuzende und in unterschiedliche Richtungen weisende Pfeile angezeigt.  
  
## <a name="undoredo"></a>Rückgängig/Wiederholen  
 Die Funktion zum Rückgängigmachen bzw. Wiederholen ist in der Inhaltsmodellansicht für folgende Aktionen aktiviert:  
  
-   Hinzufügen eines einzelnen Knotens per Drag & Drop  
  
-   Hinzufügen mehrerer Knoten aus dem Suchergebnisfenster im Schema-Explorer  
  
-   Hinzufügen von Knoten aus der Ausgangsansicht  
  
-   Löschen einzelner oder mehrerer Knoten  
  
## <a name="zoom"></a>Zoom  
 Die Zoomfunktion befindet sich in der unteren rechten Ecke der Inhaltsmodellansicht.  
  
 Der Zoomfaktor kann wie folgt gesteuert werden:  
  
-   Halten Sie die STRG-TASTE gedrückt, und drehen Sie das Mausrad, während Sie die Maus über die Oberfläche der Inhaltsmodellansicht bewegen.  
  
-   Verwenden Sie das Schieberegler-Steuerelement. Auf dem Schieberegler wird der aktuelle Zoomfaktor angezeigt.  
  
Der Zoomschieberegler ist nicht transparent, wenn Sie ihn auswählen, mit der Maus darauf zeigen oder mit der STRG-TASTE und dem Mausrad zoomen. Ansonsten ist er transparent.  
  
## <a name="xml-editor-integration"></a>Integration des XML-Editors  
 Sie können über das Kontextmenü zwischen dem XSD-Designer und dem XML-Editor hin- und herwechseln.  
  
 Wenn Sie im XML-Editor Änderungen am Schemaset vornehmen, werden die Änderungen in der Inhaltsmodellansicht synchronisiert. Weitere Informationen finden Sie unter [Integration mit XML-Editor](../xml-tools/integration-with-xml-editor.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeitsbereich des XML-Schema-Designers](../xml-tools/xml-schema-designer-workspace.md)