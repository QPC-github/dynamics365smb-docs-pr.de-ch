---
title: Crossdock für Artikel
description: 'Erfahren Sie, wie Sie Artikel empfangen und versenden, ohne sie einzulagern.'
author: brentholtorf
ms.author: bholtorf
ms.reviewer: andreipa
ms.topic: conceptual
ms.date: 03/08/2023
ms.custom: bap-template
ms.search.form: '15, 5703, 7302, 7332, 5768'
---
# <a name="cross-dock-items" />Crossdock für Artikel

Cross-Docking-Artikel sind Artikel, die Sie erhalten und versenden, ohne sie einzulagern. Die Einlagerungs- und Kommissionierungsprozesse erfordern eine begrenzte Handhabung von Artikeln. Sie können Artikel für den Warenausgang als auch für Fertigungsaufträge zuordnen.

## <a name="cross-dock-bins-and-zones" />Crossdocklagerplätze und-zonen

Wenn Sie Lagerplätze verwenden, richten Sie mindestens einen Crossdocklagerplatz ein und geben dann den Lagerplatz im Feld **Cross-Docking-Lagerplatzcode** an Ihren Lagerorten an. Wenn Sie die gesteuerte Einlagerung und Kommissionierung verwenden, richten Sie eine Crossdockzone ein.

Wenn Sie einen Warenausgang vorbereiten oder Artikel für die Produktion kommissionieren und Sie Lagerplätze verwenden, kommissioniert die Anwendung automatisch die Artikel aus einem Crossdocklagerplatz, bevor sie andere Lagerplätze berücksichtigt. Sie müssen im Crossdockbereich nachsehen, um festzustellen, ob die Artikel, die Sie benötigen, verfügbar sind, bevor Sie die Artikel aus ihrem normalen Lagerbereich holen.  

Wenn Sie Crossdockmengen berechnet haben, werden Einlagerungszeilen für den Crossdocklagerplatz für Crossdockberechnungen erzeugt, wenn Sie den Wareneingang buchen. Andere Einlagerungszeilen werden wie üblich erzeugt.  

## <a name="cross-dock-select-lines-for-a-receipt" />Crossdockauswahlpositionen für einen Eingang

Wenn Sie die zugeordneten Artikel sofort buchen möchten, um sie für die Kommissionierung verfügbar zu machen, müssen Sie ebenfalls eine Einlagerung für die anderen Artikel aus der Wareneingangszeile, nämlich die, die eingelagert werden müssen, erfassen. Wenn Crossdock nur für einige der Artikel der Wareneingangszeile ausgefüht wird, müssen Sie sich daher bemühen, die anderen Artikel so schnell wie möglich einzulagern. Alternativ dazu kann Ihre Lagerpolitik so aussehen, dass Sie – wenn möglich – für ganze Wareneingangszeilen Crossdockings durchführen möchten.

Löschen Sie in der Einlagerungsanweisung die Entnahme- und Kommissionierungsanweisungszeilen für jede Wareneingangszeile für die einzulagernden Artikel. Sie können die Anweisungszeilen später als Einlagerungszeilen aus dem Einlagerungsarbeitsblatt oder dem gebuchten Wareneingang neu erzeugen. Nachdem Sie die Anweisungszeilen gelöscht haben, können Sie die Zeilen für Crossdockartikel einlagern und registrieren.  

## <a name="about-the-put-away-worksheet-page" />Infos zur Einlagerungsarbeitsblattseite

Wenn Sie den Schalter **Einlagerungsarbeitsblatt verwenden** auf der Seite **Lagerortkarte** aktivieren und den Wareneingang mit berechneten Zuordnungen gebucht haben, werden alle Wareneingangszeilen im Arbeitsblatt verfügbar. Die Informationen zum Crossdock sind verloren und können nicht wiederhergestellt werden. Um also die Crossdockfunktionalität zu nutzen, sollten Sie Zeilen in das Einlagerungsarbeitsblatt übertragen, indem Sie Einlagerungsanweisungen löschen, anstatt die automatische Übertragungsfunktion im Feld **Einlagerungsarbeitsblatt verwenden** zu nutzen.  

Wenn Sie den Wareneingang buchen, und der Schalter **Einlagerungsarbeitsblatt verwenden** deaktiviert ist, werden die Cross-Docking-Artikel zu einzelnen Zeilen in der Einlagerungsanweisung. Das Feld **Cross-Dock-Informationen** auf jeder Einlagerungsposition zeigt an, ob die Zeile Folgendes enthält:

