# TIA Openness Manager v1.0.1 - Release Notes

**Release Date:** 2025-12-18

## Bug Fixes

- **Checkbox state lost during search/filter** - Checkboxes in left and right tree now persist when filtering or searching multiple times
- **Selection count incorrect with filter** - Import/Export selection count now correctly reflects checked items even when filter is active
- **Delete Selection fails with filter** - Delete operation now works correctly when tree is filtered
- **Single block import progress bar** - Progress bar now updates correctly for imports with less than 5 files
- **Right-click doesn't select item** - Right-clicking on a tree item now selects it before showing context menu
- **Missing Import button in right tree** - Added Import option to right tree context menu
- **FindUnused false positives** - Fixed reference detection for FC calls with direct Component pattern in XML
- **Fingerprint export progress** - Progress bar now includes fingerprint cache update phase after export
- **MCP Generate FC fails** - Fixed VAR section removal regex to only remove standalone VAR, not VAR_INPUT/VAR_OUTPUT/VAR_TEMP
