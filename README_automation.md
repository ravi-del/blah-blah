# API-AUTOMATION

API Testing script using TestNG testing framework.

## Tools & Libraries
The test automation framework is comprised of following tools and libraries: <br />
JAVA   : Programming language  
TestNg : TestNg Java testing framework (TestNG library included in maven's pom)<br/>
Maven  : Build tool <br/>
Github : Git repository hosted server<br/>
Eclipse: Integrated Development Environment 

## Implementation
To execute test cases and generate a TestNG report you should perform following steps:

1. Clone the git hub repository to local.<br/>
`git clone https://github.com/delhivery/api-autommation.git`

2. Use maven package command to create a fat jar.<br/>
`mvn package`

3. Make you shell script executable using chmod and then execute it.<br/>
`chmod +x startup.sh` <br/>
`./startup.sh`

To see TestNG report open `/test-output/index.html` in your browser.

## How to add a Test Case for a New Service
### Writing test cases
Write you TestNG test cases in java file (preferably in package com.delhivery.tests.modules) with the `@Test` annotation.
```bash
private TestDataFactory testdf = TestDataFactory.getTestDataFactory();
@Test(groups = {"group_name"})
  public void testFunction() throws Exception {
  /* Example of a Test Case:
   * TestUtils.exAndValidateAPICall(testdf.getTestData(id));
   * where id = id of the corresponding test case in postgres table
   */
  }
```
Add this Main Class into pom.xml file.

### Initializing the Postgres Database
Add a table in Postgresql Database with the test data.
```bash
sudo -su postgres psql
CREATE USER your-username WITH PASSWORD your-password;
CREATE DATABASE database_name OWNER your-username;
GRANT ALL PRIVILEGES ON database_name TO your-username;
CREATE TABLE table_name(
  id INTEGER NOT NULL,
  service VARCHAR,
  requestjson VARCHAR,
  reqtype VARCHAR, -- request type
  qparam VARCHAR,  -- query parameter
  expectedjson VARCHAR,
  httpcode INTEGER,
  baseurl VARCHAR,
    PRIMARY KEY (id)
);
CREATE INDEX service_index ON table_name (service);
```

### Configuring `startup.sh` file
The shell script `startup.sh` file contains <br />
`java -jar target/ClientTest-0.0.1-SNAPSHOT-fat.jar -f=file_name.xml -config=config_name/config_name.config`<br/> where,
* `target/ClientTest-0.0.1-SNAPSHOT-fat.jar` is the jar created by maven package,<br />
* `file_name.xml` is the TestNG suite file,<br />
* `config_name/config_name.config` is the configuration file.



### TestNG '.xml' suites file
`/suites/file_name.xml` <br />
Configure the suite file (`file_name.xml` in this case) of TestNG by specifying the groups and classes in the suite tag. This will invoke the testing according to the details in file_name.xml file.




### Configuration file 
`/config/config_name/config_name.config` <br />
Configure the .config file (`config_name/config_name.config` in this case) to suit a service. Specify the endpoint of the service (The test cases would pick up the endpoint from config file according to the value of key 'service' in the data base) and the details of the Postgres Data Base being used such as Database name, username, password, table name, Database driver name, etc. in the configuration file.
