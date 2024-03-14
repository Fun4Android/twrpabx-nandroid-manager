    #build twrpabx and install it into my linux
    #or download from https://github.com/diyism/twrpabx/releases/tag/0.0.1 and run "install twrpabx" in linux
    autoconf && ./configure && make && sudo make install

    #"power button + volume up" to reboot my phone into teamwin recovery
    #in my linux, run these commands:
    adb backup --twrp      //while in my phone's teamwin recovery, select only "Data" partition,
                           //get the file backup.ab, it may be over 30GB
    twrpabx backup.ab      //convert backup.ab into data.f2fs.win
                           //the data.f2fs.win is a tar file, we can "archivemount data.f2fs.win /mnt/tar"
                           //but the files in /mnt/tar are FBE(file based encrypted) format
                           //so we need push it into phone and let nandroid manager to decrypt it
    adb push data.f2fs.win /sdcard/TWRP/BACKUPS/00000/
    adb install nandroid_manager_v3.0_alpha-9.apk
    #open nandroid manager in my android phone, maybe pop up busybox installation(need reinstall busybox every reboot)
    #nandroid manager found "00000", click "00000", click "RESTORE DATA", 
    #click "Restore Apps+Data", loading all apps, select apps, click "RESTORE" button

twrpabx: Convert TWRP ADB format(backup.ab) into TWRP/nandroid format(data.f2fs.win)

"TWRP(teamwin recovery) + twrpabx + nandroid manager app" can replace Titanium Backup Pro

    Redmi K30用了整三年后一次充电拔线后启动卡死在G logo页面,
    到teamwin recovery里wipe掉cache和dalvik cache仍不能正常启动,
    可能是data分区某个系统设置有损坏,
    执行factory reset能启动, 但会清空data分区所有应用,
    最后用adb backup --twrp+twrpabx+nandroid manager修复
