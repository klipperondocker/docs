# Serial Path
Replace ```/dev/``` in serial path with ```/hostdevices/```

Example:
```
[mcu]
serial: /dev/some/path
pin_map: arduino
```
becomes
```
[mcu]
serial: /hostdevices/some/path
pin_map: arduino
```

# Virtual SD Card
```
[virtual_sdcard]
path: /opt/storage/uploads/
```

# List files Gcode Macro
```
[gcode_macro REFRESH_SD_CARD]
gcode:
  M20
  M21
```
