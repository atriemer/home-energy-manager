# Entity-Mapping

Der Home Energy Manager trennt die allgemeine HEM-Logik von konkreten Geräten und Integrationen.

## Ziel

Das Entity-Mapping ermöglicht es, den HEM ohne Anpassung der Entscheidungslogik mit unterschiedlichen Geräten zu betreiben.

## Aufbau

Die gerätespezifischen Entity-IDs werden in einer zentralen Mapping-Schicht zusammengefasst.

Die Decision Engine arbeitet ausschließlich mit generischen HEM-Entitäten.

## Aktueller Entwicklungsstand

Der aktuelle Stand enthält noch einige fest eingebaute Growatt-Entity-IDs im Data Layer und im Growatt-Adapter.

Diese werden schrittweise in eine konfigurierbare Mapping-Schicht überführt.

## Langzeitziel

- hardwareunabhängig
- integrationsunabhängig
- lokale Datenquellen bevorzugt
- Cloud als Fallback
- leicht anpassbar
