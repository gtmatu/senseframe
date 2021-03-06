# How to use the sample Web App

The WebApp consists of two separate scripts: receiver.py and initPage.py.  
 </br> 
`initPage.py` will open the web app at the IP : http://127.0.0.1:5000/  
`receiver.py` will generate logs for three nodes while continuously updating the JSON (`status.json`) file from which the web page reads.

### Set up
In order to run the web app, a few settings must be adjusted. 
In receiver.py : 

```
user = "YourApplicationID"
password = "ApplicationKey"
```

These can be found in the overview page of your application on The Things Network Console.
 
Instructions on how to set up an application on TTN, [here](https://github.com/alexander3605/SenseFrame/wiki/3.---How-To-Use-The-Framework#the-gateway-and-application).

The following dictionary must also be updated in `API_network_callbacks.py`:

```
nodeInfo = {       
    "A" : {
        "dev_id" : "node1",
        "dev_addr" : "26012FDF"
    },
    "B" : {
        "dev_id" : "node2",
        "dev_addr" : "26012F6D"
    },

    "C" :{        
        "dev_id" : "node3",
        "dev_addr" : "26012F8C"
    }
}
```
After registering your devices, update the table above with the respective values, found on the overview page of each device on the TTN console.

### Using the Web App
Once the set up is complete, the web app can be run by running both scripts simultaneously. The receiver script will generate logs, one per node. Each log contains all uplink and join messages, displaying some relevant data alongside that such as the transceiver settings, signal strength upon reception and the payload. The script will add on to the log every time the system sends a message. If you wish to start a new log, delete the current log, or rename the file. This will cause the script to generate a new log file for the appropriate node.  
</br>
The web app then displays the data being sent by the three nodes, along with the time at which the last packet was received, and connection status. The data is currently set to pressure, temperature and light intensity, however there is no processing done to the data received from the node, it is simply displayed in the box.  
The web app deems a node to be disconnected when it had not received a message from that node for more than 1 minute.


### Example of page running
![alt text](https://github.com/alexander3605/senseframe/blob/master/images/WebAppScreenshot.png "WebApp Screenshot" )
