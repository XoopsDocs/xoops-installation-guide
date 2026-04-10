# Appendix 3: Translating XOOPS to a Local Language

XOOPS 2.7.0 ships with English language files only. Translations into other languages are maintained by the community and distributed through GitHub and the various local XOOPS support sites.

## Where to find existing translations

- **GitHub** — community translations are increasingly published as separate repositories under the [XOOPS organization](https://github.com/XOOPS) and on individual contributors' accounts. Search GitHub for `xoops-language-<your-language>` or browse the XOOPS organization for current packages.
- **Local XOOPS support sites** — many regional XOOPS communities publish translations on their own sites. Visit [https://xoops.org](https://xoops.org) and follow the links to local communities.
- **Module translations** — translations for individual community modules typically live next to the module itself in the `XoopsModules25x` GitHub organization (the `25x` in the name is historical; modules there are maintained for both XOOPS 2.5.x and 2.7.x).

If a translation for your language already exists, drop the language directories into your XOOPS install (see "How to install a translation" below).

## What needs to be translated

XOOPS 2.7.0 keeps language files next to the code that consumes them. A complete translation covers all of these locations:

- **Core** — `htdocs/language/english/` — site-wide constants used by every page (login, common errors, dates, mail templates, etc.).
- **Installer** — `htdocs/install/language/english/` — strings shown by the installation wizard. Translate these *before* running the installer if you want a localized install experience.
- **System module** — `htdocs/modules/system/language/english/` — by far the largest set; covers the entire admin Control Panel.
- **Bundled modules** — each of `htdocs/modules/pm/language/english/`, `htdocs/modules/profile/language/english/`, `htdocs/modules/protector/language/english/`, and `htdocs/modules/debugbar/language/english/`.
- **Themes** — a handful of themes ship their own language files; check `htdocs/themes/<theme>/language/` if it exists.

A "core only" translation is the minimum useful unit and corresponds to the first two bullets above.

## How to translate

1. Copy the `english/` directory next to it and rename the copy to your language. The directory name should be the lowercase English name of the language (`spanish`, `german`, `french`, `japanese`, `arabic`, etc.).

   ```
   htdocs/language/english/    →    htdocs/language/spanish/
   ```

2. Open each `.php` file in the new directory and translate the **string values** inside the `define()` calls. Do **not** change the constant names — they are referenced from PHP code throughout the core.

   ```php
   // Before:
   define('_CM_COMDELETED',  'Comment(s) deleted.');
   define('_CM_COMDELETENG', 'Could not delete comment.');
   define('_CM_DELETESELECT', 'Delete all its child comments?');

   // After (Spanish):
   define('_CM_COMDELETED',  'Comentario(s) eliminado(s).');
   define('_CM_COMDELETENG', 'No se pudo eliminar el comentario.');
   define('_CM_DELETESELECT', '¿Eliminar también todos sus comentarios secundarios?');
   ```

3. **Save every file as UTF-8 *without* BOM.** XOOPS 2.7.0 uses `utf8mb4` end-to-end (database, sessions, output) and rejects files with a byte-order mark. In Notepad++ this is the **"UTF-8"** option, *not* "UTF-8-BOM". In VS Code it is the default; just confirm the encoding in the status bar.

4. Update the language and charset metadata at the top of each file to match your language:

   ```php
   // _LANGCODE: es
   // _CHARSET : UTF-8
   // Translator: Your Name
   ```

   `_LANGCODE` should be the [ISO 639-1](https://www.loc.gov/standards/iso639-2/php/code_list.php) code for your language. `_CHARSET` is always `UTF-8` in XOOPS 2.7.0 — there is no longer an ISO-8859-1 variant.

5. Repeat for the installer, the System module, and any bundled modules you need.

## How to install a translation

If you obtained a finished translation as a directory tree:

1. Copy each `<language>/` directory into the matching `language/english/` parent in your XOOPS install. For example, copy `language/spanish/` into `htdocs/language/`, `install/language/spanish/` into `htdocs/install/language/`, and so on.
2. Make sure file ownership and permissions are readable by the web server.
3. Either select the new language at install time (the wizard scans `htdocs/language/` for available languages) or, on an existing site, change the language in **Admin → System → Preferences → General Settings**.

## Sharing your translation back

Please contribute your translation back to the community.

1. Create a GitHub repository (or fork an existing language repository if one exists for your language).
2. Use a clear name such as `xoops-language-<language-code>` (e.g. `xoops-language-es`, `xoops-language-pt-br`).
3. Mirror the XOOPS directory structure inside your repository so files line up with where they get copied:

   ```
   xoops-language-es/
   ├── language/spanish/(files).php
   ├── install/language/spanish/(files).php
   └── modules/system/language/spanish/(files).php
   ```

4. Include a `README.md` documenting:
   - Language name and ISO code
   - XOOPS version compatibility (e.g. `XOOPS 2.7.0+`)
   - Translator and credits
   - Whether the translation is core-only or covers bundled modules
5. Open a pull request against the relevant module/core repository on GitHub or post an announcement on [https://xoops.org](https://xoops.org) so the community can find it.

> **Note**
>
> If your language requires changes to the core for date or calendar formatting, include those changes in the package as well. Languages with right-to-left scripts (Arabic, Hebrew, Persian, Urdu) work out of the box in XOOPS 2.7.0 — RTL support was added in this release and individual themes pick it up automatically.
