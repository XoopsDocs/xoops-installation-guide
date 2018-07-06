### Chapter 9: Upgrade Existing XOOPS Installation


>	**Warning **

>If you use custom templates, you should convert them into files inside your theme folder before upgrading. 

Assuming that you have a structure in your existing XOOPS Installation as discussed above, and would like to upgrade it to XOOPS 2.5.2, i.e. you have renamed and moved your xoops_lib and xoops_data directories outside of Document Root, these are the steps to upgrade your XOOPS Installation:

1)	Backup all XOOPS files & your XOOPS database!!! 
2)	Pre-Upgrade Instructions: 
<br>a.	Unzip the downloaded “XOOPS Release” into a temporary folder 
<br>b.	Delete unneeded Files/Folders from /htdocs 
<br>i.	Delete cache, install, and templates_c folders 
<br>ii.	Delete mainfile.php, favicon.ico (typically, but leave if you didn’t modify it)

![](../assets/img_41.jpg)

<br>c.	Copy upgrade folder into /htdocs 
<br>d.	If you have installed AltSys Module: 
<br>i.	Copy altsys folder in current XOOPS_TRUST folder to xoops_lib/modules folder 
<br>ii.	In xoops_lib folder, make symlink of libs -> modules (for altsys compatibility) 
<br><br>3)	Merge Core/Module Modifications (if in core release) 
<br>a.	Merge any core files modified for your installations 
<br>i.	robots.txt (only if changed)
<br>b.	Merge Frameworks 
<br>i.	Essentially, start with the latest Frameworks 1.22 (and/or merged with 1.35      if used), then add/overwrite files with Frameworks for XOOPS 2.5.0, then      add/overwrite files with the XOOPS 2.5.x core files. 
<br>c.	Merge images, languages, uploads folders 
<br>d.	Merge WYSIWYG editor changes 
<br>4)	Delete /modules/system from existing site
<br>5) Copy/Move Files (over existing site)  
	
![](../assets/img_44.jpg)

6)	Perform Upgrade
<br>a.	Remove files from cache and templates_c folders (keep the index.html files) 
<br>b.	Make mainfile.php writeable
<br>c.	Run upgrade script (http://yoursite.com/upgrade) 
<br>i.	Point to xoops_data and xoops_lib directories 
<br>d.	Update system, protector, and other core modules if installed 
<br>e.	Delete upgrade folder 
<br>f.	Update non-core modules individually (make sure using the latest versions) 
<br>7)	Post-Upgrade File Restructuring 
<br>a.	Move new xoops_lib and xoops_data folders into XOOPS_TRUST directory; remove    the old, unneeded files and folders 
<br>b.	Delete and redirect cache and templates_c folders via symbolic link 
<br>c.	Update mainfile.php to reflect the above changes 
<br>d.	Make mainfile.php unwriteable (chmod 444)
<br>e.	Make Module Specific Changes 
<br>f.	Remove old, unneeded files 
<br>g.	Update FCKeditor module-specific configurations in all modules (if any) 
<br>8)	Test - Perform integration/regression testing on all modules 
<br>a.	Review templates changes/updates for all modules and incorporate as appropriate

> **Warning** 

> If you use any modules that utilize the “XOOPS_TRUST_PATH” and you have them installed on your Website, make sure that the content of it is being moved to your “xoops_lib” directory, and the current “XOOPS_TRUST_PATH”” is deleted, and if needed, the mainfile.php is modified accordingly. 

XOOPS can post only to one “XOOPS_TRUST_PATH”” directory, which in XOOPS 2.5.x is the xoops_lib directory 


-----------------------------------
