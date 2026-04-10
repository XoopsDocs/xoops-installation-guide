# XOOPS 2.7.0 Compatibility Review For This Guide

This document lists the changes needed in this repository so the Installation Guide matches XOOPS 2.7.0.

Review basis:

- Current guide repository: `L:\GitHub\XoopsDocs\xoops-installation-guide`
- XOOPS 2.7.0 core reviewed at: `L:\GitHub\MAMBAX7\CORE\XoopsCore27`
- Primary 2.7.0 sources checked:
  - `README.md`
  - `release_notes.txt`
  - `htdocs/install/language/english/welcome.php`
  - `htdocs/install/include/config.php`
  - `htdocs/install/include/page.php`
  - `htdocs/install/class/pathcontroller.php`
  - `htdocs/install/page_dbsettings.php`
  - `htdocs/install/page_configsave.php`
  - `htdocs/install/page_siteinit.php`
  - `htdocs/install/page_end.php`
  - `htdocs/mainfile.dist.php`
  - `upgrade/preflight.php`
  - `upgrade/README.md`
  - `upgrade/upd_2.5.11-to-2.7.0/index.php`

## Scope

This repo currently contains:

- Root-level English Markdown files used as the main guide.
- A partial `en/` copy.
- Full `de/` and `fr/` book trees with their own assets.

The root-level files need the first pass. After that, equivalent changes need to be mirrored into `de/book/` and `fr/book/`. The `en/` tree also needs cleanup because it only appears to be partially maintained.

## 1. Global Repository Changes

### 1.1 Versioning and metadata

Update all guide-level references from XOOPS 2.5.x to XOOPS 2.7.0.

Files affected:

- `README.md`
- `SUMMARY.md` — primary live TOC for the root guide; navigation labels and section headings need to match the new chapter titles and the renamed Historical Upgrade Notes section
- `en/README.md`
- `en/SUMMARY.md`
- `de/README.md`
- `de/SUMMARY.md`
- `fr/README.md`
- `fr/SUMMARY.md`
- `chapter-2-introduction.md`
- `about-xoops-cms.md`
- `appendix-1-working-with-the-new-admin-gui-our-dashboard.md`
- `appendix-5-increase-security-of-your-xoops-installation.md`
- localized `de/book/*.md` and `fr/book/*.md`

Required changes:

- Change `for XOOPS 2.5.7.x` to `for XOOPS 2.7.0`.
- Update copyright year from `2018` to `2026`.
- Replace old XOOPS 2.5.x and 2.6.0 references where they describe the current release.
- Replace SourceForge-era download guidance with GitHub Releases:
  - `https://github.com/XOOPS/XoopsCore27/releases`

### 1.2 Link refresh

`about-xoops-cms.md` and localized `10aboutxoops.md` files still point to old 2.5.x and 2.6.0 GitHub locations. Those links need to be updated to the current 2.7.x project locations.

### 1.3 Screenshot refresh

All screenshots showing the installer, upgrade UI, admin dashboard, theme picker, module picker, and post-install screens are outdated.

Asset trees affected:

- `.gitbook/assets/`
- `en/assets/`
- `de/assets/`
- `fr/assets/`

This is a full refresh, not a partial one. The 2.7.0 installer uses a different Bootstrap-based layout and different visual structure.

## 2. Chapter 2: Introduction

File:

- `chapter-2-introduction.md`

### 2.1 System requirements must be rewritten

The current chapter only says Apache, MySQL, and PHP. XOOPS 2.7.0 has explicit minimums:

| Component | 2.7.0 minimum | 2.7.0 recommendation |
| --- | --- | --- |
| PHP | 8.2.0 | 8.4+ |
| MySQL | 5.7.8 | 8.4+ |
| Web server | Any server supporting required PHP | Apache or Nginx recommended |

Notes to add:

- IIS is still listed in the installer as possible, but Apache and Nginx are the recommended examples.
- Release notes also call out MySQL 9.0 compatibility.

### 2.2 Add required and recommended PHP extension checklist

The 2.7.0 installer now separates hard requirements from recommended extensions.

Required checks shown by the installer:

- MySQLi
- Session
- PCRE
- filter
- `file_uploads`
- fileinfo

Recommended extensions:

- mbstring
- intl
- iconv
- xml
- zlib
- gd
- exif
- curl

### 2.3 Remove checksum instructions

Current step 5 describes `checksum.php` and `checksum.mdi`. Those files are not part of XOOPS 2.7.0.

Action:

- Remove the checksum verification section completely.

### 2.4 Update package and upload instructions

