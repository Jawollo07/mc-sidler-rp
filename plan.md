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
- [x] README aktualisieren

## Phase 2 – Soldaten-Rendering
- [x] Separate Client-Entities für Infanterie, Bogenschütze und Kavallerie
- [x] Soldatentypen durch eigene Geometrien visuell unterscheiden
- [x] Infanterie mit schwererer Silhouette und Schutzdetails darstellen
- [x] Bogenschütze mit leichterer Silhouette und Köcher darstellen
- [x] Kavallerie mit Reiter-Silhouette, Schutzdetails und Helmzier darstellen
- [ ] Typ-spezifische Kampfanimationen für Infanterie, Bogenschütze und Kavallerie nach erfolgreicher Rendering-Validierung erneut aktivieren
- [ ] Infanterie-Nahkampfhieb mit Schwertbewegung
- [ ] Bogenschützen-Animation mit Bogenspannen und Schussbewegung
- [ ] Kavallerie-Angriff mit nach vorne geneigter Reiterhaltung und kräftigem Hieb
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
- [ ] Animationen auf Idle → Move → Attack Übergänge testen
- [ ] Sichtbarkeit der Soldaten mit dem stabilen Animation Controller auf Bedrock 1.26.x testen
- [ ] Typ-spezifische Kampfanimationen einzeln aktivieren und testen
- [ ] Individuelle Laufanimationen auf unterschiedlichen Bewegungsgeschwindigkeiten testen
- [ ] Händler-Varianten im Spiel mit allen sieben Typen testen
- [ ] Texturen optimieren und fehlende Texturen ergänzen
- [x] Pack-Icon ergänzen

## Designziel

Der Resource Pack soll einen klaren, wiedererkennbaren Siedler-Look erhalten und gleichzeitig performant genug für größere Gefechte mit vielen Soldaten bleiben. Rendering-Logik und Gameplay-Daten bleiben im Behavior Pack; das Resource Pack konzentriert sich auf Darstellung, Modelle, Animationen und Attachables. Stabilität der Client-Entities hat Vorrang vor zusätzlichen Animationseffekten.
