Shopping Application Demo
======================================

This demo project will get you started with automatically installing two server instances, one with JBoss Data Virtualization and the other with JBoss Fuse, and then configuring the application.


Setting up your local environment
---------------------------------


1. [Pull the project down from github](#pull-the-project-down-from-github)

2. [Install MySQL](#install-mysql)

3. [Install PostreSQL](#install-postgresql)

4. [Install JBoss Data Virtualization](#install-jboss-data-virtualization). Note that this also installs EAP, so this is all you need to run the demos.  

5. [Install local development environment - JBoss Developer Studio](#install-and-setup-jboss-developer-studio)

6. [Install JBoss Fuse](install-jboss-fuse). Only required if it is desired to run on Fuse.

7. [Install SoapUI](#install-soapui) to run the Web Service demo.

8. [Set up and run application](#setup-and-run-the-application)


Running the demos
---------------------------------

1. [View the shopping application and show products](#view-the-shopping-application-and-show-products)

2. [Add products by calling a web service](#add-products-by-calling-a-web-service)

3. [Authenticate](#authenticate)


### Pull the project down from github


[Download and unzip](https://github.com/jbossdemocentral/fuse-dv-shopping-integration-demo/archive/master.zip) the archive file.  If running on Windows, it is reccommended the project be extracted to a location near the root drive path due to limitations of length of file/path names.  Or just clone from git.

[*Back to setup*](#setting-up-your-local-environment)

### Install MySQL

1. Install MySQL Database - http://dev.mysql.com/downloads/

2. Install MySQL Workbench - http://dev.mysql.com/downloads/workbench/

3. Start server using command 'sudo mysqld_safe &'

4. Open Workbench

5. Open SQL Tab to execute the content of the following query: [support/sql-support/init_mysql.sql](support/sql-support/init_mysql.sql)

[*Back to setup*](#setting-up-your-local-environment)

### Install PostgreSQL

1. Install the PostgreSQL server (http://www.postgresql.org/download/). 

2. Open SQL Tab to execute the content of the following query: [support/sql-support/init_postgres.sql](support/sql-support/init_postgres.sql)

[*Back to setup*](#setting-up-your-local-environment)

### Install JBoss Data Virtualization

Note that this also installs EAP, so this is all you need to run the demos.

1. Go to http://access.redhat.com

2. Download JBoss Data Virtualization 6.1 (jboss-dv-installer-6.1.0.redhat-3.jar). Put this in the software folder in your local environment.

3. Run this using:

        java -jar jboss-dv-installer-6.1.0.redhat-3.jar

4. Select the "target" folder (see [screenshot](/docs/img/dv-install-location.png)) and complete the installation
	* Select all products
	* Choose passwords
	* Perform the default configuration
	* See [key options](/docs/img/dv-install-options.png)

[*Back to setup*](#setting-up-your-local-environment)


### Install and Setup JBoss Developer Studio

1. Go to http://access.redhat.com

2. Download and install JBoss Developer Studio - we used version 7.1.1 for development of these examples. 

3. Download and install the Fuse plugin. Instructions are located at https://access.redhat.com/documentation/en-US/Red_Hat_JBoss_Fuse/6.1/html-single/Tooling_Installation_Guide/.

4. Install the data virtualization development plugin. Go to JBoss Central within dev studio to install. (see [screenshot](/docs/img/dev-studio-datai-virt.png))

5. Import the project into eclipse as a Maven project.

[*Back to setup*](#setting-up-your-local-environment)


### Install JBoss Fuse

Only required if it is desired to run on Fuse.

[*Back to setup*](#setting-up-your-local-environment)


### Install SoapUI

Steps to install SoapUI TODO

[*Back to setup*](#setting-up-your-local-environment)


### Setup and run the application

The init.sh/init.bat files will be updated to complete these steps. To complete manually:

1. Install the teiid security files: copy support/dv-support/teiid-security-roles.properties AND teiid-security-users.properties to target/dv/standalone/configuration/

2. Install mysql and postgres JDBC drivers into EAP: copy support/dv-support/modules/\* to target/dv/modules

3. Install the configuration file for EAP: copy support/dv-support/standalone.dv.xml to target/dv/standalone/configuration/standalone.xml

4. Install the demo virtual database: copy support/dv-support/vdb to target/dv/standalone/deployments

5. Build the project: in the projects/shopping-demo-application run 
        mvn clean install

6. Install the WAR file into EAP: copy projects/shopping-demo-application/target/1.0.0-SNAPSHOT.shoppingApplication.war to target/dv/standalone/deployments/shoppingApplication.war

7. Start the application server: run target/dv/bin/standalone.sh or standalone.bat



[*Back to setup*](#setting-up-your-local-environment)



### View the shopping application and show products

1. Goto URL...

2. The page should display

3. Click show products. This calls ... and pulls back all the ...

[*Back to running*](#running-the-demos)

### Add products by calling a web service

TODO

[*Back to running*](#running-the-demos)

### Authenticate

TODO

[*Back to running*](#running-the-demos)



# THIS IS NO LONGER NEEDED

Once the databases are created we can move to the installation and deployment section

Configure the PROJECT.HOME/support/standalone.dv.xml file 
----------------------------------------------------------

The standalone.dv.xml holds the configuration of the datasources mapping to the JDV server. We have provided "postgres" as default username and password and for Postgres datasource and root as username and password for mysql. The user can change these values in standalone.dv xml found under /fuse-shoppng-aplication/support/dv-support.

Installing Jboss and Deploying the Application  
----------------------------------------------    

1. [Download and unzip.](https://github.com/jbossdemocentral/fuse-dv-shopping-integration-demo/archive/master.zip).  If running on Windows, it is reccommended the project be extracted to a location near the root drive path due to limitations of length of file/path names.  
  
2. Add the DV and Fuse Products to the software directory.  
  
3. Run 'init.sh' or 'init.bat' to setup the environment locally. 'init.bat' must be run with Administrative privileges.  
  
4. Run 'run.sh' or 'run.bat' to start the servers, create the container and deploy the bundles.  
  
5. Sign onto the Fuse Management console and check the console log to see the output from the routes for the use cases.  You can also view the Camel Diagrams.
