    #build twrpabx and install it into my linux
    #or download from https://github.com/diyism/twrpabx/releases/tag/0.0.1 and run "install twrpabx" in linux
    autoconf && ./configure && make && sudo make install

    #"power button + volume up" to reboot my phone into teamwin recovery
    #in my linux, run these commands:
    adb backup --twrp      //while in my phone's teamwin recovery, select only "Data" partition
    twrpabx backup.ab      //convert backup.ab into data.f2fs.win
    adb push data.f2fs.win /sdcard/TWRP/BACKUPS/00000/
    adb install nandroid_manager_v3.0_alpha-9.apk
    #open nandroid manager in my android phone, maybe pop up busybox installation
    #nandroid manager found "00000", click "00000", click "RESTORE DATA", click "Restore Apps+Data", loading all apps, select apps, click "RESTORE" button

Extractor for TWRP ADB backup format

Output format is one or more files in TWRP in-place backup format
