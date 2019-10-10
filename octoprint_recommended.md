
# While doing the Octoprint setup

## Restart Octoprint
* set this into Settings -> Server -> Commands -> Restart OctoPrint
```
curl --verbose "http://dockerapi:8080/?command=docker%20restart%20klipperondocker_octoprint_1"
```  

# After Octoprint setup
* install Octoklipper plugin
  * ...
* Settings -> Folders 
  * set Upload Folder to "/uploads"
* Settings -> Serial Connection
  * Serial port: "/tmp/printer"
  * Baud rate: 115200
  * Additional serial ports: "/tmp/printer"

On the Octoprint main page
* on the file tab
  * click on wrench icon, select "Only show files on SD card"
