---
title: "Daten_hochladen_nach_PostgreSQL_Datenbank"
draft: false
type: "page"
menu: 
  main:
    name: "Daten hochladen"
    weight: 4
    
---
# Daten hochladen nach PostgreSQL Datenbank
```bash

osm2pgsql -c -d <Datenbankname> -U <Nutzername> -H localhost -S /usr/share/osm2pgsql/default.style schleswig-holstein-latest.osm.pbf

```

## Parameter
* -a : Fügt die Daten an die bestehenden Daten an.
* -c: Erstellt die Datenbanktabellen neu.
* -d: Datenbankname
* -Output: Pfad zur Ausgabedatei.
   * pgsql: PostgreSQL Datenbank
   * flex: Flex
   * multi: Multi
   * gazetteer: 
   * null: Null

* --hstore : Erstellt eine zusätzliche Spalte mit allen Tags als hstore.
* -G : Erstellt eine zusätzliche Spalte mit allen Tags als JSON.
* -a : Fügt die Daten an die bestehenden Daten an.
* -O : Erstellt eine zusätzliche Spalte mit allen Tags als OSM XML.
* -S : Pfad zur Style Datei.
* -k : Erstellt eine zusätzliche Spalte mit allen Tags als Text.
  *  --hstore : Erstellt eine zusätzliche Spalte mit allen Tags als hstore.
  * --tag-transform-script : Pfad zu einer Lua Datei, die die Tags transformiert.
* -- drop : Löscht die Datenbanktabellen.
* -C : Anzahl der Prozesse, die osm2pgsql verwendet.
* -F : Erstellt eine zusätzliche Spalte mit allen Tags als Text.

## Beispiel
```bash
osm2pgsql  -d thorsten --create   -G --hstore  schleswig-holstein-latest.osm.pbf -O flex
```



