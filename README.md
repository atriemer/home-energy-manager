# Home Energy Manager

Der Home Energy Manager, kurz HEM, ist ein modularer und nachvollziehbarer
Energiemanager für Home Assistant.

Das Projekt wird zunächst für den Growatt steuerbares Energiesystem entwickelt. Die interne
Logik ist jedoch so aufgebaut, dass sie nicht direkt von Growatt, GroBro oder
bestimmten Home-Assistant-Entitäten abhängig ist.

## Ziele

Der HEM soll:

- den Eigenverbrauch maximieren,
- Netzeinspeisung möglichst vermeiden,
- die Akkus schonen,
- sicherheitskritische Zustände priorisieren,
- Entscheidungen nachvollziehbar dokumentieren,
- lokale Daten bevorzugen,
- Cloud-Daten nur als Fallback verwenden,
- für andere Installationen leicht anpassbar sein.

## Grundprinzipien

### Local First

Lokale Datenquellen werden bevorzugt. Cloud-Daten dürfen verwendet werden,
wenn lokale Daten fehlen, veraltet oder unplausibel sind.

### Hardwareunabhängiger Kern

Die Decision Engine arbeitet ausschließlich mit logischen HEM-Entitäten wie:

- `sensor.hem_pv_power`
- `sensor.hem_house_power`
- `sensor.hem_grid_power`
- `sensor.hem_battery_soc`
- `sensor.hem_battery_power`

Konkrete Quell-Entitäten werden ausschließlich im Mapping hinterlegt.

### Nachvollziehbare Entscheidungen

Jede spätere Steuerentscheidung soll mindestens folgende Informationen liefern:

- aktuelle Betriebsphase,
- gewählte Aktion,
- Entscheidungsgrund,
- verwendete Datenquellen,
- Datenqualität,
- aktive Begrenzungen,
- überstimmte Komfort- oder Schonungsregeln.

### Sichere Einführung

Bestehende Automationen bleiben aktiv, bis der HEM ausreichend getestet wurde.
Der HEM erhält zunächst ausschließlich lesenden Zugriff auf die Eingangsdaten.

## Prioritäten der Regelung

1. Sicherheit
2. Energieverlust und unerwünschte Netzeinspeisung vermeiden
3. Akkuschonung
4. Komfort und Optimierung

Die Prioritäten sind nicht als starre Einzelregeln zu verstehen. Die Decision
Engine bewertet immer die Gesamtsituation.

Beispielsweise darf bei hoher PV-Leistung und fast vollem Akku eine stärkere
Entladung sinnvoll sein, obwohl Temperatur- oder SoC-Differenzen normalerweise
für eine reduzierte Leistung sprechen würden.

## Projektstatus

Aktueller Entwicklungsstand:

- [x] Projektstruktur
- [x] Architekturgrundlagen
- [x] logischer Datenvertrag
- [ ] Mapping-Konzept
- [ ] Diagnosekonzept
- [ ] Home-Assistant-Helper
- [x] Data-Layer-Templates
- [ ] Plausibilitätsprüfung
- [x] Decision Engine (Beobachtungsmodus)
- [ ] Control Layer
- [ ] Dashboard
- [ ] produktiver Parallelbetrieb
- [ ] Ablösung bestehender Automationen

## Dateien

```text
packages/
└── home_energy_manager/
    ├── 00_templates.yaml
    ├── 02_situationsbewertung.yaml
    ├── 03_controller.yaml
    ├── 04_adapter_growatt.yaml
    ├── 10_helpers.md
    ├── README.md
    └── CHANGELOG.md

docs/
```

## Entwicklungsregeln

- Änderungen erfolgen schrittweise.
- Nach jedem Schritt wird die Home-Assistant-Konfiguration geprüft.
- Bestehende Automationen werden zunächst nicht verändert.
- Der Standardbetrieb während der Entwicklung ist beobachtend und nicht steuernd.
- Neue Funktionen müssen dokumentiert werden.
- Quell-Entitäten dürfen nicht direkt in der Decision Engine verwendet werden.
