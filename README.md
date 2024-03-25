# AISA

our AISA will scan nearby drone and decode all the opendroneid packets instantly


Description of the program :
->The AISA.py is the main python file  
The ODIDScanDelegate calss basically starts scanning all nearby bluetooth device .
Opendroneid protocol broadcast packet comes with a 16b service data . and it starts
with "faff" so There is a check that  if the value startswith("faff") then i use 
binascii to priliminary decode and  the call the method  decode_service_data(service_data).
which basically decode the 16b service packet data .

-> The estimateDistance function is designed to calculate the distance 

-> The decode_longitude and decode_longitude function to estimate the latitude and logitude 
as well as also i use struck to get the accurate data.

-> insert_data_into_db method to insert data into databse . but mysql databse needs to be installed and it needs to be changes according to raspberry pi database credentials.

->parse_packet is another funtion also for decode the 16b service packet data but using fromhex .

->At the end i also use a logic to run the code as long as the raspverry pi in drone fly.


Requirements >

python version 3 

installation steps >

1. git clone the repository 

2. Navigate to cloned repository "cd AISA"

3. run the program for AISA  command "sudo python3 AISA.py"

-> To run the in every boot up of raspberry pi automattically the procedure is below 

Create a shell script: First create a shell script that will run your Python script and open a terminal window. 
Let's call it run_script.sh:

xterm -e sudo python3 /path/to/AISA.py
Replace /path/to/AISA.py with the actual path to your Python script.

Make script executable: Make the script executable by running:
chmod +x run_script.sh
Edit Crontab: Open the crontab editor by running:
crontab -e
Add Entry: Add the following line to your crontab file:
@reboot /path/to/run_script.sh
Replace /path/to/run_script.sh with the actual path to the shell script.
Save and Exit: Save your changes and exit the editor.

Now, your Python script should run every time you boot the Raspberry Pi and a terminal window should appear to display the output.

