# Chapter 9: Upgrade an existing XOOPS installation to 2.7.0

XOOPS 2.7.0 introduces **Smarty 4**, a new admin theme set, modernized libraries, and PHP 8.2+ baseline code. The upgrade process from 2.5.x has been redesigned to support this safely.

> **Warning**
>
> If you use custom themes or custom module templates, move them into theme folders (not the database) before upgrading so that the preflight scanner can analyze them.

## 1. Back up

Make a full backup of both the XOOPS files *and* the XOOPS database before making any changes. Do not skip this — the upgrade touches templates, database schema, and configuration files.

## 2. Prepare the site for the upgrade

1. Enable debugging in **System Options → Preferences → General Settings** (optional but helpful).
2. Turn the site off in **System Options → Preferences → General Settings** so that visitors do not hit the site mid-upgrade.

## 3. Copy the distribution over the site

From the XOOPS 2.7.0 distribution:

1. Copy the contents of `htdocs/` over your live web root.
2. Copy the contents of `htdocs/xoops_lib/` into the directory you are using as `XOOPS_PATH` (renamed/relocated or not).
3. Copy the contents of `htdocs/xoops_data/` into the directory you are using as `XOOPS_VAR_PATH`. Existing customized config files in `xoops_data/configs/` will **not** be overwritten by the installer.
4. Copy the distribution `upgrade/` directory into your web root.

## 4. Run the Smarty 4 preflight (required)

XOOPS 2.7.0 replaces Smarty 2/3 with Smarty 4. Old templates may use syntax that Smarty 4 rejects. The `upgrade/preflight.php` script scans your themes and modules for such issues and can fix many of them automatically.

1. Point your browser at `http://your-site/upgrade/preflight.php`.
2. Log in as an administrator when prompted.
3. Accept the defaults to scan `/themes/` and `/modules/` for `.tpl` and `.html` files, or narrow the scan with the provided form.
4. Review the reported issues.
5. Optionally check the **run fix** box and re-submit the form to apply automatic repairs.
6. Repeat the scan until no issues remain. Manual edits may still be needed for templates with non-trivial Smarty syntax.
7. When the scanner shows zero issues, click the **End scan** button. This marks the preflight as complete and lets you proceed to the upgrade itself.

Do not skip this step. The regular upgrade flow will refuse to run until `preflight.php` has been completed at least once.

## 5. Run the upgrade

1. Point your browser at `http://your-site/upgrade/` and follow the prompts.
2. Log in as an administrator.
3. Step through any needed updates. The 2.7.0 upgrade path handles:
   - creating the new `tokens` table used by the CSRF/form-token layer;
   - widening `bannerclient.passwd` to accommodate modern password hashes;
   - adding session cookie preference settings;
   - removing obsolete bundled directories;
   - other schema adjustments required by the 2.7.0 core.

## 6. Update modules

1. Follow the link at the end of the upgrade to update the **system** module.
2. Update the **pm**, **profile**, and **protector** modules if installed.
3. Update any third-party modules you have installed. Check each module's support page for a 2.7.0-compatible release before updating.

## 7. Finish up

1. Delete the `upgrade/` directory from your web root.
2. Delete any remaining `install_cleanup_*.php` or renamed `install_remove_*` directories from earlier installs.
3. Set `mainfile.php` to read-only again if your filesystem changed its permissions during the upgrade.
4. Turn the site back on in **System Options → Preferences → General Settings**.

Your XOOPS site should now be running on 2.7.0.

## Troubleshooting

- **Preflight reports many template issues.** Use the automatic repair option where possible, then manually fix the remaining ones. Compare with an untouched copy of a 2.7.0-compatible theme (for example `xswatch5`) to see what the expected Smarty 4 syntax looks like.
- **Upgrade UI refuses to run.** Ensure you completed `preflight.php` and clicked **End scan**. The preflight state is tracked in the session.
- **Site breaks after the upgrade.** Re-enable debugging temporarily, check the reported errors, and visit the XOOPS support forums at [https://xoops.org/modules/newbb/](https://xoops.org/modules/newbb/) if the cause is not obvious.

## Upgrading from versions older than 2.5.x

The upgrade path from 2.0.x / 2.2.x / 2.3.x / 2.4.x directly to 2.7.0 is not recommended. If you are on a version older than 2.5.x, upgrade to a late 2.5.x release first, then follow this chapter to move from 2.5.x to 2.7.0. See the legacy upgrade notes bundled with older XOOPS releases for the intermediate steps.
