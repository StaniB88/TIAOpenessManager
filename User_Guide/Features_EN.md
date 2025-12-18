# TIA Openness Manager - Feature Overview

## Product Description

The **TIA Openness Manager** is a powerful tool for Siemens TIA Portal developers that revolutionizes the export, import, and management of PLC program blocks. With an intuitive user interface and advanced features like difference comparison, protection profiles, and AI integration, it significantly increases productivity and reduces errors in project management.

---

## Main Features

### Import & Export

- **Bulk Export** - Export hundreds of blocks with a single click
- **Selective Export** - Choose exactly the blocks you need
- **XML & SCL Support** - Full support for Simatic ML and SCL files
- **Folder Structure Preservation** - TIA Portal folder structure is maintained
- **Automatic Compilation** - Automatically compiles and saves after import
- **Configurable Folder Names** - Customize export folder names (Source, Blocks, Tags, etc.)
- **Optional Source Folder** - Enable/disable the Source folder wrapper in exports

### HMI Export/Import

- **Screen Export** - Export HMI screens as XML
- **Screen Template Export** - Export reusable screen templates
- **HMI Tag Tables** - Export/import HMI tag tables
- **VB Scripts** - Export HMI VB scripts
- **Connections** - Export HMI connection configurations
- **Text Lists & Graphic Lists** - Full support for HMI lists

### Hardware Tab

- **Device List** - Complete overview of all devices (PLCs, HMIs, Drives, Switches)
- **PROFINET Names** - View and edit PROFINET device names directly
- **IP Addresses** - Display IP address configuration for all devices
- **Firmware Versions** - Show firmware version for each device
- **Article Numbers** - Display Siemens article/order numbers
- **I/O Mapping** - Show input/output address ranges
- **CSV Export** - Export complete hardware list to CSV for documentation
- **WinCC Unified Support** - Full support for WinCC Unified HMI panels

### Hardware Export

- **Device Configuration** - Export hardware configuration as XML
- **Module Configuration** - Export individual module settings
- **Network Configuration** - Export network/communication settings

### Watch/Force Tables

- **Table Export** - Export Watch Tables and Force Tables
- **Variable Lists** - Export monitored variable configurations
- **Debug Support** - Preserve debugging setups across projects

### Difference Comparison (Preview Diff)

- **Fingerprint-based** - Fast comparison without full export
- **Change Detection** - Detects modified, new, and deleted blocks
- **Detailed Diff Viewer** - Shows differences line by line
- **Selective Re-Export** - Export only changed blocks

### Code Editor

- **Integrated Editor** - View and edit block code directly
- **Syntax Highlighting** - For SCL, STL, and other languages
- **Block Details** - Shows metadata like number, language, author
- **Quick Navigation** - Search in project tree

### Protection System (Protected Items)

- **Block Protection** - Protect important blocks from accidental overwriting
- **Profiles** - Save and load protection configurations
- **Visual Marking** - Protected blocks are clearly marked
- **Hierarchical Protection** - Protect entire folders or individual blocks

### Find Unused Blocks

- **Dead Code Detection** - Finds unused blocks
- **Call-Graph Analysis** - Based on actual calls, not just references
- **Safety Block Support** - Also supports F-blocks (F_FB, F_FC, F_DB, F_OB)
- **Export Function** - Export results as CSV
- **Delete Function** - Remove unused blocks directly

### AI Integration (MCP Server)

- **Model Context Protocol** - Integration with Claude and other AI assistants
- **Project Context** - AI has access to your project structure
- **Code Generation** - AI can generate SCL source code for blocks
- **DB Generation** - AI can create Data Blocks with Simatic ML templates
- **UDT Generation** - AI can create User-Defined Types
- **Tag Table Generation** - AI can create Tag Tables
- **Auto Import** - Generated code can be automatically imported into TIA Portal
- **Block Analysis** - AI can read and analyze existing blocks

---

## Supported TIA Portal Versions

| Version | Status |
|---------|--------|
| TIA Portal V18 | Fully supported |
| TIA Portal V19 | Fully supported |
| TIA Portal V20 | Fully supported |

---

## Supported Block Types

### PLC Blocks
- **OB** - Organization Blocks (incl. F_OB)
- **FB** - Function Blocks (incl. F_FB)
- **FC** - Functions (incl. F_FC)
- **DB** - Data Blocks (Global, Instance, Array, incl. F_DB)
- **UDT** - User-Defined Data Types
- **Tag Tables** - Variable Tables
- **Technology Objects** - Motion Control, PID Controllers, Counters, etc.
- **Software Units** - V18+ Software Unit containers

### HMI Elements
- **Screens** - HMI screens and popups
- **Screen Templates** - Reusable screen templates
- **HMI Tag Tables** - HMI-specific tag tables
- **VB Scripts** - VB script functions
- **Connections** - PLC/HMI connections
- **Text Lists** - Multi-language text lists
- **Graphic Lists** - Graphic/symbol lists

### Hardware
- **Device Configuration** - Hardware setup as AML/XML

---

## License Options

### Trial (5 Days)
- All features available
- 1 file export/import limit
- Ideal for testing

### Basic
- 200 files export/import
- All block types
- Find Unused Blocks
- Block Compare

### Professional
- 1,000 files export/import
- Everything in Basic
- Protection Profiles
- MCP Server Integration
- Priority Support

### Enterprise
- Unlimited files
- Everything in Professional
- Multi-user licenses
- Dedicated support
- Volume discounts


- **Multi-language** - German, English, French, Italian

---

**Contact:** For licensing and questions, contact us at [TIAOpenessManager@outlook.com]
