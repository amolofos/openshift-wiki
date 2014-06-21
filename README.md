openshift-wiki
=====================
The OpenShift `jbossews` cartridge documentation can be found at:

http://openshift.github.io/documentation/oo_cartridge_guide.html#tomcat

Build
============================
Assuming that user has a openshift account and has setup already the command line tools.

1. rhc create-app wiki jbossews-2.0
2. rhc create-app wiki jbossews-2.0
   Root User: ***
   Root Password: ***
   Database Name: wiki
Connection URL:
postgresql://$OPENSHIFT_POSTGRESQL_DB_HOST:$OPENSHIFT_POSTGRESQL_DB_PORT
3. Setup Confluence based on https://confluence.atlassian.com/display/DOC/Installing+the+Confluence+EAR-WAR+Edition
  1. wget http://www.atlassian.com/software/confluence/downloads/binary/atlassian-confluence-5.5.2-war.tar.gz inside OPENSHIFT_DATA_DIR on Openshift
  2. tar -xzf atlassian-confluence-5.5.2-war.tar.gz
  3. mv confluence-5.5.2 confluence-install
  4. Setup pre-installation properties
    1. Editing confluence-install\confluence\WEB-INF\classes\confluence-init.properties by setting
confluence.home=/var/lib/openshift/53a5620750044692bd000076/app-root/data/confluence
    2. Create a file called confluence.xml and save in the <tomcat-directory>/conf/Catalina/localhost sub-directory of Tomcat.
    3. Open your new wiki.xml file and add these lines:
      ```xml
      <Context
        path="/wiki"
        docBase="/var/lib/openshift/53a5620750044692bd000076/app-root/data/confluence-install/confluence"
        debug="0"
        reloadable="true">
      </Context>
      ```
    4. Edit conf/server.xml and find the line where the Coyote HTTP Connector is defined. Add a URIEncoding="UTF-8"property to the connector:
      ```xml
      <Connector port="8080" URIEncoding="UTF-8"/>
      ```
4. Setup environmental variables :
rhc env-set atlassian.plugins.enable.wait=300 -a wiki

Changelog
============================
2014-06-21 Creating Confluence 5.5.2 on Openshift.