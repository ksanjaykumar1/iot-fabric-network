

![alt text](https://github.com/ksanjaykumar1/iot-fabric-network/blob/main/docs/IOT-fabroc-network.jpg?raw=true)


1. Registering and enrolling 
   1a. Sensor/IOT will send register and enroll request to backend express server
   1b. Backend server will send request to Certificate Authority to generate crypto materials and certificates for the  Sensor/IOT 
   1c. Certificate Authority (CA)  will create crypto martieral and certificate for sensor/IOT and send it to sensor/IOT, these crypto material and certificates are needed for communicating with the network
2. Transaction 
   2a. Sensor will send request to  backend express server to create a transaction
   2b. Backend server will create a transaction request and send it to all the peer,
3. Transaction Execution 
   3a. Peers will receive the transaction request and authenticate the sensor/IOT’s certificate 
   3b. Peer will invoke the chaincode and simulate the transaction by reading the current ledger state and running the chaincode to get the values , and adding these read values and write values which peer got from running the chaincode (R-W set).
   3c. Each peer will send the simulated transaction to the backend server
4. Once the backend server will collect the simulated transaction from peers , then it will send the transaction to orderer nodes 
5. Orderer will take the transaction and put the transaction into the block and send the block to peer nodes
6. Peer nodes will validate the transaction and then commit it to the ledger.
