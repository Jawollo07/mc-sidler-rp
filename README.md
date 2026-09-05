# Siedler Logic – Resource Pack

Resource Pack für das **Minecraft Siedler**-Projekt. Das Paket enthält die clientseitige Darstellung der benutzerdefinierten Siedler-Entitäten, insbesondere Soldaten und Händler.

## Aktueller Stand

### Soldaten
- Drei getrennte Client-Entities: `siedler:infantry`, `siedler:archer` und `siedler:cavalry`.
- Eigene Geometrie für jeden Soldatentyp.
- Pillager-orientierte Animation Controller für Bewegung, Zielblick, Arm-Bob und Angriff.
- Infanterie und Kavallerie verwenden die Vanilla-Humanoid/Pillager-Nahkampfbasis.
- Bogenschützen verwenden eine Pillager-inspirierte Crossbow-Hold-/Zielhaltung.
- Attachables für Waffen und Rüstung werden über `enable_attachables` unterstützt.

### Kavallerie-Mount
Die Kavallerie verwendet **kein eigenes Pferde-Resource-Pack-Model mehr**. Das Behavior Pack spawnt ein normales `minecraft:horse` und setzt den `siedler:cavalry`-Soldaten über den nativen `/ride`-Befehl auf das Pferd.

Damit kommt die komplette Pferdedarstellung direkt aus Minecraft:

```text
siedler:cavalry
      ↓
   /ride
      ↓
minecraft:horse
      ↓
Vanilla-Pferdemodell + Vanilla-Pferdetextur
```

Die früheren Dateien `entity/cavalry_horse.entity.json`, `models/entity/cavalry_horse.geo.json` und `render_controllers/cavalry_horse.render_controllers.json` wurden entfernt. Dadurch gibt es keine eigene Pferdegeometrie mehr, die zu klein dargestellt werden könnte.

### Händler
- `siedler:trader` besitzt eine gemeinsame Client-Entity mit sieben visuellen Varianten.
- Die Variante wird über `minecraft:variant` aus dem Behavior Pack ausgewählt.
- Lebensmittel-, Baustoff-, Rohstoff-, Werkzeug-, Waffen-, Versorgungs- und Soldatenhändler besitzen eigene visuelle Details.

## Animationen

```text
Infantry  → controller.animation.soldier.infantry
Archer    → controller.animation.soldier.archer
Cavalry   → controller.animation.soldier.cavalry
```

Alle drei Soldaten verwenden eine gemeinsame Vanilla-Pillager/Humanoid-Bewegungsbasis.

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

Das Pferd benötigt keine eigene RP-Definition:

```text
minecraft:horse
        ↓
Vanilla Client Entity
        ↓
Vanilla Horse Model
        ↓
Vanilla Horse Texture
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
│   ├── infantry.entity.json
│   ├── soldier.entity.json
│   └── trader.entity.json
├── models/
│   └── entity/
│       ├── soldier.geo.json
│       ├── soldier_equipment.geo.json
│       ├── soldier_types.geo.json
│       └── trader_types.geo.json
├── render_controllers/
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

Der Resource Pack soll einen klaren, wiedererkennbaren Siedler-Look erhalten und performant genug für größere Gefechte bleiben. Soldaten verwenden für Bewegung und Kampf bewusst einen Vanilla-Pillager/Humanoid-Stil. Die Kavallerie verwendet für das Mount bewusst das native Minecraft-Pferd, damit Größe, Animationen und Darstellung vollständig Vanilla-kompatibel bleiben.