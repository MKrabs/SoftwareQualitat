# Hausarbeit Softwarequalitat
**Author**: Marc Gokce  
**Kurs**: TINF 20b4  
**Vorlesung**: Softwarequalitat  
**Dozent**: Dennis Kube

_Hinweis: Alle in dieser Hausarbeit verwendeten Grafiken wurden von mir selbst erstellt._

# Inhaltsverzeichniss

0. Inhaltsverzeichniss
1. Einleitung
2. Hintergrund und Rahmenbedingungen des Projekts
    1. Beschreibung der persönlichen Blog-Webseite
    2. Probleme und Herausforderungen im bestehenden Code
3. Qualitätssichernde Maßnahmen
    1. QTK (Qualität, Kosten, Zeit)
    2. Magisches Dreieck im Fall des Projektes
    3. Bedeutung von Qualitätssicherung im Softwareprojekt
4. Analyse der bestehenden Situation
    1. Mängel in der Architektur und im Code
    2. Fehlende Tests und Testverfahren
    3. Auswirkungen auf die Benutzererfahrung
5. Verbesserungsvorschläge und Lösungsansätze
    1. Anwendung des Repository Patterns
    2. Aufteilung des Codes für bessere Wartbarkeit und Erweiterbarkeit
    3. Einführung von automatisierten Tests
    4. Risikoanalyse und Identifizierung potenzieller Probleme
6. Umsetzung der Verbesserungen
    1. Implementierung des Repository Patterns
    2. Code-Refactoring und Strukturierung der Django-Modelle und Views
    3. Einführung von automatisierten Tests
    4. Identifizierung und Umgang mit Risiken
7. Bewertung der Verbesserungen
    1. Auswirkungen auf die Qualität
    2. Auswirkungen auf das Magische Dreieck des Projektes
    3. Erfüllung der QTK-Anforderungen
8. Fazit
9. Ausblick und Empfehlungen für zukünftige Projekte


# Einleitung

Softwarequalität spielt eine entscheidende Rolle in unserer heutigen digitalen Welt, in der Softwareanwendungen in nahezu allen Bereichen unseres Lebens präsent sind. Ob in der Gesundheitsversorgung, im Bankwesen, im Transportwesen oder in der Unterhaltungsindustrie - die Qualität der Software beeinflusst direkt die Effizienz, Zuverlässigkeit und Sicherheit der Systeme, mit denen wir täglich interagieren. In diesem Zusammenhang ist es von größter Bedeutung, das Software-Qualitätsmanagement (SQM) zu bewerten und zu optimieren, um den Nutzern die bestmögliche Erfahrung zu bieten und gleichzeitig die Entwicklungsprozesse zu optimieren.

<div style="text-align:center">
  <img style="max-height: 200px" src="banner.png" alt="Peek-website"/>
</div>

Diese Hausarbeit konzentriert sich auf die Analyse und Bewertung des SQM anhand eines praktischen Fallbeispiels. Wir werden uns mit der Entwicklung einer persönlichen Blog-Webseite befassen, bei der wichtige Aspekte des Software-Qualitätsmanagements vernachlässigt wurden. Der Code wurde ohne Berücksichtigung von Design Patterns oder einer guten Architektur entwickelt, was zu Wartungsproblemen und Schwierigkeiten bei der Erweiterung führte. Es wurden keine Tests verwendet, was die Qualität und Benutzererfahrung beeinträchtigen könnte. Unser Ziel ist es, diese Situation zu analysieren, Optimierungsmöglichkeiten zu identifizieren und konkrete Maßnahmen zur Verbesserung der Softwarequalität vorzuschlagen.

