Appendix 3: Translating XOOPS to Local Language

If you're looking for a XOOPS 2.5.x translations into local languages, you will be able to download them most of the time from your local support sites.
After release of each XOOPS version, you will be able to download some of them from the SourceForge Files area, in the "XOOPS Core Translations" section. There are two flavors:
1) Full XOOPS 2.5.x Local Installations 
2) XOOPS 2.5.x Language Files - you install first the standard XOOPS, and then copy the language files over your XOOPS files.
You can also check the SVN Source Code for Language translations
If your language files are not available, you’ll need to translate the files yourself. All files that need to be translated, are located in directories called “/language/english”. There are several of them within XOOPS. As first, make a copy the folder and rename the new folder to your local language, e.g. /spanish. Then translate the English text within each file into your language.  
The easiest way to translate is to use http://google.com/translate
1.	Open file to translate (e.g. /language/english/comment.php)
2.	The text to translate is included in the “define” lines, e.g.

define('_CM_COMDELETED', 'Comment(s) deleted.');
define('_CM_COMDELETENG', 'Could not delete comment.');
define('_CM_DELETESELECT', 'Delete all its child comments?');
3.	Copy these lines to the Translation window in http://google.com/translate
4.	Select your local language and click “Translate”. If your local language is German, you would see something like:

define('_CM_COMDELETED', 'Comment (s) gelöscht.');
define('_CM_COMDELETENG', 'Konnte keine Kommentar löschen.');
define('_CM_DELETESELECT', 'Löschen Sie alle untergeordneten Kommentare?');
5.	Replace the English text in the file with the translated text. Of course, the mechanical translation is not always correct, and you’ll need to review it before saving. 

But this should get you on the way.  You can also use the "xTransam" module for it, but you would have to install XOOPS first, before using it.
We'll need both ISO and UTF-8 translations. To have UTF-8 file, you can save the ISO file as UTF-8 file using notepad++, but make sure that you select in "Format" menu, the "Convert to UTF-8 without BOM" option.
Once you finalize your translation, please share it with other XOOPS users:
Guidelines for Translation Submissions
1. Package name: lang-2.5.0-< language code >.< encoding >.zip or .tar.gz
The language code and character set encoding is the same as in global.php (_LANGCODE and _CHARSET).
e.g. lang-2.5.0-pt_BR.UTF-8.zip 
     lang-2.5.0-da.ISO-8859-1.tar.gz

2. The translation package should only include *core language* files, no system files or module language files except for the system module. Use the same language directory structure as the XOOPS core package. 
e.g. lang-2.5.0-da.ISO-8859-1/install/language/danish/(files).php 
                              /language/danish/(files).php 
                              /modules/system/language/danish/(files).php

Required information:
- Name of language (of course)
- Name of translator(s)/credits
- URL link to translation package
- (optional) support url - where people can post their comments about the translation

 	Note
1. Languages requiring core changes for date/calendar formats can also include the changed core files in the package.
2. core change to include the language in the $language_array variable of install/install.php is also ok.

 
