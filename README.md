# Siedler Logic – Resource Pack

Resource Pack für das **Minecraft Siedler**-Projekt. Das Paket enthält die clientseitige Darstellung der benutzerdefinierten Siedler-Entitäten, insbesondere Soldaten und Händler.

## Aktueller Stand

### Soldaten
- Drei getrennte Client-Entities: `siedler:infantry`, `siedler:archer` und `siedler:cavalry`.
- Eigene Geometrie für jeden Soldatentyp.
- **Alle drei Soldatentypen verwenden jetzt einen eigenen, Pillager-orientierten Animation Controller.**
- Die grundlegende Animation folgt dem Vanilla-Pillager/Humanoid-Aufbau: Zielblick, Bewegung, Arm-Bob und Angriff werden additiv kombiniert.
- Die Laufbewegung verwendet die Vanilla-Humanoid-Formel mit `variable.tcos0` sowie gegenläufigen Armen und Beinen.
- Kein eigenes Ganzkörper-Wippen mehr als Bestandteil der Laufanimation.
- Die Kopfbewegung folgt dem Vanilla-Humanoid/Pillager-Zielblick über `query.target_x_rotation` und `query.target_y_rotation`.
- Die dezente Arm-Bob-Bewegung entspricht dem Vanilla-Humanoid-Stil.
- Infanterie und Kavallerie verwenden die Vanilla-Humanoid/Pillager-Nahkampfangriffsbewegung.
- Bogenschützen verwenden die Pillager-inspirierte Crossbow-Hold-/Zielhaltung für ihre Fernkampfpose.
- Attachables für Waffen und Rüstung werden über `enable_attachables` unterstützt.
- Enchanting-Glint wird über eigene Render-Controller unterstützt.

### Händler
- `siedler:trader` besitzt eine gemeinsame Client-Entity mit sieben visuellen Varianten.
- Die Variante wird über `minecraft:variant` aus dem Behavior Pack ausgewählt.
- **Lebensmittelhändler:** Schürze und Warenkorb.
- **Baustoffhändler:** Kopfbedeckung, Werkzeug-/Bauausstattung und Bauplan.
- **Rohstoffhändler:** Bergmanns-Kopfbedeckung und Erz-/Rohstofftasche.
- **Werkzeughändler:** Werkzeug-/Werkzeuggürtel und Hammer.
- **Waffenhändler:** Helm, Waffenhalter und Schwert.
- **Versorgungshändler:** großer Rucksack und zusammengerollte Versorgungslast.
- **Soldatenhändler:** militärische Silhouette, Helmzier und Waffengürtel.

## Animationen

Die drei Soldaten besitzen getrennte Controller, nutzen aber dieselbe Vanilla-Pillager/Humanoid-Bewegungsbasis:

```text
Infantry  → controller.animation.soldier.infantry
Archer    → controller.animation.soldier.archer
Cavalry   → controller.animation.soldier.cavalry
```

Gemeinsamer Vanilla-Pillager-Aufbau:

```text
Look at Target
      +
Pillager/Humanoid Move
      +
Pillager/Humanoid Bob
      +
Typ-spezifische Kampfpose
```

Die Bewegungsanimation verwendet die von Mojang verwendete `variable.tcos0`-Berechnung. Dadurch laufen Arme und Beine synchron gegenläufig wie bei einem normalen Vanilla-Humanoid/Pillager. Die Angriffsebenen werden nur bei `query.is_attacking` zugeschaltet.

Für den Bogenschützen wird die Pillager-Crossbow-Hold-Haltung als Fernkampfpose verwendet und an die vorhandenen Soldaten-Bones angepasst. Dadurch erhalten alle drei Soldatentypen denselben Vanilla-Grundcharakter, ohne ihre eigenen Geometrien zu verlieren.

## Rendering-Kette

```text
siedler:infantry / archer / cavalry
        ↓
Typ-spezifische Client Entity
        ↓
Eigene Soldaten-Geometrie
        ↓
controller.render.soldier
        ↓
Pillager/Humanoid Animation Controller
        ↓
Look + Move + Bob + Attack
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

Das Resource Pack ist für die Entitäten und Animationen des zugehörigen Behavior Packs `mc-siedler-bp` gedacht. Die Identifier und Soldatentypen müssen zwischen Behavior Pack und Resource Pack übereinstimmen.

## Entwicklung

Änderungen am Resource Pack sollten immer zusammen mit dem aktuellen Stand des Behavior Packs getestet werden. Nach Änderungen an Modellen, Animationen oder Attachables sollte ein vollständiger Client-Neustart bzw. ein erneutes Laden des Packs erfolgen.

## Ziel

Der Resource Pack soll einen klaren, wiedererkennbaren Siedler-Look erhalten und performant genug für größere Gefechte mit vielen Soldaten bleiben. Die drei Soldatentypen behalten ihre eigenen Geometrien und Ausrüstung, verwenden für Bewegung und Kampf aber bewusst den Vanilla-Pillager/Humanoid-Stil. Dadurch soll die Bewegung ruhig, lesbar und Minecraft-nativ wirken, ohne das zuvor beobachtete starke Wippen oder Zappeln.