Im Verlauf dieser Arbeit werden wir verschiedene Aspekte des SQM behandeln. Zunächst werden wir die Hintergrundinformationen und Rahmenbedingungen des Projekts präsentieren, um ein Verständnis für die persönliche Blog-Webseite und die damit verbundenen Probleme zu schaffen. Anschließend werden wir die qualitätssichernden Maßnahmen im Softwareprojekt diskutieren und die Bedeutung von Qualitätssicherung beleuchten. In der Analyse der bestehenden Situation werden wir spezifische Mängel in der Architektur und im Code, das Fehlen von Tests sowie die Auswirkungen auf die Benutzererfahrung untersuchen. Darauf aufbauend werden wir Verbesserungsvorschläge und Lösungsansätze präsentieren, wie die Anwendung des Repository Patterns, die Aufteilung des Codes, die Einführung von automatisierten Tests und die Identifizierung potenzieller Risiken. Schließlich werden wir die Umsetzung der Verbesserungen betrachten, ihre Auswirkungen auf die Qualität und das magische Dreieck des Projekts bewerten und abschließend ein Fazit ziehen sowie Empfehlungen für zukünftige Projekte geben.

Diese Arbeit bietet eine umfassende Betrachtung des SQM anhand eines praxisnahen Beispiels und stellt konkrete Maßnahmen zur Optimierung vor. Durch die Analyse dieses Fallbeispiels werden wir die Bedeutung von Softwarequalität erkennen und lernen, wie wir durch gezielte Verbesserungen eine bessere Benutzererfahrung und effizientere Entwicklungsprozesse erreichen können.

# Hintergrund und Rahmenbedingungen des Projekts

## Beschreibung der persönlichen Blog-Webseite

