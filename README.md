API-AUTOMATION
==============

API Testing script using TestNG testing framework.

## Tools & Libraries
The test automation framework is comprised of following tools and libraries: <br />
JAVA   : Programming language  
TestNg : TestNg Java testing framework (TestNG library included in maven's pom)
Maven  : Build tool <br />
Github : Git repository hosted server  
Eclipse: Integrated Development Environment 

## Implementation
To generate a TestNG report you should perform following steps:
```bash
git clone https://github.com/delhivery/api-autommation.git
mvn package
./startup.sh
```
To see a TestNG report open `/test-output/index.html` in your browser.

### Configuring `startup.sh` file
`startup.sh` file contains <br />
`java -jar target/ClientTest-0.0.1-SNAPSHOT-fat.jar -f=file_name.xml -config=config_name/config_name.config`<br/> where,
* `target/ClientTest-0.0.1-SNAPSHOT-fat.jar` is the jar created by maven package,<br />
* `file_name.xml` is the TestNG suite file,<br />
* `config_name/config_name.config` is the configuration file.
### TestNG '.xml' file
`/suites/file_name.xml` <br />
Configure the xml file (eg: file_name.xml) of TestNG by specifying the groups and classes in the suite tag. This will invoke the testing according to the details in file_name.xml file.

### Configuration file 
`/config/config_name/config_name.config` <br />
Configure the .config file (eg: config_name/config_name.config) to suit a service. Specify the endpoint and the details of the Data Base being used.

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
  expectedjson VARCHAR,aaaaaa
  httpcode INTEGER,
  baseurl VARCHAR,
    PRIMARY KEY (id)
);
```

### Test Cases
Write you TestNG test cases in the file .java with the @Test annotation.
```bash
@Test(groups = {"group_name"})
  public void testFunction() throws Exception {
  /* Example of a Test Case:
   * TestUtils.exAndValidateAPICall(testdf.getTestData(id));
   * where id = id of the corresponding test case in postgres table
   */
  }
```

