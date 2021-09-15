

![alt text](https://github.com/ksanjaykumar1/iot-fabric-network/blob/main/docs/IOT-fabroc-network.jpg?raw=true)

How sensor will communicate with the IOT-fabric-network


1. Registering and enrolling new IOT device
   
   a. The admin of the certificate Authority(CA) registers the identity of the device into CA’s server.

   b. CA’s admin will send the enrollment ID and password to the IOT device.

   c. The IOT device will enroll by sending a request to CA’s server with enrollment ID and password  

   d. CA will receive the public key-private key and crypto material needed to communicate to the gateway
   
   e. Gateway will send it back to the IoT device
1. Transaction Request
   
   a. Sensor will send request to  Gateway to create a transaction

   b. Gateway will create a transaction request and send it to all the peer,
2. Transaction Simulation 
   
   a. Peers will receive the transaction request and authenticate the sensor/IOT’s certificate 

   b. Peer will invoke the chaincode and simulate the transaction by reading the current ledger state and running the chaincode to get the values , and adding these read values and write values which peer got from running the chaincode (R-W set).

   c. Each peer will send the simulated transaction to the Gateway
3. Once the Gateway will collect the simulated transaction from peers , then it will send the transaction to orderer nodes 
4. Orderer will take the transaction and put the transaction into the block and send the block to peer nodes
5. Peer nodes will validate the transaction and then commit it to the ledger.