Meine persönliche Blog-Webseite ([mkrabs.de](https://mkrabs.de)), die im Rahmen dieses Fallbeispiels analysiert wird, dient als Plattform für einen Blogger, um seine Gedanken, Erfahrungen und Interessen mit anderen Nutzern zu teilen. Die Webseite ermöglicht es dem Blogger, Artikel zu verfassen, diese zu veröffentlichen und von den Lesern kommentieren zu lassen. Darüber hinaus bietet die Webseite Funktionen zur Verwaltung der Benutzerprofile und zur Kategorisierung der Artikel.

## Probleme und Herausforderungen im bestehenden Code

Bei der Entwicklung der persönlichen Blog-Webseite wurden einige grundlegende Softwarequalitätsprinzipien nicht beachtet. Der Code wurde innerhalb wenigen Wochen erstellt, ohne die Verwendung von Design Patterns oder eine gutachtung für Architektur. Als Ergebnis wurden alle Django-Modelle in einer einzigen Datei zusammengefasst, ebenso wie alle Views. Dies führte zu einer unübersichtlichen Codebasis, die schwer zu warten und zu erweitern war. Bei Änderungen oder Erweiterungen mussten große Teile des Codes neu geschrieben werden, anstatt bestehende Komponenten wiederzuverwenden.

Ein weiteres Problem war das Fehlen von Tests und nicht existierende Testverfahren / Test Driven Developement. Es wurden keine automatisierten Tests implementiert, was zu manuellen und unübersichtlichen Prozessen führte. Dadurch war es schwierig, die Funktionalität der Webseite zu überprüfen und sicherzustellen, dass sie wie erwartet funktioniert. Dies stellte ein Risiko für die Qualität der Software dar und beeinträchtigte möglicherweise die Benutzererfahrung.

Um die Softwarequalität zu verbessern, wurden erste Maßnahmen ergriffen, indem das Repository Pattern angewendet wurde. Dadurch wurde der Code aufgeteilt und die Erweiterbarkeit erleichtert. Allerdings führte dies auch zu einer erhöhten Menge an (instant legacy) Boilerplate-Code, der gewartet und gepflegt werden muss.

In dieser Arbeit werden wir uns eingehend mit den bestehenden Problemen und Herausforderungen im Code der persönlichen Blog-Webseite befassen. Wir werden analysieren, wie diese Probleme die Softwarequalität beeinflussen und welche Schritte unternommen werden können, um sie zu beheben.

# Qualitätssichernde Maßnahmen

## QTK (Qualität, Kosten, Zeit)

Das QTK-Dreieck, bestehend aus Qualität, Kosten und Zeit, ist ein grundlegendes Konzept im Projektmanagement. Es beschreibt die enge Verknüpfung dieser drei Faktoren und verdeutlicht, dass Veränderungen an einem dieser Faktoren Auswirkungen auf die anderen haben können. Im Kontext des Software-Qualitätsmanagements ist es wichtig, ein ausgewogenes Verhältnis zwischen Qualität, Kosten und Zeit zu finden.

<div style="text-align:center">
  <img style="max-height: 200px" src="QTK.drawio.png" alt="qtk-kreis"/>
</div>

Qualitätssicherung ist ein wesentlicher Bestandteil des SQM und trägt dazu bei, die Softwarequalität zu verbessern. Allerdings kann die Implementierung qualitätssichernder Maßnahmen zusätzliche Kosten verursachen und den Zeitplan beeinflussen. Es ist daher wichtig, die Auswirkungen auf das QTK-Dreieck zu berücksichtigen und die richtige Balance zu finden, um die gewünschte Qualität zu erreichen, während gleichzeitig die Kosten und der Zeitrahmen eingehalten werden.

## Magisches Dreieck im Fall des Projektes

Im vorliegenden Fallbeispiel der persönlichen Blog-Webseite können wir das magische Dreieck - bestehend aus Funktionalität, Qualität und Zeit - anwenden, um die Herausforderungen und Ziele des Projekts zu analysieren.



<div style="text-align:center">
  <img style="max-height: 200px" src="MD.drawio.png" alt="qtk-kreis"/>
</div>

Die Funktionalität der Webseite besteht darin, dem Blogger die Möglichkeit zu geben, Artikel zu verfassen, zu veröffentlichen und Kommentare der Leser zu erhalten. Diese Kernfunktionalität sollte reibungslos funktionieren und eine gute Benutzererfahrung bieten.

Die Qualität der Webseite bezieht sich auf verschiedene Aspekte wie die Zuverlässigkeit, Wartbarkeit, Erweiterbarkeit und Benutzerfreundlichkeit. Im aktuellen Zustand der Webseite sind Mängel in der Architektur, im Code und das Fehlen von Tests festzustellen. Die Verbesserung der Qualität ist daher ein Hauptziel des Projekts.

Die Zeit ist ein weiterer wichtiger Faktor. Die Webseite wurde in kürzester Zeit entwickelt, was zu einer schnellen Bereitstellung führte. Allerdings führte der Mangel an Qualitätssicherung zu Problemen bei der Wartung und Erweiterung des Codes. Das Projekt erfordert daher eine zeitliche Planung, um die erforderlichen Verbesserungen durchzuführen, ohne den laufenden Betrieb zu beeinträchtigen.

## Bedeutung von Qualitätssicherung im Softwareprojekt

Die Bedeutung von Qualitätssicherung im Softwareprojekt kann nicht genug betont werden. Durch gezielte Qualitätssicherungsmaßnahmen können Mängel und Probleme frühzeitig erkannt und behoben werden. Dadurch wird die Software stabiler, zuverlässiger und fehlerfreier. Eine gute Qualitätssicherung trägt auch zur Benutzerzufriedenheit bei, da die Software die erwartete Funktionalität bietet und eine angenehme Benutzererfahrung gewährleistet.

Darüber hinaus ermöglicht eine effektive Qualitätssicherung eine bessere Wartbarkeit und Erweiterbarkeit des Codes. Durch die Implementierung von Tests und Testverfahren können Änderungen oder Erweiterungen mit größerer Zuversicht durchgeführt werden, da die Auswirkungen auf die bestehende Funktionalität überprüft werden können.

Im Fall des Projekts der persönlichen Blog-Webseite ist die Qualitätssicherung von entscheidender Bedeutung, um die Mängel in der Architektur, im Code und bei den Tests zu beheben. Durch geeignete Qualitätssicherungsmaßnahmen können die Softwarequalität verbessert, die Benutzererfahrung optimiert und zukünftige Wartungs- und Erweiterungsarbeiten erleichtert werden.

# Analyse der bestehenden Situation

> _Hinweis:_ Das gesamte Projekt, einschließlich des Quellcodes, der Verbesserungen und der umgesetzten Maßnahmen, ist auf GitHub unter dem folgenden Link einsehbar: [github.com/Mkrabs/Blog](https://github.com/Mkrabs/Blog). Dort finden Sie eine detaillierte Aufzeichnung aller Änderungen und eine vollständige [Dokumentation](https://github.com/MKrabs/Blog/blob/main/docs/ASE_is_fun/structure.md) des Projekts, im Rahmen der Vorlseung Andvamced Software Engineering.
>
> Um jeden Refactoring-Schritt oder jede Änderung zu veranschaulichen, werden wir Beispiele aus dem Code-Basisstand mit dem Commit-Hash [#`5f0837`](https://github.com/MKrabs/Blog/tree/5f0837dd26a84c0e7e2687a66cbd54fd4254c209) verwenden. Dieser Commit repräsentiert den Code, wie er vor Beginn dieses Projekts existierte.

## Mängel in der Architektur und im Code

Bei der Analyse der bestehenden Situation der persönlichen Blog-Webseite lassen sich verschiedene Mängel in der Architektur und im Code identifizieren. Durch das Fehlen von Design Patterns und einer guten Architektur wurde der Code unstrukturiert und unübersichtlich. Alle Django-Modelle und Views wurden in einer einzigen Datei zusammengefasst, was zu einer monolithischen Codebasis führte. Dies erschwert die Wartung und Erweiterung der Webseite, da Änderungen an einer Komponente zu umfangreichen Anpassungen im gesamten Code führen können. Die mangelnde Modularität und Trennung der Verantwortlichkeiten erschwert auch die Zusammenarbeit im Entwicklungsteam.

```
blog/
├── migrations
│   └── ...
├── admin.py
├── apps.py
├── forms.py
├── models.py (127 lines)
├── tests.py  (  0 lines)
└── views.py  (250 lines)
```

## Fehlende Tests und Testverfahren

Ein weiterer wesentlicher Mangel in der bestehenden Situation ist das Fehlen von Tests und Testverfahren. Es wurden keine automatisierten Tests implementiert, um die Funktionalität der Webseite zu überprüfen. Dies führt zu einer unsicheren Codebasis, da mögliche Fehler und Probleme nicht frühzeitig erkannt werden können. Die Durchführung manueller Tests ist zeitaufwändig und nicht nachhaltig, insbesondere bei wachsender Komplexität des Codes. Ohne geeignete Testverfahren besteht das Risiko, dass Fehler in die Produktionsumgebung gelangen und die Benutzererfahrung beeinträchtigen.

## Auswirkungen auf die Benutzererfahrung

Die Mängel in der Architektur, im Code und das Fehlen von Tests haben direkte Auswirkungen auf die Benutzererfahrung der persönlichen Blog-Webseite. Durch die unstrukturierte Codebasis und die fehlende Modularität kann es zu Performance-Problemen, inkonsistentem Verhalten und unerwarteten Fehlern kommen. Die Webseite könnte instabil sein und unter Last zusammenbrechen. Darüber hinaus können Änderungen oder Erweiterungen der Webseite nur langsam und mit erheblichem Aufwand umgesetzt werden, was die Weiterentwicklung und Anpassung an die Bedürfnisse der Benutzer einschränkt. Die mangelnde Qualitätssicherung führt zu einer unsicheren Benutzererfahrung, da Fehler und Probleme nicht proaktiv erkannt und behoben werden.

In der nächsten Phase werden wir Verbesserungsvorschläge und Lösungsansätze erarbeiten, um diese Mängel zu beheben und die Softwarequalität der persönlichen Blog-Webseite zu verbessern.


# Verbesserungsvorschläge und Lösungsansätze

Um die bestehenden Mängel in der Architektur, im Code und bei den Tests der persönlichen Blog-Webseite zu beheben, sind folgende Verbesserungsvorschläge und Lösungsansätze empfehlenswert:

## Anwendung des Repository Patterns

Durch die Anwendung des Repository Patterns kann der Code der Webseite besser strukturiert und modularer gestaltet werden. Dieses Entwurfsmuster ermöglicht es, Datenzugriffslogik von der Geschäftslogik zu trennen und die Datenbankinteraktion in spezialisierte Repository-Klassen auszulagern. Dadurch wird der Code besser lesbar, wartbar und erweiterbar. Die Verwendung des Repository Patterns erleichtert auch die Implementierung von Tests, da Datenbankzugriffe abstrahiert werden können.

## Aufteilung des Codes für bessere Wartbarkeit und Erweiterbarkeit

Um die Wartbarkeit und Erweiterbarkeit des Codes zu verbessern, sollte der aktuelle monolithische Ansatz aufgebrochen werden. Der Code der persönlichen Blog-Webseite kann in kleinere, überschaubare Module und Komponenten aufgeteilt werden. Dies ermöglicht eine klare Trennung der Verantwortlichkeiten und erleichtert Änderungen und Erweiterungen. Durch die Verwendung von Django Apps können verschiedene Funktionalitäten und Module isoliert voneinander entwickelt und gewartet werden.

## Einführung von automatisierten Tests

Die Einführung automatisierter Tests ist entscheidend, um die Qualität der persönlichen Blog-Webseite sicherzustellen. Es sollten geeignete Testverfahren entwickelt werden, um die Funktionalität der Webseite zu überprüfen, einschließlich der Hauptfunktionen wie Artikelveröffentlichung, Kommentarfunktion und Benutzerverwaltung. Durch die Implementierung von Unittests, Integrationstests und ggf. Akzeptanztests können Fehler frühzeitig erkannt und behoben werden. Die automatisierten Tests ermöglichen eine regelmäßige Überprüfung der Webseite und bieten Sicherheit bei zukünftigen Änderungen und Erweiterungen.

## Risikoanalyse und Identifizierung potenzieller Probleme

Es ist wichtig, eine Risikoanalyse durchzuführen, um potenzielle Probleme und Risiken zu identifizieren, die die Softwarequalität der Webseite beeinträchtigen könnten. Dabei sollten potenzielle Schwachstellen in der Architektur, im Code und bei den Tests berücksichtigt werden. Durch die Identifizierung von Risiken können gezielte Maßnahmen ergriffen werden, um diese zu minimieren oder zu vermeiden. Dies könnte beispielsweise die Implementierung von Sicherheitsmechanismen, Fehlerbehandlungsstrategien oder Überwachungssystemen umfassen.

Durch die Umsetzung dieser Verbesserungsvorschläge und Lösungsansätze wird angestrebt, die Softwarequalität der persönlichen Blog-Webseite deutlich zu verbessern und die Probleme in der bestehenden Situation zu beheben. In der nächsten Phase werden wir die konkrete Umsetzung dieser Verbesserungen und deren Auswirkungen auf die Qualität und das Projektdreieck analysieren.


# Umsetzung der Verbesserungen

## Implementierung des Repository Patterns

Um das Repository Pattern in der persönlichen Blog-Webseite einzuführen, müssen entsprechende Änderungen am Code vorgenommen werden. Zunächst sollten separate Repository-Klassen erstellt werden, die für den Datenzugriff zuständig sind. Diese Klassen abstrahieren die Datenbankinteraktionen und bieten eine Schnittstelle für die Geschäftslogik. Durch die Verwendung des Repository Patterns wird der Code besser strukturiert, lesbarer und einfacher zu testen. Die Implementierung des Repository Patterns erfordert möglicherweise auch Anpassungen in den vorhandenen Django-Modellen und Views.

```
blog/
├── application
│   ├── forms
│   │   ├── profile_form_service.py
│   │   └── user_form_service.py
│   ├── comment_service.py
│   ├── like_service.py
│   ├── post_service.py
│   ├── profile_service.py
│   └── user_service.py
├── domain
│   ├── entities
│   │   ├── comment.py
│   │   ├── like.py
│   │   ├── post.py
│   │   ├── profile.py
│   │   ├── report.py
│   │   └── tag.py
│   └── repository
│       ├── comment_repository.py
│       ├── like_repository.py
│       ├── post_repository.py
│       ├── profile_repository.py
│       ├── report_repository.py
│       └── tag_repository.py
├── infrastructure
│   ├── repositories
│   │   ├── comment_repository.py
│   │   ├── like_repository.py
│   │   ├── post_repository.py
│   │   ├── profile_repository.py
│   │   ├── report_repository.py
│   │   └── tag_repository.py
│   └── serializers
│       ├── comment_serializer.py
│       ├── post_serializer.py
│       └── profile_serializer.py
├── migrations
│   └── ...
├── presentation
│   ├── api
│   │   ├── post_api.py
│   │   ├── profile_api.py
│   │   └── urls.py
│   ├── static
│   │   ├── css ...
│   │   ├── img ...
│   │   └── js  ...
│   ├── templates
│   │   ├── blog
│   │   │   ├── 404.html
│   │   │   ├── base.html
│   │   │   ├── comment.html
│   │   │   ├── comment_menu.html
│   │   │   ├── footer.html
│   │   │   ├── index.html
│   │   │   ├── markdownHelp.html
│   │   │   ├── pagination.html
│   │   │   ├── post.html
│   │   │   ├── profile_picture.html
│   │   │   ├── user_history.html
│   │   │   ├── userprofile.html
│   │   │   └── userprofile_short.html
│   │   └── registration
│   │       ├── login.html
│   │       └── register.html
│   └── views
│       ├── comment_endpoint.py
│       ├── homepage_view.py
│       ├── like_endpoint.py
│       ├── post_view.py
│       ├── profile_view.py
│       ├── registration_view.py
│       └── urls.py
├── test
│   ├── test_comment_repository.py
│   ├── test_comment_serializer.py
│   ├── test_post_api.py
│   ├── test_post_repository_application.py
│   ├── test_post_repository.py
│   └── test_profile_api.py
├── admin.py
└── apps.py
```

## Code-Refactoring und Strukturierung der Django-Modelle und Views

Ein wichtiger Schritt zur Verbesserung der Wartbarkeit und Erweiterbarkeit besteht darin, den Code der persönlichen Blog-Webseite zu refaktorieren und neu zu strukturieren. Die Django-Modelle und Views sollten in separate Dateien aufgeteilt werden, um die Verantwortlichkeiten klarer zu trennen. Jedes Modell und jede View sollte nur eine spezifische Aufgabe erfüllen. Durch die Aufteilung des Codes wird der Entwicklungsprozess effizienter und die Zusammenarbeit im Team erleichtert. Zusätzlich sollten bewährte Vorgehensweisen und Design Patterns bei der Strukturierung des Codes berücksichtigt werden.

## Einführung von automatisierten Tests

Die Einführung automatisierter Tests ist ein entscheidender Schritt, um die Qualität der persönlichen Blog-Webseite zu verbessern. Es sollten Unittests, Integrationstests und ggf. Akzeptanztests entwickelt und implementiert werden. Die Tests sollten alle wichtigen Funktionalitäten und Szenarien der Webseite abdecken. Durch regelmäßige Testläufe können potenzielle Fehler und Probleme frühzeitig erkannt und behoben werden. Die automatisierten Tests stellen sicher, dass die Webseite korrekt funktioniert und keine Regressionen auftreten, wenn Änderungen oder Erweiterungen vorgenommen werden.

```
# https://github.com/MKrabs/Blog/blob/main/blog/test/test_post_repository.py#LL37C1-L42C47

def test_get_count_by_author(self):
    for i in range(3):
        self.create_post(title=f"Title {i}")

    posts_by_testuser = self.post_repo.get_count_by_author(user_id=self.user.id)
    self.assertEqual(posts_by_testuser, 3)
```

## Identifizierung und Umgang mit Risiken

Es ist wichtig, eine gründliche Risikoanalyse durchzuführen und potenzielle Probleme zu identifizieren, die die Softwarequalität der Webseite beeinträchtigen könnten. Hierbei sollten potenzielle Schwachstellen in der Architektur, im Code und bei den Tests berücksichtigt werden. Nach der Identifizierung der Risiken sollten geeignete Maßnahmen ergriffen werden, um diese zu minimieren oder zu vermeiden. Dies könnte die Implementierung von Sicherheitsmechanismen, Fehlerbehandlungsstrategien oder Überwachungssystemen umfassen. Durch den proaktiven Umgang mit Risiken wird die Stabilität und Zuverlässigkeit der Webseite verbessert.

Die Umsetzung dieser Verbesserungen erfordert eine sorgfältige Planung, Zusammenarbeit im Entwicklungsteam und die Anwendung bewährter Praktiken im Software-Qualitätsmanagement. In der nächsten Phase werden wir die Auswirkungen dieser Verbesserungen auf die Qualität der Webseite, das Projektdreieck und die QTK-Anforderungen bewerten.

# Bewertung der Verbesserungen

## Auswirkungen auf die Qualität

Die umgesetzten Verbesserungen haben signifikante Auswirkungen auf die Qualität der persönlichen Blog-Webseite. Durch die Anwendung des Repository Patterns wird der Code besser strukturiert und modularisiert, was zu einer verbesserten Wartbarkeit und Erweiterbarkeit führt. Die klare Trennung der Verantwortlichkeiten und die Abstraktion der Datenbankinteraktionen erleichtern auch die Implementierung von automatisierten Tests. Die Einführung automatisierter Tests ermöglicht eine regelmäßige Überprüfung der Funktionalität und hilft dabei, potenzielle Fehler frühzeitig zu erkennen. Durch den identifizierten Risiken und deren gezielte Behandlung wird die Stabilität und Zuverlässigkeit der Webseite erhöht. Insgesamt führen die Verbesserungen zu einer höheren Codequalität, besseren Testbarkeit und einer insgesamt besseren Benutzererfahrung.

## Auswirkungen auf das Magische Dreieck des Projektes

Das Magische Dreieck des Projektes besteht aus den drei Faktoren Qualität, Kosten und Zeit. Die Verbesserungen haben direkte Auswirkungen auf alle drei Faktoren. Durch die Steigerung der Qualität werden potenzielle Fehler und Probleme reduziert, was langfristig zu Kosteneinsparungen führt. Die Implementierung des Repository Patterns und die Strukturierung des Codes verbessern die Wartbarkeit und Erweiterbarkeit, was die zukünftige Entwicklung beschleunigen kann. Die Einführung automatisierter Tests ermöglicht eine effizientere Fehlererkennung und -behebung, was wiederum die Zeit für Fehlerkorrekturen verringert. Obwohl die Umsetzung der Verbesserungen zunächst einen zusätzlichen Aufwand erfordert, führen sie langfristig zu einem ausgewogeneren Magischen Dreieck, da die Qualität gesteigert und die Kosten und die Zeit für Fehlerbehebung reduziert werden.

## Erfüllung der QTK-Anforderungen

Die Verbesserungen tragen zur Erfüllung der QTK-Anforderungen bei:

- **Qualitätsmanagement** (QM): Durch die Einführung des Repository Patterns, die Strukturierung des Codes und die Implementierung von automatisierten Tests wird die Qualität der persönlichen Blog-Webseite signifikant verbessert. Die Verbesserungen ermöglichen eine bessere Wartbarkeit, Erweiterbarkeit und eine höhere Codequalität insgesamt.

- **Kostenmanagement** (KM): Obwohl die Umsetzung der Verbesserungen zunächst einen zusätzlichen Aufwand erfordert, führt sie langfristig zu Kosteneinsparungen. Durch die Reduzierung von potenziellen Fehlern und Problemen werden die Kosten für Fehlerbehebung und Wartung der Webseite verringert.

- **Terminlicher Koordination** (TM): Die Verbesserungen haben Auswirkungen auf die Entwicklungszeit. Die Anwendung des Repository Patterns, die Strukturierung des Codes und die Einführung automatisierter Tests können die zukünftige Entwicklung beschleunigen. Darüber hinaus reduzieren sie die Zeit für Fehlerbehebung, da Fehler frühzeitig erkannt und behoben werden.

Insgesamt erfüllen die umgesetzten Verbesserungen die QTK-Anforderungen, indem sie die Qualität steigern, potenzielle Kosten senken und die Entwicklungs- und Fehlerbehebungszeit optimieren.

---

# Fazit

In diesem Hausarbeit wurde das Thema Software-Qualitätsmanagement (SQM) anhand eines praktischen Fallbeispiels einer persönlichen Blog-Webseite behandelt. Zunächst wurden die Hintergrundinformationen und Rahmenbedingungen des Projekts erläutert, einschließlich der Beschreibung der Webseite und der identifizierten Probleme im bestehenden Code. Anschließend wurden qualitätssichernde Maßnahmen und deren Bedeutung im Softwareprojekt diskutiert.

Im Rahmen der Analyse der bestehenden Situation wurden Mängel in der Architektur und im Code, das Fehlen von Tests und Testverfahren sowie die Auswirkungen auf die Benutzererfahrung aufgezeigt. Basierend auf diesen Erkenntnissen wurden konkrete Verbesserungsvorschläge und Lösungsansätze präsentiert, darunter die Anwendung des Repository Patterns, die Aufteilung des Codes für bessere Wartbarkeit und Erweiterbarkeit, die Einführung von automatisierten Tests sowie die Risikoanalyse und Identifizierung potenzieller Probleme.

In der Umsetzung der Verbesserungen wurden die einzelnen Maßnahmen detailliert beschrieben, einschließlich der Implementierung des Repository Patterns, des Code-Refactorings und der Strukturierung der Django-Modelle und Views, der Einführung automatisierter Tests sowie der Identifizierung und des Umgangs mit Risiken.

Die Bewertung der Verbesserungen ergab positive Auswirkungen auf die Qualität der Webseite, das Magische Dreieck des Projektes (Qualität, Kosten, Zeit) und die Erfüllung der QTK-Anforderungen. Die Qualität wurde durch die bessere Code-Struktur, die Einführung von Tests und die Behandlung von Risiken gesteigert. Das Magische Dreieck wurde ausgewogener, da potenzielle Kosten für Fehlerbehebung reduziert und die Entwicklungszeit optimiert wurden. Die Verbesserungen erfüllen die Anforderungen an Qualität, Kosten und Zeit im Rahmen des Projekts.

# Ausblick und Empfehlungen für zukünftige Projekte

Abschließend bieten sich verschiedene Möglichkeiten für zukünftige Projekte im Bereich des Software-Qualitätsmanagements. Es ist ratsam, von Anfang an auf eine solide Architektur und eine gute Code-Struktur zu achten, um spätere Probleme zu vermeiden. Die Verwendung bewährter Design Patterns und Softwarearchitekturprinzipien kann dazu beitragen, die Wartbarkeit und Erweiterbarkeit des Codes zu verbessern.

Die Einführung von automatisierten Tests sollte als integraler Bestandteil des Entwicklungsprozesses betrachtet werden. Durch regelmäßiges Testen können potenzielle Fehler frühzeitig erkannt und behoben werden, was die Qualität der Software erhöht. Es ist auch wichtig, Risikoanalyse und Risikomanagement in den Entwicklungsprozess einzubeziehen, um potenzielle Probleme zu identifizieren und geeignete Maßnahmen zu ergreifen.

Zukünftige Projekte sollten auch die Bedeutung der Benutzererfahrung berücksichtigen. Eine benutzerfreundliche und intuitiv bedienbare Oberfläche trägt maßgeblich zum Erfolg einer Software bei. Daher sollten User Experience (UX) und User Interface (UI) Designprinzipien in den Entwicklungsprozess integriert werden.

Abschließend lässt sich sagen, dass das Software-Qualitätsmanagement einen wesentlichen Einfluss auf den Erfolg eines Projekts hat. Durch die Anwendung qualitätssichernder Maßnahmen, die Analyse und Optimierung bestehender Systeme und die Berücksichtigung von Best Practices können die Qualität der Software verbessert, Kosten gesenkt und die Effizienz gesteigert werden.

---

Vielen Dank fürs Lesen!  
\- Marc
