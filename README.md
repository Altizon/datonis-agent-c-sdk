# datonis-agent-c-sdk
C language version of Datonis Agent SDK

How to use this C SDK for communicating via MQTT/HTTP:
1. There is a directory called MQTTPacket. This source is copied from PAHO and modified slightly:
   http://git.eclipse.org/gitroot/paho/org.eclipse.paho.mqtt.embedded-c.git
   It provides utility functions needed for talking MQTT i.e. it converts user data into a MQTT understandable form.
   Nothing needs to be done here by you as an Agent Implementer.
2. There is a directory called Edge. This handles the Datonis packet structure and communication protocols (MQTT/HTTP) essential for communication
   Functions declared in the edgegateway.h should be called by your Business logic for pushing data/receiving data.
3. There is a directory called Implementation. This is where you should be implementing the hardware specific stuff. Example: TCP/IP socket communication API, time related utilities
   A sample that runs on Linux is provided. YOU NEED TO IMPLEMENT THIS SOCKET COMMUNICATION API AS PER YOUR UNDERLYING HARDWARE.
   CHANGE THE transport.c, timeutil.c FILES ACCORDINGLY
4. sample.c is the file that contains an example business logic that sends data using the edgegateway.h interface
5. Compiling:
   run: make clean install

