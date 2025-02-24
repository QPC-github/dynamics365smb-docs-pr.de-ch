---
title: Ermöglichen der Power BI-Integration in Business Central
description: 'Erfahren Sie, wie Sie die Verbindung zu Power BI festlegen. Mit Power BI-Berichten können Sie Insights, Business Intelligence und KPIs aus Ihren Business Central-Daten erhalten.'
author: jswymer
ms.topic: get-started-article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: 'Power BI, setup, analysis, reporting, financial report, business intelligence, KPI'
ms.date: 07/13/2022
ms.author: jswymer
---
# <a name="enabling-power-bi-integration-with-includeprodshortincludesprodshortmd" />Ermöglichen der Power BI-Integration mit [!INCLUDE[prod_short](includes/prod_short.md)]

Dieser Artikel beschreibt, wie man [!INCLUDE[prod_short](includes/prod_short.md)] für die Integration mit Power BI vorbereitet. [!INCLUDE[prod_short](includes/prod_short.md)] online ist bereits für die Integration vorbereitet, obwohl Sie eventuell einige Informationen zur Lizenzierung lesen möchten. Für [!INCLUDE[prod_short](includes/prod_short.md)] on-premises müssen Sie Ihre Umgebung für die Verbindung mit Power BI einrichten, bevor Benutzer damit arbeiten können.

## <a name="a-namelicenseapower-bi-licensing" /><a name="license"></a>Power BI-Lizenzierung

Mit [!INCLUDE[prod_short](includes/prod_short.md)] erhalten Benutzer eine kostenlose Power BI-Lizenz, die Zugriff auf die gängigsten Funktionen von [!INCLUDE[prod_short](includes/prod_short.md)] und Power BI bietet. Sie können auch eine Power BI Pro-Lizenz kaufen, die Zugriff auf zusätzliche Funktionen bietet. Die folgende Tabelle bietet einen Überblick über die Funktionen, die mit jeder Lizenz verfügbar sind.

|Power-Lizenz|Berichte anzeigen|Berichte erstellen|Berichte teilen|Berichte aktualisieren| [!INCLUDE[prod_short](includes/prod_short.md)]-Apps|
|-------------|--------||
|Power BI kostenlos|![ein häkchen.](media/check.png)|![ein weiteres Häkchen](media/check.png)|(eingeschränkt)|(eingeschränkt)||
|Power BI Pro|![noch ein Häkchen.](media/check.png)|![noch ein Häkchen](media/check.png)|![wieder ein Häkchen](media/check.png)|(umfangreich)|![letztes Häkchen](media/check.png)|

Weitere Informationen finden Sie unter [Lizenzierung des Power BI-Dienstes für Benutzer in Ihrer Organisation](/power-bi/admin/service-admin-licensing-organization) oder unter [Als Einzelperson für den Power BI-Dienst anmelden](/power-bi/fundamentals/service-self-service-signup-for-power-bi).

## <a name="a-nameexposedataaexpose-data-through-api-or-odata-web-services" /><a name="exposedata"></a>Daten über API-Seiten oder OData-Webdienste verfügbar machen

Business Central bietet zwei Möglichkeiten, Daten freizugeben, die von Power BI-Berichten genutzt werden können: API-Seiten oder Abfragen und Open Data Protocol (OData)-Webdienste.

### <a name="api-pages-and-queries" />API-Seiten und Abfragen

> **Gilt nur für:** Business Central online

Entwickler können Seitenobjekte definieren und Objekte abfragen, die vom Typ *API* sind. Auf diese Weise können sie Daten aus Datenbanktabellen über einen Webhook-unterstützten, OData v4-fähigen REST-Dienst verfügbar machen. Dieser Datentyp kann nicht in der Benutzeroberfläche angezeigt werden, sondern ist für den Aufbau zuverlässiger Integrationsdienste gedacht.

Business Central online verfügt über einen Satz integrierter APIs, mit denen Sie Daten für die allgemeinsten Entitäten wie Kunden, Artikel, Verkaufsaufträge und mehr festlegen können. Es ist keine zusätzliche Arbeit oder Einrichtung erforderlich, um diese APIs als Datenquelle für Power BI-Berichte zu verwenden. Weitere Informationen über diese APIs finden Sie unter [Business Central API V2.0](/dynamics365/business-central/dev-itpro/api-reference/v2.0/).

Business Central online unterstützt auch angepasste APIs. Anwendungsentwickler von Business Central-Lösungen können ihre eigenen API-Seiten und Abfragen erstellen und diese in Apps verpacken. Anschliessend installieren Sie die Apps für Ihren Mandanten. Nach der Installation verwenden Sie die API-Seiten für Ihre Power BI-Berichte, wie Sie es mit den integrierten APIs (v2.0) tun würden. Weitere Informationen darüber, wie Sie eine API durch die Bereitstellung von Seiten oder Abfragen erstellen, finden Sie unter [Entwickeln einer benutzerdefinierten API](/dynamics365/business-central/dev-itpro/developer/devenv-develop-custom-api).

