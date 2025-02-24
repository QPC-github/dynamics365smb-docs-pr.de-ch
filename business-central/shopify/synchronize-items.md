---
title: Artikel und Inventar synchronisieren
description: Synchronisierungen von Artikeln zwischen Shopify und Business Central einrichten und ausführen
ms.date: 06/06/2023
ms.topic: article
ms.service: dynamics365-business-central
ms.search.form: '30116, 30117, 30126, 30127,'
author: AndreiPanko
ms.author: andreipa
ms.reviewer: bholtorf
---

# Artikel und Inventar synchronisieren

Die **Artikel** in [!INCLUDE[prod_short](../includes/prod_short.md)] entsprechen den *Produkten* in Shopify und umfassen physische Waren, digitale Downloads, Dienstleistungen und Geschenkkarten, die Sie verkaufen. Es gibt zwei Hauptgründe für die Synchronisierung von Artikeln:

1. Die Datenverwaltung läuft hauptsächlich in [!INCLUDE[prod_short](../includes/prod_short.md)] ab. Sie müssen alle oder einige Daten von dort dorthin nach Shopify exportieren und sichtbar machen. Sie können den Artikelnamen, die Beschreibung, das Bild, die Preise, die Verfügbarkeit, die Varianten, die Angaben zum Kreditor und den Barcode exportieren. Nach dem Export können Sie die Artikel überprüfen oder sofort sichtbar machen.
2. Bei einer Bestellung von Shopify importiert wird, sind die Informationen zu den Artikeln für die Weiterverarbeitung des Dokuments in [!INCLUDE[prod_short](../includes/prod_short.md)] unerlässlich.

Die vorhergehenden Szenarien sind immer aktiviert.

Ein drittes Szenario ist die Verwaltung von Daten in Shopify, importieren Sie diese Artikel jedoch in grossen Mengen in [!INCLUDE[prod_short](../includes/prod_short.md)]. Dieses Szenario kann für Datenmigrationsereignisse hilfreich sein, wenn Sie einen bestehenden Onlineshop mit einer neuen [!INCLUDE[prod_short](../includes/prod_short.md)]-Umgebung verbinden möchten.

## Artikelsynchronisierungen definieren

1. Wählen Sie das Suchsymbol ![Glühbirne, die die „Wie möchten Sie weiter verfahren“-Funktion öffnet](../media/ui-search/search_small.png "Wie möchten Sie weiter verfahren?") aus , und geben Sie **Shopify-Shop** ein. Öffnen Sie den Shop, für den Sie die Artikelsynchronisierung konfigurieren möchten.
2. Wählen Sie im Feld **Artikel synchronisieren** die erforderliche Option aus.

   Die Optionen werden in der folgenden Tabelle beschrieben.

