
# Entitlements

Collection of scripts for determining which [Entitlements](https://developer.apple.com/documentation/bundleresources/entitlements) macOS (Mach-O) binaries have.

Inspired by:
* [Cedric Owens](https://twitter.com/cedowens)'s [EntitlementCheck](https://github.com/cedowens/EntitlementCheck)
* [Jonathan Levin](https://twitter.com/morpheus______)'s [OS X/iOS Entitlement Database](http://newosxbook.com/ent.jl) 

For lists of and descriptions of Entitlements see:
* Apple Developer Documentation
  * [Bundle Resources > Entitlements](https://developer.apple.com/documentation/bundleresources/entitlements)
  * [Security > App Sandbox](https://developer.apple.com/documentation/security/app_sandbox)


# Hardened Runtime


## Sources
* [Notarization: the hardened runtime](https://eclecticlight.co/2021/01/07/notarization-the-hardened-runtime/) by [Howard Oakley](https://twitter.com/howardnoakley)
* [The ‘hardened runtime’ explained](https://eclecticlight.co/2019/08/10/the-hardened-runtime-explained/) by [Howard Oakley](https://twitter.com/howardnoakley)
* [Hardened Runtime](https://developer.apple.com/documentation/security/hardened_runtime) by Apple
* [Your Apps and the Future of macOS Security (WWDC2018 Session 702)](https://developer.apple.com/videos/play/wwdc2018/702/) (22:00 mark) by Apple

# Interesting Entitlements


## `com.apple.private.security.clear-library-validation` 
* Formerly `com.apple.security.cs.disable-library-validation`
* Can load arbitrary unsigned plugins/frameworks
* [About com.apple.private.security.clear-library-validation](https://theevilbit.github.io/posts/com.apple.private.security.clear-library-validation/) by [Csaba Fitzl](https://twitter.com/theevilbit)


## `com.apple.security.cs-allow-dyld-environment-variables`
* [Allow DYLD Environment Variables Entitlement](https://developer.apple.com/documentation/bundleresources/entitlements/com_apple_security_cs_allow-dyld-environment-variables/)
* Allows injecting Dynamic Libraries (dylib's) via the `DYLD_INSERT_LIBRARIES` environment variable
* [DYLD_INSERT_LIBRARIES DYLIB injection in macOS / OSX](https://theevilbit.github.io/posts/dyld_insert_libraries_dylib_injection_in_macos_osx_deep_dive/) by [Csaba Fitzl](https://twitter.com/theevilbit)


## `com.apple.security.get-task-allow`
* Allows other processes to attach via a debugger
## `com.apple.security.cs.allow-unsigned-executable-memory`
* [Allow Unsigned Executable Memory Entitlement](https://developer.apple.com/documentation/bundleresources/entitlements/com_apple_security_cs_allow-unsigned-executable-memory/)
* Allows overriding or patching C code
  * Via `NSCreateObjectFileImageFromMemory` (which is fundamentally insecure)
  * Or use the DVDPlayback framework
## `com.apple.security.files.downlaods.read-only`
* [`com.apple.security.files.downloads.read-only`](https://developer.apple.com/documentation/bundleresources/entitlements/com_apple_security_files_downloads_read-only/)
* May have access to files the user has selected in an open or save dialog
## `com.apple.security.files.downloads.read-write`
* May have access to files the user has selected in an open or save dialog
## `com.apple.security.files.all`
## `com.apple.security.files.user-selected.read-only`
## `com.apple.security.files.user-selected.read-write`
## `com.apple.private.tcc.allow`
* May have TCC access to some protected portions of the OS

