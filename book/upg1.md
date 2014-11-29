## Upgrading from XOOPS 2.4.5 (easy way)


0. Get the right update package from the sourceforge file repository
1. Delete the /modules/system directory
2. Overwrite files in XOOPS directory on your server with the content of /htdocs <br><br> - make sure that you copy the content of /xoops_lib to whatever directory you keep it on the server now (e.g. if you moved it outside of the Document Root), then delete the /xoops_lib directory. There can NOT be two directories with the content of /xoops_lib<br><br>
3. If you have Protector previously installed, open the "mainfile.php" file , and remove the Pre-check and Post-check lines (if they exist):<br><br>include XOOPS_TRUST_PATH.'/modules/protector/include/precheck.inc.php' ;<br>
include XOOPS_TRUST_PATH.'/modules/protector/include/postcheck.inc.php' ;<br><br>
4. If you're upgrading from XOOPS 2.5.x, make the file /include/license.php writeable (permission 0777 on Linux)
5. Access /upgrade/ with a browser, and follow the instructions
6. Follow the instructions to update your database
7. Delete the "upgrade" folder from your server
8. Update the "system" module from the modules administration interface. Other modules, especially "Profile" and "Protector" are recommended to update as well
