### Chapter 7: Administration Settings 


After the tables have been created, the Administrator account settings are entered.

Figure 13: This is the form where you create your site's webmaster.
In the field called [Admin Login] the login name for the site SuperUser or Administrator should be entered. A common choice is, of course, webmaster, but any name can be used. 
The Admin e-mail field should be filled with the address where mail sent to the site administrator or webmaster should be delivered. The final step is to enter and confirm a password for the webmaster.
The Password Generator will create a very strong password and its use is highly recommended.  To use it, click on “Generate”, and then on “Copy” to copy it automatically to the appropriate password field.
It is important that the password be saved for future reference.  “KeyPass” is a good tool that can be used to store it in a database (see Appendix 4)  

 

Figure 14: Copying the generated password to Administrator fields
The Installation Wizard will confirm that the passwords match.  Clicking [Next] will move the process forward to step 10/14 (Figure 15).
 

Figure 15: Saving settings to the database tables and creating System Key
At this point of the installation, XOOPS created a unique System Key for your installation.

 	Note 

XOOPS 2.5.x includes a License System Key that is stored in /include/license.php 
This file has to be writeable by the Installation Wizard, the same way as “mainfile.php”.
On most system the Installer  is able to write files, but if  it isn't, you will have to chmod /include/license.php to 777. Just like the mainfile.php, you have to be careful with this file in later upgrades. The file is chmod'd back to 444 when it is finalized. Do not write over this file, you can generate it again if you do by running the upgrade.  
Also, 19 of 32 tables have received data. The following list provides an outline of the data added to the tables:
xef9_banner received 3 entries. These are located in the folder images/banners and are xef9_banner.gif, xef9_banner_2.gif and banner.swf. Flash files can also be included as banners. 
xef9_bannerclient received 1 entry. This particular client is no other than XOOPS itself. The three banners inserted into the database belong to XOOPS.  The new site will go live with three XOOPS banners, which can be changed or removed. 
xef9_block_module_link received 12 entries. This corresponds with the 12 entries also inserted into xef9_newblocks. This means the System module has 12 blocks defined: “User Menu”, “Login”, “Search”, “Waiting Contents”, “Main Menu”, “Site Info”, “Who's Online”, “Top Posters”, “New Members”, “Recent Comments”, “Notification Options” and “Themes”. These are all blocks that can be managed within the Template Manager. 
xef9_config received 130 entries. To view what was written to this table, either open MySQL Admin and  look at the table, or, look at the file “install/makedata.php” where lines 154-292 show the whole list of entries. Note that number of entries listed in makedata.php does not match the number of inserted entries.  This is normal as through the evolution of XOOPS, entries like 25 and 26 were dropped. 
xef9_configcategory received 7 entries. These categories are “General Settings”, “User Info Settings”, “Meta Tags and Footer”, “Word Censoring Options”, “Search Options” and “Mail Setup”. These options are revealed in the site's preferences in the admin section. 
xef9_configoption received 47 entries.  Information on these entries can be found in lines 44-82 of the file install/ sql/mysql.data.sql. They are default values for a lot of general options of the new site. 
xef9_groups received 3 entries, corresponding to the three default user groups: webmasters, registered users and anonymous users.
xef9_grouppermission received 57 entries, that have to do with permissions for groups for the module installed (System) and its 12 blocks. The 57 entries include: 1 to let webmasters manage the System module, 3 to let the three groups read the System module, and 17 for the System Admin. The other 36 define, for each group and each block of the System module, a permission level (12 x 3 = 36 entries). 
xef9_groups_users_link received 2 entries. This means the one user created in step 9/14 (Figure 16)  belongs to both the webmaster and registered users groups. 
xef9_imgset received 1 entry. This defines the default image set. 
xef9_imgset_tplset_link received 1 entry. This links the default image set to the default template set. 
xef9_modules received 1 entry. This is the entry associated to the System module, the only one installed by XOOPS. 
xef9_newblocks received 12 entries.  These entries are for the 12 blocks associated to the System module. 
xef9_ranks received 7 entries.  They are "Just popping in", "Not too shy to talk", "Quite a regular", "Just can't stay away", "Home away from home", "Moderator" and "Webmaster". These are the default values of user ranking, which can be changed in the administration area. 
xef9_session received 1 entry. 
xef9_smiles received 17 entries. These are the 17 smilies first available when using the XOOPS editor.
xef9_tplset received 1 entry, the corresponding to the default template set. 
xef9_tplfile received 50 entries. These are the templates associated with the default template set and used by the System module. 
xef9_tplsource also received 50 entries. These are the templates sources stored in the database and used by the System module. 
xef9_users received 1 entry. This corresponds to the single user created during step 9/14 (Figure 14) of the installation.
The next step is to configure the website, including the site name, Meta Tags, Meta Description, Author, and Copyright information.

 

Figure 16: Site configuration data entry

The information entered in step 11/14 will have an impact on the site’s SEO score.  Information can be found here: http://en.wikipedia.org/wiki/Meta_element. It is not necessary to make all decisions at this step as the information can be edited later via the site administration area.


 

Figure 17: Theme Selection screen
The next step is to select the website theme. The Installation Wizard provides three themes that can be changed later.  Hundreds themes are available for XOOPS – see the XOOPS Theme Gallery: http://www.xoops.org/modules/extgallery/ . We select the Zetagenesis theme.
The next step is to install the modules provided with XOOPS: 
 

Figure 18: Module selection screen

Installation of the three modules included with the core package is recommended.  They provide both useful functionality and security.

 

Figure 19: All modules are selected to install

 	Tip
Experienced XOOPS users may choose to add additional modules.  Additional modules can be added to the /modules directory before activating the Installation Wizard. The Installation Wizard will install all modules at one time and can save considerable time vs. installing each of them one at a time later on.  


Once the modules are selected, click on [Next] to install them. Each module will provide feedback to confirm proper installation (Figure 20).
 

Figure 20: Module Installation feedback

Scroll down the list to confirm the modules installed successfully and click on [Next].
 
