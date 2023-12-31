# BambuLabOBSOverlay
Utility script to poll your printers MQTT and write telemtry to text files that can be consumed by OBS

# Requirements
- BambuLab printer with OBS configured to livestream (https://wiki.bambulab.com/en/software/bambu-studio/virtual-camera).  This has only been tested on the X1 Carbon
- Python3 execution environment on same machine OBS is running

# Configuration
There are 4 variables at the top of the script you need to populate with your specific info:

Found on printer touch screen under Settings (hex icon) -> Network:

BAMBU_IP_ADDRESS - The IP address of your printer.
ACCESS_CODE - Network access code generated by your printer


Found on printer touch screen under Settings (hex icon) -> General:
SERIAL - Serial number of your printer

OUTPUT_PATH - What ever directory you want the output files written to

# Output files:
All files are written under OUTPUT_PUT.

telemetry.txt - Info about printer (layer, temp, speed)
ams.txt - Info specific to AMS.  More info is provided for Bambu filament.
telemetry.json - Full JSON doc from that last query.  Provided for inspection and debugging purposes 
telemetry.err.json - When the JSON returned doesn't match expectations for keys.  Provided for debugging

# Usage:
Edit the script to populate the variables mentioned in Configuration and run.  Changes you want to make
for content written to files can be done in the on_message handler.  The script will need to be started independantly
of your live stream and kept running as long as you want the on screen stats to update.


Inside of OBS configure "Text (GDI)" sources for each text file.

Done.
