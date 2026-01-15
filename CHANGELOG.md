# TIA Openness Manager - Changelog

## v1.2.3 (2026-01-15)

### New Features
- **Improved UI Responsiveness** - The application stays responsive during long operations
- **Auto-Detect TIA Version** - No longer need to manually select TIA Portal version in settings
- **Extended Attach Support** - Can now attach to TIA Portal V15, V16, V17, and V21 (previously only V18-V20)

### Improvements
- **Faster Import All** - Performance optimizations for large imports
- **Better Safety Block Detection** - Improved recognition of Safety tag tables
- **Cleaner About Window** - Simplified design

### Bug Fixes
- **Fixed Long Path Crash** - Protected against Windows MAX_PATH limitations
- **Fixed Protection Errors** - Resolved path conflicts during protection operations

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
