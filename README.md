# COS-MQTTClient
MQTT Client implemented in Caché Object Script

Fully functional sample implementation to demonstrate all kind of MQTT Client activities (publish, subscribe).
For more information regarding the MQTT protocol visit the http://mqtt.org website,
 or examine the OASIS standard specification: http://docs.oasis-open.org/mqtt/mqtt/v3.1.1/os/mqtt-v3.1.1-os.html

Questions, bug reports, recommendations are highly welcome to Attila.Toth@InterSystems.com

Installation
- Import and compile the MQTTClient.xml file onto one of your Caché / Ensemble namespaces.

Usage
- For detailed information- including usage exmpale look into the class documentation of Net.MQTT.Client

There are a few known (and maybe some unknown) limitations:
- It's not prepared for SSL / TLS communication.
- TCP/IP based only, cannot be used with web-socket based MQTT Brokers.
- Communication of the Net.MQTT.Client and background Net.MQTT.Agent instances is limited to the tasks to be done / completed. 
   This could be enriched with for example status information of the Agent, which would make it easier to monitor the background job from the Client interface 
   and check its health status in certain scenarios.
- Incoming and outgoing messages are simply logged into the Net.MQTT.MessageStore class. No any checks for duplicate messages are done 
   (when an incoming message is repeated by the Broker, due to a lost acknowledge).
- For incoming QoS Level 2 messages no retry mechanism is implemented: if no PUBREL message would arrive for the PUBREC acknowledge, 
   the Agent will message remains in the Net.MQTT.Aux.MessageStatus table (registered with a "waiting for PUBREL" status).

Version history
- 0.9: Initial version  