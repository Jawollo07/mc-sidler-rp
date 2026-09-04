# Siedler Logic – Resource Pack

Resource Pack für das **Minecraft Siedler**-Projekt. Das Paket enthält die clientseitige Darstellung der benutzerdefinierten Siedler-Entitäten, insbesondere Soldaten und Händler.

## Aktueller Stand

### Soldaten
- Drei getrennte Client-Entities: `siedler:infantry`, `siedler:archer` und `siedler:cavalry`.
- Eigene Geometrie für jeden Soldatentyp.
- Individuelle Laufanimationen pro Soldatentyp.
- Der Soldaten-Animation-Controller wurde auf den zuletzt bekannten stabilen Stand zurückgesetzt, damit die Client-Entities wieder zuverlässig gerendert werden.
- Der Angriff verwendet aktuell bewusst die gemeinsame, stabile `animation.soldier.attack`-Animation.
- Typ-spezifische Kampfanimationen werden erst wieder aktiviert, nachdem die Sichtbarkeit auf Bedrock 1.26.x verifiziert wurde.
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

Die Soldaten verwenden aktuell wieder den stabilen Animationspfad:

```text
Idle → Move → Attack
```

Die typ-spezifischen Laufanimationen bleiben erhalten. Die zuletzt hinzugefügten individuellen Angriffsanimationen (`infantry_attack`, `archer_attack`, `cavalry_attack`) sind vorübergehend nicht an die Client-Entities gebunden, bis die Rendering-Kompatibilität auf Bedrock 1.26.x getestet wurde.

## Rendering-Kette

```text
siedler:infantry / archer / cavalry
        ↓
Client Entity
        ↓
Geometry.default
        ↓
controller.render.soldier
        ↓
Animation Controller
        ↓
Idle / Move / Attack
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

Der Resource Pack soll einen klaren, wiedererkennbaren Siedler-Look erhalten und performant genug für größere Gefechte mit vielen Soldaten bleiben. Die drei Soldatentypen sollen anhand von Silhouette, Ausrüstung und Bewegung unterscheidbar sein. Neue Animationen werden erst nach erfolgreicher Validierung der Rendering-Kette aktiviert.
