# TIA Openness Manager - User Manual

**Version:** 1.0
**Date:** December 2025

---

## Table of Contents

1. [Introduction](#1-introduction)
2. [Installation & System Requirements](#2-installation--system-requirements)
3. [User Interface](#3-user-interface)
4. [Project Management](#4-project-management)
5. [Import/Export Tab](#5-importexport-tab)
6. [Project Tab](#6-project-tab)
7. [Protected Items Tab](#7-protected-items-tab)
8. [MCP Tab (AI Integration)](#8-mcp-tab-ai-integration)
9. [Hardware Tab](#9-hardware-tab)
10. [Find Unused Blocks](#10-find-unused-blocks)
11. [Settings](#11-settings)
12. [Licensing](#12-licensing)
13. [Troubleshooting & FAQ](#13-troubleshooting--faq)

---

## 1. Introduction

### What is TIA Openness Manager?

TIA Openness Manager is a desktop application that uses the Siemens TIA Portal Openness API to export, import, and manage PLC program blocks. It provides a user-friendly alternative to manual export/import operations directly in TIA Portal.

### Main Use Cases

- **Version Control** - Export blocks as XML for Git/SVN
- **Project Migration** - Transfer blocks between projects
- **Backup** - Create regular backups of your program blocks
- **Code Review** - Compare changes with the Preview Diff function
- **Cleanup** - Find and remove unused blocks

---

## 2. Installation & System Requirements

### System Requirements

| Component | Requirement |
|-----------|-------------|
| Operating System | Windows 10/11 (64-bit) |
| TIA Portal | V18, V19, V20, or V21 |
| .NET Framework | 4.8 or higher |
| RAM | Minimum 4 GB (8 GB recommended) |
| Disk Space | 500 MB |

### Installation

1. Download the TiaOpennessManager archive
2. Extract the archive to a folder of your choice (e.g., `C:\Tools\TiaOpennessManager`)
3. Run `TiaOpennessManager.exe`

> **Note:** No separate installation is required. The application is portable. TIA Portal must be installed on the system.

---

## 3. User Interface

### Main Window Overview

The application is divided into several areas:

```
┌─────────────────────────────────────────────────────────────┐
│  [Open] [Attach] [Close]              [Settings] [License]  │
├─────────────┬───────────────────────────────────────────────┤
│             │  [Editor] [Import/Export] [Protected] [MCP]   │
│  Project    ├───────────────────────────────────────────────┤
│  Tree       │                                               │
│             │              Tab Content                      │
│  (Left)     │                                               │
│             │                                               │
├─────────────┴───────────────────────────────────────────────┤
│  Status Bar with Progress Indicator                         │
└─────────────────────────────────────────────────────────────┘
```

### Left Panel - Project Tree

- Shows the structure of the opened TIA Portal project
- Hierarchy: Project → Hardware → Source → PLC → Blocks/Datatypes/Tags
- Checkboxes enable multiple selection for export

### Right Panel - Tabs

- **Project** - Code editor for selected blocks
- **Import/Export** - Main workspace for file operations
- **Find Unused** - Dead code detection and cleanup
- **MCP** - AI integration status
- **Hardware** - Device list with PROFINET names and IP configuration

### Toolbar

| Icon | Function |
|------|----------|
| Open Project | Opens a TIA Portal project |
| Attach to Portal | Connects to running TIA Portal |
| Close | Closes the current project |
| Settings | Opens settings |
| License | Shows license information |

---

## 4. Project Management

### Open Project (Headless Mode)

1. Click **Open Project**
2. Navigate to the project file (`.ap18`, `.ap19`, `.ap20`)
3. Click **Open**

Headless Mode starts TIA Portal in the background without a visible user interface. This is faster for pure export/import operations.

### Connect to TIA Portal (Attach Mode)

1. Open your project in TIA Portal
2. In TIA Openness Manager, click **Attach to Portal**
3. Select the desired project from the list

**Advantages of Attach Mode:**
- Faster connection (no project loading)
- You can work in TIA Portal simultaneously
- Changes are immediately visible

**Note:** For large bulk operations (25+ files), the application automatically switches to Attach Mode for better stability.

### Archive Project

Creates a compressed archive (.zap file) of the current project:

1. Click **Archive Project** in the toolbar
2. Select a destination folder
3. The project is archived with all associated files

**Note:** The project must be saved before archiving.

### Safety Printout

Generates a safety documentation printout for F-blocks:

1. Ensure you are logged in with Safety credentials (click **Safety Login** first)
2. Click **Safety Printout** in the Tree Controls area
3. Select a destination folder
4. A PDF is generated with all safety-relevant documentation

**Note:** This feature requires an active Safety login and is only available for projects with F-blocks.

### Close Project

Click **Close** to close the project. In Headless Mode, TIA Portal will be terminated.

---

## 5. Import/Export Tab

The Import/Export Tab is the heart of the application.

### Layout

```
┌──────────────────┬──────────────────┬───────────────────────┐
│   TIA Project    │    Actions       │   Working Directory   │
│   (Left)         │    (Center)      │   (Right)             │
├──────────────────┼──────────────────┼───────────────────────┤
│ □ Blocks         │ Export Selected→ │ [Refresh] [Path: ...] │
│   □ Main [OB1]   │ Export All →     │ □ Main.xml            │
│   □ Motor [FB1]  │                  │ □ Motor.xml           │
│   □ Calc [FC1]   │ ← Import Selected│ □ Calc.xml            │
│ □ Datatypes      │ ← Import All     │                       │
│ □ Tags           │                  │                       │
└──────────────────┴──────────────────┴───────────────────────┘
```

### Right Directory (Export/Import Directory)

The Right Directory is the folder on your file system where exported XML files are stored and from which files are imported.

**Setting:**
1. Click **...** next to the "Right directory" field
2. Select a folder
3. The folder is saved with the Profile and loaded on each start

**Tip:** Use a Git repository folder for automatic version control.

> **Note:** The "Working Directory" in Settings refers to the "Find Unused Blocks" function and is a separate folder.

### Export Operations

#### Export Selected
1. Check the boxes next to the desired blocks in the left tree
2. Click **Export Selected**
3. The selected blocks are exported as XML

#### Export All
1. Click **Export All**
2. ALL blocks, data types, and tag tables are exported

### Import Operations

#### Import Selected
1. Check the boxes next to the desired XML files in the right tree
2. Click **Import Selected**
3. The selected files are imported

#### Import All
1. Click **Import All**
2. ALL XML files in the Working Directory are imported

**Important:** Import overwrites existing blocks with the same name!

### Import/Export Options

The toolbar above the right tree provides options to customize import and export behavior:

**Import Options:**

| Option | Description |
|--------|-------------|
| Ignore Structural Changes | Ignores structure modifications when importing |
| Ignore Missing References | Continues import even if referenced objects are missing |

**Export Options:**

| Option | Description |
|--------|-------------|
| Export With Defaults | Includes default values in the exported XML |
| Export With Read Only | Marks exported blocks as read-only |

These options help resolve common import issues and customize export behavior for version control.

**S7DCL Export Options (TIA Portal V20+ only):**

The S7DCL (SIMATIC 7 Declaration Language) export feature provides additional text-based exports alongside the standard XML and source code files.

| Option | Description | Export Result |
|--------|-------------|---------------|
| SCL + S7DCL | Additionally export SCL blocks as S7DCL format | `.xml` + `.scl` + `.s7dcl` |
| AWL + S7DCL | Additionally export AWL/STL blocks as S7DCL format | `.xml` + `.awl` + `.s7dcl` |
| LAD/FBD + S7DCL | Additionally export LAD/FBD/GRAPH blocks as S7DCL format | `.xml` + `.s7dcl` |

**Why use S7DCL export?**
- **Better readability:** Text-based format ideal for code review
- **Version control:** Perfect for diff comparison in Git/SVN
- **Multi-format:** Keep both standard formats AND S7DCL for maximum compatibility
- **Graphical languages:** Enables text export for LAD/FBD blocks (normally only XML)

**Important Notes:**
- S7DCL files (`.s7dcl`) are **export-only** - they **cannot be re-imported** into TIA Portal
- The checkboxes enable **additional** exports, not replacements - you always get the standard formats
- For LAD/FBD blocks, S7DCL provides a text representation that would otherwise not exist
- S7DCL export requires TIA Portal V20 or higher

**Access S7DCL Settings:**
Click the **gear icon** (⚙) in the toolbar above the right tree to open Import/Export Settings.

### Preview Diff

The Preview Diff function shows differences between the TIA Portal project and the Working Directory:

1. Click **Preview Diff**
2. The application compares fingerprints (hashes) of blocks
3. A window shows:
   - **Changed** - Blocks whose content differs
   - **New in TIA** - Blocks that only exist in the project
   - **Deleted** - Blocks that only exist in the Working Directory

### Compare (Manual Comparison)

The Compare function allows a detailed line-by-line comparison between a TIA Portal block and any XML file.

**How to use manual comparison:**

1. Select a block in the left tree (TIA Project)
2. Select an XML file in the right tree (Working Directory)
3. Click **Compare**
4. The Compare window opens and shows:
   - **Left (TIA Portal):** Name of the selected block
   - **Right (Filesystem):** Name of the selected file
5. Click **Start Compare**
6. The diff viewer shows differences line by line

**Advantages of manual comparison:**

- **Free matching** - Compare any block with any file, regardless of name
- **Quick single comparison** - Ideal for targeted checks without scanning all files
- **SCL support** - If available, the more readable SCL file is automatically used

**Note:** Unlike Preview Diff (hash-based), Compare performs a direct text comparison. The block is temporarily exported and compared line by line with the file.

### HMI Export/Import

For projects with HMI devices (WinCC Unified, Comfort Panels, etc.):

**Export HMI Selected:**
1. Select HMI elements in the left tree (under the HMI device node)
2. Click **Export HMI Selected**
3. Selected screens, templates, tags, scripts are exported

**Export HMI All:**
1. Click **Export HMI All**
2. All HMI elements from all HMI devices are exported

**Supported HMI Elements:**
- Screens and Popups
- Screen Templates
- HMI Tag Tables
- VB Scripts
- Connections
- Text Lists
- Graphic Lists

### Hardware Export

Export hardware configuration as AML/XML:

1. Expand the **Hardware** node in the project tree
2. Select devices or modules to export
3. Click **Export Selected**

**Note:** Hardware export creates AutomationML (.aml) files that can be re-imported or used for documentation.

---

## 6. Project Tab

### Code Display

When you select a block in the project tree, its source code is displayed in the code editor.

**Supported Languages:**
- SCL (Structured Control Language)
- STL (Statement List)
- LAD/FBD (as XML representation)

### Block Details Panel

Metadata is displayed next to the code:
- **Block Type:** OB, FB, FC, DB
- **Number:** e.g., OB1, FB10
- **Language:** SCL, STL, LAD, FBD, GRAPH
- **Author:** If available
- **Last Modified:** Timestamp

### Project Tree Search

Use the search field above the project tree to quickly find blocks:
- Search by name
- Search by number
- Case-insensitive

---

## 7. Protected Items Tab

### Concept

The protection system prevents important blocks from being accidentally overwritten.

### Protecting Blocks

1. Switch to the **Protected Items** tab
2. Navigate to the desired block
3. Check the box next to the block

Protected blocks will:
- Be skipped during import
- Be marked with a lock icon
- Appear in the protection list

### Profiles

Profiles save your protection configuration:

**Save Profile:**
1. Configure your protected blocks
2. Click **Save Profile**
3. Enter a name

**Load Profile:**
1. Click **Load Profile**
2. Select a saved profile

---

## 8. MCP Tab (AI Integration)

### What is MCP?

The Model Context Protocol (MCP) allows AI assistants like Claude to access your TIA Portal project.

### MCP Server Status

The tab shows:
- **Server Status:** Running / Stopped
- **Connected Clients:** Number of active connections
- **Available Tools:** List of MCP functions

### Usage with Claude

1. Start the MCP Server in TIA Openness Manager
2. Configure Claude with the MCP server address
3. Claude can now:
   - Query project structure
   - Read block code
   - Perform analyses

---

## 9. Hardware Tab

The Hardware Tab provides a comprehensive overview of all devices in your TIA Portal project with the ability to view and edit network configuration.

### Device List

The tab displays a table with all hardware devices:

| Column | Description | Editable |
|--------|-------------|----------|
| Device | Device name from project | No |
| Device Type | PLC, HMI, Drive, Switch, etc. | No |
| PROFINET Name | PROFINET device name | Yes |
| Article Number | Siemens order number | No |
| Firmware Version | Current firmware version | No |
| IP Address 1-4 | Up to 4 IP addresses per device | Yes |
| Input Addresses | I/O input address range | Yes |
| Output Addresses | I/O output address range | Yes |

### Actions

**Refresh Hardware:**
Reloads the device list from the TIA Portal project.

**Export to CSV:**
Exports the complete hardware list to a CSV file for documentation or further processing.

**Save Changes:**
Saves modified PROFINET names and IP addresses back to the TIA Portal project.

### Supported Device Types

- S7-1200/1500 PLCs
- WinCC Unified HMI Panels
- WinCC Comfort Panels
- SINAMICS Drives
- SCALANCE Switches
- ET 200 distributed I/O
- Other PROFINET devices

### Notes

- Changes to PROFINET names and IP addresses require the project to be saved afterward
- Some fields may be read-only depending on device type
- WinCC Unified devices are fully supported

---

## 10. Find Unused Blocks

### Function

Find Unused Blocks analyzes your project and finds blocks that are never called.

### Usage

1. Open a project
2. Click **Find Unused Blocks** in the toolbar
3. The analysis starts automatically:
   - Phase 1: Collect blocks
   - Phase 2: Export to XML
   - Phase 3: Build call graph
   - Phase 4: Find unreachable blocks

### Results Window

Results are organized in 8 tabs:

**Standard Blocks:**
| Tab | Content |
|-----|---------|
| Functions (FC/FB) | Unused functions and function blocks |
| Data Blocks (DB) | Unused global data blocks |
| UDTs | Unused user-defined data types |
| Variables/Tags | Unused PLC tags |

**Safety Blocks (marked in red):**
| Tab | Content |
|-----|---------|
| Safety Functions | Unused F_FC/F_FB blocks |
| Safety DBs | Unused F_DB blocks |
| Safety UDTs | Unused safety data types |
| Safety Tags | Unused safety tags |

### Actions

**Selection:**
- **Select All** - Selects all items in current tab
- **Deselect All** - Deselects all items
- **Delete Selected** - Deletes only selected items

**Delete by Category:**
- **Standard Blocks** - Delete all unused FC/FB
- **Data Blocks (DB)** - Delete all unused DBs
- **UDTs** - Delete all unused data types
- **Tags** - Delete all unused tags

**Delete Safety (with warning):**
- **⚠ Safety Blocks** - Delete all unused F_FC/F_FB
- **⚠ Safety DBs** - Delete all unused F_DBs
- **⚠ Safety UDTs** - Delete all unused F_UDTs
- **⚠ Safety Tags** - Delete all unused F_Tags

**Export:**
- **Export to Text** - Exports the list as a text file
- **Copy All** - Copies all items to clipboard

### Notes

- OBs (Organization Blocks) are never marked as "unused" since they are entry points
- Safety blocks require Safety login for complete analysis
- Deleting safety blocks requires confirmation due to safety implications

---

## 11. Settings

### Opening

Click the **Gear icon** in the upper right corner.

### Available Settings

| Setting | Description |
|---------|-------------|
| Working Directory | Default export folder for Find Unused Blocks |
| Language | User interface language (EN, DE, FR, IT) |
| TIA Portal Version | Select V18, V19, or V20 API |
| Theme | Color scheme (only Dark Theme available) |
| Debug Logging | Enables extended logging |
| Log Path | Path for log files |

### Folder Name Customization

Customize the folder names used in export paths and tree view:

| TIA Portal Name | Default Export Name | Configurable |
|-----------------|---------------------|--------------|
| (Device) | Source | ✓ |
| Program blocks | Blocks | ✓ |
| PLC data types | Datatypes | ✓ |
| PLC tags | Tags | ✓ |
| Technology objects | Technology Objects | ✓ |
| Software units | Software Units | ✓ |

### Create Source Folder Option

The **"Create Source folder"** checkbox controls whether exports include a Source folder wrapper:

| Setting | Export Path |
|---------|-------------|
| ✓ Enabled | `WorkingDir/Source/PLC_1/Blocks/...` |
| ☐ Disabled | `WorkingDir/PLC_1/Blocks/...` |

This setting also affects the project tree structure and import path detection.

### Log Files

When Debug Logging is enabled, detailed logs are created:
- Location: Configurable in settings
- Format: `TIA_Openness_Log_YYYYMMDD_HHMMSS.txt`

---

## 12. Licensing

### License Tiers

| Feature | Basic (FREE) | Pro (€25/mo) | Enterprise (€40/mo) |
|---------|--------------|--------------|---------------------|
| Price | Free forever | €25/mo or €250/year | €40/mo or €400/year |
| Files | 1 | 1,000 | Unlimited |
| Export/Import | Yes | Yes | Yes |
| Block Compare | Yes | Yes | Yes |
| Code Editor | Yes | Yes | Yes |
| Find Unused | No | Yes | Yes |
| Safety Blocks | No | Yes | Yes |
| Protection Profiles | No | Yes | Yes |
| MCP Server | No | Yes | Yes |
| Multi-User | No | No | Yes |

### Activate License (Online)

1. Purchase a subscription (Pro or Enterprise)
2. You will receive an activation code via email
3. Click **License** in the toolbar
4. Enter the activation code
5. Click **Activate**
6. The license will be bound to your hardware

**Important:** The software validates the license every 7 days online. If no internet connection is available, the software can be used **offline for up to 14 days**. After 14 days, a new online validation is required.

### Hardware Binding

Each license is bound to a unique hardware ID generated from:
- CPU ID (Processor Serial Number)
- Motherboard Serial Number
- Primary MAC Address

### Manage Subscription

- Click **Manage Subscription** in the License dialog
- Opens the Stripe portal for:
  - Changing payment method
  - Downloading invoices
  - Canceling subscription

### View License Information

In the License dialog, you can see:
- Current license type (Basic/Pro/Enterprise)
- Current period expiry date
- Hardware ID
- Activation code

---

## 13. Troubleshooting & FAQ

### Common Problems

#### "TIA Portal not found"

**Cause:** TIA Portal is not installed or wrong version.

**Solution:**
1. Check if TIA Portal V18, V19, or V20 is installed
2. Make sure the Openness components are installed

#### "Access denied" when opening

**Cause:** Insufficient permissions to access TIA Portal or the project file.

**Solution:**
1. Run the application as Administrator
2. Ensure the project file is not read-only
3. Check that no other instance has the project open exclusively

#### "ObjectDisposedException" during operation

**Cause:** COM object became invalid.

**Solution:**
1. Close the project
2. Open it again
3. For large projects: Use Attach Mode

#### Export takes very long

**Cause:** Many blocks or slow hard drive.

**Solution:**
1. Export in smaller batches
2. Use an SSD
3. Close other applications

### FAQ

**Q: Can I work in TIA Portal during export?**
A: No. During bulk operations, an ExclusiveAccess dialog appears in TIA Portal that blocks user interaction until the operation completes. This prevents conflicts and ensures data integrity.

**Q: Are comments preserved during export/import?**
A: Yes, all block attributes are stored in the XML file.

**Q: Does the application support Safety projects?**
A: Yes, F-blocks are fully supported. Some operations require Safety login.

**Q: Can I open multiple projects at once?**
A: No, currently only one project at a time is supported.

---

## Support

For further questions or problems, contact support:

- **Email:** [tiaopenessmanager@outlook.com]
- **Documentation:** See `Information/` folder

---

## Disclaimer

The software is provided "as is". The provider assumes no liability for:
- Damages caused by faulty LLM outputs
- Data loss or production downtime
- Engineering errors or faulty code generation
- Damages caused by improper use

**The user bears full responsibility for reviewing and validating all generated content.**

See EULA and Disclaimer at https://www.tiaopenessmanager.ch for details.

---

**© 2025 AnyAutomation. All rights reserved.**

**End of User Manual**
