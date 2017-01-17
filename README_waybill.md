# Waybill as a service

This service generates and manages the waybills for Delhivery clients.

## Tools & Libraries
The Waybill service is comprised of following tools and libraries: <br/>
JAVA   : Programming language<br/>
Vert.x : Web application framework<br/>
Maven  : Build tool <br/>
Github : Git repository hosted server<br/>

## Catalogue

### Maven Projects
#### 1. `SfMain` 
This project contains :
* The code for all APIs of Waybill Service.
* StartVerticle.java is where the execution starts. This will deploy three Vertx verticles namely `HttpVerticle`,`LotWaybillVerticle`,`HttpClientVerticle`.
 * `HttpVerticle` - Reads the configuration file and starts HTTP server on a port.
 * `LotWaybillVerticle` - Registers the request handlers

#### 2. `lambdas`
This project contains

#### 3. `Util` 

### Database Tables
#### 1. Lots Table
#### 2. Prefix Table 
#### 3. Client Sequence Table
#### 4. Waybills Table

### APIs
#### 1. Create Lot 
#### 2. Lot by ID
#### 3. Lots by Client
#### 4. Create Dynamic Waybill
#### 5. Consume Waybill
#### 6. UnConsume Waybill
#### 7. Waybill by ID
#### 8. Validate Waybill

## Execution
```bash
git clone https://ravi-del@bitbucket.org/DelhiveryTech/waybill_service.git
cd Util/utils
mvn clean install
cd ../../SfMain/
mvn clean package
chmod +x startup.sh
./startup.sh
```
