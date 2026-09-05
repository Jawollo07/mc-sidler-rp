# Siedler Logic – Resource Pack

Resource Pack für das **Minecraft Siedler**-Projekt. Das Paket enthält die clientseitige Darstellung der benutzerdefinierten Siedler-Entitäten, insbesondere Soldaten, Kavallerie und Händler.

## Aktueller Stand

### Soldaten
- Drei getrennte Client-Entities: `siedler:infantry`, `siedler:archer` und `siedler:cavalry`.
- Eigene Geometrie für jeden Soldatentyp.
- **Alle drei Soldatentypen verwenden einen eigenen, Pillager-orientierten Animation Controller.**
- Die grundlegende Animation folgt dem Vanilla-Pillager/Humanoid-Aufbau: Zielblick, Bewegung, Arm-Bob und Angriff werden additiv kombiniert.
- Die Laufbewegung verwendet die Vanilla-Humanoid-Formel mit `variable.tcos0` sowie gegenläufigen Armen und Beinen.
- Infanterie und Kavallerie verwenden die Vanilla-Humanoid/Pillager-Nahkampfangriffsbewegung.
- Bogenschützen verwenden eine Pillager-inspirierte Crossbow-Hold-/Zielhaltung.
- Attachables für Waffen und Rüstung werden über `enable_attachables` unterstützt.

### Kavallerie-Mount
- `siedler:cavalry_horse` besitzt eine eigene Client-Entity und Geometrie.
- Die Geometrie verwendet jetzt echte Pferde-Modellabmessungen statt extrem kleiner Sub-Block-Koordinaten.
- Der frühere Root-Scale-Hack wurde entfernt; die Modellkoordinaten sind direkt auf die gewünschte Pferdegröße skaliert.
- Die sichtbare Größe ist auf das Behavior-Pack-Mount mit einer Collision Box von `1.4 × 1.6` abgestimmt.
- Das Mount verwendet weiterhin den Vanilla-Pferdetexturpfad `textures/entity/horse/horse_brown`.

### Händler
- `siedler:trader` besitzt eine gemeinsame Client-Entity mit sieben visuellen Varianten.
- Die Variante wird über `minecraft:variant` aus dem Behavior Pack ausgewählt.
- Lebensmittel-, Baustoff-, Rohstoff-, Werkzeug-, Waffen-, Versorgungs- und Soldatenhändler besitzen eigene visuelle Details.

## Animationen

Die drei Soldaten besitzen getrennte Controller, nutzen aber dieselbe Vanilla-Pillager/Humanoid-Bewegungsbasis:

```text
Infantry  → controller.animation.soldier.infantry
Archer    → controller.animation.soldier.archer
Cavalry   → controller.animation.soldier.cavalry
```

## Rendering-Kette

```text
siedler:infantry / archer / cavalry
        ↓
Typ-spezifische Client Entity
        ↓
Eigene Soldaten-Geometrie
        ↓
Render Controller
        ↓
Pillager/Humanoid Animation Controller
```

Für das Mount:

```text
siedler:cavalry_horse
        ↓
entity/cavalry_horse.entity.json
        ↓
geometry.siedler.cavalry_horse
        ↓
controller.render.siedler.cavalry_horse
        ↓
Vanilla-Pferdetextur
```

## Verzeichnisstruktur

```text
.
├── animation_controllers/
│   └── soldier.animation_controllers.json
├── animations/
│   └── soldier.animation.json
├── attachables/
│   ├── soldier_boots.attachable.json
│   ├── soldier_chestplate.attachable.json
│   ├── soldier_helmet.attachable.json
│   ├── soldier_leggings.attachable.json
│   ├── soldier_shield.attachable.json
│   └── soldier_sword.attachable.json
├── entity/
│   ├── archer.entity.json
│   ├── cavalry.entity.json
│   ├── cavalry_horse.entity.json
│   ├── infantry.entity.json
│   ├── soldier.entity.json
│   └── trader.entity.json
├── models/
│   └── entity/
│       ├── cavalry_horse.geo.json
│       ├── soldier.geo.json
│       ├── soldier_equipment.geo.json
│       ├── soldier_types.geo.json
│       └── trader_types.geo.json
├── render_controllers/
│   ├── cavalry_horse.render_controllers.json
│   ├── soldier.render_controllers.json
│   └── trader.render_controllers.json
├── textures/entity/
│   ├── soldier.png
│   └── trader.png
└── manifest.json
```

## Abhängigkeit

Das Resource Pack ist für die Entitäten und Animationen des zugehörigen Behavior Packs `mc-siedler-bp` gedacht. Die Identifier müssen zwischen Behavior Pack und Resource Pack übereinstimmen.

## Entwicklung

Änderungen am Resource Pack sollten immer zusammen mit dem aktuellen Stand des Behavior Packs getestet werden. Nach Änderungen an Modellen, Animationen oder Attachables sollte ein vollständiger Client-Neustart bzw. ein erneutes Laden des Packs erfolgen.

## Ziel

Der Resource Pack soll einen klaren, wiedererkennbaren Siedler-Look erhalten und performant genug für größere Gefechte bleiben. Soldaten verwenden für Bewegung und Kampf bewusst einen Vanilla-Pillager/Humanoid-Stil. Die Kavallerie erhält zusätzlich ein korrekt proportioniertes Pferde-Mount.
