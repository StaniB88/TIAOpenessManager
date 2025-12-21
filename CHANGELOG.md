# TIA Openness Manager - Changelog

## v1.1.5 (2025-12-21)

### Bug Fixes
- **Language Switching Fixed** - Language switching now works correctly in the installed version
  - Added missing language satellite assemblies to installer
  
## v1.1.4 (2025-12-21)

### Improvements
- **Simplified Activation** - Enter your activation code received via email to unlock Pro/Enterprise features
- **Free Basic Tier** - Basic tier is now permanently free (no trial expiration)

---

## v1.1.3 (2025-12-20)

### Bug Fixes
- **Auto-Update not working** - Added missing AutoUpdater.NET.dll to installer package (update feature was broken since v1.1.0)

---

## v1.1.2 (2025-12-20)

### Bug Fixes
- **FindUnused false positives on some machines** - Removed debug code that caused XML parsing to fail silently on machines without a specific folder structure

---

## v1.1.1 (2025-12-20)

### New Features
- **Clear Code Button** - New button to clear the code editor content
- **Clear Results Button** - New button to clear Find Unused results
- **Auto-Clear on Project Close** - Code editor and Find Unused results are automatically cleared when project is closed

### Bug Fixes
- **Instance DBs marked as unused** - FindUnused now correctly detects Instance DB references from FB calls (prevents false positives)
- **ObjectDisposedException after detach** - Fixed stale facade reference when detaching from attached TIA Portal instance

### Improvements
- **Import Progress Display** - Progress label now shows current file name being imported
- **About Dialog** - Added clickable GitHub link for easy access to the repository
- **Third-Party Licenses** - Added AutoUpdater.NET to the licenses list in About dialog and THIRD_PARTY_NOTICES.txt

---

## v1.1.0 (2025-12-20)

### New Features
- **Auto-Update Check** - Application now checks for updates at startup and notifies when a new version is available
- **Update Settings** - New checkbox in Settings to enable/disable automatic update checks

### Bug Fixes
- **Progress bar not fully filled** - Progress bar now shows 100% when operations complete (Analysis, Export, HMI Export)

---

## v1.0.1 (2025-12-18)

### Bug Fixes

- **Checkbox state lost during search/filter** - Checkboxes in left and right tree now persist when filtering or searching multiple times
- **Selection count incorrect with filter** - Import/Export selection count now correctly reflects checked items even when filter is active
- **Delete Selection fails with filter** - Delete operation now works correctly when tree is filtered
- **Single block import progress bar** - Progress bar now updates correctly for imports with less than 5 files
- **Right-click doesn't select item** - Right-clicking on a tree item now selects it before showing context menu
- **Missing Import button in right tree** - Added Import option to right tree context menu
- **FindUnused false positives** - Fixed reference detection for FC calls with direct Component pattern in XML
- **Fingerprint export progress** - Progress bar now includes fingerprint cache update phase after export
- **MCP Generate FC fails** - Fixed VAR section removal regex to only remove standalone VAR, not VAR_INPUT/VAR_OUTPUT/VAR_TEMP
