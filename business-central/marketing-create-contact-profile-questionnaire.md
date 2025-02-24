---
title: 'Verwenden Sie Profile, um Kontakte zu klassifizieren'
description: 'Rot darüber, wie Sie Profilfragebögen festlegen können, um die Profile Ihrer Geschäftskontakte zu klassifizieren.'
author: edupont04
ms.topic: conceptual
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: 'contacts, profiles'
ms.search.form: '5109, 5110'
ms.author: edupont
ms.date: 05/20/2022
---

# <a name="use-profile-questionnaires-to-classify-business-contacts" />Verwenden Sie Profilbefragungen, um Geschäftskontakten zu klassieren

Sie können einen Interessenten bewerten und so die idealen Interessenten erkennen, auf die Sie sich in Ihrer Verkaufskampagne konzentrieren. Sie können Profilbefragungen einrichten, die Sie beim Eingeben der Informationen über die Profile Ihrer Kontakte verwenden möchten. In jedem Fragebogen können Sie die unterschiedlichen Fragen einrichten, die Sie Ihren Kontakten stellen möchten. Auf diese Weise können Sie Kontakte gruppieren, sodass Ihre Kampagnen eher auf die richtigen Personen ausgerichtet sind, basierend auf den Kriterien, die Sie mit den Fragebögen definieren.  

Mit den richtigen Fragebögen können Sie Ihre Interessenten bewerten und in Kategorien einteilen. Sie können vorhandene Fragen und Antworten verwenden und diese mit neuen Fragen und Antworten kombinieren, um die Grundlage für Ihre Bewertung zu schaffen. Jede Antwort in der Bewertung erhält einen Punktewert, und abhängig von dem Bereich, den Sie für die Kategorien festgelegt haben (*Von-Wert* und *Bis-Wert*), gruppiert das Bewertungssystem Ihre Kontakte nach den definierten Kategorien. Z. B. *ABC*-Debitoren, Lieferanten mit *hoher/niedriger Loyalität* oder *Platin/Gold/Silber*-Interessenten.  

Sie können die Befragung auch dazu verwenden, um einige Fragen zum Kontakt, Debitor oder Kreditor automatisch zu beantworten.  

## <a name="to-add-a-profile-questionnaire" />So fügen Sie eine Profilbefragung hinzu

1. Wählen Sie die ![Glühbirne, die die „Wie möchten Sie weiter verfahren“-Funktion öffnet.](media/ui-search/search_small.png "Tell Me-Funktion") Symbol. Geben Sie **Fragebogen Einrichtung** ein und wählen Sie dann den zugehörigen Link.  
2. Wählen Sie die Aktion **Neu**.  
3. Füllen Sie die Felder je nach Bedarf aus. [!INCLUDE[tooltip-inline-tip](includes/tooltip-inline-tip_md.md)]  

## <a name="to-add-questions-to-a-profile-questionnaire" />So fügen Sie einen Fragebogen einer Profilbefragung hinzu

1. Wählen Sie den entsprechenden Profilfragebogen aus und wählen Sie dann die Aktion **Einstellung Fragebogen bearbeiten**.  
2. Wählen Sie in der ersten leeren Zeile im Feld **Art** die Option **Frage** aus, und geben Sie im Feld **Beschreibung** Ihre Frage ein. Füllen Sie die anderen Felder in dieser Zeile aus.  

    Fügen Sie der Frage optional Details hinzu.

    1. Wählen Sie die Zeile mit der Frage, danach das Menü **Zeile** und anschliessend die Option **Fragendetails** aus.  

    2. Wählen Sie auf der Seite **Profilfragendetails** im Inforegister **Klassifizierung** das Feld **Autom. Kontaktklassifizierung** aus.  

    3. Wählen Sie im Feld **Kontaktklassifizierungsfeld** die Option **Bewertung** aus.  

    4. Füllen Sie das Feld **Min. % beantworteter Fragen** aus. Der Standardwert lautet **0**.  

        Dies gibt die Anzahl der Fragen in Prozent an, die für die Berechnung dieser Bewertung beantwortet werden müssen.

    5. Wählen Sie auf der Registerkarte **Aktionen** in der Gruppe **Seite** die Option **Antwortpunkte** aus. Geben Sie die Punkte ein, die Sie für die Antworten auf der Seite **Antwortpunkte** vergeben möchten.

        Wenn Sie sich einen Überblick über die von Ihnen vergebenen Punkte für jede Antwort verschaffen möchten, wählen Sie die Aktion **Antwortpunkte** aus.

    6. Um ein Update auszuführen, kehren Sie zur Seite **Profilbefragung Einrichtung** zurück. Wählen Sie im Menü **Aktionen** in der Gruppe **Funktionen** **Kontaktklassifizierung aktual.** aus.

    Auf der Seite **Profilbefragung einrichten** wird die Anzahl der Kontakte, die diese Kriterien erfüllen, im Feld **Anzahl KontakteProfil** sowie in der **Kontaktkarte** jedes Kontaktes angezeigt.

