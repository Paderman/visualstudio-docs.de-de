---
title: Intl.DateTimeFormat-Objekt (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DateTimeFormat
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: cc555ac2-f31c-4239-a612-b84c08e3a37f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c50d6d7d939ebe05ce3ff9b434111413803ea40
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="intldatetimeformat-object-javascript"></a>Intl.DateTimeFormat-Objekt (JavaScript)
Stellt die gebietsschemaspezifischen Datums- und Uhrzeitformatierungen bereit.  
  
## <a name="syntax"></a>Syntax  
  
```  
dateTimeFormatObj = new Intl.DateTimeFormat([locales][, options])  
```  
  
#### <a name="parameters"></a>Parameter  
 `dateTimeFormatObj`  
 Erforderlich. Der Variablenname, der dem `DateTimeFormat`-Objekt zugewiesen wird.  
  
 `locales`  
 Dies ist optional. Ein Array von Gebietsschemazeichenfolgen, das einen oder mehrere Sprach- oder Gebietsschematags enthält. Wenn Sie mehr als eine Gebietsschemazeichenfolge einschließen, führen Sie sie in absteigender Reihenfolge ihrer Priorität auf, sodass der erste Eintrag das bevorzugte Gebietsschema ist. Wenn Sie diesen Parameter weglassen, wird das Standardgebietsschema der JavaScript-Laufzeit verwendet. Weitere Informationen finden Sie im Abschnitt Hinweise.  
  
 `options`  
 Dies ist optional. Ein Objekt mit einer oder mehreren Eigenschaften zur Angabe von Formatierungsoptionen für Datum und Uhrzeit. Weitere Informationen finden Sie im Abschnitt Hinweise.  
  
## <a name="remarks"></a>Hinweise  
 Die `locales` Parameter entsprechen [BCP-47](http://tools.ietf.org/html/rfc5646) Sprach- oder gebietsschematags Tags wie "En-US" und "Zh-CN". Das Tag enthält möglicherweise Sprache, Region, Land und Varianten. Beispiele für Sprachtags, finden Sie unter [Anhang A](http://tools.ietf.org/html/rfc5646#appendix-A) BCP-47. Für `DateTimeFormat`, fügen Sie möglicherweise die **-u** enthalten eine oder beide der folgenden Unicode-Erweiterungen in der gebietsschemazeichenfolge:  
  
-   -Nu, um eine zahlensystemerweiterung anzugeben: *Sprache*-*Region*-u-Nu -*Numberingsystem*  
  
     wobei *Numberingsystem* einer der folgenden sein: arabische, Arabext, schmuggelte., Beng, Delta, Fullwide, Gujr, Experte, Hanidec, Khmr, Knda, Laoo, Latn, Wagen, Mylm, Mong, Mymr, Orya, Tamldec, Telu, Thai, Tibt.  
  
-   -ca auf einen Kalender angeben: *Sprache*-*Region*-u-ca -*Kalender*  
  
     auf dem *Kalender* einer der folgenden sein: buddhistischen, Chinesisch, Gregory Islamische, Islamicc, Japanisch.  
  
 Der `options`-Parameter enthält möglicherweise die folgenden Eigenschaften:  
  
|Eigenschaft|Beschreibung|Mögliche Werte|Standardwert|  
|--------------|-----------------|---------------------|-------------------|  
|`localeMatcher`|Gibt den zu verwendenden Algorithmus für die Gebietsschemaübereinstimmung an.|"lookup","best fit"|"best fit"|  
|`formatMatcher`|Gibt den zu verwendenden Algorithmus für die Formatübereinstimmung an.|"basic", "best fit"|"best fit"|  
|`hour12`|Gibt an, ob für Zeitangaben das 12-Stunden-Format verwendet wird.|`true` (für ein 12-Stunden-Format), `false` (für ein 24-Stunden-Format)||  
|`timeZone`|Gibt die Zeitzone an. Mindestens "UTC" wird immer unterstützt.|Ein Zeitzonenwert wie "UTC".|"UTC"|  
|`weekday`|Gibt die Formatierung für den Wochentag an.|"narrow", "short", "long".|nicht definiert|  
|`era`|Gibt die Formatierung für den Zeitraum an.|"narrow", "short", "long"|nicht definiert|  
|`year`|Gibt die Formatierung für das Jahr an.|"2-digit", "numeric"|nicht definiert oder "numeric"|  
|`month`|Gibt die Formatierung für den Monat an.|"2-digit", "numeric", "narrow", "short", "long"|nicht definiert oder "numeric"|  
|`day`|Gibt die Formatierung für den Tag an.|"2-digit", "numeric"|nicht definiert oder "numeric"|  
|`hour`|Gibt die Formatierung für die Stunde an.|"2-digit", "numeric"|nicht definiert|  
|`minute`|Gibt Formatierung für die Minute an.|"2-digit", "numeric"|nicht definiert|  
|`second`|Gibt die Formatierung für die Sekunde an.|"2-digit", "numeric"|nicht definiert|  
|`timeZoneName`|Gibt die Formatierung für die Zeitzone an. Diese Eigenschaft wird derzeit nicht unterstützt.|"short", "long".|Diese Eigenschaft wird derzeit nicht unterstützt.|  
  
 Der Standardwert für `weekday`, `era`, `year`, `month`, `day`, `hour`, `minute` und `second` lautet: `undefined`. Wenn Sie diese Eigenschaften nicht festlegen, wird die Formatierung "numeric" für `year`, `month` und `day` verwendet.  
  
 Jedes Gebietsschema muss mindestens die folgenden Formate unterstützen:  
  
-   Wochentag, Jahr, Monat, Tag, Stunde, Minute, Sekunde  
  
-   Wochentag, Jahr, Monat, Tag  
  
-   Jahr, Monat, Tag  
  
-   Jahr, Monat  
  
-   Monat, Tag  
  
-   Stunde, Minute, Sekunde  
  
-   Stunde, Minute  
  
## <a name="properties"></a>Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften des `DateTimeFormat`-Objekts aufgelistet.  
  
|||  
|-|-|  
|Eigenschaft|Beschreibung|  
|[Konstruktor](../../javascript/reference/constructor-property-intl-datetimeformat.md)|Gibt die Funktion an, die ein Formatierungsobjekt für Datum/Uhrzeit erstellt.|  
|[format](../../javascript/reference/format-property-intl-datetimeformat.md)|Gibt eine Funktion zurück, die mithilfe der Formatierungseinstellungen für Datum/Uhrzeit ein gebietsschemaspezifisches Datum formatiert.|  
|[Prototyp](../../javascript/reference/prototype-property-intl-datetimeformat.md)|Gibt einen Verweis auf den Prototyp für einen Datum-/Uhrzeit-Formatierer zurück.|  
  
## <a name="methods"></a>Methoden  
 In der folgenden Tabelle werden die Methoden des `DateTimeFormat`-Objekts aufgelistet.  
  
|||  
|-|-|  
|Methode|Beschreibung|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-datetimeformat.md)|Gibt ein Objekt zurück, das die Eigenschaften und die Werte des Datums-/Formatierungsobjekts enthält.|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird das Ergebnis der Übergabe eines Datumsobjekts an `DateTimeFormat` mit unterschiedlichen Gebietsschemas veranschaulicht.  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
if (console && console.log) {  
    console.log(new Intl.DateTimeFormat("en-US").format(date));  
    // Returns ‎2‎/‎1‎/‎2013  
    console.log(new Intl.DateTimeFormat("ja-JP").format(date));  
    // Returns ‎2013‎年‎2‎月‎1‎日  
    console.log(new Intl.DateTimeFormat("ar-SA", options).format(date));  
    // Returns ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
    console.log(new Intl.DateTimeFormat("hi-IN", options).format(date));  
    // Returns ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
}  
```  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein `DateTimeFormat`-Objekt erstellt, das den aktuellen Wochentag im Langformat mit dem Gebietsschema "Arabisch (Saudi-Arabien)", dem islamischen Kalender und dem lateinischen Zahlensystem angibt.  
  
```JavaScript  
var dtf = new Intl.DateTimeFormat(["ar-SA-u-ca-islamic-nu-latn"], {  
    weekday: "long",  
    year: "numeric",  
    day: "numeric",  
    month: "long"  
});   
  
If (console && console.log) {  
    console.log(dtf.format(new Date()));  
    // Returns ‏الجمعة‏, ‏19‏ ‏رمضان‏, ‏1434  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [ToLocaleString (Datum)](../../javascript/reference/tolocalestring-date.md)   
 [ToLocaleDateString-Methode (Datum)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)   
 [ToLocaleTimeString-Methode (Datum)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)   
 [Intl.Collator-Objekt](../../javascript/reference/intl-collator-object-javascript.md)   
 [Intl.NumberFormat-Objekt](../../javascript/reference/intl-numberformat-object-javascript.md)