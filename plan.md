# Resource Pack – Entwicklungsplan

## Phase 1 – Stabilität
- [x] Manifest auf aktuellen Entwicklungsstand bringen
- [x] Soldat-Client-Entities prüfen und stabilisieren
- [x] `enable_attachables` für Waffen und Rüstung aktivieren
- [x] Render-Controller vereinheitlichen
- [x] Idle-, Lauf- und Angriffsanimationen verbessern
- [x] Laufanimation gegen Gleitbewegung absichern
- [x] Individuelle Laufanimationen für Infanterie, Bogenschütze und Kavallerie
- [x] Animation Controller von optionalen Custom-Properties entkoppeln
- [x] Rendering-Kette der Soldaten auf robusten bekannten Stand zurückgesetzt
- [x] Typ-spezifische Kampfanimationen sicher direkt an Client-Entities gebunden
- [x] README aktualisieren

## Phase 2 – Soldaten-Rendering
- [x] Separate Client-Entities für Infanterie, Bogenschütze und Kavallerie
- [x] Soldatentypen durch eigene Geometrien visuell unterscheiden
- [x] Infanterie mit schwererer Silhouette und Schutzdetails darstellen
- [x] Bogenschütze mit leichterer Silhouette und Köcher darstellen
- [x] Kavallerie mit Reiter-Silhouette, Schutzdetails und Helmzier darstellen
- [x] Typ-spezifische Kampfanimationen direkt über die Client-Entities anbinden
- [x] Infanterie-Nahkampfhieb mit kontrollierter Aushol- und Schlagbewegung
- [x] Bogenschützen-Animation mit ruhiger Spann-/Schussbewegung
- [x] Kavallerie-Angriff mit nach vorne geneigter Haltung und kräftigem Hieb
- [x] Idle-Animation beruhigen und Bewegungsamplituden reduzieren
- [x] Laufanimationen natürlicher und weniger robotisch gestalten
- [x] Infanterie-Laufanimation auf einen ruhigen, klassischen Marsch ohne Ganzkörper-Wippen reduzieren
- [x] Soldatenanimationen auf den Vanilla-Humanoid/Pillager-Bewegungsstil umgestellt
- [x] Vanilla-artige Laufbewegung mit synchronen gegenläufigen Armen und Beinen
- [x] Vanilla-artige Idle- und Kopfbewegung integriert
- [x] Vanilla-artige Nahkampf-Angriffsbewegung integriert
- [x] Bogenschützen-Zielhaltung an den Vanilla-Humanoid-Stil angepasst
- [x] **Infanterie, Bogenschütze und Kavallerie vollständig auf Pillager-orientierte Controller umgestellt**
- [x] **Vanilla `variable.tcos0`-Laufberechnung für alle drei Soldaten aktiviert**
- [x] **Pillager/Humanoid Bob-, Look-at-Target- und Bewegungsanimationen als gemeinsame Basis verwendet**
- [x] **Pillager-Nahkampfangriff für Infanterie und Kavallerie übernommen**
- [x] **Pillager-Crossbow-Hold-/Zielpose für den Bogenschützen übernommen**
- [ ] Rüstung pro Ausrüstungsstufe sichtbar unterscheiden
- [ ] Waffenmodelle für unterschiedliche Waffentypen ergänzen
- [ ] Schilddarstellung und Offhand-Ausrichtung testen
- [ ] Treffer-/Schadensanimation ergänzen
- [ ] Sterbeanimation ergänzen, sofern sie mit dem Behavior Pack sinnvoll synchronisiert werden kann

## Phase 3 – Level und Teams
- [ ] Level bzw. Rang des Soldaten sichtbar machen
- [ ] Optionale Rangabzeichen oder Banner ergänzen
- [ ] Teamfarben/Team-Markierungen vorbereiten
- [ ] Ausgewählte Soldaten visuell hervorheben
- [ ] Gruppen-/Formationsdarstellung unterstützen

## Phase 4 – Händler und Wirtschaft
- [x] Händler visuell von Soldaten stärker abheben
- [x] Mehrere Händler-Typen mit eigenen Erscheinungsbildern
- [x] Händler für Warenhandel
- [x] Händler für Soldaten-Rekrutierung
- [x] Händler für Spezial-/Militärwaren
- [x] Händler-Varianten über persistente Variant-Tags mit dem Behavior Pack verbinden
- [x] Eigene Geometrien für Lebensmittel-, Baustoff-, Rohstoff-, Werkzeug-, Waffen-, Versorgungs- und Soldatenhändler

## Phase 5 – Qualität
- [ ] Alle JSON-Dateien gegen die aktuelle Bedrock-Version testen
- [ ] Modelle auf Z-Fighting und Clipping prüfen
- [ ] Attachables mit allen unterstützten Ausrüstungs-Kombinationen testen
- [ ] Animationen auf Vanilla-Pillager-Look → Move → Attack Übergänge testen
- [x] Sichtbarkeit der Soldaten mit einem stabilen Animation Controller auf Bedrock 1.26.x wiederhergestellt
- [ ] Typ-spezifische Kampfanimationen auf dem Server mit echten Angriffen testen
- [ ] Vanilla-Pillager-Laufbewegung auf unterschiedlichen Bewegungsgeschwindigkeiten testen
- [ ] Pillager-Crossbow-Hold-Pose des Bogenschützen mit echter Ziel-/Angriffslogik testen
- [ ] Händler-Varianten im Spiel mit allen sieben Typen testen
- [ ] Texturen optimieren und fehlende Texturen ergänzen
- [x] Pack-Icon ergänzen

## Designziel

Der Resource Pack soll einen klaren, wiedererkennbaren Siedler-Look erhalten und gleichzeitig performant genug für größere Gefechte mit vielen Soldaten bleiben. Infanterie, Bogenschütze und Kavallerie behalten ihre eigenen Geometrien und Ausrüstung, verwenden für die Animationen aber dieselbe Vanilla-Pillager/Humanoid-Grundlogik. Dadurch sollen alle Soldaten wie konsistente Minecraft-Humanoide laufen, schauen und kämpfen, ohne die zuvor beobachteten künstlichen Fisch-/Gleitbewegungen.
