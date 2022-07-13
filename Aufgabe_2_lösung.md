
# Implementation von Software-Lösungen für datenintensive Prozesse und Datenanalysen


Die im [Exposé](https://github.com/cbroschinski/MALIS-21.3-WPM_T9_Christoph_Broschinski/blob/master/Aufgabe_2_expos%C3%A9.md) beschriebenen Verbesserungen wurden erfolgreich umgesetzt. Da die Änderungen direkt in das Projekt [OpenAPC](https://github.com/OpenAPC/openapc-de) einfließen sollen (bzw. bereits sind), ist der entsprechende Code dort zu finden. Als Abgabe dient der Branch [institution_table_testing](https://github.com/OpenAPC/openapc-de/commits/institution_table_testing) ab seinem Fork vom master-Branch ([f982a3d4](https://github.com/OpenAPC/openapc-de/commit/f982a3d44a026d3304640e734d57126bc917a14f)).

Die im Sinne der Aufgabenstellung relevante Datei ist die neue [Testsammlung](https://github.com/OpenAPC/openapc-de/blob/institution_table_testing/python/test/test_institutions_table.py) für die [Institutionen-Tabelle](https://github.com/OpenAPC/openapc-de/blob/institution_table_testing/data/institutions.csv).

Folgende Tests wurden implementiert:

- Überprüfung der Spaltenanzahl
- Überprüfung des in `openapc_data_dir` angegeben Verzeichnisses
- Wechselseitige Prüfung der `institution` mit den entsprechenden Identifiern im [Datensatz](https://github.com/OpenAPC/openapc-de/blob/institution_table_testing/data/apc_de.csv)
- Überprüfung der in `info_url` angegeben Adresse. Dieser Test konnte durch Verwendung von Nebenläufigkeiten enorm beschleunigt werden.

Zur Ausführung des Tests sind folgende Schritte nötig (getestet auf einem frischen Ubuntu 20.04 LTS):

- Installation von python, pip und virtualenv. Die verwendete Python-Version ist 3.8, ältere Varianten *sollten* allerdings auch funktionieren.

```
git clone https://github.com/OpenAPC/openapc-de.git
cd openapc-de
git checkout institution_table_testing
virtualenv venv
source venv/bin/activate
pip install -r python/requirements.txt
pytest python/test/test_institutions_table.py
```
