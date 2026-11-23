---
title: Übersicht User Interface
description: Übersicht User Interface (UI) von Obtainium
---

# UI-Übersicht

Die Apps-Seite ist der Hauptbildschirm. „App hinzufügen“ und die Einstellungen werden von dort über die Hinzufügen-Schaltfläche bzw. das Zahnrad-Symbol in der oberen Leiste geöffnet. Auf Tablets und Android TV können App-Liste und App-Details nebeneinander angezeigt werden.

## Apps-Seite

Dies ist der Hauptbildschirm; er enthält eine Liste der Apps, die von Obtainium überwacht werden, und liefert die grundlegenden Informationen zu jeder App.

Auf dieser Seite können Sie mit den Schaltflächen am unteren Rand des Bildschirms verschiedene Vorgänge für mehrere Apps auf einmal durchführen. Dies kann nach Auswahl einer oder mehrerer Apps erfolgen, entweder durch langes Drücken, oder über die Schaltfläche „Alle auswählen“, um in den Mehrfachauswahlmodus zu gelangen. Zu den verfügbaren Batch-Vorgängen gehören Aktualisieren, Installieren, Löschen, Kategorisieren, Anheften/Lösen, Teilen von App-URLs oder Exportlinks und Markieren ausgewählter Apps als aktualisiert.

Apps können Kategorien zugewiesen werden, die als farbige Balken am linken Rand jedes App-Eintrags angezeigt werden. Wenn „Gruppieren nach“ unter Einstellungen → Erscheinungsbild aktiviert ist, wird die App-Liste nach Kategorie oder Quelle in erweiterbare Abschnitte unterteilt.

In der Detailansicht einer einzelnen App können Sie die Versionsinformationen, das Veröffentlichungsdatum, das Änderungsprotokoll und die APK-Signaturzertifikats-Hashes der App einsehen (lang drücken zum Kopieren). Wenn eine Umbenennung des Repositorys erkannt wird, erscheint ein Hinweis mit der Option, die URL der App automatisch zu aktualisieren.

Sie können auch Apps suchen und nach bestimmten Apps filtern, indem Sie auf die Schaltfläche 🔍 klicken. Auf diese Weise können Sie nur die Apps anzeigen, die bestimmte Kriterien erfüllen (z. B. installiert/nicht installiert, aktuell/veraltet, Quellseite, Kategorie usw.).

## Seite „App hinzufügen“ {#add-app-page}

Auf dieser Seite können Sie eine Anwendung anhand ihrer Quell-URL hinzufügen.

Bei der Eingabe der Quell-URL erkennt Obtainium automatisch, welche [Quellenlogik](app_tracking.de.md/#grundlagen) verwendet werden soll, und zeigt die entsprechenden Optionen an. Wenn eine URL keiner unterstützten Quelle entspricht, wird die „[HTML](sources.de.md/#html)“-Quelle als Standard ausgewählt. Diese Quelle ist ein allgemeiner Fallback, der in einigen Fällen funktionieren kann. Wenn Sie der Meinung sind, dass Obtainium die falsche Wahl getroffen hat, können Sie den zu verwendenden Quellentyp mithilfe des Dropdown-Menüs manuell festlegen.

Bei den meisten Quellen müssen Sie die URL nicht genau angeben. Die GitHub-Quelle akzeptiert beispielsweise jede GitHub-URL, die die Basis-URL des Projektarchivs enthält (z.B. `https://github.com/ImranR98/Obtainium/releases/latest` wird automatisch auf `https://github.com/ImranR98/Obtainium` gekürzt). Ihre URL muss jedoch präziser sein in zwei Situationen:

1. Bei Verwendung der HTML-Quelle
      - Zum Beispiel ist die Tor Android APK unter `https://www.torproject.org/download/` zu finden, also würde die Eingabe von `https://www.torproject.org/` nicht funktionieren.
2. Bei der manuellen Auswahl einer Quelle (die die HTML-Fallback-Auswahl von Obtainium außer Kraft setzt)

Auf dieser Seite können Sie auch nach Apps in allen Quellen suchen, die diese Funktion unterstützen. Nur weil eine App in den Suchergebnissen auftaucht, heißt das nicht, dass sie erfolgreich hinzugefügt wird – sie muss noch alle anderen Kriterien erfüllen.

Schließlich werden auf dieser Seite alle unterstützten Quellen aufgelistet, zusammen mit zusätzlichen Informationen, z. B. ob eine Quelle durchsuchbar ist.

## Import/Export-Seite

Import/Export ist über die Einstellungen erreichbar. Dort können Sie Ihre Obtainium-Daten exportieren, damit sie später importiert werden können. Sie können auch automatische Exporte aktivieren, die immer dann erfolgen, wenn sich Daten ändern, und festlegen, ob Geheimnisse (wie API-Token) in den Export einbezogen werden sollen.

Auf dieser Seite finden Sie auch verschiedene andere Möglichkeiten, eine große Anzahl von Anwendungen zu importieren:

- **Obtainium-Import**: Eine Obtainium-Exportdatei wiederherstellen.
- **URL-Listen-Import**: Fügen Sie eine Liste von App-URLs ein oder laden Sie eine Datei, um sie alle auf einmal zu importieren.
- **Massenquellen-Importe**: Importieren Sie Apps aus Bulk-Quellen wie den GitHub-Sterne-Repositories eines Benutzers.

Die quellenübergreifende App-Suche befindet sich auf der Seite „App hinzufügen“ und nicht unter Import/Export.

## Einstellungen

Diese Seite bietet verschiedene Einstellungen für die Benutzeroberfläche und das Verhalten, organisiert in Unterseiten:

- **Updates**: Hintergrundaktualisierungsintervall und manuelle Prüfungen, stille Installationen im Hintergrund, WLAN-/Ladeeinschränkungen, Überprüfung beim Start, parallele Downloads, Zertifikat-Pinning, Installationsmethoden wie Shizuku und Root (mit der Option, sich als Google Play auszugeben) und „Verified Apps“-Integration zur Überprüfung von APKs vor der Installation.
- **Quellspezifisch**: Anmeldedaten für bestimmte Quellen (z. B. GitHub/GitLab persönliche Zugriffstoken) und andere quellspezifische Konfigurationseinstellungen.
- **Erscheinungsbild**: Design (System/Hell/Dunkel), schwarzes Design, Material You dynamische Farben, benutzerdefinierte Akzentfarbe, Sortierreihenfolge, Sprachüberschreibung, Systemschriftart, In-App-WebView, Gruppierung nach Kategorie oder Quelle, Dichte der App-Liste und Aktionsleiste.
- **Kategorien**: Kategorien werden auf der Seite „Erscheinungsbild“ und in der App-Detailansicht verwaltet.

Der Abschnitt „Über“ der Einstellungsseite enthält Links zum App-Quellcode, zu diesem Wiki und zu den App-Protokollen. Der Link zu den von der Gemeinschaft erstellten App-Konfigurationen befindet sich auf der Seite „App hinzufügen“.
