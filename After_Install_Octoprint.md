
# While doing the Octoprint setup

* restart Octoprint
  * curl "http://dockerapi:8080/?command=docker restart klipperondocker_dockerapi_1"
  

# After Octoprint setup
* install Octoklipper plugin
  * ...
* Settings -> Folders 
  * set Upload Folder to "/uploads"
* Settings -> Serial Connection
  * Serial port: "/tmp/printer"
  * Baud rate: 115200
