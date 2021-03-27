# macos-scripts
Various scripts for macOS tasks

![Shellcheck](https://github.com/0xmachos/macos-scripts/workflows/Shellcheck/badge.svg)


### [`c0design`](https://github.com/0xmachos/macos-scripts/blob/master/c0design)
- Wrapper for `codesign`, `spctl`, `stapler` & `pkgutil`
- Check codesigning and notarisation of application or package (`.pkg`) at `$path_to_verify`
  - Equivalent of `codesign --verify --deep --strict` && `spctl --assess --type exec`
  - Equivalent of `pkgutil --check-signature` && `spctl --assess --type install`
- Check codesigning and notarisation of all non system (thirdparty) applications
- Usage: `./c0design {usage | list | verify $path_to_verify | thirdparty}`


### [`debug`](https://github.com/0xmachos/macos-scripts/blob/master/debug)
- Print some debug info about the current system
- Usage: `./debug`
- Usage: `./debug | pbcopy` (Copies output to the clipboard)


### [`detect-vmware`](https://github.com/0xmachos/macos-scripts/blob/master/detect-vmware)
- Try to determine if being run in a VMware Virtual Machine  
- Usage: `./detect-vmware`


### [`legacy-check`](https://github.com/0xmachos/macos-scripts/blob/master/legacy-check)
- Check system for 32-bit applications & third party kernel extensions
- Usage: `./legacy-check`


### [`office-macro-security`](https://github.com/0xmachos/macos-scripts/blob/master/office-macro-security)
- Disable/ restrict Microsoft Office macro execution
- Usage: `./office-macro-security {list | disable | restrict | both | undo}`


### [`pkg-expand`](https://github.com/0xmachos/macos-scripts/blob/master/pkg-expand)
- Expands package (`--expand-full`)
- Finds and expands embeded packages 
- Dumps Bill of Material (Bom) files 
- Usage: `./pkg-expand /tmp/example.pkg`

