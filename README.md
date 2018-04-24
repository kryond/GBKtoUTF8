With this plugin, you can edit and save the files which encodings are not supported by Sublime Text currently, especially for those used by CJK users, such as GB2312, GBK, BIG5, EUC-KR, EUC-JP, etc. GBKtoUTF8 supports both Sublime Text 2 and 3.

--------------------
Using [Package Control](https://packagecontrol.io/installation) to find, install and upgrade *GBKtoUTF8* is the recommended method to install this plug-in.

Configuration
------------------
Please check GBKtoUTF8.sublime-settings file for details. You should save your personal settings in a file named "GBKtoUTF8.sublime-settings" under "User" folder. You can set project-specific settings (except encoding_list and max_cache_size) in the .sublime-project file which can be opened via "Project > Edit Project" menu.

* encoding_list: encoding selection list when detection is failed
* max_cache_size: maximum encoding cache size, 0 means no cache (default: 100)
* max_detect_lines: maximum detection lines, 0 means unlimited (default: 600)
* preview_action: converting the file's content to UTF-8 when previewing it (default: false)
* default_encoding_on_create: specific the default encoding for newly created file (such as "GBK"), empty value means using sublime text's "default_encoding" setting (default: "")
* convert_on_load: convert the file's content to UTF-8 when it is loaded (default: true)
* convert_on_save: convert the file's content from UTF-8 to its original (or specific) encoding when it is saved (default: true)
* convert_on_find: convert the text in Find Results view to UTF-8 (default: false)
* lazy_reload: save file to a temporary location, and reload it in background when switching to other windows or tabs (default: false)
* confidence: The minimum confidence rate which the converting will be performed automatic. (default: 0.95)

Usage
------------------
In most cases, this plug-in will take care of encoding issues automatically.

You can also use the "File > Set File Encoding to" menu entry to transform between different encodings. For example, you can open a UTF-8 file, and save it to GBK, and vice versa.

Note:
* if convert_on_save is set to `false`, the file will *NEVER* be saved to the selected encoding
* please do not edit the file before the encoding detection process is finished
* please try either increasing the value of max_detect_lines or set the encoding manually if the detection result is not accurate
* due to limitation of API, when lazy_reload is set to `true`, quit Sublime Text immediately after saving a file will cause the file to be saved as UTF-8, the correct content will be reload next time Sublime Text starts

Q & A
------------------
* Q: It is not working after installation, how do I fix it?

  A: Please try the following steps:
  1. Restart Sublime Text
  2. Make sure the plug-in folder is named "GBKtoUTF8" (skip this step if you install via "Package Control")
  3. See [Note section above](#note)
  4. Disable other encoding related plug-ins
  5. Contact me

* Q: Which encodings are supported?

  A: Any [encoding supported by Python](http://docs.python.org/library/codecs.html#standard-encodings) will be fine, other encodings like EUC-TW will not be supported.

* Q: Why does the content become a mess when the window is re-activated?

  A: This is caused by reloading and has been fixed, please update your *GBKtoUTF8* to latest version.

* Q: Why does ST2 ask me that file "Has changed on disk. Do you want to reload it?" when the window is re-activated.

  A: Same reason as above. Please choose "Cancel" if you have unsaved changes to the file.

* Q: When saving the file, Sublime Text tells me the file is saved as UTF-8, why?

  A: Don't worry, the plug-in will convert your file to original encoding.

* Q: My file was saved as UTF-8 and it's in a mess, how can I recover it?

  A: Please open the file and make sure its encoding is UTF-8, then choose the menu entry "File > Save with Encoding > Western (Windows 1252)", close and reopen this file.
