# Upgrading a non UTF-8 site

> **Historical reference**
>
> This page describes a legacy upgrade path that pre-dates XOOPS 2.7.0. XOOPS 2.7.0 uses `utf8mb4` by default and there is no supported direct upgrade path from a non-UTF-8 site to 2.7.0 — convert the site to UTF-8 first using the procedure below, then follow [Chapter 9](chapter-9-upgrade-existing-xoops-installation.md).

UTF-8 encoding has been introduced into XOOPS 2.3 as default charset. However, there might be some problems with converting existing websites from non UTF-8 charset to UTF-8.

Before there is a good enough solution for this conversion, following settings are recommended when you upgrade an existing website if you are not an experienced user:

* Select "Do not change" option in "Database character set and collation" step during upgrade process
* Modify /languages/yourlanguage/global.php to use your previous \_CHARSET value, if it has been changed to UTF-8 in your new global.php file as define\('\_CHARSET', 'UTF-8'\);

