    #build twrpabx and install it into my linux, or download from https://github.com/diyism/twrpabx/releases/tag/0.0.1 and run "install twrpabx" in linux
    autoconf && ./configure && make && sudo make install

    adb backup --twrp
    twrpabx backup.ab      //conert backup.ab into data.f2fs.win
    adb push data.f2fs.win /sdcard/TWRP/BACKUPS/00000/
    adb install nandroid_manager_v3.0_alpha-9.apk
    #open nandroid manager in my android phone and restore selected apps and app data

Extractor for TWRP ADB backup format

Output format is one or more files in TWRP in-place backup format
