---
title: Schliessen Sie Erfolgsrechnung-Konten
description: 'Am Jahresende beispielsweise müssen Sie die Stapelverarbeitung "Erfolgsrechnungskonten Nullstellung" laufen lassen, um dies Buchhaltungsperioden zu schliessen, aus der sich das Geschäftsjahr zusammensetzt.'
author: jswymer
ms.topic: conceptual
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: 'year closing, close accounting period, close fiscal year, bank account detailed trial balance'
ms.date: 06/25/2021
ms.author: jswymer
---
# <a name="closing-income-statement-accounts" />Erfolgsrechnung-Konten Nullstellung
Wenn ein Geschäftsjahr vorbei ist, müssen die Perioden, aus denen es besteht, geschlossen werden. Verwenden Sie dazu den Stapelverarbeitungsjob **Jahresabschluss**. Dieser Job überträgt die Ergebnisse des Jahrs auf ein Bilanzkonto und führt die Erfolgsrechnung durch. Hierfür erstellen Sie Zeilen in einem Erf.-Journal, die Sie dann buchen können.

## <a name="to-run-the-close-income-statement-batch-job" />Verwenden Sie dazu den Stapelverarbeitungsjob Erfolgsrechnung.
1. Schliessen Sie das Geschäftsjahr ab. Das Geschäftsjahr muss geschlossen werden, bevor die Stapelverarbeitung aufgerufen werden kann. Weitere Informationen finden Sie unter [Abschliessen von Buchhaltungsperioden](year-close-account-periods.md).
2. Wählen Sie die ![Glühbirne, die die „Wie möchten Sie weiter verfahren“-Funktion öffnet.](media/ui-search/search_small.png "Tell me-Funktion") Symbol. Geben Sie **Gewinn- und Verlustrechnung Nullstellung abschliessen** ein, und wählen Sie dann den zugehörigen Link.
3. Wählen Sie die Schaltfläche **OK**, um den Batchauftrag zu starten.

## <a name="about-the-close-income-statement-batch-job" />Mehr Informationen zum Stapelverarbeitungsjob Erfolgsrechnung.
Mithilfe dieses Batchauftrags werden alle Fibukonten der Art "Erfolgsrechnung" bearbeitet und Buchungszeilen erzeugt, die eine Nullstellung ihrer Salden bewirken. Anders ausgedrückt, entspricht jeder Posten der Summe aller Fibuposten auf dem Konto im Geschäftsjahr. Diese neuen Posten werden in ein Erfassungsjournal eingefügt, in dem Sie ein Gegenkonto und ein Abschlusskonto GuV in der Bilanz angeben müssen, bevor diese gebucht werden. Wenn Sie das Erfassungsjournal buchen, wird ein Posten auf jedes Erfolgsrechnungskonto gebucht, sodass der Saldo des Kontos Null ist und gleichzeitig das Jahresergebnis in die Bilanz übertragen wird.

Sie müssen das Erfassungsjournal manuell buchen. Durch den Batchauftrag erfolgt keine automatische Buchung der Posten, es sei denn, es wird eine Berichtswährung verwendet. Wenn eine zusätzliche Berichtswährung verwendet wird, bucht die Stapelverarbeitung die Posten direkt in die Fibu.

Das Datum, das von dem Batchauftrag in die Zeilen eingefügt wird, ist stets das Ultimodatum des Geschäftsjahrs. Das Ultimodatum ist ein fiktives Datum zwischen dem letzten Tag des alten und dem ersten Tag des neuen Geschäftsjahres. Der Vorteil des Buchens zu einem Ultimodatum liegt darin, dass die Salden des Geschäftsjahres mit normalen Datumsangaben erhalten bleiben.

Die Stapelverarbeitung **Jahresabschluss** kann mehrmals aufgerufen werden. Sie können im vorigen Geschäftsjahr buchen, selbst wenn die Erfolgskonten-Nullstellung bereits vorgenommen wurde, sofern Sie die Stapelverarbeitung erneut ausführen.

## <a name="see-also" />Siehe auch

[Schliessen der Bücher](year-close-books.md)  
[So buchen Sie den Jahresabschlussposten](year-how-post-year-end-close-entry.md)  
[Arbeiten mit Buchhaltungsperioden und Geschäftsjahren](finance-accounting-periods-and-fiscal-years.md)  
[Arbeiten mit [!INCLUDE[prod_short](includes/prod_short.md)]](ui-work-product.md)


[!INCLUDE[footer-include](includes/footer-banner.md)]