Keep the `docs/`, `extras/`, `htdocs/`, `upgrade/` package layout description, but update the upload and preparation text to reflect current writable-path expectations:

- `mainfile.php`
- `uploads/`
- `uploads/avatars/`
- `uploads/files/`
- `uploads/images/`
- `uploads/ranks/`
- `uploads/smilies/`
- `xoops_data/caches/`
- `xoops_data/caches/xoops_cache/`
- `xoops_data/caches/smarty_cache/`
- `xoops_data/caches/smarty_compile/`
- `xoops_data/configs/`
- `xoops_data/configs/captcha/`
- `xoops_data/configs/textsanitizer/`
- `xoops_data/data/`
- `xoops_data/protector/`

The guide currently understates this.

### 2.5 Replace SourceForge translation/download language

Current text still says to visit XOOPS on SourceForge for other language packages. That needs to be replaced with current project/community download guidance.

## 3. Chapter 3: Server Configuration Check

File:

- `chapter-3-server-configuration-check.md`

Required changes:

- Rewrite the page description around the current two-block layout:
  - Requirements
  - Recommended extensions
- Replace the old screenshot.
- Explicitly document the requirement checks listed above.

## 4. Chapter 4: Take the Right Path

File:

- `chapter-4-take-the-right-path.md`

Required changes:

- Add the new `Cookie Domain` field.
- Update the names and descriptions of the path fields to match 2.7.0:
  - XOOPS Root Path
  - XOOPS Data Path
  - XOOPS Library Path
  - XOOPS URL
  - Cookie Domain
- Add a note that changing the library path now requires a valid Composer autoloader at `vendor/autoload.php`.

This is a real compatibility check in 2.7.0 and should be documented clearly. The current guide does not mention Composer at all.

## 5. Chapter 5: Database Connections

File:

- `chapter-5-database-connections.md`

Required changes:

- Keep the statement that only MySQL is supported.
- Update the database configuration section to reflect:
  - default charset is now `utf8mb4`
  - collation selection updates dynamically when charset changes
- Replace screenshots for both database connection and configuration pages.

The current text saying charset and collation do not need attention is too weak for 2.7.0. It should at least mention the new `utf8mb4` default and the dynamic collation selector.

## 6. Chapter 6: Final System Configuration

File:

- `chapter-6-final-system-configuration.md`

### 6.1 Generated configuration files changed

The guide currently says the installer writes `mainfile.php` and `secure.php`.

In 2.7.0 it also installs config files into `xoops_data/configs/`, including:

- `xoopsconfig.php`
- captcha config files
- textsanitizer config files

### 6.2 Existing config files in `xoops_data/configs/` are not overwritten

The non-overwrite behavior is **scoped**, not global. Two distinct code paths in `page_configsave.php` write configuration files:

- `writeConfigurationFile()` (called at lines 59 and 66) **always** regenerates `xoops_data/data/secure.php` and `mainfile.php` from the wizard input. There is no existence check; an existing copy is replaced.
- `copyConfigDistFiles()` (called at line 62, defined at line 317) only copies the `xoops_data/configs/` files (`xoopsconfig.php`, the captcha configs, the textsanitizer configs) **if the destination does not already exist**.

The chapter rewrite must reflect both behaviors clearly:

- For `mainfile.php` and `secure.php`: warn that any hand-edits to these files will be overwritten when the installer is re-run.
- For the `xoops_data/configs/` files: explain that local customizations are preserved across re-runs and upgrades, and that restoring shipped defaults requires deleting the file and re-running (or copying the corresponding `.dist.php` by hand).

Do not generalize "existing files are preserved" across all installer-written config files — that is incorrect and would mislead administrators editing `mainfile.php` or `secure.php`.

### 6.3 HTTPS and reverse proxy handling changed

The generated `mainfile.php` now supports broader protocol detection, including reverse-proxy headers. The guide should mention this instead of implying only direct `http` or `https` detection.

### 6.4 Table count is wrong

The current chapter says a new site creates `32` tables.

XOOPS 2.7.0 creates `33` tables. The missing table is:

- `tokens`

Action:

- Update the count from 32 to 33.
- Add `tokens` to the table list.

## 7. Chapter 7: Administration Settings

File:

- `chapter-7-administration-settings.md`

### 7.1 Password UI description is outdated

The installer still includes password generation, but it now also includes:

- zxcvbn-based password strength meter
- visual strength labels
- 16-character generator and copy flow

Update the text and screenshots to describe the current password panel.

### 7.2 Email validation is now enforced

Admin email is validated with `FILTER_VALIDATE_EMAIL`. The chapter should mention that invalid email values are rejected.

### 7.3 License key section is wrong

