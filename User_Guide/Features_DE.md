# TIA Openness Manager - Feature-Übersicht

## Produktbeschreibung

Der **TIA Openness Manager** ist ein leistungsstarkes Werkzeug für Siemens TIA Portal Entwickler, das den Export, Import und die Verwaltung von SPS-Programmbausteinen revolutioniert. Mit einer intuitiven Benutzeroberfläche und fortschrittlichen Funktionen wie Differenzvergleich, Schutzprofilen und KI-Integration steigert es die Produktivität und reduziert Fehler bei der Projektverwaltung erheblich.

---

## Hauptfeatures

### Import & Export

- **Bulk Export** - Exportieren Sie hunderte Blöcke mit einem Klick
- **Selektiver Export** - Wählen Sie genau die Blöcke, die Sie benötigen
- **XML & SCL Support** - Vollständige Unterstützung für Simatic ML und SCL-Dateien
- **S7DCL Export (V20+)** - Zusätzliches textbasiertes Export-Format (.s7dcl) für bessere Versionskontrolle
- **Ordnerstruktur-Erhaltung** - Die TIA Portal Ordnerstruktur wird beibehalten
- **Automatische Kompilierung** - Kompiliert und speichert automatisch nach Import
- **Konfigurierbare Ordnernamen** - Passen Sie Export-Ordnernamen an (Source, Blocks, Tags, etc.)
- **Optionaler Source-Ordner** - Source-Ordner im Export aktivieren/deaktivieren

### HMI Export/Import

- **Bildschirm-Export** - HMI-Bildschirme als XML exportieren
- **Bildschirmvorlagen-Export** - Wiederverwendbare Bildschirmvorlagen exportieren
- **HMI-Variablentabellen** - HMI-Variablentabellen exportieren/importieren
- **VB-Skripte** - HMI VB-Skripte exportieren
- **Verbindungen** - HMI-Verbindungskonfigurationen exportieren
- **Text- & Grafiklisten** - Vollständige Unterstützung für HMI-Listen

### Hardware-Tab

- **Geräteliste** - Vollständige Übersicht aller Geräte (SPSen, HMIs, Antriebe, Switches)
- **PROFINET-Namen** - PROFINET-Gerätenamen direkt anzeigen und bearbeiten
- **IP-Adressen** - IP-Adresskonfiguration für alle Geräte anzeigen
- **Firmware-Versionen** - Firmware-Version für jedes Gerät anzeigen
- **Artikelnummern** - Siemens Artikel-/Bestellnummern anzeigen
- **I/O-Mapping** - Ein-/Ausgabe-Adressbereiche anzeigen
- **CSV-Export** - Komplette Hardware-Liste als CSV für Dokumentation exportieren
- **WinCC Unified Support** - Volle Unterstützung für WinCC Unified HMI-Panels

### Hardware-Export

- **Gerätekonfiguration** - Hardware-Konfiguration als XML exportieren
- **Modulkonfiguration** - Individuelle Moduleinstellungen exportieren
- **Netzwerkkonfiguration** - Netzwerk-/Kommunikationseinstellungen exportieren

### Watch/Force-Tabellen

- **Tabellen-Export** - Watch-Tabellen und Force-Tabellen exportieren
- **Variablenlisten** - Überwachte Variablenkonfigurationen exportieren
- **Debug-Unterstützung** - Debugging-Setups projektübergreifend erhalten

### Differenzvergleich (Preview Diff)

- **Fingerprint-basiert** - Schneller Vergleich ohne vollständigen Export
- **Änderungserkennung** - Erkennt geänderte, neue und gelöschte Blöcke
- **Detaillierter Diff-Viewer** - Zeigt Unterschiede Zeile für Zeile
- **Selektiver Re-Export** - Nur geänderte Blöcke exportieren

### Code Editor

- **Integrierter Editor** - Betrachten und bearbeiten Sie Blockcode direkt
- **Syntax-Highlighting** - Für SCL, STL und andere Sprachen
- **Block-Details** - Zeigt Metadaten wie Nummer, Sprache, Autor
- **Schnelle Navigation** - Suche im Projektbaum

### Schutz-System (Protected Items)

- **Block-Schutz** - Schützen Sie wichtige Blöcke vor versehentlichem Überschreiben
- **Profile** - Speichern und laden Sie Schutz-Konfigurationen
- **Visuelle Markierung** - Geschützte Blöcke sind klar gekennzeichnet
- **Hierarchischer Schutz** - Schützen Sie ganze Ordner oder einzelne Blöcke

### Find Unused Blocks

