
# Implementation von Software-Lösungen für datenintensiven Prozesse und Datenanalysen

Für die zweite Aufgabe würde ich im Wesentlichen gerne die Punkte umsetzen, die in der ersten Aufgabe im Abschnitt ["Verbesserungspotential"](https://github.com/cbroschinski/MALIS-21.3-WPM_T9_Christoph_Broschinski/blob/master/Aufgabe_1.md#verbesserungspotential) beschrieben wurden. Diese Änderungen hätten insbesondere den Vorteil, dass sie keinen toten Code darstellen, sondern tatsächlich sinvolle und langfristig benötigte Verbesserungen der OpenAPC-Infrastruktur darstellen.

## Details

Um das Test-Framework in Python zu erweitern, sind zunächst einige Vorarbeiten erforderlich. Diese sind strengenommen nicht Teil der Aufgabenstellung, der Vollständigkeit halber werden sie hier aber trotzdem aufgeführt.

### Vorarbeiten

Wie erwähnt soll das [R Markdown-Template](https://github.com/OpenAPC/openapc-de/blob/master/README.Rmd#L63) der README-Datei so abgeändert werden, dass die teilnehmenden Einrichtungen nicht mehr hardkodiert sind, sondern automatisch aus der bestehenden [Institutionen-Tabelle](https://github.com/OpenAPC/openapc-de/blob/master/data/institutions.csv) eingefügt werden (das wird zusätzlich zur Aufgabenstellung etwas R-Code erfordern). Wichtig ist hierbei die Modellierung, um die Institutionen-Tabelle so zu erweitern, dass die bestehenden Strukturen sauber abgebildet werden können. 

Wie man sieht, sind Einrichtungen ausserhalb Deutschlands einfach nur unterhalb ihrer jeweiligen Landessektion aufgelistet, was einfach abzubilden wäre. Bei deutschen Einrichtungen ist die Sache etwas komplexer: Es gibt zunächst eine Unterteilung nach

1. Universitäten
2. Einrichtungen der Forschungsgemeinschaften
3. Andere Einrichtungen 

Die Forschungsinstitute sind zusätzlich noch einmal unterteilt nach der jeweiligen Gemeinschaft. Diese Struktur ist explizit so gewünscht und muss erhalten bleiben. Es wäre also erforderlich, zunächst den Einrichtungstyp aufzunehmen (Universität/Institut/Other o.ä.) und außerdem müsste eine zusätzliche Klassifikation eingezogen werden, um eine Unterteilung nach Forschungsgemeinschaften zu ermöglichen (Diese Abstraktion würde dann ebenfalls ermöglichen, beispielsweise die Hochschulen in Universitäten und FHs zu untergliedern, falls das irgendwann gewünscht sein sollte). Beide Felder sollten auch leer bleiben dürfen (`NA`), um wie im Fall der anderen Länder bewusst keine Untergliederung zu generieren. Weiterhin muss natürlich der Link zum Informationsangebot aufgenommen werden (Grundlage für die eigentliche Aufgabe), außerdem wäre es sinnvoll, ein Kommentarfeld aufzunehmen, da einige der Einrichtungen mit zusätzlichen Anmerkungen annotiert sind ([Beispiel](https://github.com/OpenAPC/openapc-de/blob/master/README.Rmd#L159)). Zusammengefasst müsste die `institutions.csv` also um folgende Felder erweitert werden, die allesamt nicht verpflichtend sind:

- institution_type
- institution_group
- info_url
- comment

Als letzter Schritt müsste noch eine zusätzliche Mapping-Tabelle geschaffen werden, die die Länderkürzel, Einrichtungstypen und Gruppenbezeichner auflöst ("SWE": "Sweden", "WGL": "Leibniz Association" etc.)

### Aufgabe