This is one of the most important factual fixes.

Current guide says:

- there is a `License System Key`
- it is stored in `/include/license.php`
- `/include/license.php` must be writable during installation

That is no longer accurate.

What 2.7.0 actually does:

- installation writes the license data to `xoops_data/data/license.php`
- `htdocs/include/license.php` is now just a deprecated wrapper that loads the file from `XOOPS_VAR_PATH`
- the old wording about making `/include/license.php` writable should be removed

Action:

- Rewrite this section instead of deleting it.
- Update the path from `/include/license.php` to `xoops_data/data/license.php`.

### 7.4 Theme list is outdated

The current guide still refers to Zetagenesis and the older 2.5-era theme set.

Themes present in XOOPS 2.7.0:

- `default`
- `xbootstrap`
- `xbootstrap5`
- `xswatch4`
- `xswatch5`
- `xtailwind`
- `xtailwind2`

Also note:

- `xswatch4` is the current default theme inserted by installer data.
- Zetagenesis is no longer part of the packaged theme list.

### 7.5 Module list is outdated

Modules present in the 2.7.0 package:

- `system` — installed automatically during the table-fill / data-insertion steps. Always present, never visible in the picker.
- `debugbar` — selectable in the installer step.
- `pm` — selectable in the installer step.
- `profile` — selectable in the installer step.
- `protector` — selectable in the installer step.

Important: the module installer page (`htdocs/install/page_moduleinstaller.php`) builds its candidate list by iterating over `XoopsLists::getModulesList()` and **filtering out anything already in the modules table** (lines 95-102 collect `$listed_mods`; line 116 skips any directory present in that list). Because `system` is installed before this step runs, it never appears as a checkbox.

Guide changes needed:

- Stop saying there are only three bundled modules.
- Describe the installer step as showing **four selectable modules** (`debugbar`, `pm`, `profile`, `protector`), not five.
- Document `system` separately as the always-installed core module that does not appear in the picker.
- Add `debugbar` to the bundled-module description as new in 2.7.0.
- Note that the installer's default module preselection is now empty; modules are available to choose, but not pre-checked by installer config.

## 8. Chapter 8: Ready To Go

File:

- `chapter-8-ready-to-go.md`

### 8.1 Install cleanup process needs rewriting

The current guide says the installer renames the install folder to a unique name.

That is still true in effect, but the mechanism changed:

- an external cleanup script is created in the web root
- the final page triggers cleanup through AJAX
- install folder is renamed to `install_remove_<unique suffix>`
- fallback to `cleanup.php` still exists

Action:

- Update the explanation.
- Keep the user-facing instruction simple: delete the renamed install directory after installation.

### 8.2 Admin dashboard appendix references are obsolete

Chapter 8 still points readers toward the old Oxygen-era admin experience. That needs to align with current admin themes:

- `default`
- `dark`
- `modern`
- `transition`

### 8.3 Post-install path editing guidance needs correction

Current text tells readers to update `secure.php` with path definitions. In 2.7.0, those path constants are defined in `mainfile.php`, while `secure.php` holds secure data. The example block in this chapter should be corrected accordingly.

### 8.4 Production settings should be added

The guide should explicitly mention the production defaults now present in `mainfile.dist.php`:

- `XOOPS_DB_LEGACY_LOG` should remain `false`
- `XOOPS_DEBUG` should remain `false`

## 9. Chapter 9: Upgrade Existing XOOPS Installation

File:

- `chapter-9-upgrade-existing-xoops-installation.md`

This chapter requires the largest rewrite.

### 9.1 Add mandatory Smarty 4 preflight step

XOOPS 2.7.0 upgrade flow now forces the preflight process before upgrade completion.

New required flow:

1. Copy the `upgrade/` directory to the site root.
2. Run `/upgrade/preflight.php`.
3. Scan `/themes/` and `/modules/` for old Smarty syntax.
4. Use the optional repair mode where appropriate.
5. Re-run until clean.
6. Continue into `/upgrade/`.

Current chapter does not mention this at all, which makes it incompatible with 2.7.0 guidance.

### 9.2 Replace the manual 2.5.2-era merge narrative

The current chapter still describes a manual 2.5.2-style upgrade with framework merges, AltSys notes, and hand-managed file restructuring. That should be replaced with the actual 2.7.x upgrade sequence from `release_notes.txt` and `upgrade/README.md`.

Recommended chapter outline:

