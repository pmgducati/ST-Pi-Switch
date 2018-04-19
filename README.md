# ST-Pi-Switch
Pi Zero Version Relay Pin 13(GPIO27) LED Pin 15(GPIO22)


1. Setup the pi and make sure it has a static IP on the same network as the ST Hub
2. Copy pi-smartthings-task-runner.py to the home directory and edit the file
    sudo nano pi-smartthings-task-runnery.py
        Change door and door1 to the desired names, 11 to target pin, if more than one is device is going to be controlled add second line (see ex below))

ex:
          'door':   [{'name': 'door1', 'gpio': {'activate':11}},
                     {'name': 'door2', 'gpio': {'activate':12}}]



Save and exit

3. Update Pi and install all pre-reqs:
    sudo apt-get update && sudo apt-get upgrade && sudo apt-get update && sudo apt-get upgrade && sudo apt-get install python3 && sudo apt-get install python3-pip && sudo apt-get install python3-rpi.gpio  && sudo pip3 install flask

4. Test Rpi functionality:
    sudopython3 pi-smarthings-task-runner.py
    In Chrome: 192.168.X.X:82/door/door1/activate (change door and door 1 to match your variables)

5. Smartthings Setup:
    Goto https://graph.api.smartthings.com/
    
    Make sure Hub is registering in My hubs
    
    Goto Device Handler and add a new one
        Give it a name
        Create a unique identifier in the namespace field
        choose "Switch" Type
        Scroll to the bottom and select "Create"

        A Code Window will open
            Copy the code from coffee.groovy (below the dotted line)
            In the Smartthings window delete everything after -capability "Switch"- and paste the code
                    edit "Coffee Maker button was pushed" to your desired message (line 68)
            save and publish

    Create a Device
        Enter Desired Name
        Enter unique device network id
        Choose Type (custom Device Handlers will be at the bottom of the list)
        Select your Hub
        Save
        edit the preferences and input the IP and port id the pi (ex. 192.168.1.132:82)
        Save

DONE!


Thanks Rob S. for all your Help!
