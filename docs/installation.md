# Installation

## Voraussetzungen

- Home Assistant mit aktivierter Package-Unterstützung
- unterstützter Geräteadapter, aktuell Growatt
- vorhandene Sensoren für PV, Netz, Batterie und Hausverbrauch

## Installation

1. Das Verzeichnis `packages/home_energy_manager` nach `/config/packages/home_energy_manager` kopieren.

2. In der Datei `configuration.yaml` die Package-Unterstützung aktivieren:

   ```yaml
   homeassistant:
     packages: !include_dir_named packages
   ```

3. Die Home-Assistant-Konfiguration prüfen.

4. Home Assistant neu starten.

5. Den Home Energy Manager zunächst ausschließlich im Beobachtungsmodus betreiben.

6. Erst nach erfolgreicher Prüfung aller Sensoren, Entscheidungen und Sollwerte den Schreibzugriff des Geräteadapters aktivieren.

## Sicherheitshinweis

Die Schreibfreigabe darf erst aktiviert werden, wenn das Entity-Mapping vollständig an die eigene Installation angepasst und getestet wurde.
