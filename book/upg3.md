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
