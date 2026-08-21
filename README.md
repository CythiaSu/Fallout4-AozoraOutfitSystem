# Fallout 4 Aozora Outfit System

Source repository for **Aozora Outfit Management System 2.0.3**.

This project is an upgrade of Fallout4 Outfit Manager. It provides outfit
slots, outfit preview and confirmation, material-swap previews for supported
mod clothing, NPC/player outfit management, and optional weapon preservation.

## Source Layout

```text
CHS/2.0.3/      Chinese source and UI configuration
EN/2.0.3/       English source and UI configuration
tools/           Asset and UI validation utilities
docs/            Build and release notes
```

The native logic is kept aligned between CHS and EN. The language-specific
native files contain localized messages and slot-name comments. Papyrus and
UI sources are kept separately so either language can be packaged without
mixing files.

## Requirements

- Fallout 4 Script Extender (F4SE)
- Address Library for F4SE Plugins
- Mod Configuration Menu (MCM)
- Prisma UI Framework 2.0.3 or a compatible later 2.x version
- Garden of Eden Papyrus Script Extender (GOE)
- Visual Studio 2022 x64 toolchain for the native plugin
- CommonLibF4 and spdlog build dependencies
- Caprica or an equivalent Fallout 4 Papyrus compiler

## Build Notes

The native project uses `xmake.lua` and CommonLibF4. Build each language
variant from its own `Native` directory. Papyrus sources are under each
language's `Papyrus/Source/User` directory and are compiled separately.

The repository intentionally does not include generated DLL, PEX, ESP, object,
library, build-cache files, or release-only mascot images. The release package
is assembled from the selected language source, its UI/MCM files, and the
mascot assets kept with the stable release package.

The UI is keyboard/gamepad driven in this stable release. Mouse input remains
disabled because of the Prisma UI 2.x focus regression.

## Compatibility Scope

Material Swap support primarily targets mod clothing that exposes material
variants through MSWP records. Workbench or third-party modifications can be
restored when the final item is represented by a base item plus OMOD data;
script-driven or other custom runtime data cannot be guaranteed.

The system supports 500 outfit slots and preserves the existing OutfitManager
plugin/data identifiers for global outfit data compatibility.
