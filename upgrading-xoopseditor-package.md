# Upgrading XoopsEditor package

> **Historical reference**
>
> This page describes a legacy XOOPS Editor package upgrade procedure that pre-dates XOOPS 2.7.0. The editors bundled with the modern XOOPS distribution have changed; only the editors shipped with the active 2.7.x release are supported. **For upgrading a 2.5.x site to XOOPS 2.7.0, see [Chapter 9](chapter-9-upgrade-existing-xoops-installation.md).**

In the XOOPS package, there are eight editors included: dhtmltextarea and textarea for plain text, fckeditor, tinymce, koivi, wymeditor, Xinha, and Spaw2 for WYSIWYG HTML.

Since there are some directory structure changes in both fckeditor and tinymce editors, you are recommended to remove existing editors before uploading the new editors.

And if you are using fckeditor for modules, please modify module specific configs following the files in /fckeditor/modules/, especially if you use "article" module.

**To increase Security of your XOOPS Installation: please make sure to read Appendix 5** 

