# TIA Openness Manager - Changelog

## v1.2.4 (2026-01-17)

### New Features
- **Compare Files** - Added file comparison feature for exported projects (same-side comparison)
- **Open Exported Project** - Left tree now supports opening exported project folders

### Bug Fixes
- **Instance DB Import** - Fixed import errors ("Element cannot be found") when importing Instance DBs after SCL compilation

### Improvements
- **Compare Tab** - Removed auto-tab-jump behavior, added green highlight for Graphic tab selection

---

## v1.2.3 (2026-01-16)

### Security
- **Enhanced Clock Manipulation Detection** - Now detects both backward and forward system clock manipulation attempts
- **Server-Time Validation** - Additional check compares local time against server expiry date to prevent bypass attempts

### Improvements
- **Installer: Extended TIA Version Check** - Installer now checks for TIA Portal V15-V20 (previously only V18-V20)

---

## v1.2.2 (2026-01-02)

### Bug Fixes
- **Remove V21 from Settings** - Removed TIA Portal V21 option from API version dropdown to prevent crashes (V21 support not yet stable)

---

## v1.2.1 (2026-01-01)

### New Features
- **Legal Document Access** - Quick access to Privacy Policy and EULA directly from the About Window
- **Website Link** - Clickable website link in About Window opens [tiaopenessmanager.ch](https://tiaopenessmanager.ch)

### Bug Fixes
- **Find Unused** - Fixed incorrect detection of Instance DBs

### Improvements
- About Window redesigned with action buttons for better usability
- Updated User Guides with latest documentation 

## v1.2.0 (2025-12-30)

Various bugfixes, performance optimizations, and stability improvements.

---

## v1.1.7 (2025-12-30)

### New Features
- **Import/Export Settings Window** - New dialog for configuring import and export behavior
- **SPL Export Support** - Export SCL/AWL/LAD/FBD blocks as SIMATIC Source Documents (.spl format, V20+)
- **Export Options** - Configure export with defaults and read-only attributes
- **Import Options** - Ignore structural changes and missing references during import

### Improvements
- **Safety Block Detection** - Improved detection of Safety blocks in S7DCL format (V20 Update 4+)

### Technical
- Added ExportBlockToSplAsync method for SIMATIC Source Document export
- Updated documentation with V21 references for future releases

---

## v1.1.6 (2025-12-22)

### New Features
- **7-Day Full Trial** - New users get a 7-day trial with ALL features unlocked (Enterprise-level)

## v1.1.5 (2025-12-21)

### Bug Fixes
- **Language Switching Fixed** - Language switching now works correctly in the installed version
  - Added missing language satellite assemblies to installer
