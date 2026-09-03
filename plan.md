# Resource Pack – Entwicklungsplan

## Phase 1 – Stabilität
- [x] Manifest auf aktuellen Entwicklungsstand bringen
- [x] Soldat-Client-Entities prüfen und stabilisieren
- [x] `enable_attachables` für Waffen und Rüstung aktivieren
- [x] Render-Controller vereinheitlichen
- [x] Idle-, Lauf- und Angriffsanimationen verbessern
- [x] Laufanimation gegen Gleitbewegung absichern
- [x] Individuelle Laufanimationen für Infanterie, Bogenschütze und Kavallerie
- [x] README aktualisieren

## Phase 2 – Soldaten-Rendering
- [x] Separate Client-Entities für Infanterie, Bogenschütze und Kavallerie
- [x] Soldatentypen durch eigene Geometrien visuell unterscheiden
- [x] Infanterie mit schwererer Silhouette und Schutzdetails darstellen
- [x] Bogenschütze mit leichterer Silhouette und Köcher darstellen
- [x] Kavallerie mit Reiter-Silhouette, Schutzdetails und Helmzier darstellen
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
- [ ] Händler visuell von Soldaten stärker abheben
- [ ] Mehrere Händler-Typen mit eigenen Erscheinungsbildern
- [ ] Händler für Warenhandel
- [ ] Händler für Soldaten-Rekrutierung
- [ ] Händler für Spezial-/Militärwaren

## Phase 5 – Qualität
- [ ] Alle JSON-Dateien gegen die aktuelle Bedrock-Version testen
- [ ] Modelle auf Z-Fighting und Clipping prüfen
- [ ] Attachables mit allen unterstützten Ausrüstungs-Kombinationen testen
- [ ] Animationen auf Idle → Move → Attack Übergänge testen
- [ ] Individuelle Laufanimationen auf unterschiedlichen Bewegungsgeschwindigkeiten testen
- [ ] Texturen optimieren und fehlende Texturen ergänzen
- [ ] Pack-Icon ergänzen

## Designziel

Der Resource Pack soll einen klaren, wiedererkennbaren Siedler-Look erhalten und gleichzeitig performant genug für größere Gefechte mit vielen Soldaten bleiben. Rendering-Logik und Gameplay-Daten bleiben im Behavior Pack; das Resource Pack konzentriert sich auf Darstellung, Modelle, Animationen und Attachables. Die drei Soldatentypen sollen zusätzlich über ihre Bewegung klar unterscheidbar sein.
