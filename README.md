# rdf4j_on_tomcat_install
Provides a ready-to-use Tomcat install and RDF4J war files to install RDF4J  over Tomcat.

The process involves:
- Install Tomcat
- StartTomcar html manager
- Deploy RDF4J

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
   <user username="admin" password="password" roles="admin-gui,manager-gui"/>
</tomcat-users>
```   
