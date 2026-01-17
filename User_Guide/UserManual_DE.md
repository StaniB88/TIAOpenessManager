# TIA Openness Manager - Benutzerhandbuch

**Version:** 1.2
**Stand:** Januar 2026

---

## Inhaltsverzeichnis

1. [Einführung](#1-einführung)
2. [Installation & Systemvoraussetzungen](#2-installation--systemvoraussetzungen)
3. [Benutzeroberfläche](#3-benutzeroberfläche)
4. [Projekt-Management](#4-projekt-management)
5. [Import/Export Tab](#5-importexport-tab)
6. [Project Tab](#6-project-tab)
7. [Protected Items Tab](#7-protected-items-tab)
8. [MCP Tab (KI-Integration)](#8-mcp-tab-ki-integration)
9. [Hardware Tab](#9-hardware-tab)
10. [Find Unused Blocks](#10-find-unused-blocks)
11. [Einstellungen](#11-einstellungen)
12. [Lizenzierung](#12-lizenzierung)
13. [Fehlerbehebung & FAQ](#13-fehlerbehebung--faq)

---

## 1. Einführung

### Was ist der TIA Openness Manager?

Der TIA Openness Manager ist eine Desktop-Anwendung, die die Siemens TIA Portal Openness API nutzt, um SPS-Programmbausteine zu exportieren, importieren und zu verwalten. Er bietet eine benutzerfreundliche Alternative zu manuellen Export/Import-Operationen direkt im TIA Portal.

### Hauptanwendungsfälle

- **Versionskontrolle** - Exportieren Sie Blöcke als XML für Git/SVN
- **Projekt-Migration** - Übertragen Sie Blöcke zwischen Projekten
- **Backup** - Erstellen Sie regelmäßige Sicherungen Ihrer Programmbausteine
- **Code-Review** - Vergleichen Sie Änderungen mit der Preview Diff Funktion
- **Aufräumen** - Finden und entfernen Sie ungenutzte Blöcke

---

## 2. Installation & Systemvoraussetzungen

### Systemvoraussetzungen

| Komponente | Anforderung |
|------------|-------------|
| Betriebssystem | Windows 10/11 (64-bit) |
| TIA Portal | V15, V16, V17, V18, V19 oder V20 |
| .NET Framework | 4.8 oder höher |
| RAM | Mindestens 4 GB (8 GB empfohlen) |
| Festplatte | 50 MB |

> **Hinweis:** Die TIA Portal Version wird automatisch erkannt, wenn Sie ein Projekt öffnen oder sich mit einer laufenden Instanz verbinden. Keine manuelle Konfiguration erforderlich.

### Installation

1. Laden Sie das TiaOpennessManager-Archiv herunter
2. Entpacken Sie das Archiv in einen Ordner Ihrer Wahl (z.B. `C:\Tools\TiaOpennessManager`)
3. Starten Sie `TiaOpennessManager.exe`

> **Hinweis:** Es ist keine separate Installation erforderlich. Die Anwendung ist portable. TIA Portal muss auf dem System installiert sein.

---

## 3. Benutzeroberfläche

### Hauptfenster-Übersicht

Die Anwendung ist in mehrere Bereiche unterteilt:

```
┌─────────────────────────────────────────────────────────────┐
│  [Open] [Attach] [Close]              [Settings] [License]  │
├─────────────┬───────────────────────────────────────────────┤
│             │  [Editor] [Import/Export] [Protected] [MCP]   │
│  Projekt-   ├───────────────────────────────────────────────┤
│  Baum       │                                               │
│             │              Tab-Inhalt                       │
│  (Links)    │                                               │
│             │                                               │
├─────────────┴───────────────────────────────────────────────┤
│  Status-Leiste mit Fortschrittsanzeige                      │
└─────────────────────────────────────────────────────────────┘
```

### Linker Bereich - Projektbaum

- Zeigt die Struktur des geöffneten TIA Portal Projekts
- Hierarchie: Projekt → Hardware → Source → PLC → Blocks/Datatypes/Tags
- Checkboxen ermöglichen Mehrfachauswahl für Export

### Rechter Bereich - Tabs

- **Project** - Code-Editor für ausgewählte Blöcke
- **Import/Export** - Haupt-Arbeitsbereich für Datei-Operationen
- **Find Unused** - Dead-Code-Erkennung und Aufräumen
- **MCP** - KI-Integrations-Status
- **Hardware** - Geräteliste mit PROFINET-Namen und IP-Konfiguration

### Symbolleiste

| Symbol | Funktion |
|--------|----------|
| Open Project | Öffnet ein TIA Portal Projekt |
| Attach to Portal | Verbindet mit laufendem TIA Portal |
| Close | Schließt das aktuelle Projekt |
| Settings | Öffnet die Einstellungen |
| License | Zeigt Lizenz-Informationen |

---

## 4. Projekt-Management

### Projekt öffnen (Headless Mode)

1. Klicken Sie auf **Open Project**
2. Navigieren Sie zu Ihrer TIA Portal Projektdatei (`.ap15`, `.ap16`, `.ap17`, `.ap18`, `.ap19`, `.ap20`, `.apx`)
3. Klicken Sie auf **Öffnen**

Die TIA Portal Version wird automatisch aus der Projektdatei-Erweiterung erkannt.

Der Headless Mode startet TIA Portal im Hintergrund ohne sichtbare Benutzeroberfläche. Dies ist schneller für reine Export/Import-Operationen.

### Mit TIA Portal verbinden (Attach Mode)

1. Öffnen Sie Ihr Projekt in TIA Portal
2. Klicken Sie im TIA Openness Manager auf **Attach to Portal**
3. Wählen Sie das gewünschte Projekt aus der Liste

**Vorteile des Attach Mode:**
- Schnellere Verbindung (kein Projekt-Laden)
- Sie können gleichzeitig in TIA Portal arbeiten
- Änderungen sind sofort sichtbar

**Hinweis:** Bei großen Bulk-Operationen (25+ Dateien) wechselt die Anwendung automatisch in den Attach Mode für bessere Stabilität.

### Projekt archivieren

Erstellt ein komprimiertes Archiv (.zap-Datei) des aktuellen Projekts:

1. Klicken Sie auf **Archive Project** in der Toolbar
2. Wählen Sie einen Zielordner
3. Das Projekt wird mit allen zugehörigen Dateien archiviert

**Hinweis:** Das Projekt muss vor dem Archivieren gespeichert werden.

### Safety Printout

Generiert einen Safety-Dokumentations-Ausdruck für F-Blöcke:

1. Stellen Sie sicher, dass Sie mit Safety-Anmeldedaten eingeloggt sind (klicken Sie zuerst **Safety Login**)
2. Klicken Sie auf **Safety Printout** im Tree Controls Bereich
3. Wählen Sie einen Zielordner
4. Ein PDF wird mit allen sicherheitsrelevanten Dokumentationen generiert

**Hinweis:** Diese Funktion erfordert einen aktiven Safety-Login und ist nur für Projekte mit F-Blöcken verfügbar.

### Projekt schließen

Klicken Sie auf **Close**, um das Projekt zu schließen. Im Headless Mode wird TIA Portal beendet.

---

## 5. Import/Export Tab

Der Import/Export Tab ist das Herzstück der Anwendung.

### Layout

```
┌──────────────────┬──────────────────┬───────────────────────┐
│   TIA Projekt    │    Aktionen      │   Working Directory   │
│   (Links)        │    (Mitte)       │   (Rechts)            │
├──────────────────┼──────────────────┼───────────────────────┤
│ □ Blocks         │ Export Selected→ │ [Refresh] [Pfad: ...] │
│   □ Main [OB1]   │ Export All →     │ □ Main.xml            │
│   □ Motor [FB1]  │                  │ □ Motor.xml           │
│   □ Calc [FC1]   │ ← Import Selected│ □ Calc.xml            │
│ □ Datatypes      │ ← Import All     │                       │
│ □ Tags           │                  │                       │
└──────────────────┴──────────────────┴───────────────────────┘
```

### Right Directory (Export-/Import-Verzeichnis)

Das Right Directory ist der Ordner auf Ihrem Dateisystem, in dem exportierte XML-Dateien gespeichert werden und aus dem Dateien importiert werden.

**Festlegen:**
1. Klicken Sie auf **...** neben dem Feld "Right directory"
2. Wählen Sie einen Ordner aus
3. Der Ordner wird mit dem Profil gespeichert und bei jedem Start geladen

**Tipp:** Verwenden Sie einen Git-Repository-Ordner für automatische Versionskontrolle.

> **Hinweis:** Das "Working Directory" in den Einstellungen bezieht sich auf die "Find Unused Blocks" Funktion und ist ein separater Ordner.

### Export-Operationen

#### Export Selected
1. Setzen Sie Häkchen bei den gewünschten Blöcken im linken Baum
2. Klicken Sie auf **Export Selected**
3. Die ausgewählten Blöcke werden als XML exportiert

#### Export All
1. Klicken Sie auf **Export All**
2. ALLE Blöcke, Datentypen und Tag-Tabellen werden exportiert

### Import-Operationen

#### Import Selected
1. Setzen Sie Häkchen bei den gewünschten XML-Dateien im rechten Baum
2. Klicken Sie auf **Import Selected**
3. Die ausgewählten Dateien werden importiert

#### Import All
1. Klicken Sie auf **Import All**
2. ALLE XML-Dateien im Working Directory werden importiert

**Wichtig:** Der Import überschreibt bestehende Blöcke mit gleichem Namen!

### Import/Export-Einstellungen

Klicken Sie auf das **Zahnrad-Symbol** (⚙) in der Toolbar, um den Dialog für Import/Export-Einstellungen zu öffnen. Dieser Dialog ermöglicht die Anpassung des Import- und Export-Verhaltens.

#### Import-Optionen

Diese Einstellungen steuern, wie Blöcke in Ihr TIA Portal Projekt importiert werden:

| Option | Was es bewirkt |
|--------|----------------|
| **Ignore Structural Changes** | Importiert Blöcke auch wenn sich ihre interne Struktur seit dem letzten Export geändert hat. Nützlich wenn die Block-Schnittstelle gleich ist, aber die interne Implementierung abweicht. |
| **Ignore Missing References** | Setzt den Import fort, wenn einige referenzierte Blöcke noch nicht im Projekt existieren. Hilfreich beim schrittweisen Import von Blöcken. |
| **Fault Tolerant Import** | Wenn ein Block nicht importiert werden kann, wird mit dem Rest fortgefahren. Empfohlen für große Imports, um die erfolgreichen Imports zu maximieren. |

#### Export-Optionen

Diese Einstellungen steuern, wie Blöcke exportiert werden:

| Option | Was es bewirkt |
|--------|----------------|
| **Export With Defaults** | Standardparameterwerte in den exportierten Dateien einschließen. Nützlich für vollständige Dokumentation. |
| **Export With ReadOnly** | Schreibgeschützte Eigenschaften in Exporte einschließen. |

#### SPL Export-Optionen (nur V20 und später)

SPL (SIMATIC Programming Language) Dateien sind textbasierte Quelldokumente, die einfacher zu lesen und zu vergleichen sind als XML.

| Option | Was es bewirkt |
|--------|----------------|
| **Export SCL As SPL** | SCL-Blöcke als textbasierte Quelldokumente (`.spl` Dateien) speichern |
| **Export AWL As SPL** | AWL/STL-Blöcke als textbasierte Quelldokumente speichern |
| **Export LAD/FBD As SPL** | Grafische Programmierblöcke (LAD, FBD, GRAPH) als textbasierte Dokumente speichern |

**Warum SPL Export verwenden?**
- **Bessere Lesbarkeit** - SPL-Dateien sind reiner Text, leicht lesbar in jedem Text-Editor
- **Versionskontrolle** - Sehen Sie genau, was sich zwischen Versionen in Git oder SVN geändert hat
- **Code-Review** - Einfacher, Änderungen Zeile für Zeile zu überprüfen

> **Hinweis:** SPL-Dateien dienen nur zur Ansicht und Versionskontrolle. Sie können nicht zurück in TIA Portal importiert werden. Diese Option erfordert TIA Portal V20 oder später.

#### Versionskontroll-Optionen

Diese Einstellungen helfen, sauberere Exporte für Git, SVN oder andere Versionskontrollsysteme zu erstellen. Sie entfernen Daten, die sich ändern, auch wenn sich der eigentliche Code nicht geändert hat.

| Option | Was es bewirkt |
|--------|----------------|
| **Exclude Document Info** | Metadaten entfernen, die sich bei jedem Export ändern |
| **Normalize Timestamps** | Alle Datumsangaben auf einen festen Wert setzen (1. Januar 2000), damit unveränderte Blöcke keine Unterschiede zeigen |
| **Clear Installed Products** | Maschinenspezifische Informationen aus Exporten entfernen |
| **Remove Object List** | Interne Tracking-Daten aus Code-Blöcken entfernen |
| **Normalize Whitespace** | Konsistente Textformatierung sicherstellen |

> **Tipp:** Wenn Sie Git oder SVN verwenden, aktivieren Sie alle Versionskontroll-Optionen. Dies verhindert "falsche Änderungen", bei denen Dateien unterschiedlich aussehen, obwohl sich der tatsächliche Code nicht geändert hat.

### Preview Diff

Die Preview Diff Funktion zeigt Unterschiede zwischen dem TIA Portal Projekt und dem Working Directory:

1. Klicken Sie auf **Preview Diff**
2. Die Anwendung vergleicht Fingerprints (Hashes) der Blöcke
3. Ein Fenster zeigt:
   - **Geändert** - Blöcke, deren Inhalt sich unterscheidet
   - **Neu in TIA** - Blöcke, die nur im Projekt existieren
   - **Gelöscht** - Blöcke, die nur im Working Directory existieren

### Compare (Manueller Vergleich)

Die Compare-Funktion ermöglicht einen detaillierten Zeilenvergleich zwischen einem TIA Portal Block und einer beliebigen XML-Datei.

**So verwenden Sie den manuellen Vergleich:**

1. Wählen Sie einen Block im linken Baum (TIA Projekt)
2. Wählen Sie eine XML-Datei im rechten Baum (Working Directory)
3. Klicken Sie auf **Compare**
4. Das Compare-Fenster öffnet sich und zeigt:
   - **Links (TIA Portal):** Name des ausgewählten Blocks
   - **Rechts (Dateisystem):** Name der ausgewählten Datei
5. Klicken Sie auf **Vergleich starten**
6. Der Diff-Viewer zeigt die Unterschiede Zeile für Zeile

**Vorteile des manuellen Vergleichs:**

- **Freie Zuordnung** - Vergleichen Sie beliebige Blöcke mit beliebigen Dateien, unabhängig vom Namen
- **Schneller Einzelvergleich** - Ideal für gezielte Überprüfungen ohne alle Dateien zu scannen
- **SCL-Unterstützung** - Falls verfügbar, wird automatisch die besser lesbare SCL-Datei verwendet

**Hinweis:** Im Gegensatz zu Preview Diff (Hash-basiert) führt Compare einen direkten Textvergleich durch. Der Block wird temporär exportiert und Zeile für Zeile mit der Datei verglichen.

### HMI Export/Import

Für Projekte mit HMI-Geräten (WinCC Unified, Comfort Panels, etc.):

**Export HMI Selected:**
1. Wählen Sie HMI-Elemente im linken Baum aus (unter dem HMI-Geräteknoten)
2. Klicken Sie auf **Export HMI Selected**
3. Ausgewählte Bildschirme, Vorlagen, Variablen, Skripte werden exportiert

**Export HMI All:**
1. Klicken Sie auf **Export HMI All**
2. Alle HMI-Elemente von allen HMI-Geräten werden exportiert

**Unterstützte HMI-Elemente:**
- Bildschirme und Popups
- Bildschirmvorlagen
- HMI-Variablentabellen
- VB-Skripte
- Verbindungen
- Textlisten
- Grafiklisten

### Hardware-Export

Hardware-Konfiguration als AML/XML exportieren:

1. Erweitern Sie den **Hardware**-Knoten im Projektbaum
2. Wählen Sie Geräte oder Module zum Export
3. Klicken Sie auf **Export Selected**

**Hinweis:** Der Hardware-Export erstellt AutomationML (.aml) Dateien, die reimportiert oder für Dokumentation verwendet werden können.

---

## 6. Project Tab

### Code-Anzeige

Wenn Sie einen Block im Projektbaum auswählen, wird sein Quellcode im Code-Editor angezeigt.

**Unterstützte Sprachen:**
- SCL (Structured Control Language)
- STL (Statement List)
- LAD/FBD (als XML-Darstellung)

### Block-Details Panel

Neben dem Code werden Metadaten angezeigt:
- **Block-Typ:** OB, FB, FC, DB
- **Nummer:** z.B. OB1, FB10
- **Sprache:** SCL, STL, LAD, FBD, GRAPH
- **Autor:** Falls verfügbar
- **Letzte Änderung:** Zeitstempel

### Suche im Projektbaum

Nutzen Sie das Suchfeld über dem Projektbaum, um Blöcke schnell zu finden:
- Suche nach Name
- Suche nach Nummer
- Groß-/Kleinschreibung wird ignoriert

---

## 7. Protected Items Tab

### Konzept

Das Schutz-System verhindert, dass wichtige Blöcke versehentlich überschrieben werden.

### Blöcke schützen

1. Wechseln Sie zum **Protected Items** Tab
2. Navigieren Sie zum gewünschten Block
3. Setzen Sie ein Häkchen beim Block

Geschützte Blöcke werden:
- Beim Import übersprungen
- Mit einem Schloss-Symbol markiert
- In der Schutzliste angezeigt

### Profile

Profile speichern Ihre Schutz-Konfiguration:

**Profil speichern:**
1. Konfigurieren Sie Ihre geschützten Blöcke
2. Klicken Sie auf **Save Profile**
3. Geben Sie einen Namen ein

**Profil laden:**
1. Klicken Sie auf **Load Profile**
2. Wählen Sie ein gespeichertes Profil

---

## 8. MCP Tab (KI-Integration)

### Was ist MCP?

Das Model Context Protocol (MCP) ermöglicht KI-Assistenten, auf Ihr TIA Portal Projekt zuzugreifen.

### MCP Server Status

Der Tab zeigt:
- **Server Status:** Running / Stopped
- **Verbundene Clients:** Anzahl aktiver Verbindungen
- **Verfügbare Tools:** Liste der MCP-Funktionen

### Verwendung mit KI-Assistenten

1. Starten Sie den MCP Server im TIA Openness Manager
2. Konfigurieren Sie Ihren KI-Assistenten mit der MCP-Server-Adresse
3. Der KI-Assistent kann nun:
   - Projektstruktur abfragen
   - Block-Code lesen
   - Analysen durchführen

---

## 9. Hardware Tab

Der Hardware Tab bietet eine umfassende Übersicht über alle Geräte in Ihrem TIA Portal Projekt mit der Möglichkeit, Netzwerkkonfigurationen anzuzeigen und zu bearbeiten.

### Geräteliste

Der Tab zeigt eine Tabelle mit allen Hardware-Geräten:

| Spalte | Beschreibung | Editierbar |
|--------|--------------|------------|
| Device | Gerätename aus dem Projekt | Nein |
| Device Type | SPS, HMI, Antrieb, Switch, etc. | Nein |
| PROFINET Name | PROFINET-Gerätename | Ja |
| Article Number | Siemens-Bestellnummer | Nein |
| Firmware Version | Aktuelle Firmware-Version | Nein |
| IP Address 1-4 | Bis zu 4 IP-Adressen pro Gerät | Ja |
| Input Addresses | E/A-Eingangsadressbereich | Ja |
| Output Addresses | E/A-Ausgangsadressbereich | Ja |

### Aktionen

**Refresh Hardware:**
Lädt die Geräteliste aus dem TIA Portal Projekt neu.

**Export to CSV:**
Exportiert die komplette Hardware-Liste als CSV-Datei für Dokumentation oder Weiterverarbeitung.

**Save Changes:**
Speichert geänderte PROFINET-Namen und IP-Adressen zurück ins TIA Portal Projekt.

### Unterstützte Gerätetypen

- S7-1200/1500 SPSen
- WinCC Unified HMI-Panels
- WinCC Comfort-Panels
- SINAMICS-Antriebe
- SCALANCE-Switches
- ET 200 dezentrale Peripherie
- Andere PROFINET-Geräte

### Hinweise

- Änderungen an PROFINET-Namen und IP-Adressen erfordern anschließendes Speichern des Projekts
- Einige Felder können je nach Gerätetyp schreibgeschützt sein
- WinCC Unified-Geräte werden vollständig unterstützt

---

## 10. Find Unused Blocks

### Funktion

Find Unused Blocks analysiert Ihr Projekt und findet Bausteine, die nirgends aufgerufen werden.

### Verwendung

1. Öffnen Sie ein Projekt
2. Klicken Sie auf **Find Unused Blocks** in der Toolbar
3. Die Analyse startet automatisch:
   - Phase 1: Blöcke sammeln
   - Phase 2: Nach XML exportieren
   - Phase 3: Call-Graph aufbauen
   - Phase 4: Unerreichbare Blöcke finden

### Ergebnis-Fenster

Ergebnisse sind in 8 Tabs organisiert:

**Standard-Blöcke:**
| Tab | Inhalt |
|-----|--------|
| Functions (FC/FB) | Ungenutzte Funktionen und Funktionsbausteine |
| Data Blocks (DB) | Ungenutzte globale Datenbausteine |
| UDTs | Ungenutzte benutzerdefinierte Datentypen |
| Variables/Tags | Ungenutzte PLC-Variablen |

**Safety-Blöcke (rot markiert):**
| Tab | Inhalt |
|-----|--------|
| Safety Functions | Ungenutzte F_FC/F_FB Blöcke |
| Safety DBs | Ungenutzte F_DB Blöcke |
| Safety UDTs | Ungenutzte Safety-Datentypen |
| Safety Tags | Ungenutzte Safety-Variablen |

### Aktionen

**Auswahl:**
- **Select All** - Wählt alle Einträge im aktuellen Tab
- **Deselect All** - Hebt Auswahl auf
- **Delete Selected** - Löscht nur ausgewählte Einträge

**Löschen nach Kategorie:**
- **Standard Blocks** - Löscht alle ungenutzten FC/FB
- **Data Blocks (DB)** - Löscht alle ungenutzten DBs
- **UDTs** - Löscht alle ungenutzten Datentypen
- **Tags** - Löscht alle ungenutzten Variablen

**Safety löschen (mit Warnung):**
- **⚠ Safety Blocks** - Löscht alle ungenutzten F_FC/F_FB
- **⚠ Safety DBs** - Löscht alle ungenutzten F_DBs
- **⚠ Safety UDTs** - Löscht alle ungenutzten F_UDTs
- **⚠ Safety Tags** - Löscht alle ungenutzten F_Tags

**Export:**
- **Export to Text** - Exportiert die Liste als Textdatei
- **Copy All** - Kopiert alle Einträge in die Zwischenablage

### Hinweise

- OBs (Organization Blocks) werden nie als "unused" markiert, da sie Einstiegspunkte sind
- Safety-Blöcke erfordern Safety-Login für vollständige Analyse
- Das Löschen von Safety-Blöcken erfordert Bestätigung aufgrund der Sicherheitsauswirkungen

---

## 11. Einstellungen

### Öffnen

Klicken Sie auf das **Zahnrad-Symbol** in der oberen rechten Ecke.

### Verfügbare Einstellungen

| Einstellung | Beschreibung |
|-------------|--------------|
| **Language** | Sprache der Benutzeroberfläche (Deutsch, Englisch, Französisch, Italienisch). Erfordert Neustart. |
| **Working Directory** | Standardordner für "Find Unused Blocks" Exporte |
| **Log Path** | Speicherort für Log-Dateien wenn Debug Logging aktiviert ist |
| **Debug Logging** | Aktiviert detaillierte Protokollierung für Fehlerbehebung |
| **Auto-Update Check** | Automatisch beim Programmstart nach neuen Versionen suchen |

> **Hinweis:** Die TIA Portal Version wird jetzt automatisch erkannt, wenn Sie ein Projekt öffnen oder sich mit einer laufenden Instanz verbinden. Eine manuelle Auswahl ist nicht mehr erforderlich.

### Ordnernamen-Anpassung

Passen Sie die Ordnernamen für Export-Pfade und Baumansicht an:

| TIA Portal Name | Standard Export-Name | Konfigurierbar |
|-----------------|----------------------|----------------|
| (Gerät) | Source | ✓ |
| Programmbausteine | Blocks | ✓ |
| PLC-Datentypen | Datatypes | ✓ |
| PLC-Variablen | Tags | ✓ |
| Technologieobjekte | Technology Objects | ✓ |
| Software Units | Software Units | ✓ |

### Source-Ordner Option

Die **"Create Source folder"** Checkbox steuert, ob Exporte einen Source-Ordner-Wrapper enthalten:

| Einstellung | Export-Pfad |
|-------------|-------------|
| ✓ Aktiviert | `WorkingDir/Source/PLC_1/Blocks/...` |
| ☐ Deaktiviert | `WorkingDir/PLC_1/Blocks/...` |

Diese Einstellung beeinflusst auch die Projektbaumstruktur und die Import-Pfaderkennung.

### Log-Dateien

Bei aktiviertem Debug Logging werden detaillierte Logs erstellt:
- Speicherort: Konfigurierbar in Einstellungen
- Format: `TIA_Openness_Log_YYYYMMDD_HHMMSS.txt`

---

## 12. Lizenzierung

### Lizenz-Tiers

| Feature | Basic (GRATIS) | Pro (€25/Mo) | Enterprise (€40/Mo) |
|---------|----------------|--------------|---------------------|
| Preis | Kostenlos | €25/Mo oder €250/Jahr | €40/Mo oder €400/Jahr |
| Dateien | 1 | 1.000 | Unbegrenzt |
| Export/Import | Ja | Ja | Ja |
| Block Compare | Ja | Ja | Ja |
| Code Editor | Ja | Ja | Ja |
| Find Unused | Nein | Ja | Ja |
| Safety Blocks | Nein | Ja | Ja |
| Protection Profiles | Nein | Ja | Ja |
| MCP Server | Nein | Ja | Ja |
| Multi-User | Nein | Nein | Ja |

### Lizenz aktivieren (Online)

1. Kaufen Sie eine Subscription (Pro oder Enterprise)
2. Sie erhalten einen Aktivierungscode per E-Mail
3. Klicken Sie auf **License** in der Toolbar
4. Geben Sie den Aktivierungscode ein
5. Klicken Sie auf **Activate**
6. Die Lizenz wird an Ihre Hardware gebunden

**Wichtig:** Die Software validiert die Lizenz alle 7 Tage online. Bei fehlender Internetverbindung kann die Software **bis zu 14 Tage offline** genutzt werden. Nach 14 Tagen ist eine erneute Online-Validierung erforderlich.

### Hardware-Bindung

Jede Lizenz ist an eine eindeutige Hardware-ID gebunden, die generiert wird aus:
- CPU-ID (Prozessor-Seriennummer)
- Mainboard-Seriennummer
- Primäre MAC-Adresse

### Subscription verwalten

- Klicken Sie auf **Manage Subscription** im License-Dialog
- Öffnet das Stripe-Portal für:
  - Zahlungsmethode ändern
  - Rechnungen herunterladen
  - Subscription kündigen

### Lizenz-Information anzeigen

Im License-Dialog sehen Sie:
- Aktueller Lizenz-Typ (Basic/Pro/Enterprise)
- Ablaufdatum der aktuellen Periode
- Hardware-ID
- Aktivierungscode

---

## 13. Fehlerbehebung & FAQ

### Häufige Probleme

#### "TIA Portal wird nicht gefunden"

**Ursache:** TIA Portal ist nicht installiert oder keine kompatible Version verfügbar.

**Lösung:**
1. Prüfen Sie, ob TIA Portal V15, V16, V17, V18, V19 oder V20 installiert ist
2. Stellen Sie sicher, dass die Openness-Komponenten installiert sind (Teil der TIA Portal Installation)

#### "Access denied" beim Öffnen

**Ursache:** Unzureichende Berechtigungen für den Zugriff auf TIA Portal oder die Projektdatei.

**Lösung:**
1. Führen Sie die Anwendung als Administrator aus
2. Stellen Sie sicher, dass die Projektdatei nicht schreibgeschützt ist
3. Prüfen Sie, ob keine andere Instanz das Projekt exklusiv geöffnet hat

#### "ObjectDisposedException" während Operation

**Ursache:** COM-Objekt wurde ungültig.

**Lösung:**
1. Schließen Sie das Projekt
2. Öffnen Sie es erneut
3. Bei großen Projekten: Verwenden Sie Attach Mode

#### Export dauert sehr lange

**Ursache:** Viele Blöcke oder langsame Festplatte.

**Lösung:**
1. Exportieren Sie in kleineren Batches
2. Verwenden Sie eine SSD
3. Schließen Sie andere Anwendungen

### FAQ

**F: Kann ich während des Exports in TIA Portal arbeiten?**
A: Nein. Bei Massenoperationen erscheint ein ExclusiveAccess-Dialog im TIA Portal, der die Benutzerinteraktion blockiert, bis die Operation abgeschlossen ist. Dies verhindert Konflikte und gewährleistet Datenintegrität.

**F: Werden Kommentare beim Export/Import erhalten?**
A: Ja, alle Block-Attribute werden in der XML-Datei gespeichert.

**F: Unterstützt die Anwendung Safety-Projekte?**
A: Ja, F-Blöcke werden vollständig unterstützt. Für einige Operationen ist ein Safety-Login erforderlich.

**F: Kann ich mehrere Projekte gleichzeitig öffnen?**
A: Nein, aktuell wird nur ein Projekt gleichzeitig unterstützt.

---

## Support

Bei weiteren Fragen oder Problemen kontaktieren Sie den Support:

- **E-Mail:** [tiaopenessmanager@outlook.com]
- **Dokumentation:** Siehe `Information/` Ordner

---

## Haftungsausschluss

Die Software wird „as is" geliefert. Der Anbieter übernimmt keine Haftung für:
- Schäden durch fehlerhafte LLM-Ausgaben
- Datenverlust oder Produktionsausfälle
- Engineering-Fehler oder fehlerhafte Code-Generierung
- Schäden durch unsachgemäße Nutzung

**Der Anwender trägt die volle Verantwortung für die Prüfung und Validierung aller generierten Inhalte.**

Siehe EULA und Haftungsausschluss auf https://www.tiaopenessmanager.ch für Details.

---

**© 2026 AnyAutomation. Alle Rechte vorbehalten.**

**Ende des Benutzerhandbuchs**