3. Wählen Sie in der nächsten leeren Zeile im Feld **Art** die Option **Antwort** aus, und geben Sie im Feld **Beschreibung** Ihre Antwort ein.  
4. Wählen Sie im Feld **Priorität** die Priorität aus. Definieren Sie in den Feldern **Von Wert** und **Bis Wert** einen Punktbereich. Kontakte, die innerhalb des definierten Bereichs Punkte erhalten, erhalten die Antwort.  

Wiederholen Sie diese Schritte, um alle Fragen und Antworten für die Profilbefragung einzugeben.

Nachdem Sie eine Befragung erstellt haben, können Sie Ihre Kontakte damit bewerten und klassifizieren. Sie können auch Fragen einrichten, die automatisch auf Grundlage der Informationen in der Kontaktkarte bewertet werden.  

> [!NOTE]
> Wenn Sie eine Frage eingeben, die automatisch beantwortet werden soll, wählen Sie die Optionen **Zeile** und dann **Fragendetails** aus, um die Kriterien einzugeben, die zur automatischen Beantwortung verwendet werden.

## <a name="apply-questionnaires-to-contacts" />Fragebögen auf Kontakte anwenden

Sie können Ihre Fragebögen manuell auf Kontakte anwenden. Öffnen Sie einfach die entsprechende Kontaktkarte, und wählen Sie dann die Aktion **Profil** aus. Sobald Sie die gewünschten Fragebögen angewendet haben, können Sie mit der Verwendung der Kategorien in Ihren Kampagnen beginnen.  

## <a name="the-automatic-classification-of-contacts" />Die automatische Klassifizierung von Kontakten

Sie können Ihre Kontakte nach Debitoren, Kreditoren und Kontaktinformationen klassifizieren, indem Sie auf der Seite Profilbefragung einrichten automatisch beantwortete **Profilbefragungen** einrichten.  

> [!NOTE]
> Nur als Debitor gespeicherten Kontakten kann eine Klassifizierung auf Debitordatenbasis zugeordnet werden und nur als Kreditor gespeicherten Kontakten kann eine Klassifizierung auf Kreditordatenbasis zugeordnet werden. Die automatische Klassifizierung wird nicht automatisch aktualisiert. Deshalb können Sie die Profilbefragungen aktualisieren, nachdem Sie die Debitor-, Kreditor- oder Kontaktdaten aktualisiert haben, auf denen sie basieren.  

Nachdem Sie automatische beantwortete Profilbefragungen eingerichtet haben, werden dem Kontakt [!INCLUDE[prod_short](includes/prod_short.md)] automatisch die richtigen Antworten zugeordnet, wenn Sie die Profilbefragung mit diesen Fragen einem Kontakt zuordnen.  

## <a name="example" />Beispiel

Sie können Ihre Kontakte danach klassifizieren, wie viel sie bei Ihnen gekauft haben:

|Antwort|Gilt für|
|--- |--- |
|A|Kontakte, die für 500.000 MW oder mehr gekauft haben|
|B|Kontakte, die von 100.000 bis 499.999 MW gekauft haben|
|U|Kontakte, die für 99.999 MW oder weniger gekauft haben|

Füllen Sie hierzu die Seite **Profilbefragung einrichten** folgendermassen aus:

| Art     | Beschreibung        | Automatische Klassifizierung     | Von Wert | Nach Wert |
|----------|--------------------|------------------------------|------------|----------|
| Frage | ABC Klassifizierung | Klicken Sie in das Feld, um ein Häkchen einzufügen. |            |          |
| Antwort   | A                  |                              | 500.000    |          |
| Antwort   | B                  |                              | 100.000    | 499.999  |
| Antwort   | U                  |                              |            | 99.999   |

Füllen Sie dann das Fenster **Profilfragendetails** folgendermassen aus:

| Feld                         | Wert         |
|-------------------------------|---------------|
| Feld für die Klassifizierung des Debitors | Umsatz (LCY)   |
| Klassifizierungsmethode         | Definierter Wert |

Wenn Sie einem Kontakt die Profilbefragung mit dieser Frage zuordnen, wird die Anwendung in die Profilzeilen der Kontaktkarte automatisch die entsprechende Antwort für diesen Kontakt eingetragen.

## <a name="see-also" />Siehe auch

[Kontakte erstellen](marketing-create-contact-companies.md)  


[!INCLUDE[footer-include](includes/footer-banner.md)]
