# Siedler Logic – Resource Pack

Resource Pack für das **Minecraft Siedler**-Projekt. Das Paket enthält die clientseitige Darstellung der benutzerdefinierten Siedler-Entitäten, insbesondere Soldaten und Händler.

## Aktueller Stand

### Soldaten
- `siedler:soldier` wird über eine eigene Client-Entity dargestellt.
- Eigenes Humanoid-Modell mit getrennten Knochen für Körper, Kopf, Arme und Beine.
- Idle-, Lauf- und Angriffsanimationen.
- Animation Controller reagiert auf `siedler:combat_state`.
- Attachables für Schwert, Schild und Rüstung sind vorbereitet.
- Enchanting-Glint wird über eigene Render-Controller unterstützt.
- Waffen und Rüstung werden über `enable_attachables` gerendert.

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
│   ├── soldier.entity.json
│   └── trader.entity.json
├── models/
│   ├── entity/soldier.geo.json
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

Das Resource Pack soll schrittweise eine klar erkennbare, einheitliche Darstellung für das Siedler-System liefern: Soldatentypen, Ausrüstung, Händler und später weitere Einheiten und Gebäude.