1. Back up files and database.
2. Turn site off.
3. Copy `htdocs/` over the live root.
4. Copy `htdocs/xoops_lib` into the active library path.
5. Copy `htdocs/xoops_data` into the active data path.
6. Copy `upgrade/` to the web root.
7. Run `preflight.php`.
8. Run `/upgrade/`.
9. Complete updater prompts.
10. Update the `system` module.
11. Update `pm`, `profile`, and `protector` if installed.
12. Delete `upgrade/`.
13. Turn site back on.

### 9.3 Document real 2.7.0 upgrade changes

The updater for 2.7.0 includes at least these concrete changes:

- create `tokens` table
- widen `bannerclient.passwd` for modern password hashes
- add session cookie preference settings
- remove obsolete bundled directories

The guide does not need to expose every implementation detail, but it should stop implying the upgrade is only a file copy plus module update.

## 10. Historical Upgrade Pages

Files:

- `upgrading-from-xoops-2.4.5-easy-way.md`
- `upgrading-from-xoops-2.0.-above-2.0.14-and-2.2..md`
- `upgrading-from-any-xoops-2.0.7-to-2.0.13.2.md`
- `upgrading-a-non-utf-8-site.md`
- `upgrading-xoopseditor-package.md`

**Status:** the structural decision is already resolved — the root `SUMMARY.md` moves these into a dedicated **Historical Upgrade Notes** section, and each file carries a "Historical reference" callout pointing readers to Chapter 9 for 2.7.0 upgrades. They are no longer first-class upgrade guidance.

**Remaining work (consistency only):**

- Make sure `README.md` (root) lists these under the same "Historical Upgrade Notes" heading, not under a generic "Upgrades" header.
- Mirror the same separation in `de/README.md`, `de/SUMMARY.md`, `fr/README.md`, `fr/SUMMARY.md`, and `en/SUMMARY.md`.
- Ensure each historical upgrade page (root and the localized `de/book/upg*.md` / `fr/book/upg*.md` copies) carries a stale-content callout linking back to Chapter 9.

## 11. Appendix 1: Admin GUI

File:

- `appendix-1-working-with-the-new-admin-gui-our-dashboard.md`

This appendix is tied to the Oxygen admin GUI and needs a rewrite.

Required changes:

- replace all Oxygen references
- replace old icon/menu screenshots
- document the current admin themes:
  - default
  - dark
  - modern
  - transition
- mention current 2.7.0 admin capabilities called out in release notes:
  - template overload capability in system admin themes
  - updated admin theme set

## 12. Appendix 2: Uploading XOOPS Via FTP

File:

- `appendix-2-uploading-xoops-via-ftp.md`

Required changes:

- remove HostGator-specific and cPanel-specific assumptions
- modernize the file-upload wording
- note that `xoops_lib` now includes Composer dependencies, so uploads are larger and should not be selectively trimmed

## 13. Appendix 5: Security

File:

- `appendix-5-increase-security-of-your-xoops-installation.md`

Required changes:

- remove `register_globals` discussion completely
- remove outdated host-ticket language
- correct permissions text from `404` to `0444` where readonly is intended
- update the `mainfile.php` and `secure.php` discussion to match 2.7.0 layout
- add the new cookie-domain security-related constant context:
  - `XOOPS_COOKIE_DOMAIN_USE_PSL`
  - `XOOPS_COOKIE_DOMAIN`
- add production guidance for:
  - `XOOPS_DB_LEGACY_LOG`
  - `XOOPS_DEBUG`

## 14. Cross-Language Maintenance Impact

After root-level English files are fixed, equivalent updates are needed in:

- `de/book/`
- `fr/book/`
- `de/README.md`
- `fr/README.md`
- `de/SUMMARY.md`
- `fr/SUMMARY.md`

The `en/` tree also needs review because it contains a separate README and asset set, but only appears to have a partial `book/` tree.

## 15. Priority Order

### Critical before release

1. Update repo/version references to 2.7.0.
2. Rewrite Chapter 9 around the real 2.7.0 upgrade flow and Smarty 4 preflight.
3. Update system requirements to PHP 8.2+ and MySQL 5.7.8+.
4. Correct Chapter 7 license-key file path.
5. Correct theme and module inventories.
6. Correct Chapter 6 table count from 32 to 33.

### Important for accuracy

7. Rewrite writable-path guidance.
8. Add Composer autoloader requirement to path setup.
9. Update database charset guidance to `utf8mb4`.
10. Fix Chapter 8 path-editing guidance so constants are documented in the right file.
11. Remove checksum instructions.
12. Remove `register_globals` and other dead PHP guidance.

### Release-quality cleanup

13. Replace all installer and admin screenshots.
14. Move historical upgrade pages out of the main flow.
15. Sync German and French copies after English is corrected.
16. Clean up stale links and duplicated README lines.
