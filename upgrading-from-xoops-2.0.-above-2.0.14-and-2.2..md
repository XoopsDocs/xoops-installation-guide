# Upgrading from XOOPS 2.0. above 2.0.14 and 2.2.

\(using the full package\)

1. Unpack the archive to your LOCAL computer \(e.g. PC\) in a temporary directory.
2. Move the "upgrade" folder inside the "htdocs" folder \(it's been kept out as it's not needed for full installs\) on your local computer
3. Delete htdocs/mainfile.php, htdocs/install/, htdocs/cache/, htdocs/template\_c/, htdocs/themes/, htdocs/uploads/, and htdocs/modules/system from the "htdocs" folder on your LOCAL computer   - if you have created XOOPS\_TRUST\_PATH folder on your server, copy the content of /xoops\_lib to that directory, and delete /xoops\_lib from the "htdocs" folder on your LOCAL computer  
4. Upload the content of the /htdocs folder on your LOCAL computer over your existing files on your server
5. For security considerations, you are encouraged to move directories xoops\_lib \(for XOOPS libraries\) and xoops\_data \(for XOOPS data\) out of Document Root, and change the folder names.
6. Make the directory of xoops\_data/ writable; Create and make the directories of xoops\_data/caches/, xoops\_data/caches/xoops\_cache/, xoops\_data/caches/smarty\_cache/ and xoops\_data/caches/smarty\_compile/ writable.
7. Ensure the server can write to mainfile.php
8. If you have Protector previously installed, open the "mainfile.php" file , and remove the Pre-check and Post-check lines \(if they exist\):  
  
   include XOOPS\_TRUST\_PATH.'/modules/protector/include/precheck.inc.php' ;  


   include XOOPS\_TRUST\_PATH.'/modules/protector/include/postcheck.inc.php' ;  
  

9. Access /upgrade/ with a browser, and follow the instructions
10. Follow the instructions to update your database
11. Write-protect mainfile.php again \(permission 0444 on Linux\)
12. Delete the "upgrade" folder from your server
13. Update the "system" module from the modules administration interface, other modules are recommended to update as well

