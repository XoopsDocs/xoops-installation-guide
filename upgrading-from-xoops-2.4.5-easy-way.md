# Upgrading from XOOPS 2.4.5 \(easy way\)

1. Get the right update package from the sourceforge file repository
2. Delete the /modules/system directory
3. Overwrite files in XOOPS directory on your server with the content of /htdocs    - make sure that you copy the content of /xoops\_lib to whatever directory you keep it on the server now \(e.g. if you moved it outside of the Document Root\), then delete the /xoops\_lib directory. There can NOT be two directories with the content of /xoops\_lib  
4. If you have Protector previously installed, open the "mainfile.php" file , and remove the Pre-check and Post-check lines \(if they exist\):  
  
   include XOOPS\_TRUST\_PATH.'/modules/protector/include/precheck.inc.php' ;  


   include XOOPS\_TRUST\_PATH.'/modules/protector/include/postcheck.inc.php' ;  
  

5. If you're upgrading from XOOPS 2.5.x, make the file /include/license.php writeable \(permission 0777 on Linux\)
6. Access /upgrade/ with a browser, and follow the instructions
7. Follow the instructions to update your database
8. Delete the "upgrade" folder from your server
9. Update the "system" module from the modules administration interface. Other modules, especially "Profile" and "Protector" are recommended to update as well