> [!IMPORTANT]
> Ab Februar 2022 werden die Power BI-Berichte für [!INCLUDE[prod_short](includes/prod_short.md)] online aus Leistungsgründen von einer sekundären, schreibgeschützten Datenbankreplik bezogen. Folglich sollten AL-Entwickler es vermeiden, API-Seiten zu entwerfen, die Datenbankänderungen vornehmen, während die Seiten geöffnet oder Datensätze geladen werden. Beachten Sie vor allem den Code der AL-Auslöser: OnInit, OnOpenPage, OnFindRecord, OnNextRecord, OnAfterGetRecord, und OnAfterGetCurrRecord. Diese Datenbankänderungen können in einigen Fällen zu Leistungsproblemen führen und verhindern, dass der Bericht die Daten aktualisiert. Weitere Informationen finden Sie unter [Performance-Artikel für Entwickler](/dynamics365/business-central/dev-itpro/performance/performance-developer?branch=main#writing-efficient-web-services) in Business Central-Entwicklungsinhalten.
>
> In seltenen Fällen verursacht das Verhalten einen Fehler, wenn ein Benutzer versucht, Daten von der API für einen Bericht in Power BI Desktop zu erhalten. Wenn jedoch Datenbankänderungen in der benutzerdefinierten API erforderlich sind, können Benutzer mit Power BI Desktop das Verhalten erzwingen. Weitere Informationen finden Sie unter [Erstellung von Power BI-Berichten zur Anzeige von Business Central-Daten](across-how-use-financials-data-source-powerbi.md#fixing-problems).

### <a name="odata-web-services" />OData-Webdienste

Sie können Business Central-Anwendungsobjekte, wie Codeunits, Seiten und Abfragen, als [OData Webdienste](/dynamics365/business-central/dev-itpro/webservices/odata-web-services) veröffentlichen. Bei Business Central online sind standardmässig viele Webdienste veröffentlicht. Eine einfache Methode, die Webdienste zu finden ist, in *Webdiensten* in [!INCLUDE[prod_short](includes/prod_short.md)] zu suchen. Vergewissern Sie sich, dass auf der Seite **Webdienste** das Feld **Veröffentlichen** für die oben aufgeführten Webdienste ausgewählt ist. Weitere Informationen zum Veröffentlichen von Webdiensten finden Sie unter [Webdienst veröffentlichen](across-how-publish-web-service.md).

Um zu erfahren, wie Sie vom Business Central Server (Endpunkt) und vom Verbaucher (dem Client) aus gesehen die optimale Leistung von Webdiensten erzielen, lesen Sie [Effiziente Webdienste schreiben](/dynamics365/business-central/dev-itpro/performance/performance-developer#writing-efficient-web-services).

### <a name="choosing-whether-to-use-api-pages-or-odata-web-services" />Auswahl, ob Sie API-Seiten oder OData-Webdienste verwenden wollen

Wann immer möglich, sollten Sie API-Seiten anstelle von OData-Webdiensten verwenden. API-Seiten sind im Allgemeinen schneller beim Laden von Daten in Power BI-Berichten als OData-Webdienste. Ausserdem sind sie flexibler, weil Sie damit Daten aus Tabellenfeldern abrufen können, die nicht in einem Seitenobjekt definiert sind.

## <a name="a-namesetupaset-up-includeprodshortincludesprodshortmd-on-premises-for-power-bi-integration" /><a name="setup"></a>[!INCLUDE[prod_short](includes/prod_short.md)] on-premises für die Power BI-Integration einrichten

In diesem Abschnitt werden die Anforderungen für eine Bereitstellung von [!INCLUDE[prod_short](includes/prod_short.md)] on-premises zur Integration mit Power BI erläutert.

1. Konfigurieren Sie die Authentifizierung für die Bereitstellung entweder mit NavUserPassword oder Azure Active Directory.  
    
    > [!NOTE]
    > Die Power BI Integration unterstützt keine Windows-Authentifizierung und wird auf dem Windows-Client nicht unterstützt.

2. OData-Webdienste und ODataV4-Endpunkt aktivieren.

    Der OData-Webdienst muss auf dem [!INCLUDE[server](includes/server.md)] aktiviert sein und der OData-Port in der Firewall muss offen sein. Weitere Informationen finden Sie unter [Konfigurieren von Business Central Server – OData-Webdienste](/dynamics365/business-central/dev-itpro/administration/configure-server-instance#ODataServices).

    Der lokale Server muss über das Internet erreichbar sein.

3. [!INCLUDE[prod_short](includes/prod_short.md)]-Benutzerkonten erhalten einen Webdienst-Zugriffsschlüssel.

    Zur Anzeige von [!INCLUDE[prod_short](includes/prod_short.md)]-Daten in Power BI wird nur ein Webdienst-Zugriffsschlüssel benötigt. Sie können jedem Benutzerkonto einen Webdienst-Zugriffsschlüssel zuweisen. Oder erstellen Sie stattdessen ein bestimmtes Konto mit einem Webdienst-Zugriffsschlüssel, der von allen Benutzern verwendet werden kann. Weitere Informationen finden Sie unter [Webdienst-Authentifizierung](/dynamics365/business-central/dev-itpro/webservices/web-services-authentication#generate-a-web-service-access-key).

    <!--
    > [!IMPORTANT]
    > With [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online, the use of access keys (Basic Auth) for web service authentication is [deprecated](/dynamics365/business-central/dev-itpro/upgrade/deprecated-features-w1#accesskeys). We recommend that you use OAuth2 instead. For more information, see [Use OAuth to Authorize Business Central Web Services](/dynamics365/business-central/dev-itpro/webservices/authenticate-web-services-using-oauth).-->

4. Erstellen Sie eine Anwendungsregistrierung für [!INCLUDE[prod_short](includes/prod_short.md)] in Microsoft Azure.

    Um Power BI-Berichte anzuzeigen, die in [!INCLUDE[prod_short](includes/prod_short.md)]-Seiten eingebettet sind, muss für [!INCLUDE[prod_short](includes/prod_short.md)] in Microsoft Azure eine Anwendung registriert werden. Die registrierte Anwendung benötigt Berechtigungen für Power BI-Dienste. Für die App ist mindestens die Berechtigung **User.ReadWrite.All** erforderlich. Damit Benutzer Berichte von freigegebenen Power BI-Arbeitsbereichen anzeigen können, erfordert die App die Berechtigung **Workspace.Read.All**. Weitere Informationen finden Sie unter [Registrieren von [!INCLUDE[prod_short](includes/prod_short.md)] On-Premises in Azure AD zur Integration mit anderen Diensten](/dynamics365/business-central/dev-itpro/administration/register-app-azure).

    > [!NOTE]
    > Wenn Ihre Bereitstellung die NavUserPassword-Authentifizierung verwendet, stellt [!INCLUDE[prod_short](includes/prod_short.md)] für alle Benutzer eine Verbindung mit demselben Power BI-Dienst her. Sie geben dieses Dienstkonto bei der Registrierung der Anwendung an. Wenn Sie die Azure AD-Authentifizierung verwenden, verbindet sich [!INCLUDE[prod_short](includes/prod_short.md)] mit dem Power BI-Dienst, der den einzelnen Benutzerkonten zugeordnet ist.

    <!-- Windows authentication can also be used but you can't get data from BC in Power BI -->
5. Stellen Sie die erste Verbindung von Business Central zu Power BI her.

    Bevor Endbenutzer Power BI in [!INCLUDE[prod_short](includes/prod_short.md)] verwenden können, muss ein Azure-Anwendungsadministrator dem Power BI-Service zustimmen.

    Um die erste Verbindung herzustellen, öffnen Sie [!INCLUDE[prod_short](includes/prod_short.md)], und führen Sie **Erste Schritte mit Power BI** über die Startseite aus. Diese Aktion führt Sie durch den Einwilligungsprozess und überprüft Ihre Power BI-Lizenz. Wenn Sie dazu aufgefordert werden, melden Sie sich mit einem Azure-Administratorkonto an. Weitere Informationen finden Sie unter [Mit Power BI verbinden – nur ein Mal](across-working-with-powerbi.md#connect).


## <a name="see-related-microsoft-trainingtrainingmodulesconfigure-powerbi-excel-dynamics-365-business-centralindex" />Siehe verwandte [Microsoft Schulungen](/training/modules/Configure-powerbi-excel-dynamics-365-business-central/index)

## <a name="see-also" />Siehe auch

[Business Central und Power BI](admin-powerbi.md)  
[Übersicht über die Power BI-Integrationskomponente und -Architektur für [!INCLUDE[prod_short](includes/prod_short.md)]](admin-powerbi-overview.md)  
[Power BI für Verbraucher](/power-bi/consumer/end-user-consumer)  
[Der "neue Look" des Power BI Service](/power-bi/service-new-look)  
[Schnellstart: Stellen Sie eine Verbindung zu Daten her in Power BI Desktop](/power-bi/desktop-quickstart-connect-to-data)  
[Power BI Dokumentation](/power-bi/)  
[Business Intelligence](bi.md)  
[Vorbereitungen zum Tätigen von Geschäften](ui-get-ready-business.md)  
[Geschäftsdaten aus anderen Finanzsystemen importieren](across-import-data-configuration-packages.md)  
[Einrichten [!INCLUDE[prod_short](includes/prod_short.md)]](setup.md)  
[[!INCLUDE[prod_short](includes/prod_short.md)] als Power BI-Datenquelle verwenden](across-how-use-financials-data-source-powerbi.md)  
[[!INCLUDE[prod_short](includes/prod_short.md)] als Power Apps-Datenquelle verwenden](across-how-use-financials-data-source-powerapps.md)  
[[!INCLUDE[prod_short](includes/prod_short.md)] in Power Automate verwenden](across-how-use-financials-data-source-flow.md)  




[!INCLUDE[footer-include](includes/footer-banner.md)]
