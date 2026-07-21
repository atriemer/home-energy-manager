# Home-Assistant-Helper

Diese Datei beschreibt alle vom Home Energy Manager benötigten Helper.

Die Helper werden über die Home-Assistant-Oberfläche angelegt. Für jeden Helper
sind Typ, Name, Entity-ID, Wertebereich, Schrittweite, Standardwert, Einheit,
Icon und Zweck dokumentiert.

## Leistungsgrenzen

### Maximale Abgabeleistung

- Typ: Zahl
- Name: HEM Maximale Abgabeleistung
- Entity-ID: `input_number.hem_max_output_power`
- Minimum: 0
- Maximum: 2000
- Schrittweite: 10
- Standardwert: 800
- Einheit: W
- Icon: `mdi:transmission-tower-export`
- Zweck: Absolute, vom Betreiber festgelegte Obergrenze für die Abgabeleistung.
- Verhalten: Harte Schranke. Darf vom Automatismus niemals überschritten werden.

### Maximale Ladeleistung

- Typ: Zahl
- Name: HEM Maximale Ladeleistung
- Entity-ID: `input_number.hem_max_charge_power`
- Minimum: 0
- Maximum: 2000
- Schrittweite: 10
- Standardwert: 800
- Einheit: W
- Icon: `mdi:battery-arrow-up`
- Zweck: Absolute, vom Betreiber festgelegte Obergrenze für die Ladeleistung.
- Verhalten: Harte Schranke. Darf vom Automatismus niemals überschritten werden.

### Bevorzugte Entladeleistung

- Typ: Zahl
- Name: HEM Bevorzugte Entladeleistung
- Entity-ID: `input_number.hem_preferred_discharge_power`
- Minimum: 0
- Maximum: 2000
- Schrittweite: 10
- Standardwert: 400
- Einheit: W
- Icon: `mdi:battery-arrow-down`
- Zweck: Bevorzugte akkuschonende Entladeleistung.
- Verhalten: Weiche Schranke. Darf bei höher priorisiertem Einspeiserisiko
  überstimmt werden.

### Bevorzugte Ladeleistung

- Typ: Zahl
- Name: HEM Bevorzugte Ladeleistung
- Entity-ID: `input_number.hem_preferred_charge_power`
- Minimum: 0
- Maximum: 2000
- Schrittweite: 10
- Standardwert: 400
- Einheit: W
- Icon: `mdi:battery-arrow-up-outline`
- Zweck: Bevorzugte akkuschonende Ladeleistung.
- Verhalten: Weiche Schranke.

### Maximale Leistungsänderung

- Typ: Zahl
- Name: HEM Maximale Leistungsänderung
- Entity-ID: `input_number.hem_max_power_step`
- Minimum: 10
- Maximum: 1000
- Schrittweite: 10
- Standardwert: 100
- Einheit: W
- Icon: `mdi:speedometer`
- Zweck: Maximale Änderung der Sollleistung je Regelzyklus.
- Verhalten: Weiche Schranke zur Vermeidung unnötiger Leistungssprünge.

## Netzregelung

### Ziel-Netzleistung

- Typ: Zahl
- Name: HEM Ziel-Netzleistung
- Entity-ID: `input_number.hem_grid_target_power`
- Minimum: -200
- Maximum: 500
- Schrittweite: 5
- Standardwert: 20
- Einheit: W
- Icon: `mdi:transmission-tower`
- Zweck: Gewünschter Arbeitspunkt am Netzanschluss.
- Vorzeichen: Positive Werte bedeuten Netzbezug, negative Werte Einspeisung.
- Empfehlung: Ein kleiner positiver Wert reduziert ungewollte Einspeisung
  durch Mess- und Regelverzögerungen.

### Netz-Totband

- Typ: Zahl
- Name: HEM Netz-Totband
- Entity-ID: `input_number.hem_grid_deadband`
- Minimum: 0
- Maximum: 200
- Schrittweite: 5
- Standardwert: 30
- Einheit: W
- Icon: `mdi:arrow-expand-horizontal`
- Zweck: Toleranzbereich um die Ziel-Netzleistung.
- Verhalten: Innerhalb des Totbands wird keine unnötige Leistungsänderung
  ausgelöst.

## Betriebsmodus

### HEM Betriebsmodus

- Typ: Auswahl
- Name: HEM Betriebsmodus
- Entity-ID: `input_select.hem_operating_mode`
- Optionen:
  - `observe`
  - `shadow`
  - `active`
- Standardwert: `observe`
- Icon: `mdi:state-machine`
- Zweck: Legt fest, ob der HEM nur beobachtet, Stellbefehle simuliert oder
  tatsächlich steuert.

## Sicherheit

### Schreibfreigabe

- Typ: Schalter
- Name: HEM Schreibfreigabe
- Entity-ID: `input_boolean.hem_write_enabled`
- Standardwert: Aus
- Icon: `mdi:lock`
- Zweck: Zusätzliche Freigabe für schreibende Steuerbefehle.
- Verhalten: Ein Steuerbefehl darf nur gesendet werden, wenn der Betriebsmodus
  `active` ist und dieser Schalter eingeschaltet ist.

## Noch nicht anlegen

Diese Datei ist zunächst die verbindliche Dokumentation.

Die Helper werden erst dann in Home Assistant angelegt, wenn die zugehörigen
Templates und Prüfungen vorbereitet sind. Dadurch vermeiden wir ungenutzte oder
später umzubenennende Entitäten.