|Option|Description|
|------|-----------|
|**"Leer"**| Der Import von Produkten erfolgt zusammen mit dem Import von Bestellungen. Produkte werden nach Shopify exportiert, wenn Benutzer die Aktion **Artikel hinzufügen** über die Seite **Shopify-Produkte** ausführt. Diese Option ist der Standardvorgang.|
|**Zu Shopify**| Wählen Sie diese Option aus, wenn Sie nach der ersten Synchronisierung, die durch die Aktion **Artikel hinzufügen** ausgelöst wurde, Produkte manuell mit der Aktion **Produkte synchronisieren** oder über eine Aufgabenwarteschlange für wiederkehrende Aktualisierungen aktualisieren möchten. Denken Sie daran, das Feld **Kann Shopify-Produkt aktualisiseren** zu aktivieren. Wenn es nicht aktiviert ist, entspricht es der Option **Leer** (Standardprozess). Weitere Informationen finden Sie im Abschnitt [Artikel nach Shopify exportieren](synchronize-items.md#export-items-to-shopify).|
|**Von Shopify**| Wählen Sie diese Option aus, wenn Sie planen, Produkte aus Shopify in grossen Mengen zu importieren, indem Sie entweder manuell die Aktion **Produkt synchronisieren** oder die Auftragswarteschlange für wiederkehrende Aktualisierungen verwenden. Weitere Informationen finden Sie im Abschnitt [Artikel aus Shopify importieren](synchronize-items.md#import-items-from-shopify).|

## Artiekl aus Shopify importieren

Zuerst importieren Sie Artikel aus Shopify in grossen Mengen oder zusammen mit dem Import von Bestellungen. Diese Artikel werden den Tabellen **Shopify-Produkt** und **Shopify-Variante** hinzugefügt. Ordnen Sie dann importierte Produkte und Varianten den Artikeln und Varianten in [!INCLUDE[prod_short](../includes/prod_short.md)] zu. Verwalten Sie den Prozess mit den folgenden Einstellungen:

|Feld|Beschreibung|
|------|-----------|
|**Unbekannte Artikel automatisch erstellen**|Wenn Shopify-Produkte und -Varianten in [!INCLUDE[prod_short](../includes/prod_short.md)] importiert werden, versucht die [!INCLUDE[prod_short](../includes/prod_short.md)]-Funktion immer, zuerst einen übereinstimmenden Datensatz in der Artikelliste zu finden. **SKU-Zuordnung** wirkt sich darauf aus, wie der Abgleich durchgeführt wird, und erstellt neue Artikel und/oder Artikelvarianten. Aktivieren Sie diese Option, wenn Sie einen neuen Artikel erstellen möchten oder kein übereinstimmender Datensatz vorhanden ist. Der neue Artikel wird mit importierten Daten und dem **Artikelvorlagencode** erstellt. Wenn diese Option nicht aktiviert ist, müssen Sie einen Artikel manuell erstellen und die Aktion **Produkt zuordnen** auf der Seite **Shopify Produkte** verwenden.|
|**Artikelvorlagencode**|Verwenden Sie dieses Feld zusammen mit dem Umschalter **Unbekannte Artikel automatisch erstellen**.<br>Wählen Sie die Vorlage aus, die für automatisch erstellte Elemente verwendet werden soll.|
|**SKU-Zuordnung**|Wählen Sie, wie Sie den aus Shopify importierten **SKU** Wert während der Zuordnung und Erstellung von Artikeln/Varianten verwenden möchten. Erfahren Sie mehr im Abschnitt [So wirken sich in Shopifydefinierte SKUs und Barcodes auf die Zuordnung und Erstellung von Artikeln und Varianten in Business Central aus](synchronize-items.md#effect-of-shopify-product-skus-and-barcodes-on-mapping-and-creating-items-and-variants-in-business-central).|
|**SKU-Feldtrennzeichen**|Verwenden Sie dieses Feld zusammen mit **SKU-Zuordnung**, das auf die Option **[Artikelnr. und Variantencode](synchronize-items.md#effect-of-shopify-product-skus-and-barcodes-on-mapping-and-creating-items-and-variants-in-business-central)** festgelegt ist.<br>Definieren Sie ein Trennzeichen, das zum Aufteilen der SKU verwendet werden soll.<br>Wenn Sie in Shopify die Variante mit SKU „1000/001“ erstellen, geben Sie „/“ in das Feld **SKU-Feldtrennzeichen** ein, um die Artikelnummer in [!INCLUDE[prod_short](../includes/prod_short.md)] als „1000“ und den Artikelvariantencode als „001“ zu erhalten.|
|**Variantenpräfix**|Wird zusammen mit **SKU-Zuordnung** verwendet, die entweder auf die Option **Variantencode** oder **Artikelnr. und Variantencode** als Fallback-Strategie festgelegt ist, wenn die SKU aus Shopify leer ist.<br>Wenn Sie die Artikelvariante automatisch in [!INCLUDE[prod_short](../includes/prod_short.md)] erstellen möchten, müssen Sie einen Wert in **Code** eingeben. Standardmässig wird der im SKU-Feld definierte Wert aus Shopify verwendet. Wenn die SKU jedoch leer ist, wird Code generiert, der mit dem definierten Variantenpräfix und „001“ beginnt.|
|**Shopify Kann Artikel aktualisieren**|Wählen Sie diese Option aus, wenn Sie Artikel und/oder Varianten automatisch aktualisieren möchten.|

### So wirken sich in SKU und Barcode definierte Shopify-Produkte auf die Zuordnung und Erstellung von Artikeln und Varianten in Business Central aus

Wenn Produkte von Shopify in die Tabellen **Shopify-Produkte** und **Shopify-Varianten** importiert werden, versucht [!INCLUDE[prod_short](../includes/prod_short.md)] vorhandene Datensätze zu finden.

In der folgenden Tabelle wird der Unterschied zwischen den Optionen im Feld **SKU-Zuordnung** beschrieben.

|Option|Auswirkung auf die Zuordnung|Auswirkung auf die Erstellung|
|------|-----------------|------------------|
|**"Leer"**|Das SKU-Feld wird in der Artikelzuordnungsroutine nicht verwendet.|Keine Auswirkung auf die Erstellung des Elements.<br>Diese Option verhindert die Erstellung von Varianten. Im Verkaufsauftrag wird nur der Hauptartikel verwendet. Eine Variante kann weiterhin manuell auf der Seite **Shopify-Produkt** zugeordnet werden.|
|**Artikelnr.**|Legen Sie fest, ob das SKU-Feld die Artikelnummer enthält|Keine Auswirkung auf die Erstellung eines Elements ohne Varianten. Bei einem Artikel mit Varianten wird jede Variante als separater Artikel erstellt.<br>Wenn Shopify ein Produkt mit zwei Varianten aufweist und deren Lagerhaltungsdaten lauten „1000“ und „2000“, erstellt das System in [!INCLUDE[prod_short](../includes/prod_short.md)] zwei Artikel mit den Nummern „1000“ und „2000“.|
|**Variantencode**|Das SKU-Feld wird in der Artikelzuordnungsroutine nicht verwendet.|Keine Auswirkung auf die Erstellung des Elements. Beim Erstellen einer Artikelvariante dient der Wert des SKU-Felds als Code. Wenn die SKU leer ist, wird ein Code über das Feld **Variantenpräfix** erstellt.|
|**Artikelnr. und Variantencode**|Wählen Sie diese Option aus, wenn das SKU-Feld eine Artikelnummer enthält und der Artikelvariantencode durch den im Feld **SKU-Feldtrennzeichen** definierten Wert getrennt ist.|Beim Erstellen eines Artikels wird der erste Teil des Werts des SKU-Felds als **Nr.** festgelegt. Wenn das SKU-Feld leer ist, wird eine Artikelnummer mit der Nummernserie generiert, die in **Artikelvorlagencode** oder **Artikelnummern** der Seite **Lagereinrichtung** definiert ist.<br>Beim Erstellen eines Artikels verwendet die Variantenfunktion den zweiten Teil des Werts des SKU-Felds als **Code**. Wenn das SKU-Feld leer ist, wird ein Code über das Feld **Variantenpräfix** erstellt.|
|**Kreditorenartikelnr.**|Legen Sie fest, ob das SKU-Feld die Kreditorartikelnummer enthält In diesem Fall wird **Kreditorenartikelnummer** nicht auf der Seite **Artikelkarte** verwendet; eher **Kreditorenartikelnummer** aus **Artikelliefernatenkatalog** wird verwendet. Wenn der gefundene Datensatz *Artikel/Lieferanten Katalog* einen Variantencode enthält, wird dieser Code zum Zuordnen der Shopify-Variante verwendet.|Wenn ein entsprechender Lieferant in [!INCLUDE[prod_short](../includes/prod_short.md)] existiert, wird der SKU-Wert als **Lieferanten-Artikel-Nr.** auf der Seite **Artikelkarte** und als **Artikelreferenz** des Typs *Lieferant* verwendet. <br>Verhindert die Erstellung von Varianten. Dies ist nützlich, wenn Sie nur den Hauptartikel nur im Verkaufsauftrag verwenden möchten. Sie können weiterhin eine Variante manuell über die Seite **Shopify-Produkt** zuordnen.|
|**Strichcode**|Legen Sie fest, ob das SKU-Feld einen Strichcode enthält. Es wird eine Suche unter **Artikelreferenzen** des Typs *Barcode* durchgeführt. Wenn der gefundene Artikelreferenzdatensatz einen Variantencode enthält, wird dieser Variantencode zum Zuordnen der Shopify-Variante verwendet.|Keine Auswirkung auf die Erstellung des Elements. <br>Verhindert die Erstellung von Varianten. Dies ist nützlich, wenn Sie nur den Hauptartikel nur im Verkaufsauftrag verwenden möchten. Sie können weiterhin eine Variante manuell über die Seite **Shopify-Produkt** zuordnen.|

In der folgenden Tabelle werden die Auswirkungen des Felds **Strichcode** beschrieben.

|Auswirkung auf die Zuordnung|Auswirkung auf die Erstellung|
|-----------------|------------------|
|Es wird eine Suche unter **Artikelreferenzen** vom Typ „Strichcode“ für den Wert durchgeführt, der im Feld **Strichcode** in Shopify definiert ist. Wenn der gefundene Artikelreferenzdatensatz einen Variantencode enthält, wird dieser Variantencode zum Zuordnen der Shopify-Variante verwendet.|Der Barcode wird als **Artikelreferenz** für den Artikel und die Artikelvariante gespeichert.|

> [!NOTE]  
> Sie können die Zuordnung für die ausgewählten Produkte/Varianten auslösen, indem Sie **Zuordnung von Produkten suchen** auswählen oder alle importierten nicht zugeordneten Produkte auslösen über **Zuordnung suchen** auswählen.

## Artikel nach Shopify exportieren

Wählen Sie die Elemente aus Ihrer Artikelliste aus, die nach Shopify exportiert werden. Verwenden Sie die Aktion **Artikel hinzufügen** auf der Seite **Shopify-Produkte**, um der Shopify-Produktliste Artikel hinzuzufügen. 

>[!IMPORTANT]
>Das Produkt wird nur dem Vertriebskanal **Onlineshop** hinzugefügt. Sie müssen Produkte über Vertriebskanäle wie Shopify POS von Shopify veröffentlichen.

Der Prozess des Artikelexports kann mit den folgenden Einstellungen verwaltet werden:

|Feld|Description|
|------|-----------|
|**Erweiterten Text für Artikel synchronisieren**|Wählen Sie dieses Feld aus, um den Zusatztext des Artikels zu synchronisieren. Da es dem Feld *Beschreibung* hinzugefügt wird, kann es HTML-Code enthalten. |
|**Artikelattribute synchronisieren**|Wählen Sie dieses Feld aus, um die Artikelattribute zu synchronisieren. Attribute werden als Tabelle formatiert und sind im Feld *Beschreibung* in Shopify enthalten.|
|**Marketingtext für Artikel synchronisieren**|Wählen Sie dieses Feld aus, um den erweiterten Marketingtext des Artikels zu synchronisieren. Obwohl Marketingtext eine Art Beschreibung ist, unterscheidet er sich vom Feld **Beschreibung** des Artikels. Das Feld **Beschreibung** wird normalerweise als prägnanter Anzeigename verwendet, um das Produkt schnell identifizieren zu können. Der Marketingtext hingegen ist ein umfassenderer und detailreicherer Schritt. Durch ihn sollen Marketing- und Werbeinhalten hinzugefügt werden. Dieser Text kann dann mit dem Artikel in Shopify veröffentlicht werden. Es gibt zwei Möglichkeiten, Marketingtext zu erstellen. Am einfachsten gelingt der Einstieg mit Copilot, das Ihnen KI-generierten Text vorschlägt oder neu zu beginnen.|
|**Sprachcode**|Wählen Sie dieses Feld aus, um die übersetzten Versionen für Titel, Attribute und Zusatztext zu verwenden.|
|**SKU-Zuordnung**|Wählen Sie, wie Sie das SKU Feld in Shopify ausfüllen möchten. Die folgenden Optionen werden unterstützt:<br> - **Artikelnr.** zur Verwendung der Artikelnr. für Produkte und Varianten.<br> - **Artikelnummer + Variantencode**, um eine SKU durch Verkettung der Werte zweier Felder zu erstellen. Für Artikel ohne Varianten wird nur die Artikelnummer verwendet.<br>- **Artikellieferantennr.** zur Verwendung der Artikellieferantennummer, die auf der *Artikelkarte* für Produkte und Varianten definiert ist.<br> - **Barcode**  zum Verwenden des Barcodetyps der **Artikelreferenz**. Diese Option berücksichtigt Varianten.|
|**SKU-Feldtrennzeichen**|Definieren Sie ein Trennzeichen für die Option **Artikelnr. und Variantencode**.|
|**Verfolgter Lagerbestand**| Legen Sie fest, wie das Feld **Lagerbestand verfolgen** für Produkte ausgefüllt werden soll, die nach Shopify exportiert werden. Sie können Verfügbarkeitsinformationen von [!INCLUDE[prod_short](../includes/prod_short.md)] für Produkte in Shopify mit aktivierter Lagerbestandsverfolgung aktualisieren. Erfahren Sie mehr im Abschnitt [Bestand](synchronize-items.md#sync-inventory-to-shopify).|
|**Standardrichtlinie für Lagerbestand**|Wählen Sie *Verweigern* aus, um einen negativen Lagerbestand der Shopify-Seite zu vermeiden.|
|**Kann Shopify-Produkte aktualisieren**|Definieren Sie dieses Feld, wenn [!INCLUDE[prod_short](../includes/prod_short.md)] Artikel nur erstellen oder auch aktualisieren kann. Wählen Sie diese Option aus, wenn Sie nach der ersten Synchronisierung, die durch die Aktion **Artikel hinzufügen** ausgelöst wurde, Produkte manuell mit der Aktion **Produkte synchronisieren** oder über eine Aufgabenwarteschlange für wiederkehrende Aktualisierungen aktualisieren möchten. Denken Sie daran, **Mit Shopify** im Feld **Artikelsynchronisierung** auszuwählen.|

### Übersicht über Feldzuordnungen

|Shopify|Quelle beim Export aus [!INCLUDE[prod_short](../includes/prod_short.md)]|Ziel beim Importier in [!INCLUDE[prod_short](../includes/prod_short.md)]|
|------|-----------------|-----------------|
|Status     |Entsprechend des Feldes **Status für erstellte Produkte** auf der **Shopify-Shop-Karte**. Weitere Informationen finden Sie im Abschnitt [Ad-Hoc-Aktualisierungen von Shopify-Produkten](synchronize-items.md#ad-hoc-updates-of-shopify-products).|Wird nicht verwendet.|
|Titel | **Beschreibung**. Wenn der Sprachcode definiert ist und eine entsprechende Artikelübersetzung existiert, wird die Artikelübersetzung anstelle der Beschreibung verwendet.|**Beschreibung**|
|Description|Kombiniert erweiterte Texte, Marketingtexte und Attribute, wenn Sie die entsprechenden Umschalter auf der Shopify Shop-Karte aktivieren. Beachtet den Sprachcode.|Wird nicht verwendet.|
|SEO-Seitentitel|Fester Wert: leer. Weitere Informationen finden Sie im Abschnitt [Ad-Hoc-Aktualisierungen von Shopify-Produkten](synchronize-items.md#ad-hoc-updates-of-shopify-products).|Wird nicht verwendet.|
|SEO-Metabeschreibung|Fester Wert: leer. Weitere Informationen finden Sie im Abschnitt [Ad-Hoc-Aktualisierungen von Shopify-Produkten](synchronize-items.md#ad-hoc-updates-of-shopify-products).|Wird nicht verwendet.|
|Medien|**Bild**. Erfahren Sie mehr im Abschnitt [Artikelbilder synchronisieren](synchronize-items.md#sync-item-images)|**Bild**|
|Preis|Die Berechnung des Endkundenpreises enthält den Artikeleinheitspreis, die Kundenpreisgruppe, die Kundenskontogruppe und den Währungscode. Erfahren Sie mehr im Abschnitt [Preise synchronisieren](synchronize-items.md#sync-prices-with-shopify)|**Einheitspreis**. Der Preis wird nur für neu erstellte Artikel importiert, bei späteren Synchronisierungen jedoch nicht aktualisiert.|
|Preisvergleich|Die Berechnung des Preises ohne Skonto.|Wird nicht verwendet.|
|Kosten pro Artikel|**Einstandspreis**|**Einstandspreis**. Der Einstandspreis wird nur für neu erstellte Artikel importiert und bei späteren Synchronisierungen nicht aktualisiert.|
|SKU|Weitere Informationen zu SKUs finden Sie unter **SKU-Zuordnung** im Abschnitt [Artikel nach Shopify exportieren](synchronize-items.md#export-items-to-shopify).|Weitere Informationen zu SKUs finden Sie unter [So wirken sich in Shopify definierte SKUs und Barcodes auf die Zuordnung und Erstellung von Artikeln und Varianten in Business Central aus](synchronize-items.md#effect-of-shopify-product-skus-and-barcodes-on-mapping-and-creating-items-and-variants-in-business-central).|
|Strichcode|**Artikelreferenzen** vom Typ „Strickcode“|**Artikelreferenzen** vom Typ „Strickcode“|
|Menge verfolgen|Entsprechend dem Feld **Verfolgter Lagerbestand** auf der Seite **Shopify-Shop-Karte**. Erfahren Sie mehr im Abschnitt [Bestand](synchronize-items.md#sync-inventory-to-shopify). Wird nur verwendet, wenn Sie ein Produkt zum ersten Mal exportieren.|Wird nicht verwendet.|
|Weiterverkaufen, wenn ein Artikel nicht mehr auf Lager ist|Entsprechend der Option **Standardrichtlinie für Lagerbestand** auf der **Shopify-Shop-Karte**. Wird nur verwendet, wenn Sie ein Produkt zum ersten Mal exportieren.|Wird nicht verwendet.|
|Typ|**Beschreibung** von **Artikelkategoriencode**. Wenn der Typ nicht in Shopify angegeben ist, wird er als benutzerdefinierter Typ hinzugefügt.|**Artikelkategoriencode**. Zuordnung nach Beschreibung.|
|Kreditor|**Name** des Kreditors aus **Kreditorennr.**|**Kreditorennr.**-Zuordnung nach Name.|
|Gewichtung|**Bruttogewicht**.|Wird nicht verwendet.|
|Steuerpflichtig|Fester Wert: aktiviert.|Wird nicht verwendet.|
|Steuercodes|**Salestax Gruppencode**. Nur für die Umsatzsteuer relevant. Erfahren Sie mehr unter [Salestaxes festlegen](setup-taxes.md).|Wird nicht verwendet.|

### Tags

Überprüfen Sie die importierten Tags in der Infobox **Tags** auf der Seite **Shopify-Produkt**. Wählen Sie zum Bearbeiten von Tags die Aktion **Tags** auf derselben Seite aus.
Wenn die Option **Zu Shopify** im Feld **Artikel synchronisieren** ausgewählt ist, werden zugewiesene Tags bei der nächsten Synchronisation nach Shopify exportiert.

## Artikelsynchronisierung ausführen

Die vollständige oder teilweise Synchronisierung von Artikeln kann auf viele verschiedene Arten durchgeführt werden.

### Anfängliche Synchronisierung von Artikeln aus Business Central mit Shopify

1. Wechseln Sie zum Suchsymbol ![Glühbirne, die die „Wie möchten Sie weiter verfahren“-Funktion öffnet](../media/ui-search/search_small.png "Wie möchten Sie weiter verfahren?") Symbol, geben Sie **Shopify Produkte** ein und wählen Sie den entsprechenden Link.
2. Wählen Sie die Aktion **Artikel hinzufügen** aus.
3. Geben Sie im Feld **Shop-Code** den ersten Code ein. Wenn Sie das Fenster **Shopify-Produkt** über die Seite **Shop-Karte** aufrufen, wird der Shop-Code automatisch ausgefüllt.
4. Wenn Sie die Bild- und Lagersynchronisierung konfiguriert haben, können Sie sie in denselben Prozess einbeziehen. Sie in denselben Prozess einzubeziehen ist praktisch für Demo-Szenarien oder beim Umgang mit kleineren Datenmengen. 
5. Definieren Sie nach Bedarf Filter für Artikel. Sie können beispielsweise nach Artikelnummer oder nach Artikelkategoriencode filtern.
6. Wählen Sie **OK** aus.

Die resultierenden Artikel werden automatisch Shopify mit Preisen erstellt. Abhängig von Ihrer Auswahl können Bilder und Lagerebenen enthalten sein. Der Vorgang kann einige Zeit in Anspruch nehmen, wenn eine grosse Anzahl von Artikeln hinzugefügt wird.

### Produkte aus Shopify mit Business Central synchronisieren

1. Wechseln Sie zum Suchsymbol ![Glühbirne, die die „Wie möchten Sie weiter verfahren“-Funktion öffnet](../media/ui-search/search_small.png "Wie möchten Sie weiter verfahren?") , geben Sie **Shopify-Shop** ein, und wählen Sie den entsprechenden Link aus.
2. Wählen Sie den Shop, für den Sie Artikel synchronisieren möchten, um die Seite **Shopify Shop Card** zu öffnen.
3. Wählen Sie die Aktion **Produkte synchronisieren** aus.

Verwenden Sie alternativ die Aktion **Produkte synchronisieren** auf der Seite **Shopify Produkte** oder suchen Sie nach dem Batchauftrag **Produkte synchronisieren**.

Sie können die durchzuführende Aufgabe so planen, dass sie automatisiert ausgeführt werden. Erfahren Sie mehr unter [Planen Sie wiederkehrende Aufgaben](background.md#to-schedule-recurring-tasks).

### Ad-Hoc-Aktualisierungen von Shopify-Produkten

Beim Aktualisieren der Datensätze in der Tabelle **Shopify-Produkt** werden die folgenden Änderungen mit Shopify synchronisiert.

Aktualisieren:

* **Status** – Sie können zwischen „Aktiv“, „Archiviert“ oder „Entwurf“ auswählen.
* **SEO-Titel**
* **SEO-Beschreibung**

Löschung:

Basierend auf dem Wert in **Aktion für entfernte Produkte** auf der Seite **Shopify-Shop-Karte**, wird das Produkt in Shopify aktualisiert, wenn der Datensatz von der Seite **Shopify-Produkte** gelöscht wird.

* **Leer** – Es wird keine Aktion ausfgeführt. Der Benutzer muss die erforderliche Aktion ggf. über die **Shopify-Verwaltung** ausführen.
* **Status auf Entwurf** – Der Status des Produkts in Shopify ist auf *Entwurf* festgelegt.
* **Status auf Archiviert** – Das Produkt ist in Shopify archiviert.

## Artikelbilder synchronisieren

Die Synchronisierung von Bildern kann für synchronisierte Artikel konfiguriert werden. Folgende Optionen stehen zur Verfügung:

* **Deaktiviert** - Die Bildsynchronisierung ist deaktiviert.
* **Zu Shopify** – Bilder von Artikeln werden nach Shopify exportiert.
* **Von Shopify** – Bilder von Shopify werden nach [!INCLUDE[prod_short](../includes/prod_short.md)] importiert.

Die Bildsynchronisation kann auf zwei Arten initialisiert werden, die nachfolgend beschrieben werden.

### Produktbilder über die Seite „Shopify-Shop“ synchronisieren

1. Wechseln Sie zum Suchsymbol ![Glühbirne, die die „Wie möchten Sie weiter verfahren“-Funktion öffnet](../media/ui-search/search_small.png "Tell Me-Funktion") Symbol, geben Sie **Shopify Shops** ein, und wählen Sie den entsprechenden Link.
2. Wählen Sie den Shop, für den Sie Bilder synchronisieren möchten, um die Seite **Shopify Shop Card** zu öffnen.
3. Wählen Sie die Aktion **Produktbilder synchronisieren** aus.

### Produktbilder über die Seite „Shopify-Produkte“ synchronisieren

1. Wechseln Sie zum Suchsymbol ![Glühbirne, die die „Wie möchten Sie weiter verfahren“-Funktion öffnet](../media/ui-search/search_small.png "Tell Me-Funktion") Symbol, geben Sie **Shopify Produkte** ein und wählen Sie den entsprechenden Link.
2. Wählen Sie die Aktion **Produktbilder synchronisieren** aus.

### Anmerkungen zur Bildsynchronisation

* Beim Exportieren von Bildern von [!INCLUDE[prod_short](../includes/prod_short.md)] nach Shopify werden die neuen Bilder Shopify hinzugefügt und alte Bilder bleiben intakt. Wenn ein Bild in [!INCLUDE[prod_short](../includes/prod_short.md)] aktualisiert wird, müssen Sie die alten Bilder im **Shopify Admin** löschen.
* Bilder, die nach Shopify exportiert werden und den von Shopify definierten Anforderungen nicht entsprechen, werden nicht importiert. Erfahren Sie mehr über [Produktmedientypen auf help.shopify.com](https://help.shopify.com/en/manual/products/product-media/product-media-types#images).

## Preise mit Shopify synchronisieren

Der Prozess des Exportpreises kann mit den folgenden Einstellungen verwaltet werden:

|Feld|Description|
|------|-----------|
|**Debitorenpreisgruppe**|Bestimmen Sie den Preis für einen Artikel in Shopify. Der Verkaufspreis dieser Debitorenpreisgruppe wird verwendet. Wenn keine Gruppe eingegeben wird, wird der Preis der Artikelkarte verwendet.|
|**Debitorenrabattgruppe**|Bestimmen Sie den Skonto, der zur Berechnung des Preises eines Artikels in Shopify verwendet werden soll. Ermässigte Preise sind im Feld **Preis** hinterlegt und der volle Preis wird im Feld **Vergleichen mit Preis** gespeichert.|
|**Zeilenrabatt zulassen**|Gibt an, ob Zeilenskonto zulässig ist, während die Preise für Shopify berechnet werden. Diese Einstellung gilt nur für Preise auf dem Artikel. Preise für die Kundenpreisgruppe haben eigene Umschaltzeilen.|
|**Preise inkl. MWST**|Gibt an, ob Preisberechnungen für Shopify Mehrwertsteuer enthalten. Erfahren Sie mehr unter [Salestaxes festlegen](setup-taxes.md).|
|**MWST-Geschäftsbuchungsgrp.**|Gibt an, welche MWST-Geschäftsbuchungsgruppe verwendet wird, um die Preise in Shopify zu berechnen Dies sollte die Gruppe sein, die Sie für inländische Kunden verwenden. Erfahren Sie mehr unter [Salestaxes festlegen](setup-taxes.md).|
|**Währungscode**|Geben Sie einen Währungscode nur ein, wenn Ihr Online-Shop eine andere Währung als die Landeswährung (LCY) verwendet. Für die angegebene Währung müssen Wechselkurse konfiguriert sein. Wenn Ihr Onlineshop dieselbe Währung verwendet wie [!INCLUDEprod_short] verwendet, lassen Sie das Feld leer.|

Preise können für synchronisierte Artikel auf die beiden, unten beschriebenen Arten exportiert werden.

### Preise über die Seite „Shopify-Produkte“ synchronisieren

1. Wechseln Sie zum Suchsymbol ![Glühbirne, die die „Wie möchten Sie weiter verfahren“-Funktion öffnet](../media/ui-search/search_small.png "Tell Me-Funktion"). Symbol, geben Sie **Shopify Produkte** ein und wählen Sie den entsprechenden Link.
2. Wählen Sie die Aktion **Preise mit Shopify synchronisieren** aus.

### Anmerkungen zur Preisberechnung

* Bei der Preisermittlung verwendet [!INCLUDE[prod_short](../includes/prod_short.md)] die Logik des “niedrigsten Preises“. Die Niedrigstpreislogik ignoriert jedoch den auf der Artikelkarte definierten Einzelpreis, wenn ein Preis in der Preisgruppe definiert ist. Dies gilt auch dann, wenn der Stückpreis vom Artikelkartenpreis niedriger ist.
* Um Preise zu berechnen, erstellt der Konnektor eine temporäre Verkaufsofferte für den Artikel mit einer Menge von 1 und verwendet die standardmässige Preisberechnungslogik. Es werden nur Preise und Skonti verwendet, die für Menge 1 gelten. Sie können keine unterschiedlichen Preise oder Skonti basierend auf der Menge exportieren.

## Lagerbestand mit Shopify synchronisieren

Die Synchronisierung des Lagerbestands kann für bereits synchronisierte Artikel konfiguriert werden. Dazu müssen zwei Bedingungen erfüllt sein:

1. Die Tracking von Lagerbeständen muss für ein Produkt in Shopify aktiviert werden. Erwägen Sie beim Exportieren von Artikeln nach Shopify die Aktivierung von **Verfolgter Lagerbestand** auf der **Shopify-Shop**-Karte. Weitere Informationen finden Sie im Abschnitt [Artikel nach Shopify exportieren](synchronize-items.md#export-items-to-shopify).
2. Die Synchronisierung des Lagerbestands muss für **Shopify-Standorte** aktiviert sein.

### So aktivieren Sie die Synchronisierung des Lagerbestands

1. Wechseln Sie zum Suchsymbol ![Glühbirne, die die „Wie möchten Sie weiter verfahren“-Funktion öffnet](../media/ui-search/search_small.png "Tell Me-Funktion") , geben Sie **Shopify-Shop** ein, und wählen Sie den entsprechenden Link aus.
2. Wählen Sie den Shop aus, für den Sie den Lagerbestand synchronisieren möchten, um die Seite **Shopify-Shop-Karte** zu öffnen.
3. Wählen Sie die Aktion **Standorte** aus, um **Shopify-Shop-Standorte** zu öffnen.
4. Wählen Sie die Aktion **Shopify Standorte abrufen**, um alle in Shopify definierten Standorte zu importieren. Sie befinden sich in den Einstellungen für [**Standorte**](https://www.shopify.com/admin/settings/locations) in Ihrer **Shopify-Verwaltung**.
5. Fügen Sie im Feld **Standortfilter** Standorte hinzu, wenn Sie nur den Lagerbestand bestimmter Standorte einbeziehen möchten. Sie können beispielsweise *OST|WEST* eingeben, sodass nur Lagerbestände dieser beiden Standorte für den Verkauf über den Onlineshop verfügbar sind.
6. Wählen Sie die Bestandsberechnungsmethode aus, die für die ausgewählten Shopify Standorte verwendet werden soll.

Die Synchronisierung des Lagerbestands auf zwei unten beschriebene Arten initialisieren.

### Lagerbestand über die Seite „Shopify-Shop“ synchronisieren

1. Wechseln Sie zum Suchsymbol ![Glühbirne, die die „Wie möchten Sie weiter verfahren“-Funktion öffnet](../media/ui-search/search_small.png "Tell Me-Funktion") Symbol, geben Sie **Shopify Shops** ein, und wählen Sie den entsprechenden Link.
2. Wählen Sie den Shop aus, für den Sie den Lagerbestand synchronisieren möchten, um die Seite **Shopify-Shop-Karte** zu öffnen.
3. Wählen Sie die Aktion **Lagerbestand synchronisieren** aus.

### Lagerbestand über die Seite „Shopify-Produkte“ synchronisieren

1. Wechseln Sie zum Suchsymbol ![Glühbirne, die die „Wie möchten Sie weiter verfahren“-Funktion öffnet](../media/ui-search/search_small.png "Tell Me-Funktion") Symbol, geben Sie **Shopify Produkte** ein und wählen Sie den entsprechenden Link.
2. Wählen Sie die Aktion **Lagerbestand synchronisieren** aus.

### Anmerkungen zum Lagerbestand

* Die Standard-Bestandsberechnungsmethode ist **Prognostizierter verfügbarer Saldo zum Datum**. Mit der Erweiterbarkeit können Sie weitere Optionen hinzufügen. Weitere Informationen zur Erweiterbarkeit finden Sie unter [Beispiele](https://github.com/microsoft/ALAppExtensions/blob/main/Apps/W1/Shopify/extensibility_examples.md). 
* Sie können die von Shopify empfangenen Bestandsinformationen auf der Seite **Infobox „Shopify-Bestand“** überprüfen. In dieser Infobox erhalten Sie einen Überblick über den Shopify-Bestand und den zuletzt berechneten Bestand in [!INCLUDE[prod_short](../includes/prod_short.md)]. Pro Standort ist ein Datensatz verfügbar.
* Wenn die Bestandsinformationen in Shopify sich vom **Verfügbarkeitssaldo** in [!INCLUDE[prod_short](../includes/prod_short.md)] unterscheiden, wird der Bestand in Shopify aktualisiert.
* Wenn Sie einen neuen Standort hinzufügen in Shopify, müssen Sie auch Inventardatensätze dafür hinzufügen. Shopify tut dies nicht automatisch für vorhandene Produkte und Varianten, und der Konnektor synchronisiert nicht die Lagerbestände für solche Artikel am neuen Standort. Weitere Informationen finden Sie unter [Inventar zu Standorten zuweisen](https://help.shopify.com/manual/locations/assigning-inventory-to-locations).

#### Beispiel für die Berechnung des hochgerechneten verfügbaren Saldos

Es sind 10 Stück von Artikel A verfügbar und zwei ausstehende Verkaufsaufträge. –Einen für Montag mit der Menge *Eins* und einen für Donnerstag mit der Menge *Zwei*. Je nachdem, wann Sie den Lagerbestand synchronisieren, aktualisiert das System den Lagerbestand Shopify mit unterschiedlichen Mengen:

|Wenn die Bestandssynchronisierung ausgeführt wird|Wert zur Aktualisierung des Lagerbestands|Kommentar|
|------|-----------------|-----------------|
|Dienstag|9|Bestand 10 minus Kundenauftrag, der am Montag versendet werden soll|
|Freitag|7|Bestand 10 minus beide Verkaufsaufträge|

## Siehe auch 

[Erste Schritte mit dem Konnektor für Shopify](get-started.md)  
