# Siedler Logic – Resource Pack

Resource Pack für das **Minecraft Siedler**-Projekt. Das Paket enthält die clientseitige Darstellung der benutzerdefinierten Siedler-Entitäten, insbesondere Soldaten und Händler.

## Aktueller Stand

### Soldaten
- Drei getrennte Client-Entities: `siedler:infantry`, `siedler:archer` und `siedler:cavalry`.
- Eigene Geometrie für jeden Soldatentyp.
- **Infanterie:** schwere Silhouette, Schulter-/Beinschutz und Helmzier.
- **Bogenschütze:** leichterer Körper, Kopfbedeckung und sichtbarer Köcher am Rücken.
- **Kavallerie:** breiterer Reiterkörper, Schulter-/Armschutz, Gürtel und Federbusch; das Pferd bleibt eine separate Mount-Entity.
- Individuelle Laufanimationen pro Soldatentyp.
- Stabiler gemeinsamer Animation Controller für Idle → Bewegung → Angriff.
- Der Animation Controller verwendet die synchronisierte `siedler:combat_state`-Property, damit auch die per Script gesteuerte Bewegung und der Angriff zuverlässig animiert werden.
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
- Die visuellen Varianten nutzen weiterhin die gemeinsame Händlertextur und bleiben damit performant und kompatibel mit den vorhandenen Händler-Commands.

## Rendering-Fix

Die Soldaten-Entities verwenden weiterhin ihre typ-spezifischen Geometrien über `Geometry.default`. Der gemeinsame Render Controller bleibt bewusst einfach. Der Animation Controller liest `siedler:combat_state`, die vom Behavior-Pack für `idle`, `move` und `attack` synchronisiert wird. Dadurch hängt die Darstellung nicht von Vanilla-Bewegungs- oder Angriffs-Queries ab.

Die Kette ist damit:

```text
siedler:infantry / archer / cavalry
        ↓
Client Entity
        ↓
Geometry.default → geometry.soldier.<type>
        ↓
controller.render.soldier
        ↓
Material.default + Texture.default
        ↓
Animation Controller über siedler:combat_state (Idle / Move / Attack)
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

## Händler-Varianten

Die sieben Händler werden über `/siedler:trader <type>` bzw. `/siedler:trader_here <type>` erzeugt. Das Behavior Pack setzt dabei einen numerischen `minecraft:variant`-Wert und zusätzlich einen Rollen-Tag für die Soldatenhändler-Interaktion:

```text
food       → variant 0 → trader_food
building   → variant 1 → trader_building
resources  → variant 2 → trader_resources
tools      → variant 3 → trader_tools
weapons    → variant 4 → trader_weapons
supplies   → variant 5 → trader_supplies
soldiers   → variant 6 → trader_soldiers
```

Der Render Controller wählt anhand von `query.variant` die passende Geometrie. Ein Händler ohne gesetzte Variante verwendet die Basisvariante 0.

## Abhängigkeit

Das Resource Pack ist für die Entitäten und Animationen des zugehörigen Behavior Packs `mc-siedler-bp` gedacht. Die Identifier und Händler-Varianten müssen zwischen Behavior Pack und Resource Pack übereinstimmen.

## Entwicklung

Änderungen am Resource Pack sollten immer zusammen mit dem aktuellen Stand des Behavior Packs getestet werden. Nach Änderungen an Modellen, Animationen oder Attachables sollte ein vollständiger Client-Neustart bzw. ein erneutes Laden des Packs erfolgen.

## Ziel

Das Resource Pack soll einen klar erkennbaren, einheitlichen Siedler-Look erhalten. Soldaten und Händler sollen bereits anhand ihrer Silhouette, Ausrüstung, Rolle und Bewegung unterscheidbar sein, während Gameplay-Daten und KI im Behavior Pack bleiben.
