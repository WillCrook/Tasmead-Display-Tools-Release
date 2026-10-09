# Tasmead Display Tools

Legal information and third-party notices

Copyright © 2026 Will Crook. Tasmead-specific code is proprietary. See the
[Tasmead licence](LICENSE). Third-party components retain their own licences
and copyrights.

## Open-source components

Tasmead uses PySide6, Shiboken6 and Qt, copyright The Qt Company Ltd. and
other contributors, under the [GNU LGPLv3](licenses/LGPL-3.0-only.txt). The
[GPLv3 text](licenses/GPL-3.0-only.txt) is included because LGPLv3 incorporates
it; this does not put Tasmead-specific code under the GPL.

Qt WebEngine incorporates Chromium and separately licensed components,
including portions covered by [LGPLv2.1](licenses/LGPL-2.1-or-later.txt).
GNU libintl also uses LGPLv2.1-or-later. Certifi uses the
[Mozilla Public License 2.0](licenses/native-extra/MPL-2.0.txt).

Other components include Python, NumPy, pandas, pyproj/PROJ, python-dateutil,
pytz, six, packaging, setuptools and its collected dependencies, OpenSSL,
libb2, libjpeg-turbo, libtiff, liblzma and Zstandard. Their copyright
statements and licence texts are available below. The PyInstaller bootloader's
licence exception permits proprietary application packaging.

This software is based in part on the work of the Independent JPEG Group.

## Release information and third-party sources

Visit the [Tasmead release page](https://github.com/WillCrook/Tasmead-Display-Tools-Release/releases)
for release information and third-party source downloads. Choose the release
matching your application download. Each published release identifies its
corresponding source ZIP and provides the build and library replacement
information for that release.

The source ZIP is optional for normal use. It contains the covered third-party
sources, applicable patches, upstream build scripts and a README with build
instructions. It does not contain Tasmead's proprietary source.

## Your rights concerning LGPL components

You may modify or replace the LGPL components and reverse engineer Tasmead to
debug those modifications, as provided by their licences. Tasmead's proprietary
terms do not restrict those rights.

## Replacing LGPL libraries on macOS

1. Work on a copy of `Tasmead Display Tools.app`. In Finder, choose **Show
   Package Contents**. Shared libraries are under `Contents/Frameworks`;
   preserve framework structure and symlinks.

2. Build compatible replacements using the matching source ZIP's README and
   supplied build material. Follow that release's architecture, Python and
   Qt/PySide/Shiboken versions and signing instructions. Keep ABI, library
   names, dependencies and relative loader paths compatible.

3. Replace the relevant files:
   - PySide extensions and `libpyside6` are in `PySide6/`.
   - Qt frameworks are in `PySide6/Qt/lib/`.
   - Plugins are in `PySide6/Qt/plugins/`.
   - Shiboken is in `shiboken6/`.
   - `libintl.8.dylib` is directly in `Contents/Frameworks`.
   - PySide/Shiboken Python support files are external files, with symlinks
     into `Contents/Resources`.
   - WebEngine replacements may also require the matching helper, plugins and
     resources.

4. Match the original Mach-O load paths using `otool -L`, `otool -l` and
   `install_name_tool`. PyInstaller thins universal binaries and rewrites
   library identities; the source ZIP includes its path-normalization
   implementation and instructions.

5. Changes invalidate the original signature. Follow the matching release's
   instructions to re-sign and run your modified copy. For an ad-hoc-signed
   local copy, the signing commands are:

   ```sh
   codesign --force --deep --sign - "/path/to/Modified Tasmead Display Tools.app"
   codesign --verify --deep --strict "/path/to/Modified Tasmead Display Tools.app"
   ```

For other signing configurations, sign nested libraries/frameworks and the
WebEngine helper before the outer app. The original distributor's signature
and notarization do not apply to your modified copy. Use macOS's normal
explicit opening/approval procedure where applicable; system-wide security
protections do not need to be disabled.

## Copyright and licence texts

The collections below preserve upstream notices. Some cover optional
components and other platforms; a notice's inclusion does not mean that every
component described by it is part of this application.

- [Qt and PySide notices](licenses/qt-6.10.2/index.html)
- [Chromium notices](licenses/chromium-6.10.2/notices.html)

## Code and icons used by Tasmead

Debris trajectory calculations incorporate work from
[mkarachalios-1/airshow-trajectory-app](https://github.com/mkarachalios-1/airshow-trajectory-app),
copyright (c) 2025, under the
[MIT licence](licenses/airshow-trajectory-app-MIT.txt).

Six outline icons are from Tabler Icons, copyright (c) 2020–2026 Paweł Kuna,
under the [MIT licence](licenses/Tabler-Icons-MIT.txt).