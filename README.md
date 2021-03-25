# macos-scripts
Various scripts for macOS tasks

![Shellcheck](https://github.com/0xmachos/macos-scripts/workflows/Shellcheck/badge.svg)

### `debug`
- Print some debug info about the current system
- Usage: `./debug`
- Usage: `./debug | pbcopy` (Copies output to the clipboard)

### `detect-vmware`
- Try to determine if being run in a VMware Virtual Machine  
- Usage: `./detect-vmware`

### `office-macro-security`
- Disable/ restrict Microsoft Office macro execution
- Usage: `./office-macro-security {list | disable | restrict | both | undo}`

### `pkg-expand`
- Expands package (`--expand-full`)
- Finds and expands embeded packages 
- Dumps Bill of Material (Bom) files 
- Usage: `./pkg-expand /tmp/example.pkg`

### `c0design`
- Wrapper for `codesign`, `spctl` & `stapler`
- Check codesigning and notarisation of application at $application_path
  - Equivalent of `codesign --verify --deep --strict` && `spctl --assess --type exec`
- Check codesigning and notarisation of all non system (thirdparty) applications
- Usage: `./c0design {usage | list | verify $application_path | thirdparty}`


### `legacy-check`
- Check system for 32-bit applications & third party kernel extensions
- Usage: `./legacy-check`

