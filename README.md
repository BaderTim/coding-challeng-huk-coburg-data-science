# coding-challeng-huk-coburg-data-science

Repo structure:
- `/data` contains the two `.arff` data files.
- `data_exploration.ipynb` explores the datasets by plotting an overview, column densities and correlations.
- `feature_engineering.ipynb` prepares the datasets for training in multiple steps. It maps string values to numerical tokens, merges the dataframes, normalizes the data and creates weights  cwith a PDF for a weighted loss.
- `training_s.ipynb` contains the training code for Random Forest, XGBoost and a MLP for **sampled** and **unweighted** data.
- `training_w_s.ipynb` contains the training code for Random Forest, XGBoost and a MLP for **sampled** and **weighted** data.
- `training_w.ipynb` contains the training code for Random Forest, XGBoost and a MLP for the **complete** and **weighted** data.

There is room for improvement for the model results. The MLP clearly overfits while XGBoost seems to underfit.

## Challenge
Unter https://www.openml.org/d/41214 und https://www.openml.org/d/41215 finden Sie zwei Daten- sätze eines französischen Automobilversicherers. Diese beinhalten Risikomerkmale und Schaden-informationen zu Kraftfahrt-Haftpflicht-Versicherungsverträgen (eine Datensatzbeschreibung finden Sie am Ende dieses Textes). Ihre Aufgabe besteht in der Modellierung der zu erwartenden Schadenhöhe pro Versicherungsnehmer und Jahr anhand der Risikomerkmale der Kunden. Dieser Wert ist Basis für die Berechnung eines fairen Versicherungsbeitrags.  

Die Ergebnisse ihrer Auswertungen stellen Sie im Rahmen des 60-minütigen technischen Interviews
vor. Dabei haben Sie zunächst 15 Minuten Zeit, um die aus ihrer Sicht wesentlichen Ergebnisse
vorzustellen. Die Form der Präsentation (frei, Folien, Jupyter-Notebook, R-Markdown...) wählen Sie
dabei selbst. Anschließend findet eine Diskussion statt, in deren Rahmen Ihnen Fragen zu ihrer
Vorgehensweise sowie zu Ihrem Programmcode gestellt werden. Es sollte anhand ihrer Arbeit gut
nachvollziehbar sein, wie sie vorgegangen sind (beispielsweise anhand eines Jupyter-Notebooks oder
R-Markdowns).  

Gehen Sie dabei in folgenden Teilschritten vor:
- Explorative Datenanalyse: Machen Sie sich mit dem Datensatz vertraut. Identifizieren Sie dabei mögliche Probleme sowie grundlegende statistische Zusammenhänge, welche für die anschließende Modellierung wichtig sein könnten.
- Feature Engineering: Bereiten Sie, soweit für ihre Modellierung nötig, die Variablen geeignet auf.
- Modellvergleich: Entscheiden Sie sich für ein geeignetes Modell anhand einer dafür geeigneten Metrik. Erläutern Sie wie Sie dabei vorgehen und begründen Sie ihre Entscheidung.
- Modellbuilding: Trainieren Sie unter Berücksichtigung der vorangegangenen Schritte das von Ihnen gewählte Modell zur Vorhersage der erwarteten Schadenhöhe pro Kunde und Jahr. Ihr Ziel ist es, einen möglichst fairen Versicherungsbeitrag pro Jahr für einzelne Kunden anhand der Ihnen zu Verfügung stehenden Merkmale zu bestimmen. Wählen Sie mindestens eine geeignete Metrik, um die Güte des finalen Modells zu beurteilen. Zeigen Sie, welche Variablen und Zusammenhänge für Ihr finales Modell relevant sind. Überlegen Sie sich (ohne dies umzusetzen) wie Sie Ihr Modell weiter optimieren könnten.


Diese Coding Challenge ist in etwa 5h gut zu erledigen. Wir erwarten nicht, dass Sie mehr Zeit investieren. Bitte teilen Sie sich ihre Zeit entsprechend ein und konzentrieren Sie sich auf das – aus ihrer Sicht - Wesentliche. Eine erschöpfende Tiefenanalyse der Daten und oder eine aufwändige Optimierung vieler verschiedener Modelle werden dementsprechend nicht von Ihnen erwartet.

Die abhängige Variable ist definiert als ClaimAmount / Exposure.

### freMTPL2freq
The dataset freMTPL2freq contains risk features for 677,991 motor third-part liability policies (observed mostly on one year). See https://github.com/dutangc/CASdatasets for more details. The dataset is associated with 'Computational Actuarial Science with R' edited by Arthur Charpentier, CRC, 2018.  
- **IDpol**: ID des Vertrags
- **ClaimNb**: Anzahl Schäden im Versicherungszeitraum
- **Exposure**: Länge des Versicherungszeitraums (in Jahren) [Komponente der abhängigen Variable]
- **Area**: Area-Code des Versicherungsnehmers [unabhängige Variable]
- **VehPower**: Leistung des versicherten Kfz [unabhängige Variable]
- **VehAge**: Alter des versicherten Kfz [unabhängige Variable]
- **DrivAge**: Alter des Versicherungsnehmers [unabhängige Variable]
- **BonusMalus**: Schadenfreiheitsrabatt (französische Entsprechung der Schadenfreiheitsklasse) [unabhängige Variable]
- **VehBrand**: Marke des versicherten Kfz [unabhängige Variable]
- **VehGas**: Antrieb des versicherten Kfz [unabhängige Variable]
- **Density**: Anzahl der Einwohner pro km2 im Wohnort des Versicherungsnehmers [unabhängige Variable]
- **Region**: Region des Versicherungsnehmers [unabhängige Variable]

### freMTPL2sev
The dataset freMTPL2sev contains claim amounts for 26,639 motor third-part liability policies.
- **IDpol**: ID des Vertrags
- **ClaimAmount**: Höhe der einzelnen Schadenaufwände (mehrere Einträge pro Vertrag, falls im Zeitraum mehrere Schäden vorhanden waren.) [Komponente der abhängigen Variable]