# Architektur

Der Home Energy Manager besteht aus vier Schichten.

## Data Layer

Der Data Layer vereinheitlicht Messwerte verschiedener Datenquellen.

Lokale Datenquellen werden bevorzugt verwendet. Cloud-Daten dürfen als Fallback dienen. Datenalter, Verfügbarkeit und Plausibilität werden bewertet.

## Decision Engine

Die Decision Engine bewertet die Gesamtsituation. Dazu gehören unter anderem:

- PV-Leistung
- Hausverbrauch
- Netzleistung
- Ladezustand
- Ladezustände einzelner Batteriemodule
- Batterietemperaturen
- Datenqualität
- Betriebs- und Sicherheitsgrenzen

## Control Layer

Der Control Layer übersetzt die Entscheidung in gerätespezifische Befehle.

Der Kern der Entscheidungslogik enthält keine direkten Gerätebefehle. Diese werden ausschließlich in Geräteadaptern umgesetzt.

## Dashboard

Das Dashboard zeigt nicht nur Messwerte, sondern auch:

- aktive Situation
- Sollleistung
- Begrenzungsgründe
- Datenqualität
- Adapterstatus
- Schreibbereitschaft
