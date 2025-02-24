---
title: Design-Details – Artikeltracking im Lager
description: Eingehende und ausgehende Lagerbelege verfügen über eine Standardfunktionalität für die Zuweisung und Auswahl von Artikeltrackingsnummern.
author: SorenGP
ms.topic: conceptual
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: 'design, item, tracking, serial number, lot number, outbound documents'
ms.date: 06/15/2021
ms.author: edupont
---
# <a name="design-details-item-tracking-in-the-warehouse" />Designdetails: Artikeltracking im Lager
Der Umgang mit Serien- oder Chargennummern ist hauptsächlich eine Lageraufgabe; daher haben alle eingehenden und ausgehenden Lagerbelege Standardfunktionen für die Zuordnung und die Auswahl von Artikeltrackingnummern.  

Da das Reservierungssystem auf Lagerposten basiert, werden Lageraktivitätsbelege, die nur Lagerplatzposten erfassen, jedoch nicht vollständig unterstützt. Da Reservierungen und Artikeltrackingnummern nur auf Lagerort- (und nicht auf Lagerplatz- oder Zonen-)Ebene bearbeitet werden können, kann das Fenster **Artikeltrackingzeilen** nicht aus den Lageraktivitätsbelegen heraus geöffnet werden. Dies gilt auch für die Seite **Reservierung**.  

Nachdem eine Serien- oder eine Chargennummer dem Bestand an einem Lagerort hinzugefügt wurde, kann sie verschoben und frei im Lager neuklassifiziert werden, indem eine unabhängige Artikeltrackingstruktur, die keine Beziehung zum Reservierungssystem hat, verwendet wird. Auf die Felder **Seriennr.** und **Chargennr.** wird direkt auf Logistikbelegzeilen zugegriffen. Wenn die Serien- oder Chargennummer später in der ausgehenden Buchung erscheint, wird sie mit dem Reservierungssystem als Teil einer gewöhnlichen Lagerplatzanpassung synchronisiert. Weitere Informationen finden Sie unter [Designdetails: Bestandintegration](design-details-integration-with-inventory.md).  

Das Reservierungssystem berücksichtigt jedoch Lageraktivitäten, wenn es die Verfügbarkeit berechnet. Beispielsweise können Artikel, die Kommissionierungen zugewiesen oder als kommissioniert registriert sind, nicht reserviert werden. Weitere Informationen finden Sie unter [Designdetails: Verfügbarkeit im Lager](design-details-availability-in-the-warehouse.md).

## <a name="see-also" />Siehe auch
[Designdetails: Artikeltracking](design-details-item-tracking.md)  
[Designdetails: Integration mit dem Lagerbestand](design-details-integration-with-inventory.md)  
[Designdetails: Verfügbarkeit im Lager](design-details-availability-in-the-warehouse.md)  
[Designdetails: Artikeltrackingdesign](design-details-item-tracking-design.md)


[!INCLUDE[footer-include](includes/footer-banner.md)]
