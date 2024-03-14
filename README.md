    autoconf && ./configure && make && sudo make install
    adb backup --twrp
    twrpabx backup.ab

Extractor for TWRP ADB backup format

Output format is one or more files in TWRP in-place backup format
