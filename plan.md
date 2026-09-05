# Resource Pack – Entwicklungsplan

## Phase 1 – Stabilität
- [x] Manifest auf aktuellen Entwicklungsstand bringen
- [x] Soldat-Client-Entities prüfen und stabilisieren
- [x] `enable_attachables` für Waffen und Rüstung aktivieren
- [x] Render-Controller vereinheitlichen
- [x] Idle-, Lauf- und Angriffsanimationen verbessern
- [x] Animation Controller von optionalen Custom-Properties entkoppeln
- [x] Rendering-Kette der Soldaten auf robusten Stand gebracht
- [x] Typ-spezifische Kampfanimationen direkt an Client-Entities gebunden
- [x] README aktualisieren
- [x] Eigenes Kavallerie-Pferdemodell entfernt

## Phase 2 – Soldaten-Rendering
- [x] Separate Client-Entities für Infanterie, Bogenschütze und Kavallerie
- [x] Soldatentypen durch eigene Geometrien visuell unterscheiden
- [x] Infanterie, Bogenschütze und Kavallerie mit eigenen Silhouetten darstellen
- [x] Typ-spezifische Kampfanimationen
- [x] Vanilla-Pillager/Humanoid-Bewegungsstil
- [x] Vanilla `variable.tcos0`-Laufberechnung
- [x] Pillager/Humanoid Look-at-Target und Bewegungsbasis
- [x] Pillager-Nahkampfangriff für Infanterie und Kavallerie
- [x] Pillager-Crossbow-Hold-/Zielpose für Bogenschützen
- [ ] Rüstung pro Ausrüstungsstufe sichtbar unterscheiden
- [ ] Waffenmodelle für unterschiedliche Waffentypen ergänzen
- [ ] Schilddarstellung und Offhand-Ausrichtung testen
- [ ] Treffer-/Schadensanimation ergänzen
- [ ] Sterbeanimation ergänzen

## Phase 3 – Kavallerie-Mount

Die Kavallerie verwendet kein eigenes Pferde-Resource-Pack-Modell mehr. Das Behavior Pack spawnt ein normales `minecraft:horse` und setzt den `siedler:cavalry`-Soldaten über `/ride` darauf.

- [x] Custom-`siedler:cavalry_horse`-Client-Entity entfernt
- [x] Custom-`geometry.siedler.cavalry_horse` entfernt
- [x] Custom-Pferde-Render-Controller entfernt
- [x] Vanilla `minecraft:horse` als Mount verwenden
- [x] Pferde-Darstellung vollständig an Minecraft delegieren
- [ ] Reiterposition und Sattel-/Mount-Offset im Spiel feinjustieren
- [ ] Vanilla-Pferde-Laufanimation mit Kavallerie-Bewegung testen
- [ ] Mounting und Dismounting mit echten Server-Spawns testen
- [ ] Mount-Cleanup bei Soldaten-Tod/Entfernung testen
- [ ] Verhalten bei mehreren Kavallerie-Einheiten testen

## Phase 4 – Level und Teams
- [ ] Level bzw. Rang des Soldaten sichtbar machen
- [ ] Optionale Rangabzeichen oder Banner ergänzen
- [ ] Teamfarben/Team-Markierungen vorbereiten
- [ ] Ausgewählte Soldaten visuell hervorheben
- [ ] Gruppen-/Formationsdarstellung unterstützen

## Phase 5 – Händler
- [x] Händler visuell von Soldaten abheben
- [x] Mehrere Händler-Typen mit eigenen Erscheinungsbildern
- [x] Händler-Varianten über `minecraft:variant` verbinden
- [x] Eigene Händler-Geometrien

## Phase 6 – Qualität
- [ ] Alle JSON-Dateien gegen die aktuelle Bedrock-Version testen
- [ ] Modelle auf Z-Fighting und Clipping prüfen
- [ ] Attachables mit allen unterstützten Ausrüstungs-Kombinationen testen
- [ ] Animationen auf Vanilla-Pillager-Look → Move → Attack testen
- [x] Sichtbarkeit der Soldaten mit stabilem Animation Controller wiederhergestellt
- [ ] Typ-spezifische Kampfanimationen auf dem Server mit echten Angriffen testen
- [ ] Vanilla-Pillager-Laufbewegung auf unterschiedlichen Geschwindigkeiten testen
- [ ] Bogenschützen-Zielpose mit echter Ziel-/Angriffslogik testen
- [ ] Händler-Varianten im Spiel mit allen sieben Typen testen
- [ ] Kavallerie mit Vanilla-Pferden auf unterschiedlichen Kameradistanzen prüfen
- [ ] Kavallerie mit Terrain, Steigungen und Hindernissen testen
- [ ] Texturen optimieren und fehlende Texturen ergänzen
- [x] Pack-Icon ergänzen

## Designziel

Der Resource Pack soll einen klaren, wiedererkennbaren Siedler-Look erhalten und performant genug für größere Gefechte bleiben. Infanterie, Bogenschütze und Kavallerie behalten ihre eigenen Soldaten-Geometrien und Ausrüstung. Für die Kavallerie wird bewusst das native Minecraft-Pferd verwendet, damit Modellgröße, Textur und Pferdeanimationen vollständig Vanilla-kompatibel sind.