* Crossdockartikel.
* Alle Artikel einer Eingangs müssen gelagert werden.
* Einige Artikel aus einem Wareneingang müssen gelagert werden, und andere sollen Cross-Docking sein.

[!INCLUDE [prod_short](includes/prod_short.md)] führt keine separaten Aufzeichnungen für Cross-Docking-Artikel. Es registriert sie als gewöhnliche Einlagerungsanweisungen.  

## <a name="to-set-up-the-warehouse-for-cross-docking" />So richten Sie die Logistik für Crossdockings ein:

1. Wenn Sie Lagerplätze verwenden, richten Sie mindestens einen Crossdocklagerplatz ein. Wenn Sie die gesteuerte Einlagerung und Kommissionierung verwenden, richten Sie eine Crossdockzone ein.  

    Bei einem Crossdocklagerplatz ist das Feld **Crossdocklagerplatz** ausgewählt, und es müssen die Lagerplatzarten **Wareneingang** und **Kommissionierung** ausgewählt sein. Weitere Informationen zu Behältern finden Sie unter [Behälter erstellen](warehouse-how-to-create-individual-bins.md) und [Ablagetypen einrichten](warehouse-how-to-set-up-bin-types.md).  

    Wenn Sie Zonen verwenden, erstellen Sie eine Zone für Ihre Crossdocklagerplätze, und wählen Sie das Feld **Crossdocklagerplatzzone** aus. Weitere Informationen zum Einrichten von Zonen finden Sie unter [Lagerorte mithilfe von Behältern einrichten](warehouse-how-to-set-up-locations-to-use-bins.md).  

2. Wählen Sie die ![Glühbirne, die die „Wie möchten Sie weiter verfahren“-Funktion öffnet.](media/ui-search/search_small.png "Wie möchten Sie weiter verfahren?") Symbol. Geben Sie **Lagerort** ein und wählen Sie dann den zugehörigen Link.  
3. Öffnen Sie die Seite **Lagerort**, und wählen Sie den Lagerort aus, den Sie für das Lager bezüglich Cross-Dockingen einrichten möchten, und wählen Sie die Aktion **Bearbeiten** aus.  
4. Aktivieren Sie im Inforegister **Lager** den Schalter **Crossdock verwenden**, und tragen Sie im Feld **Crossd.-Fälligkeitsdatum ber.** die Zeit für die Suche nach Crossdockmöglichkeiten ein.

    Die Option **Crossdocking verwenden** ist nur verfügbar, wenn die Felder **Wareneingang erforderlich**, **Warenausgang erforderlich**, **Kommissionierung erforderlich** und **Einlagerung erforderlich** ausgewählt sind.  

5. Wenn Sie Lagerplätze verwenden, tragen Sie im Inforegister **Lagerplätze** in das Feld **Crossdocklagerplatzcode** den Code des Lagerplatzes ein, der als Vorgabelagerplatz für Crossdocking verwendet werden soll.  
6. Wählen Sie die ![Glühbirne, die die „Wie möchten Sie weiter verfahren“-Funktion öffnet.](media/ui-search/search_small.png "Wie möchten Sie weiter verfahren?") Symbol. Geben Sie **Lagerhaltungsdaten Einheit** ein und wählen Sie den zugehörigen Link.  
7. Für jeden Artikel oder alle Lagerhaltungsdaten, die Sie zum Crossdocking verwenden möchten, wählen Sie den Artikel aus, und wählen Sie die **Bearbeiten** Aktion aus.
8. Auf der Seite **Lagerhaltungsdatenkarte** wählen Sie das Kontrollkästchen **Cross-Docking verwenden** aus.  

> [!NOTE]  
>  Crossdock ist nur möglich, wenn Ihr Lagerort so eingerichtet wurde, dass die Bearbeitung des Wareneingangs und der Einlagerung erforderlich ist.  

## <a name="to-cross-dock-items-without-viewing-the-opportunities" />So ordnen Sie Artikel zu, ohne sich die Möglichkeiten anzeigen zu lassen:

