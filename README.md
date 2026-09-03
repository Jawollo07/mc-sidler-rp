# Siedler Logic – Resource Pack

Resource Pack für das **Minecraft Siedler**-Projekt. Das Paket enthält die clientseitige Darstellung der benutzerdefinierten Siedler-Entitäten, insbesondere Soldaten und Händler.

## Aktueller Stand

### Soldaten
- Drei getrennte Client-Entities: `siedler:infantry`, `siedler:archer` und `siedler:cavalry`.
- Eigene Geometrie für jeden Soldatentyp.
- **Infanterie:** schwere Silhouette, Schulter-/Beinschutz und Helmzier.
- **Bogenschütze:** leichterer Körper, Kopfbedeckung und sichtbarer Köcher am Rücken.
- **Kavallerie:** breiterer Reiterkörper, Schulter-/Armschutz, Gürtel, Helm und Federbusch; das Pferd bleibt eine separate Mount-Entity.
- Gemeinsame Idle-, Lauf- und Angriffsanimationen mit kompatiblen Bone-Namen.
- Animation Controller reagiert auf `siedler:combat_state`.
- Attachables für Waffen und Rüstung werden über `enable_attachables` unterstützt.
- Enchanting-Glint wird über eigene Render-Controller unterstützt.

### Händler
- `siedler:trader` besitzt eine eigene Client-Entity und Textur.
- Der Händler verwendet aktuell das gemeinsame Humanoid-Grundmodell.

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
│   ├── entity/soldier.geo.json
│   ├── entity/soldier_types.geo.json
│   └── soldier_equipment.geo.json
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

Das Resource Pack soll einen klar erkennbaren, einheitlichen Siedler-Look erhalten. Die Soldatentypen sollen bereits anhand ihrer Silhouette und Ausrüstung unterscheidbar sein, während Gameplay-Daten und KI im Behavior Pack bleiben.
