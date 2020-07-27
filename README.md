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

### `signature_check`
- Highlight applications which are not code signed and applications that are [notarized](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution)
- Usage: `./signature_check`


### `x86_check`
- Check whole system for 32-bit Apps
- Usage: `./x86_check`

