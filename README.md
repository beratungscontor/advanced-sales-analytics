# Advanced Sales Analytics
Demo einer Advanced Sales Analytics mit SAP DWC and SAP BAS in der SAP BTP.

Es soll eine Sales Analyse auf Verkaufsdaten ausgeführt werden. Dabei ist es das Ziel, Muster, Zusammenhänge, Auswirkungen und Trends innerhalb des Umsatzes zu identifizieren und zu belegen bzw. zu wiederlegen.

Grundlage für die Demo sind die synthetischen Kundendaten PCS dFashion, welche klassische Merkmale und Kennzahlen enthalten zur Auswertung des Umsatzes. Dabei werden ausschließlich Technologien der SAP Business Technology Platform verwendet.

* SAP Data Warehouse Cloud für das Speichern und Berechnen von Daten auf einer Datenbank (SAP HANA Cloud) innerhalb eines Spaces
* SAP Business Application Studio für das Sammeln, Auswerten und Analysieren von Daten als Python-Skripte oder Jupyter Notebooks; Ein Vorteil ist die IP-Freigabe des SAP Business Application Studios zur geschützten Auswertung

## Vorgehensweise
- [X] PCS dFashion Daten in den Space buAAP laden (BW/4HANA -> SAP HANA Cloud (SDA) -> Remote Tabelle)
- [X] Schulferien (DE) Daten in den Space buAAP laden (Externe Daten (SAP HANA) -> Datenfluss -> Tabelle)
- [X] Anlegen eines Github Repositories
- [ ] Vorbereiten eine Spaces im SAP Business Application Studio mit dem Github Repository, sowie Environment Variables für den Zugriff auf SAP Data Warehouse Cloud
- [ ] Anlage Gliederung Verzeichnisstruktur in Github Repository (siehe AAP Repository README.md)
- [ ] Python-Skript zum Laden von Wetterdaten in den SAP Data Warehouse Cloud Space
- [ ] Analyse 1: Statistisches Profil der PCS dFashion (Tabelle = stat. Dataset?); ggf. Ableitung eines Datasets für weitere Analysen
- [ ] Verknüpfen der PCS dFashion, Schulferien und Wetterdaten
- [ ] Analyse 2: Durchführung eines AutoML (Gradient Boosted Decision Tree (Regression)) auf Umsatz zur Identifikation von Einflussfaktoren; Ausgabe als Bericht
- [ ] Vorgehensweise, Methodik und Best Practices festhalten; Präsentation in Github über SAP Business Application Studio?

## SAP Business Application Studio
SAP Business Application Studio ist technisch eine angepasste Version von [code-server](https://github.com/coder/code-server) und basiert technisch auf VSCode von Microsoft. Mit der Umstellung von [Eclipse Theia](https://theia-ide.org/) in Q4.2022 ergeben sich einige technische Vorteile in der Anwendung.
* Offenes VSCode Extension Ökosystem, ergänzt um öffentliche und nicht-öffentliche SAP Extensions 
* Python 3.9.2 (Q1.2023) vorinstalliert 

### Vorbereitung SAP Business Application Studio
#### Installation Python Package Index (PyPI)
Open a new Terminal and install PyPI with following statements. 
```shell
cd ~
curl https://bootstrap.pypa.io/get-pip.py > get-pip.py && python3 get-pip.py && echo "export PATH=/home/user/.local/bin:$PATH" >> .bashrc && source ~/.bashrc
```

#### Installation Requirements
Open a new Terminal and install the Libraries with the following statement.
```shell
pip install -r requirements.txt
```

#### Einbindung Environment Variable (.env)
Create a local environment variable having the following structure.
*The credentials can be viewed in the hdi_heisights_dev|prod service for this bound application.*
```json
{
    "host":"",
    "port":443,
    "user":"",
    "password":"",
    "schema":""
}
```

### Deployment Options
#### No route mapping, no staging and no starting
```shell
cf push --no-route --no-start
```

