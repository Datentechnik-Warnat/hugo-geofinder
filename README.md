# Hugo GeoFinder

Ein Hugo-Shortcode-System zur Standortsuche basierend auf Geolocation.

## Features

- Findet die nächstgelegene Seite basierend auf der aktuellen Position des Benutzers
- Zwei verschiedene UI-Varianten: Standard-Button und Floating-Button
- Geteilte JavaScript-Funktionalität zur Vermeidung von Code-Duplikation
- Konfigurierbare maximale Entfernung
- Responsive Design

## Installation

Kopiere die folgenden Dateien in dein Hugo-Projekt:

```
layouts/
├── shortcodes/
│   ├── geofinder.html
│   ├── geofinder-floating.html
│   └── partials/
│       └── geofinderjs.html
```

## Verwendung

### Standard-Button

```markdown
{{< geofinder >}}
```

oder mit benutzerdefinierter maximaler Entfernung:

```markdown
{{< geofinder distance="500" >}}
```

### Floating-Button

```markdown
{{< geofinder-floating >}}
```

oder mit benutzerdefinierter maximaler Entfernung:

```markdown
{{< geofinder-floating distance="200" >}}
```

### Routing

Das Routing zur Position dieser Adresse kann als Button mit folgemde
```markdown
{{< geofinder_routing >}}
```

### Globale Integration

Um den Floating Button auf alle Seiten der Page zu integrieren, kann folgender Abschnitt in das baseof.html integriert werden:   
```markdown
{{ partial "geofinder-footer.html" . }}
```

## Konfiguration

### Seiten-Parameter

Füge zu deinen Seiten folgende Parameter hinzu:

```yaml
---
title: "Meine Seite"
geo_lat: 52.5200
geo_lng: 13.4050
---
```

### Site-Konfiguration

Optional kannst du eine Standard-Entfernung in deiner `config.yaml` festlegen:

```yaml
params:
  geofinder:
    maxDistance: 100  # in Metern
    floatingButtonTooltip: "Suche an aktuellem Standort"
    mobileFooter: true # Soll auf mobilgeräten ein Localisation Button sichtbar sein
    mobileRouting: true # Soll ein Routing angeboten werden

```

## Funktionalität

1. **Standortbestimmung**: Verwendet die Browser-Geolocation-API
2. **Entfernungsberechnung**: Haversine-Formel für präzise Entfernungen
3. **Automatische Weiterleitung**: Leitet zur nächstgelegenen Seite weiter, wenn sie innerhalb der maximalen Entfernung liegt
4. **Fehlerbehandlung**: Benutzerfreundliche Fehlermeldungen für verschiedene Szenarien

## Unterschiede zwischen den Varianten

### Standard-Button (`geofinder`)
- Inline-Button mit Status-Text darunter
- Ideal für Integration in Seiteninhalte
- Einfaches, minimalistisches Design

### Floating-Button (`geofinder-floating`)
- Schwebt rechts unten auf der Seite
- Status wird in einem Modal-Popup angezeigt
- Ideal für seitenweite Verfügbarkeit
- Responsive Design mit Touch-Optimierung

## Browser-Unterstützung

- Moderne Browser mit Geolocation-API-Unterstützung
- HTTPS erforderlich für Geolocation in den meisten Browsern
- Mobile Browser vollständig unterstützt

## Disclaimer

Dieses Projekt wurde durch Implementation von KI unterstützt.  
Eingesetzte Codes wurden manuell geprüft.  