- **Dead Code Erkennung** - Findet nicht verwendete Bausteine
- **Call-Graph Analyse** - Basiert auf tatsächlichen Aufrufen, nicht nur Referenzen
- **Safety-Block Support** - Unterstützt auch F-Blöcke (F_FB, F_FC, F_DB, F_OB)
- **Export-Funktion** - Ergebnisse als CSV exportieren
- **Lösch-Funktion** - Ungenutzte Blöcke direkt entfernen

### KI-Integration (MCP Server)

- **Model Context Protocol** - Integration mit Claude und anderen KI-Assistenten
- **Projekt-Kontext** - KI hat Zugriff auf Ihre Projektstruktur
- **Code-Generierung** - KI kann SCL-Quellcode für Bausteine generieren
- **DB-Generierung** - KI kann Datenbausteine mit Simatic ML-Vorlagen erstellen
- **UDT-Generierung** - KI kann benutzerdefinierte Datentypen erstellen
- **Variablentabellen-Generierung** - KI kann Variablentabellen erstellen
- **Auto-Import** - Generierter Code kann automatisch in TIA Portal importiert werden
- **Block-Analyse** - KI kann bestehende Bausteine lesen und analysieren

---

## Unterstützte TIA Portal Versionen

| Version | Status |
|---------|--------|
| TIA Portal V18 | Vollständig unterstützt |
| TIA Portal V19 | Vollständig unterstützt |
| TIA Portal V20 | Vollständig unterstützt |
| TIA Portal V21 | Geplant |

---

## Unterstützte Block-Typen

### PLC-Bausteine
- **OB** - Organisationsbausteine (inkl. F_OB)
- **FB** - Funktionsbausteine (inkl. F_FB)
- **FC** - Funktionen (inkl. F_FC)
- **DB** - Datenbausteine (Global, Instanz, Array, inkl. F_DB)
- **UDT** - Benutzerdefinierte Datentypen
- **Tag Tables** - Variablentabellen
- **Technologieobjekte** - Motion Control, PID-Regler, Zähler, etc.
- **Software Units** - V18+ Software-Unit-Container

### HMI-Elemente
- **Bildschirme** - HMI-Bildschirme und Popups
- **Bildschirmvorlagen** - Wiederverwendbare Bildschirmvorlagen
- **HMI-Variablentabellen** - HMI-spezifische Variablentabellen
- **VB-Skripte** - VB-Skriptfunktionen
- **Verbindungen** - PLC/HMI-Verbindungen
- **Textlisten** - Mehrsprachige Textlisten
- **Grafiklisten** - Grafik-/Symbollisten

### Hardware
- **Gerätekonfiguration** - Hardware-Setup als AML/XML

---

## Lizenz-Optionen

### Basic (KOSTENLOS)
- **Für immer gratis** - Keine Testphase, kein Ablauf
- 1 Datei Export/Import
- Block Compare
- Code Editor
- Hardware Overview

### Professional (€25/Monat oder €250/Jahr)
- **1.000 Dateien** Export/Import
- **Jahresabo spart 17%** (2 Monate gratis)
- Alles aus Basic, plus:
- Find Unused Blocks
- Safety Block Support (F_FB, F_FC, F_DB, F_OB)
- Protection Profiles
- MCP Server Integration (KI/Claude)
- Priority Support

### Enterprise (€40/Monat oder €400/Jahr)
- **Unbegrenzte Dateien**
- **Jahresabo spart 17%** (2 Monate gratis)
- Alles aus Professional
- Multi-User Lizenzen
- Dedizierter Support
- Mengenrabatte

---

## Aktivierung

### Online-Aktivierung
1. Subscription kaufen unter: https://www.tiaopenessmanager.ch
2. Aktivierungscode per E-Mail erhalten
3. Code im Programm eingeben unter "License" → "Activate"
4. Lizenz ist an Ihre Hardware gebunden

### Subscription verwalten
- Klicken Sie auf "Manage Subscription" im License-Dialog
- Öffnet das Stripe-Portal für Zahlungen, Rechnungen und Kündigung

---

- **Mehrsprachig** - Deutsch, Englisch, Französisch, Italienisch

---

## Haftungsausschluss

Die Software wird „as is" geliefert. Der Anbieter übernimmt keine Haftung für Schäden, die durch die Nutzung entstehen. Der Anwender trägt die volle Verantwortung für die Prüfung aller generierten Inhalte. Siehe EULA auf https://www.tiaopenessmanager.ch

---

**Kontakt:** Für Fragen kontaktieren Sie uns unter [tiaopenessmanager@outlook.com]

**© 2025 AnyAutomation. Alle Rechte vorbehalten.**