1. Wählen Sie die ![Glühbirne, die die „Wie möchten Sie weiter verfahren“-Funktion öffnet.](media/ui-search/search_small.png "Tell me-Funktion") Symbol. Geben Sie **Wareneingänge** ein, und wählen Sie dann den entsprechenden Link.  
2. Erstellen Sie Lagerbelege für einen Artikel, der angekommen ist und möglicherweise in Zuordnungen einbezogen werden kann. Weitere Informationen zu Eingängen finden Sie unter [Artikeleinkang](warehouse-how-receive-items.md).  
3. Füllen Sie das Feld **Zu liefernde Menge** aus, und wählen Sie dann die Aktion **Crossdocking berechnen** aus.  

    Ausgehende Herkunftsbelege, die die Artikel benötigen und die das Lager innerhalb der Datumsformelperiode verlassen sollen, werden identifiziert. [!INCLUDE[prod_short](includes/prod_short.md)] berechnet Mengen, damit Sie soviel wie möglich zuordnen und auf diese Art vermeiden können, Artikel einzulagern, ohne zu viele Artikel im Crossdockbereich anzusammeln. Der Wert im Feld **Menge für Crossdock** ist die Summe aller ausgehenden Zeilen für den Artikel in der Vorausschauperiode abzüglich der Menge der Artikel, die bereits in den Crossdockbereich eingelagert wurden. Oder es ist der Wert im Feld **Zu liefernde Menge** in der Lieferzeile, je nachdem, welcher geringer ist. Sie können nicht mehr zuordnen, als Sie erhalten haben.  

4. Wenn Sie die Menge wie vorgeschlagen zuordnen möchten, buchen Sie den Wareneingang. Sie können sich auch entscheiden, die zuzuordnende Menge auf einen höheren oder niedrigeren Wert zu setzen, und dann den Wareneingang zu buchen.  

    Die zuzuordnenden Mengen erscheinen jetzt als Zeilen in der Einlagerungsanweisung, vorausgesetzt, das Feld **Einlagerungsarbeitsblatt verwenden** ist deaktiviert. Die nicht zugeordneten Mengen werden auch Zeilen in der Einlagerungsanweisung.  

    Wenn Sie Lagerplätze verwenden, wurden die zugeordneten Artikel dem Vorgabe-Crossdocklagerplatz zugeordnet, der auf der Artikelkarte festgelegt wurde.  

5. Löschen Sie die Zeilen **Entnahme** und **Einlagerung** für Artikel, die Sie nicht zuordnen möchten.  
6. Drucken Sie die Einlagerungsanweisungen für die übrigen Zeilen und lagern Sie die Mengen des Wareneingangs, die eingelagert werden sollen, in die jeweiligen Lagerplätze oder in einen geeigneten Bereich im Lager ein. Lagern Sie die Crossdockartikel in den Bereich oder Lagerplatz ein, der nach der Lagerpolitik für ihn vorgesehen ist. Es ist auch möglich, dass die Lagerrichtlinien vorsehen, dass Sie die Artikel einfach im Wareneingangsbereich lassen.  
7. Wenn Sie zugeordnete Artikel als eingelagert und zum Kommissionieren registrieren möchten, wählen Sie die Aktion **Registrieren** aus.  

## <a name="to-cross-dock-items-after-viewing-the-opportunities" />So ordnen Sie Artikel zu, nachdem Sie die Verkaufschancen angezeigt haben:

1. Wählen Sie die ![Glühbirne, die die „Wie möchten Sie weiter verfahren“-Funktion öffnet.](media/ui-search/search_small.png "Tell Me-Funktion") Symbol. Geben Sie **Wareneingänge** ein, und wählen Sie dann den entsprechenden Link.  
2. Erstellen Sie Lagerbelege für einen Artikel, der angekommen ist und möglicherweise in Zuordnungen einbezogen werden kann.  

    Sie können sich die Herkunftsbelegzeilen ansehen, die den Artikel anfordern, bevor Sie den Wareneingang buchen.  
3. Wählen Sie die Aktion **Crossdocking berechnen** aus.  

   Auf der Seite **Crossdockmöglichkeiten** können Sie die wichtigsten Details zu den Zeilen sehen, die den Artikel benötigen, wie z. B. die Belegart, die erforderliche Menge und das Fälligkeitsdatum. Diese Informationen können Ihnen bei der Entscheidung helfen, wo Sie die Artikel im Crossdockbereich einlagern und wie Sie sie gruppieren.  

