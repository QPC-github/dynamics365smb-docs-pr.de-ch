---
title: Versichern von Anlagen
description: 'Sie können eine oder mehrere Anlagen einer Richtlinie zuordnen, indem Sie von der Seite **Versicherungsjournal** aus in das Sachkonto der Versicherung buchen.'
author: edupont04
ms.topic: conceptual
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: 'policy, coverage'
ms.search.form: '5647, 5644, 5653, 5651, 5655, 5652, 5645, 5656, 5646, 5648, 9275'
ms.date: 06/29/2021
ms.author: edupont
---
# <a name="insure-fixed-assets" />Versichern von Anlagen
Eine Versicherungspolice für eine Anlage wird durch eine Versicherungskarte angezeigt. Sie können eine Anlage einer Versicherungspolice oder mehreren Anlagen einer Versicherungspolice zuzuordnen.

Sie ordnen einer Anlage einer Versicherungspolice zu, indem Sie sie im Versicherungsposten auf der Seite **Versicherungs Erf.-Journal** buchen.

Zudem können Sie eine Anlage einer Versicherungspolice zuzuordnen und Versicherungsposten erstellen, wenn Sie deren Anschaffungskosten buchen. Sie tun dies, indem Sie Anschaffungskosten aus dem Anlagen Erf.-Journal buchen und das Feld **Versicherungsnr.** verwenden. Das Kontrollkästchen **Autom. Versicherungsbuchung** auf der Seite **Anlageneinrichtung** muss aktiviert sein. Weitere Informationen finden Sie unter [Wie Anlagenanschaffungen mit dem Anlagen Fibu Erf.-Journal manuell gebucht werden](fa-how-acquire.md#to-post-a-fixed-asset-acquisition-manually-with-the-fixed-asset-gl-journal).

Wenn das Kontrollkästchen **Autom. Versicherungsbuchung** auf der Seite **Anlageneinrichtung** nicht ausgewählt ist, werden beim Buchen von Anschaffungen Zeilen im Fenster **Versicherung Erf.-Journal** erstellt, die Sie dann manuell buchen müssen.

> [!WARNING]  
>   Wenn Sie das Kontrollkästchen **Autom. Versicherungsbuchung** auf der Seite **Anlageneinrichtung** auswählen, dann sollte das Versicherungs Erf.-Journal auf einer Erf.-Journalvorlage ohne Nummernserie basieren. Der Grund dafür ist, dass die eingefügten Belegnummern aus der Anl. Erf.-Journalzeile andernfalls einen Konflikt mit der Nummernserie des Versicherungs Erf.-Journals verursachen. Weitere Informationen über Erf.-Journalvorlagen und Erf.-Journalstapel finden Sie unter [Einrichten allgemeiner Anlagen-Informationen](fa-how-setup-general.md).

Nachdem Sie eine Anlage einer Versicherungspolice zugewiesen haben, wird das Kontrollkästchen **Versichert** auf der Anlagenkarte aktiviert. Wenn Sie die Anlage verkaufen, wird das Kontrollkästchen automatisch deaktiviert.

## <a name="to-create-or-modify-an-insurance-card" />So erstellen oder ändern Sie eine Versicherungskarte
Eine Versicherungspolice für eine Anlage muss durch eine Versicherungskarte angezeigt werden.

Wenn Sie Informationen über Änderungen in der Deckungssumme erhalten, müssen Sie diese in der **Versicherungskarte**aktualisieren, um sicherzustellen, dass die Versicherungsdeckung korrekt angezeigt wird.  

1. Wählen Sie die ![Glühbirne, die die „Wie möchten Sie weiter verfahren“-Funktion öffnet.](media/ui-search/search_small.png "Tell me-Funktion") Symbol. Geben Sie **Versicherung** ein, und wählen Sie dann den entsprechenden Link.
2. Wählen Sie die Aktion **Neu** aus, um eine neue Karte für eine Versicherungspolice zu erstellen. [!INCLUDE[tooltip-inline-tip](includes/tooltip-inline-tip_md.md)]
3. Alternativ wählen Sie die Versicherungspolice, die Sie ändern möchten, und wählen die Aktion **Bearbeiten** aus.

## <a name="to-assign-a-fixed-asset-to-an-insurance-policy-by-posting-from-the-insurance-journal" />So verknüpfen Sie eine Anlage mit einer Versicherungspolice durch Buchen aus einem Versicherungs Erf.-Journal
Sie verknüpfen eine Anlage mit einer Versicherungspolice, indem Sie sie in den Versicherungsposten buchen.  

Nachfolgend wird beschrieben, wie Sie eine Versicherungs Erf.-Journalzeile manuell erstellen. Wenn das Kontrollkästchen **Autom. Versicherungsbuchung** auf der Seite **Anlageneinrichtung** ausgewählt wird, werden Versicherungs Erfassungsjournalzeilen automatisch erstellt, wenn Sie Anschaffungskosten buchen. In diesem Fall müssen Sie nur das Erf.-Journal buchen.  

1. Wählen Sie die ![Glühbirne, die die „Wie möchten Sie weiter verfahren“-Funktion öffnet.](media/ui-search/search_small.png "Tell me-Funktion") Symbol. Geben Sie **Vers. Erfassungsjournale** ein und wählen Sie dann den zugehörigen Link.  
2. Öffnen Sie das relevante Erf.-Journal und füllen Sie die Erf.-Journalzeilen nach Bedarf aus.  
3. Um mehrere Anlagen einer Versicherungspolice zuzuweisen, können Sie Erfassungsjournalzeilen mit dem gleichen Wert im Feld **Versicherungsnr.** und unterschiedliche Werte im Feld **Anlagennr.**  
4. Wählen Sie die Aktion **Buchen** aus.  

    > [!NOTE]  
    >   Die Posten aus dem Versicherungs Erfassungsjournal werden nur auf die Versicherungsposten gebucht.  

## <a name="to-update-the-insurance-value-of-a-fixed-asset" />So aktualisieren Sie den Versicherungswert einer Anlage
Sie können die Stapelverarbeitung **Indexiere Versicherung** verwenden, um den Wert der versicherten Anlagen zu aktualisieren.  

1. Wählen Sie die ![Glühbirne, die die „Wie möchten Sie weiter verfahren“-Funktion öffnet.](media/ui-search/search_small.png "Tell me-Funktion") Symbol. Geben Sie **Versicherung indexieren** ein und wählen Sie dann den zugehörigen Link.
2. Füllen Sie die Felder je nach Bedarf aus.

    > [!NOTE]  
    >   Im Feld **Indexzahl** wird eine Senkung um 5 % beispielsweise als "95" eingegeben, während eine Steigerung von 2 % als "102" eingegeben wird.  
3. Wählen Sie die Schaltfläche **OK** aus.  

   Die Stapelverarbeitung berechnet den neuen Betrag als Prozentsatz des gesamten versicherten Wertes auf der Seite **Versicherungsstatistik** und erstellt dann eine Zeile im Vers. Erf.-Journal.  
4. Wählen Sie die ![Glühbirne, die die „Wie möchten Sie weiter verfahren“-Funktion öffnet.](media/ui-search/search_small.png "Tell Me-Funktion") Symbol. Geben Sie **Vers. Erfassungsjournale** ein und wählen Sie dann den zugehörigen Link.  
5. Öffnen Sie das relevante Versicherungs Erf.-Journal, prüfen Sie die erstellten Posten und buchen Sie diese dann auf die Versicherungsposten.  

## <a name="to-monitor-insurance-coverage" />So überwachen Sie die Versicherungsdeckung
[!INCLUDE[prod_short](includes/prod_short.md)] bietet dedizierte Berichte und Statistikseiten, die dazu verwendet werden können, Versicherungspolicen zu analysieren und zu überprüfen, ob Ihre Anlagen über- oder unterversichert sind.  

### <a name="overview-of-insurance-policies" />Übersicht der Versicherungspolicen
Gibt einen Überblicks über die Versicherungspolicen durch Drucken des Berichts **Versicherung-Liste**. Der Bericht zeigt die einzelnen Policen und die wichtigsten Felder der Versicherungskarten an.  

### <a name="insurance-coverage" />Versicherungsdeckung
Um zu sehen, welche Versicherungspolicen welche Anlagen in welcher Höhe abdecken, können Sie den Bericht **Versicherung – Vers. Summe** ausdrucken oder anzeigen.  

### <a name="overunder-coverage" />Unter-/Überversicherung
Folgendermassen können Sie prüfen, ob Anlagen über- oder unterversichert sind:  

* Die Seite **Versicherungsstatistik**. Ein positiver Betrag in dem Feld **Über-/Unterversichert** bedeutet, dass die Anlage überversichert ist. Ein negativer Betrag zeigt eine Unterversicherung an.  
* Die Seite **Anlagenstatistik**. Wählen Sie das Feld **Versicherte Summe**, um die Seite **Versicherungsposten** anzuzeigen.  
* Der Bericht **Unter-/Überversicherung**.  
* Der Bericht **Versicherungsanalyse**.  

### <a name="uninsured-fixed-assets" />Unversicherte Anlagen
Um zu prüfen, ob Sie vergessen haben, eine Anlage einer Versicherungspolice zuzuweisen, können Sie den Bericht **Versicherung - Unvers. Anlagen** drucken oder anzeigen. Dieser Bericht zeigt Anlagen an, für die noch keine Beträge in den Versicherungsposten gebucht wurden.  

## <a name="to-view-insurance-coverage-ledger-entries" />So zeigen Sie Versicherungsposten an
Sie können sich die einzelnen Posten anzeigen lassen, die Sie in den Versicherungsposten erstellt haben.  

1. Wählen Sie die ![Glühbirne, die die „Wie möchten Sie weiter verfahren“-Funktion öffnet.](media/ui-search/search_small.png "Tell Me-Funktion") Symbol. Geben Sie **Versicherung** ein, und wählen Sie dann den entsprechenden Link.  
2. Wählen Sie die entsprechende Versicherungspolice aus, und wählen Sie dann die Aktion **Versicherungsposten**.  

## <a name="to-view-the-total-insurance-value-of-fixed-assets" />So zeigen Sie den gesamten Versicherungswert von Anlagen an:
Eine dedizierte Matrixseite zeigt die Versicherungswerte jeder Anlage und jeder Versicherungspolice als Ergebnis der versicherungsbezogenen Beträge an, die von Ihnen gebucht wurden.  

1. Wählen Sie die ![Glühbirne, die die „Wie möchten Sie weiter verfahren“-Funktion öffnet.](media/ui-search/search_small.png "Tell Me-Funktion") Symbol. Geben Sie **Versicherung** ein, und wählen Sie dann den entsprechenden Link.  
2. Wählen Sie die entsprechende Versicherungspolice aus, und wählen Sie dann die Aktion **Versicherte Summe pro Anlage**.  
3. Füllen Sie die Felder je nach Bedarf aus.  
4. Wählen Sie die Aktion **Matrix anzeigen** aus.  
5. Um die zu Grunde liegenden Versicherungsposten anzuzeigen, aktivieren Sie einen Wert in der Matrix.  

## <a name="to-correct-insurance-coverage-entries" />So korrigieren Sie Versicherungsposten
Wenn eine Anlage der falschen Versicherung zugeordnet wurde, können Sie diese korrigieren, indem Sie zwei Umbuchungsposten aus dem Versicherungs Erf.-Journal erstellen.  

1. Wählen Sie die ![Glühbirne, die die „Wie möchten Sie weiter verfahren“-Funktion öffnet.](media/ui-search/search_small.png "Tell Me-Funktion") Symbol. Geben Sie **Vers. Erfassungsjournale** ein und wählen Sie dann den zugehörigen Link.  
2. Erstellen Sie eine Buch.-Blattzeile für die Anlage und die korrekte Versicherungspolice, in der der Wert im Feld **Betrag** positiv ist.  
3. Erstellen Sie eine weitere Buch.-Blattzeile für die Anlage und die inkorrekte Versicherungspolice, in der der Wert im Feld **Betrag** negativ ist.  
4. Wählen Sie die Aktion **Buchen** aus.  

Die Verknüpfung der Anlage mit der falschen Versicherung der zweiten Zeile wird aufgehoben und stattdessen eine Verknüpfung mit der richtigen Versicherung aus der ersten Zeile erstellt.  

## <a name="see-also" />Weitere Informationen
[Anlagen](fa-manage.md)  
[Anlagen einrichten](fa-setup.md)  
[Finanzen](finance.md)  
[Arbeiten mit [!INCLUDE[prod_short](includes/prod_short.md)]](ui-work-product.md)  


[!INCLUDE[footer-include](includes/footer-banner.md)]
