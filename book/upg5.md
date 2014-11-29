# Upgrading XoopsEditor package:

In the XOOPS package, there are eight editors included: dhtmltextarea and textarea for plain text, fckeditor, tinymce, koivi, wymeditor, Xinha, and Spaw2 for WYSIWYG HTML.

Since there are some directory structure changes in both fckeditor and tinymce editors, you are recommended to remove existing editors before uploading the new editors.

And if you are using fckeditor for modules, please modify module specific configs following the files in /fckeditor/modules/, especially if you use "article" module.

To increase Security of your XOOPS Installation: please make sure to read Appendix 5

