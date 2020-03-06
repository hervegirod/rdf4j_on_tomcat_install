# rdf4j_on_tomcat_install
Provides a ready-to-use Tomcat install and RDF4J war files to install RDF4J  over Tomcat.

The process involves:
- Install Tomcat
- StartTomcat server
- StartTomcat html manager
- Deploy RDF4J
- Configure RDF4J
- Start RDF4J

# Install Tomcat 
Unzip the Tomcat-install.zip file wnywhere on your system. Then change the following files:
- bin/startup.bat
- conf/tomcat-users.xml

## edit startup.bat
Change the `@echo off` instruction at the beginning of the file by `@echo on`

Add the following lines before the `setlocal` instruction:
```
set CATALINA_HOME=<your Tomcat directory> (for example: L:\WRK\Java\Onto\Tomcat)
set JAVA_HOME=<your JRE install directory> (for example: C:\Program Files\Java\jre1.8.0_111)
```
  
Add a `pause` instruction at the end of the file

## edit tomcat-users.xml
Add the following users declaration inside the `tomcat-users` node:
```
   <role rolename="admin-gui"/>
   <role rolename="manager-gui"/>
   <user username="admin" password="blabla" roles="admin-gui,manager-gui"/>
```   

You will have the following file:
```
<tomcat-users xmlns="http://tomcat.apache.org/xml"
              xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
              xsi:schemaLocation="http://tomcat.apache.org/xml tomcat-users.xsd"
              version="1.0">
   <role rolename="admin-gui"/>
   <role rolename="manager-gui"/>
   <user username="admin" password="blabla" roles="admin-gui,manager-gui"/>
</tomcat-users>
```   

# StartTomcat server
Start Tomcat by double clicking on the startup.bat file.

# StartTomcat html manager
Go in your web browser and type `http://localhost:8080/` in the address bar.

# Deploy RDF4J
Click on the `Manager App` button and type the admin / blabla user and password. You will be redirected in the Manager web application.

Now Deploy the two war files which are in the rdf4j-workbench.zip zip file. Note that you must wait until the first deployment is done before going to the second one. You will normally see /rdf4j-server and /rdf4j-workbench in the list of applications.

If you have several other jar files that you want to use in your RDJ4J install, now is the time:
- copy these Jar files in the directory webapps/rdf4j-server/WEB-INF/lib/ under your Tomcat install.

Now quit Tomcat by closing the Java app in the windows task bar and restart it.

# Configure RDF4J
Go in your web browser and type `http://localhost:8080/rdf4j-workbench` in the address bar. 

## Create a repository
Create a new repository. Note: Use the default configuration for all parameters, but with the following constraint:
- Use only lower case characters for the title and the id

## Add a triple store
Creating a triple store is performed by clicking on Add under the "Modify" tab.
