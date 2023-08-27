---
title: "Datenbank Installation"
draft: false
type: "page"
menu: 
  main:
    name: "Datenbank Installation"
    weight: 1
    
---
# Installation der Datenbank

## Installation von PostgreSQL

### Installation unter Ubuntu

```bash
sudo apt-get install postgresql-all
```
### Version prüfen

```bash
psql --version
```

### Nutzer anlegen

```bash
sudo adduser <Nutzername>
```

<Nutzername> durch den gewünschten Nutzernamen ersetzen.

### Nutzerrechte anpassen
Benutzer in die Gruppe sudo aufnehmen.
Sudo ist eine Gruppe, die die Rechte hat, Programme mit Root-Rechten auszuführen.

```bash
sudo usermod -aG sudo <Nutzername>
```

### Nutzer wechseln postgres
Postgres ist der Standardnutzer für die Datenbank.
```bash
sudo -u postgres -i
```
### Nutzer anlegen
```bash
createuser <Nutzername>
```
### Datenbank anlegen
```bash
createdb -E UTF8 -O <Nutzername> <Datenbankname>
```
### Shell zur Datenbank
```bash
psql <Datenbankname>
```
### Postgis Erweiterung installieren
Postgis ist eine Erweiterung für PostgreSQL, die die Datenbank um Funktionen für Geodaten erweitert.

```bash
CREATE EXTENSION postgis;
```

### hstore Erweiterung installieren
hstore ist eine Erweiterung für PostgreSQL, die die Datenbank um Funktionen für Key-Value-Paare erweitert.

```bash
CREATE EXTENSION hstore;
```

### Änderungen Tabellenrechte
```bash
ALTER TABLE geometry_columns OWNER TO <Nutzername>;
ALTER TABLE spatial_ref_sys OWNER TO <Nutzername>;
```
### Passwort für Nutzer setzen
```bash
\password <Nutzername>
```
### Datenbank verlassen
```bash
\q
```
### Nutzer wechseln
```bash
exit
```