4. Wählen Sie die Aktion **Menge für Crossdock autom. ausfüllen** aus, um anzeigen zu lassen, wie die Mengen in den Wareneingangszeilen berechnet werden. Wenn Sie die Anzahl der Artikel im Feld **Menge für Crossdock** in den einzelnen Zeilen ändern, wird die Berechnung aktualisiert, während Sie Änderungen vornehmen. Die Aktualisierung bedeutet nicht, dass die Lieferung oder der Produktionsauftrag tatsächlich die Artikel erhält, die für das Cross-Docking vorgeschlagen werden. Das Feld dient nur zu Informationszwecken. Der Prozess kann jedoch informativ sein, wenn mehr als eine Einheit beteiligt ist.  
5. Um eine Menge von Artikel für eine Auftragszeile zu reservieren, wählen Sie die Aktion **Reservieren** aus. Reservieren Sie auf der Seite **Reservierung** die verfügbare Menge des Artikels. Die Reservierung ist wie jede andere Reservierung und hat keine höhere Priorität, weil sie im Zusammenhang mit einer Cross-Docking erstellt wurde. Weitere Informationen zu Reservierungen finden Sie unter [Artikel reserrvieren](inventory-how-to-reserve-items.md).   
6. Wenn Sie mit der Neuberechnung oder der Reservierung fertig sind, wählen Sie **OK**, um die überprüfte Berechnung in das Feld **Menge für Crossdock** in der Wareneingangszeile zu bringen, oder klicken Sie auf **Abbrechen**, wenn Sie zum Wareneingang zurückkehren möchten, wo Sie den Crossdock noch einmal berechnen können, wenn Sie möchten.  
7. Buchen Sie den Wareneingang. Sie können mit der Einlagerungsanweisung fortfahren, wie in den Schritten 3 bis 7 im Abschnitt [So ordnen Sie Artikel zu, ohne sich die Möglichkeiten anzeigen zu lassen](#to-cross-dock-items-without-viewing-the-opportunities) beschrieben.  

    [!INCLUDE [preview-posting-inventory](includes/preview-posting-inventory.md)]

    > [!NOTE]  
    > In der Einlagerung können Sie fortfahren, die Mengen zu ändern – falls notwendig –, die eingelagert oder zugeordnet werden sollen. Sie können sich z. B. entscheiden, Crossdock für eine zusätzliche Menge auszuführen, um die Crossdockregistrierung zu beschleunigen.  

## <a name="to-view-cross-docked-items-in-a-shipment-or-pick-worksheet" />So zeigen Sie zugeordnete Artikel in Warenausgängen oder Kommissionierarbeitsblättern an:

Wenn Sie Lagerplätze verwenden, können Sie jedes Mal, wenn Sie einen Warenausgang oder den Kommissioniervorschlag öffnen, eine aktualisierte Berechnung der Menge jedes Artikels in den Crossdocklagerplätzen sehen. Wenn Sie sehen, dass der Artikel in einem Crossdocklagerplatz verfügbar ist, können Sie schnell eine Kommissionierung für alle Artikel des Warenausgangs erstellen. Im Auswahlarbeitsblatt können Sie die Zeilen nach Bedarf bearbeiten.  

Wenn ein Fertigungsauftrag freigegeben wurde, sind die Zeilen im Kommissioniervorschlag verfügbar und Sie können im Feld **Menge in Crossd.-Lagerplätzen** sehen, ob die Artikel, auf die Sie warten, angekommen sind und in die zugeordneten Lagerplätze eingelagert wurden. Wenn Sie eine Entnahmeanweisung erstellen, schlägt [!INCLUDE [prod_short](includes/prod_short.md)] vor, dass Sie zuerst die Cross-Dock-Artikel auswählen. Anschliessend werden Artikel in Lagerplätzen vorgeschlagen.  

Wenn Sie keine Lagerplätze verwenden, müssen Sie daran denken, den Crossdockbereich von Zeit zu Zeit zu überprüfen, oder Sie müssen sich auf die Nachrichten aus dem Wareneingang verlassen, dass die Artikel für die Produktion angekommen sind.  

## <a name="see-also" />Weitere Informationen

[Bestand](inventory-manage-inventory.md)  
[Lagerortverwaltung einrichten](warehouse-setup-warehouse.md)     
[Montageverwaltung](assembly-assemble-items.md)    
[Lagerverwaltung – Übersicht](design-details-warehouse-management.md)
[Arbeiten mit [!INCLUDE[prod_short](includes/prod_short.md)]](ui-work-product.md)  

[!INCLUDE[footer-include](includes/footer-banner.md)]
