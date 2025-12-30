# TIA Openness Manager - Changelog

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
