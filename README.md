# Fast-Reliable-File-Transfer
Customised user level application to transfer file reliably over high latency lossy link at a high speed.

For a duplex link with 20% packet loss and 200ms delay, TCP fails to provide the optimum throughput when it comes to transferring very large files(1GB). 
A customised file transfer protocol is developed that uses UDP along with NACK to ensure high speed and reliability.

This project is executed on the DETERLab testbed.

The main aim is to break the large file into packets of 1464 bytes. Each packet contains data, one flag bit(1 for last packet and 0 otherwise) and one sequence bit. The client initially sends the file size with sequence number 0 as the first packet, so that the server is updated about how many total number of packets are going to be received for that file. It then sends the packets updating the flag bit and the sequence bit for each packet. The server on the other hand sends the NACK if it does not receive a particular packet of particular sequence number. Also, the server send the NACK with -1 if it successfully receives all the packets indicating that the file was successfully sent transferred.

Steps for running the application:

Use basic.ns file to create a topology of 2 nodes connected to each other via a duplex link.
SSH into the two nodes using different terminal windows.
Adjust the delay and losses on the link.
Run server_nack.py on server node and client_nack.py on the client node.

Results obtained on 100 Mbps Duplex link with 200ms delay and 20% loss:

Throughput = 35.79Mbps
Transfer time = 240 sec
