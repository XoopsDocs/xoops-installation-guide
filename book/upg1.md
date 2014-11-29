Upgrading from XOOPS 2.4.5 (easy way)

0. Get the right update package from the sourceforge file repository
1. Delete the /modules/system directory
2. Overwrite files in XOOPS directory on your server with the content of /htdocs
* make sure that you copy the content of /xoops_lib to whatever directory you keep it on the server now (e.g. if you moved it outside of the Document Root), then delete the /xoops_lib directory. There can NOT be two directories with the content of /xoops_lib
3. If you have Protector previously installed, open the "mainfile.php" file , and remove the Pre-check and Post-check lines (if they exist):

include XOOPS_TRUST_PATH.'/modules/protector/include/precheck.inc.php' ;
include XOOPS_TRUST_PATH.'/modules/protector/include/postcheck.inc.php' ;

4. If you're upgrading from XOOPS 2.5.x, make the file /include/license.php writeable (permission 0777 on Linux)
5. Access /upgrade/ with a browser, and follow the instructions
6. Follow the instructions to update your database
7. Delete the "upgrade" folder from your server
8. Update the "system" module from the modules administration interface. Other modules, especially "Profile" and "Protector" are recommended to update as well
Upgrading from XOOPS 2.0.* above 2.0.14 and 2.2.* 
(using the full package)
0. Unpack the archive to your LOCAL computer (e.g. PC) in a temporary directory.
1. Move the "upgrade" folder inside the "htdocs" folder (it's been kept out as it's not needed for full installs) on your local computer
2. Delete htdocs/mainfile.php, htdocs/install/, htdocs/cache/, htdocs/template_c/, htdocs/themes/, htdocs/uploads/, and htdocs/modules/system from the "htdocs" folder on your LOCAL computer
* if you have created XOOPS_TRUST_PATH folder on your server, copy the content of /xoops_lib to that directory, and delete /xoops_lib from the "htdocs" folder on your LOCAL computer
3. Upload the content of the /htdocs folder on your LOCAL computer over your existing files on your server
4. For security considerations, you are encouraged to move directories xoops_lib (for XOOPS libraries) and xoops_data (for XOOPS data) out of Document Root, and change the folder names.
5. Make the directory of xoops_data/ writable; Create and make the directories of xoops_data/caches/, xoops_data/caches/xoops_cache/, xoops_data/caches/smarty_cache/ and xoops_data/caches/smarty_compile/ writable.
6. Ensure the server can write to mainfile.php
7. If you have Protector previously installed, open the "mainfile.php" file , and remove the Pre-check and Post-check lines (if they exist):

include XOOPS_TRUST_PATH.'/modules/protector/include/precheck.inc.php' ;
include XOOPS_TRUST_PATH.'/modules/protector/include/postcheck.inc.php' ;

8. Access /upgrade/ with a browser, and follow the instructions
9. Follow the instructions to update your database
10. Write-protect mainfile.php again (permission 0444 on Linux)
11. Delete the "upgrade" folder from your server
12. Update the "system" module from the modules administration interface, other modules are recommended to update as well
Upgrading from any XOOPS (2.0.7 to 2.0.13.2)
(using the full package)

0. Unpack the archive to your LOCAL computer (e.g. PC) in a temporary directory.
1. Move the "upgrade" folder inside the "htdocs" folder on your LOCAL computer (it's been kept separate as it's not needed for full installs)
2. . Delete htdocs/mainfile.php, htdocs/install/, htdocs/cache/, htdocs/template_c/, htdocs/themes/, htdocs/uploads/, and htdocs/modules/system from the "htdocs" folder on your LOCAL computer
* if you have created XOOPS_TRUST_PATH folder on your server, copy the content of /xoops_lib to that directory, and delete /xoops_lib from the "htdocs" folder on your LOCAL computer 
3. Upload the content of the htdocs folder on your LOCAL computer over your existing files on your server
4. Delete the following folders and files from your server (they belong to an old version):
* class/smarty/core
* class/smarty/plugins/resource.db.php
5. Ensure the server can write to mainfile.php (permission 0777 on Linux)
6. If you have Protector previously installed, open the "mainfile.php" file , and remove the Pre-check and Post-check lines (if they exist):

include XOOPS_TRUST_PATH.'/modules/protector/include/precheck.inc.php' ;
include XOOPS_TRUST_PATH.'/modules/protector/include/postcheck.inc.php' ;

7. For security considerations, you are encouraged to move directories xoops_lib (for XOOPS libraries) and xoops_data (for XOOPS data) out of document root, or even change the folder names.
8. Make the directory of xoops_data/ writable; Create and make the directories of xoops_data/caches/, xoops_data/caches/xoops_cache/, xoops_data/caches/smarty_cache/ and xoops_data/caches/smarty_compile/ writable.
9. Access /upgrade/ with a browser, and follow the instructions
10. Write-protect mainfile.php again (permission 0444 on Linux)
11. Delete the "upgrade" folder from your server
12. Update the "system" module from the modules administration interface, other modules are recommended to update as well
Upgrading a non UTF-8 site:
UTF-8 encoding has been introduced into XOOPS 2.3 as default charset. However, there might be some problems with converting existing websites from non UTF-8 charset to UTF-8.
Before there is a good enough solution for this conversion, following settings are recommended when you upgrade an existing website if you are not an experienced user:
- Select "Do not change" option in "Database character set and collation" step during upgrade process
- Modify /languages/yourlanguage/global.php to use your previous _CHARSET value, if it has been changed to UTF-8 in your new global.php file as
define('_CHARSET', 'UTF-8');

Upgrading XoopsEditor package:
In the XOOPS package, there are eight editors included: dhtmltextarea and textarea for plain text, fckeditor, tinymce, koivi, wymeditor, Xinha, and Spaw2 for WYSIWYG HTML.
Since there are some directory structure changes in both fckeditor and tinymce editors, you are recommended to remove existing editors before uploading the new editors.
And if you are using fckeditor for modules, please modify module specific configs following the files in /fckeditor/modules/, especially if you use "article" module.

To increase Security of your XOOPS Installation: please make sure to read Appendix 5

