---
title: App-Quellen
description: Informationen spezifisch für einzelne Quellen
---

# App-Quellen

Die Art und Weise, wie eine App hinzugefügt, auf Aktualisierungen geprüft und installiert wird, hängt von der Quelle und den vom Benutzer für diese App konfigurierten Einstellungen ab.

Die folgenden Optionen sind für alle Anwendungen unabhängig von der Quelle verfügbar:

- **Nur nachverfolgen**: Wenn Sie diese Option aktivieren, können Sie Aktualisierungsbenachrichtigungen für Apps erhalten, ohne zu versuchen, deren APKs herunterzuladen. Dies ist nützlich, um Updates für Apps zu verfolgen, für die keine APKs verfügbar sind oder die nicht einfach von Obtainium extrahiert werden können. Einige Quellen sind ausschließlich zum nachverfolgen – zum Beispiel [ApkMirror](#apkmirror). Beachten Sie, dass die [Versionserkennung](app_tracking.de.md/#version-detection) nicht für Apps funktioniert, die als „Nur nachverfolgen“ hinzugefügt wurden.
- **APKs nach regulären Ausdrücken filtern**: Wenn mehr als eine APK für eine App-Veröffentlichung verfügbar ist, wird der Benutzer aufgefordert, eine manuell auszuwählen. Dies ist nicht nur unbequem, sondern bedeutet auch, dass die App nicht im Hintergrund aktualisiert wird, auch wenn dies sonst möglich gewesen wäre. Mit dieser Option kann der Benutzer einen regulären Ausdruck angeben, mit dem die APKs herausgefiltert werden können, die nicht erwünscht sind (idealerweise bis hin zu einer Option).
- **Regulären Ausdruck invertieren (APKs nach regulärem Ausdruck filtern)**: Mit dieser Option, kann der reguläre Ausdruck invertiert werden, sodass im regulären Ausdruck die gesuchte APK angegeben werden kann.
- **Nach Möglichkeit versuchen, APKs nach CPU-Architektur zu filtern**: Mit dieser Option wird Obtainium angewiesen, automatisch alle APKs herauszufiltern, die nicht mit dem Gerät des Benutzers kompatibel zu sein scheinen. Die dafür verwendete Logik ist sehr einfach und basiert auf dem APK-Dateinamen. Sie ist daher nicht immer zuverlässig und der Benutzer muss in vielen Fällen immer noch selbst filtern.
- **App-Name**: Hier kann der Benutzer seinen eigenen Namen für die App angeben, anstatt den von Obtainium extrahierten zu nutzen.
- **Von Hintergrundaktualisierungen (falls aktiviert) ausschließen**: Mit dieser Option wird verhindert, dass die Anwendung im Hintergrund aktualisiert wird, selbst wenn Hintergrundaktualisierungen aktiviert sind und die Anwendung ansonsten alle Kriterien für eine Aktualisierung im Hintergrund erfüllt hätte.
- **Update-Benachrichtigungen vermeiden**: Mit dieser Option wird Obtainium angewiesen, den Benutzer nicht zu benachrichtigen, dass für diese App ein Update verfügbar ist oder dass sie im Hintergrund aktualisiert wurde.

Abgesehen davon hat jede Anwendung zusätzliche quellenspezifische Optionen. Die meisten dieser Optionen sind selbsterklärend und werden häufig aktualisiert, so dass sie in diesem Wiki nicht behandelt werden. Einige Quellen haben jedoch einzigartige Verhaltensweisen, die einer genaueren Erläuterung bedürfen und die im Folgenden behandelt werden.

## Derzeit unterstützte App-Quellen

- Open Source - Allgemein:
    - [GitHub](https://github.com/)
    - [GitLab](https://gitlab.com/)
    - [Codeberg](https://codeberg.org/) (Forgejo)
    - [F-Droid](https://f-droid.org/)
    - F-Droid-Repos von Drittanbietern
    - [IzzyOnDroid](https://android.izzysoft.de/)
    - [SourceHut](https://git.sr.ht/)
- Andere - Allgemein:
    - [APKPure](https://apkpure.net/)
    - [Aptoide](https://aptoide.com/)
    - [Uptodown](https://uptodown.com/)
    - [itch.io](https://itch.io/)
    - [Huawei AppGallery](https://appgallery.huawei.com/)
    - [Tencent App Store](https://sj.qq.com/)
    - [Vivo App Store](https://h5appstore.vivo.com.cn/)
    - [RuStore](https://rustore.ru/)
    - [Apk4Free](https://apk4free.net/)
    - [CoolAPK](https://www.coolapk.com/)
    - [Farsroid](https://farsroid.com/)
    - [LiteAPKs](https://liteapks.com/)
    - Jenkins Jobs
    - [APKMirror](https://apkmirror.com/) (Nur Nachverfolgen)
    - [RockMods](https://rockmods.net/) (Nur Nachverfolgen)
- App-Spezifisch:
    - [Telegram App](https://telegram.org)
    - [Neutron Code](https://neutroncode.com)
- Direkter APK-Link
- "HTML" (Fallback): Jede andere URL, die eine HTML-Seite mit Links zu APK-Dateien zurückgibt

## GitHub

GitHub legt eine Obergrenze für die Anzahl der API-Anfragen fest, die Sie innerhalb eines bestimmten Zeitraums stellen können. Da Obtainium die GitHub-API nutzt, um Versionsinformationen abzurufen, kann es zu einem "Rate Limit"-Fehler kommen, wenn Sie mehr als ein paar Dutzend GitHub-Apps haben. Sie können dies umgehen, indem Sie ein persönliches Zugriffstoken erhalten.

GitHub ermöglicht es Entwicklern auch, mehrere Versionen ihrer Anwendung zu hosten. Dies bedeutet in der Regel ältere Versionen derselben Anwendung, kann aber auch Vorabversionen, Varianten usw. umfassen - Obtainium bietet daher verschiedene Filter, mit denen Sie durch diese navigieren und genau die Versionen auswählen können, an denen Sie interessiert sind.

Einige zusätzliche Optionen haben ein weniger offensichtliches Verhalten:

- **Neuestes Tag überprüfen**: Wenn aktiviert, wählt Obtainium das Release aus, das der Entwickler als "neuestes" markiert hat, anstatt das chronologisch aktuellste. Normalerweise sind beide identisch, können aber in manchen Fällen abweichen. Dies geht zu Lasten eines zusätzlichen API-Aufrufs an GitHub (was schneller zu Ratelimits führt).
- **Sortiermethode**: Steuert, wie Versionen sortiert werden, wenn mehrere verfügbar sind. Standardmäßig werden Versionen nach Datum sortiert, aber die "intelligente Namens"-Sortierung versucht, die Versionsreihenfolge aus den Release-Titeln abzuleiten, und die "Namens"-Sortierung verwendet eine strenge alphanumerische Sortierung. Die Option "Intelligenter Name mit Datumsfallback" verwendet die namensbasierte Sortierung, fällt aber auf die datumsbasierte Sortierung zurück, wenn Namen nicht verglichen werden können.
- **Neuestes Asset-Datum als Veröffentlichungsdatum verwenden**: Wenn aktiviert, zeigt das Veröffentlichungsdatum das Datum des zuletzt hochgeladenen Assets innerhalb eines Releases anstelle des eigenen Veröffentlichungsdatums des Releases.
- **Auf Repository-Umbenennung prüfen**: Wenn aktiviert, erkennt Obtainium, wenn ein Repository umbenannt wurde, und fordert Sie auf, die URL der App entsprechend zu aktualisieren.

Sie können auch ein **GitHub-Proxy-Präfix** (z. B. `gh-proxy.com`) in den quellspezifischen Einstellungen angeben. Wenn gesetzt, werden alle GitHub-API-Anfragen über diesen Proxy geleitet, was bei der Umgehung von Ratelimits oder Zugänglichkeitsproblemen in einigen Regionen helfen kann.

Die GitHub-Quelle unterstützt die **Suche** und ermöglicht es Ihnen, die Ergebnisse nach einer Mindestanzahl von Sternen zu filtern.

### Erstellen eines GitHub Personal Access Tokens

1. Melden Sie sich bei [GitHub](https://github.com) an.
2. Gehen Sie zum Abschnitt [Feingranulare Tokens](https://github.com/settings/personal-access-tokens) in den Entwicklereinstellungen.
3. Wählen Sie **Neues Token generieren**.
4. Geben Sie Ihrem Token einen Namen und legen Sie ein Ablaufdatum fest.
5. Scrollen Sie nach unten und wählen Sie **Token generieren**.
6. Kopieren Sie das Token und fügen Sie es in die Obtainium-Einstellungen ein. Kopieren Sie Ihr Token jetzt, da Sie es nicht mehr sehen können.

## GitLab

GitLab-Versionen enthalten manchmal APKs, die auf nicht standardmäßige Weise angehängt sind, sodass Obtainium nicht einfach darauf zugreifen kann. Die GitLab-API bietet eine weitaus zuverlässigere Methode zum Extrahieren von APKs, kann aber ohne einen API-Schlüssel nicht verwendet werden. Während dies für die meisten GitLab-Repos kein Problem sein sollte, können Sie in den Obtainium-Einstellungen ein eigenes persönliches Zugriffstoken hinzufügen, um in Randfällen eine zuverlässigere APK-Extraktion zu ermöglichen.

Genau wie bei GitHub können Entwickler auch bei GitLab ältere Versionen derselben App hosten, daher werden bei Bedarf zusätzliche Optionen angeboten.

### Erstellen eines GitLab Personal Access Tokens

1. Melden Sie sich bei [GitLab](https://gitlab.com) an.
2. Gehen Sie zum Abschnitt [persönliche Zugriffstoken](https://gitlab.com/-/user_settings/personal_access_tokens) in den Einstellungen.
3. Wählen Sie **Neues Token hinzufügen**.
4. Geben Sie Ihrem Token einen Namen und legen Sie ein Ablaufdatum fest.
5. Aktivieren Sie das Kontrollkästchen `read_api`.
6. Scrollen Sie nach unten und wählen Sie **Persönliches Zugriffstoken erstellen**.
7. Kopieren Sie das Token und fügen Sie es in die Obtainium-Einstellungen ein. Kopieren Sie Ihr Token jetzt, da Sie es nicht mehr sehen können.

!!! info "Wann wird dies benötigt?"
    Siehe [diese Erklärung](https://github.com/ImranR98/Obtainium/issues/3#issuecomment-1234695412) zu nicht standardmäßigen APK-Anhängen in GitLab-Versionen

## F-Droid-Repos von Drittanbietern

Im Gegensatz zu den meisten anderen Quellen enthalten F-Droid-Repos Informationen über mehrere Apps unter derselben URL. Das bedeutet, dass Sie zusätzlich zur Repo-URL den Namen oder die ID der gewünschten App separat im Feld "App-ID oder -Name" angeben müssen. Wenn Sie nicht sicher sind, welche Apps in einem bestimmten Repo verfügbar sind, können Sie die Schaltfläche "Quelle durchsuchen" auf der [Import/Export-Seite](ui_overview.de.md/#„Import/Export“-Registerkarte) verwenden.

Beachten Sie, dass Obtainium nicht automatisch erkennen kann, ob eine bestimmte URL auf ein F-Droid-Repo eines Drittanbieters verweist. Das Hinzufügen eines solchen Repos zu Obtainium führt standardmäßig zur falschen Verwendung der [HTML-Quelle](#html). Sie müssen manuell "F-Droid-Repo eines Drittanbieters" aus dem Dropdown-Menü "Quelle überschreiben" auswählen.

Die zusätzlichen Versionsauswahloptionen haben unterschiedliche Verhaltensweisen:

- **Vorgeschlagene Version auswählen**: Obtainium versucht, den Versionscode zu verwenden, den das F-Droid-Repo als aktuell/vorgeschlagen markiert hat. Dies ist die Standardeinstellung und funktioniert für die meisten Repos gut.
- **Höchsten Versionscode automatisch auswählen**: Anstatt der vorgeschlagenen Version wählt Obtainium die Version mit der höchsten Versionscode-Nummer aus dem Repo aus. Dies kann nützlich sein, wenn das Repo keine vorgeschlagene Version korrekt markiert hat.

## APKMirror

APKMirror ist eine "Nur Nachverfolgen"-Quelle. Das bedeutet, dass Sie zwar eine APKMirror-URL zu Obtainium für Update-Benachrichtigungen hinzufügen können, aber die App nicht tatsächlich herunterladen und installieren können. Dies liegt daran, dass die Betreiber von APKMirror dies nicht erlauben (siehe [Issue #44](https://github.com/ImranR98/Obtainium/issues/44)).

Da APKMirror einen RSS-Feed zur Erkennung neuer Versionen verwendet, können Sie die verfolgten Versionen mit der Option "Release-Titel nach regulärem Ausdruck filtern" eingrenzen.

## HTML

Die "HTML"-Quelle ist eine Fallback-Option für alle App-Quellen, die nicht explizit von Obtainium unterstützt werden. Aufgrund ihrer Flexibilität ist sie auch eine Möglichkeit, Nischen- und weniger bekannte Quellen zu unterstützen, ohne die App aufzublähen.

Die HTML-Quelle funktioniert wie folgt:

1. Sie sendet eine Anfrage an die vom Benutzer angegebene Quell-URL und parst die Antwort als HTML. Dann sucht sie nach Links auf der Seite.
2. Sie filtert bestimmte Links heraus. Standardmäßig werden alle Links herausgefiltert, die nicht auf `.apk` enden, aber Sie können "Benutzerdefinierter APK-Link-Filter" verwenden, um Ihren eigenen Filter anzugeben.
3. Sie sortiert die verbleibenden Links. Diese Sortierung ist eine alphanumerische Sortierung des gesamten Links, aber Sie können wählen, ob Sie nur nach dem letzten Segment des Links sortieren möchten. Dieses letzte Segment ist normalerweise der Dateiname, kann aber auch anders sein, wenn Sie in Schritt 2 Ihren eigenen Filter verwendet haben.
4. Sie wendet einen weiteren optionalen benutzerdefinierten Filter auf alle verbleibenden Links an. Der Unterschied zwischen diesem Filter und dem aus Schritt 2 besteht darin, dass dieser ein allgemeinerer Filter ist, den alle Quellen haben - er wird von der übergeordneten `AppSource`-Klasse geerbt. Er ist wahrscheinlich in manchen Situationen einfacher zu verwenden, als einen einzigen komplizierteren regulären Ausdruck in Schritt 2 zu haben. Er ist auch nützlich, wenn er in Kombination mit der Zwischenlink-Option verwendet wird.
5. Von den verbleibenden Links wird der erste ausgewählt (oder der letzte, wenn Sie die umgekehrte Option aktiviert haben).
6. Nachdem wir den endgültigen APK-Link haben, benötigen wir eine eindeutige Release-ID, damit wir erkennen können, wann ein Update verfügbar ist. Bei anderen Quellen ist die eindeutige Release-ID die App-Version, aber bei der HTML-Quelle ist es möglicherweise nicht möglich, eine Versionszeichenfolge zu extrahieren. Standardmäßig wird daher ein Hash des Links verwendet. Es stehen drei Pseudoversionierungsmethoden zur Verfügung:
    - **Partieller APK-Hash** (Standard): Ein Hash eines Teils der APK-Datei selbst. Dies ist zuverlässiger als der URL-Hash, da er vom Dateiinhalt und nicht von der URL abhängt, erfordert aber das Herunterladen eines Teils der APK.
    - **APK-Link-Hash**: Ein Hash der APK-Download-URL. Dieser ändert sich, wenn sich die URL ändert.
    - **ETag**: Verwendet den HTTP-ETag-Header aus der APK-Download-Antwort. Dies kann nützlich sein, wenn der Server stabile ETags bereitstellt, sich die Download-URL selbst jedoch zwischen den Versionen nicht ändert.
    - Links enthalten oft Versionszeichenfolgen. Obtainium kann nicht selbstständig erkennen, wie diese extrahiert werden können (verschiedene Websites haben unterschiedliche Methoden), daher kann der Benutzer einen regulären Ausdruck angeben, der auf den Link angewendet wird, um die Version zu extrahieren - dies ist das Feld "Versionsextraktion".
    - Oft ist es schwierig, einen regulären Ausdruck zu erstellen, der die Version genau erfasst und gleichzeitig zusätzliche Zeichen ausschließt. Dafür gibt es die Option "Übereinstimmungsgruppe", mit der der Benutzer festlegen kann, welche Gruppe des regulären Ausdrucks als Version verwendet werden soll.
    - Es gibt auch eine Option "Version auf gesamter Seite extrahieren". Wenn aktiviert, versucht Obtainium, eine Versionszeichenfolge irgendwo auf der HTML-Seite zu finden, anstatt nur in der Link-URL. Dies ist nützlich, wenn die Version auf der Seite angezeigt wird, aber nicht in den Download-Link eingebettet ist.
    - Die Funktion zur Versionsextraktion ist nicht wirklich notwendig - die Verwendung von Link-Hashes ist einfacher und zuverlässiger. Einige Benutzer möchten sie vielleicht, weil die echte Version ansprechender/genauer aussieht und Obtainium in den meisten Fällen die [Versionserkennung](app_tracking.de.md/#versionserkennung) ermöglicht.

Sie können auch **benutzerdefinierte Anforderungsheader** für die HTML-Quelle festlegen. Dies ermöglicht es Ihnen, die Standard-Header (z. B. User-Agent) zu überschreiben, wenn die Zielwebsite bestimmte Header benötigt, um die APK korrekt auszuliefern.

Was den **Zwischenlink**-Filter betrifft, so fügt die HTML-Quelle, wenn dieser verwendet wird, einen vorbereitenden Schritt vor dem normalen Prozess ein:

1. Sie sucht auf einer ersten HTML-Seite nach Links.
2. Sie filtert alle Links heraus, die nicht dem Zwischenlink-Filter entsprechen.
3. Sie nimmt den ersten verbleibenden Link und verwendet ihn als Eingabe für den oben beschriebenen normalen HTML-Quellprozess.

Der Zwischenlink-Schritt hat seine eigenen Unteroptionen zur Steuerung der Filterung und Sortierung:

- **Automatisch nach Architektur filtern**: Filtert Zwischenlinks automatisch nach CPU-Architektur, wenn diese aus dem Linktext erkennbar ist.
- **Nach Linktext filtern**: Wenn aktiviert, wird der Zwischenlink-Filter auf den sichtbaren Linktext und nicht auf die URL selbst angewendet.
- **Links außerhalb von `<a>`-Tags finden**: Erkennt auch Links, die außerhalb von standardmäßigen Anker-Tags erscheinen (z. B. in JavaScript-Datenstrukturen).
- **Sortierung überspringen / Umgekehrte Sortierung / Nach letztem Linksegment sortieren**: Diese Optionen steuern, wie Zwischenlinks geordnet werden, bevor der erste ausgewählt wird.

## Hinweise zu verschiedenen anderen Quellen

- HTML: Die HTML-Quelle enthält Standard-Anforderungsheader, die für die meisten Websites geeignet sein sollten. In einigen Fällen (z. B. [SourceForge](https://sourceforge.net/)) müssen Sie diese möglicherweise löschen (und gegebenenfalls eigene angeben).
- Codeberg: Diese Quelle ist in ihren zusätzlichen Optionen fast identisch mit GitHub und unterstützt auch die Suche.
- F-Droid: Jede App von F-Droid wird wahrscheinlich mit einem anderen [Schlüssel signiert](https://developer.android.com/studio/publish/app-signing) als Versionen derselben App aus anderen Quellen. Dies bedeutet, dass der Versuch, von einer F-Droid-Version einer App auf eine Version aus einer anderen Quelle (z. B. GitHub) zu aktualisieren, wahrscheinlich fehlschlagen wird.
- Tencent App Store: APKs aus dieser Quelle können reine 32-Bit-Architektur ([armeabi-v7a](https://developer.android.com/ndk/guides/abis#v7a)) sein und können auf einigen Geräten mit neueren Arm-Architektur-SoCs nicht installiert werden.
- itch.io: Downloads von itch.io erfordern möglicherweise die Handhabung von "Name your price"-Seiten und Cloudflare-geschützten Download-URLs. Einige Apps erfordern möglicherweise benutzerdefinierte Cookies oder Header, die über die Anforderungsheader-Optionen der HTML-Quelle konfiguriert werden müssen.
- Alle Quellen, die keinen bestimmten Host haben (wie [F-Droid-Repos von Drittanbietern](#f-droid-repos-von-drittanbietern), Jenkins-Instanzen und SourceHut-Instanzen), werden von Obtainium nicht automatisch erkannt. Sie müssen die richtige Quelle manuell aus dem Dropdown-Menü "Quelle überschreiben" auswählen.
- Einige Quellen (wie APKPure) bieten möglicherweise [XAPK-Dateien](https://apkpure.com/xapk.html) anstelle von APK-Dateien an. Die XAPK-Unterstützung von Obtainium ist unvollständig und funktioniert möglicherweise nicht zuverlässig.
