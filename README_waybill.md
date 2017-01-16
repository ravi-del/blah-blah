# Waybill as a service

This service generates and manages the waybills for Delhivery clients.

## Tools & Libraries
The Waybill service is comprised of following tools and libraries: <br />
JAVA   : Programming language<br/>
Vert.x : Web application framework
Maven  : Build tool <br/>
Github : Git repository hosted server<br/>

## Catalogue
### Maven Projects
#### 1. `SfMain` 
This project comprises of the code of APIs 
### Database Tables

### APIs

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
1. Clone the git hub repository to local.<br/>
`git clone https://github.com/delhivery/api-autommation.git`
```bash
private TestDataFactory testdf = TestDataFactory.getTestDataFactory();
```
