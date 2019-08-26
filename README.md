# Fast-Reliable-File-Transfer
Customised user level application to transfer file reliably over high latency lossy link at a high speed.

For a duplex link with 20% packet loss and 200ms delay, TCP fails to provide the optimum throughput when it comes to transferring very large files(1GB). 
A customised file transfer protocol is developed that uses UDP along with NACK to ensure high speed and reliability.

The main aim is to break the large file into packets of 1464 bytes. The packet contains data, one flag bit(1 for last packet and 0 otherwise) and one sequence bit. The server sents the packets updating the flag bit and the sequence bit for each packet. The client sends the NACK if it does not receive a particular packet of that particular sequence number.
