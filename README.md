openshift-wiki
============================
The OpenShift `jbossews` cartridge documentation can be found at:

http://openshift.github.io/documentation/oo_cartridge_guide.html#tomcat

Build
============================
Assuming that user has a openshift account and has setup already the command line tools.

1.  rhc app-create -a wiki -g MEDIUM -t jbossews-2.0
2.  rhc cartridge-add -c  postgresql-9.2 -a wiki
4.  git clone https://github.com/amolofos/openshift-wiki.git wiki
5.  cd wiki
6.  git remote add openshift ssh://5426b6a3e0b8cdcf3b000791@wiki-needingmeds.rhcloud.com/~/git/wiki.git/
7.  git fetch openshift
8.  git merge openshift/master
9.  git add new files/commit
12. Removing unused files
    git rm -r src/ pom.xml
13. Inside wiki openshift installation, under app-root/data folder download and unzip wiki installation files (e.g. www.atlassian.com/software/confluence/downloads/binary/atlassian-confluence-5.6.3-war.tar.gz)
14. and follow https://confluence.atlassian.com/display/DOC/Installing+the+Confluence+EAR-WAR+Edition instructions.
15. Locally, add wiki.xml under ".openshift\config\Catalina\localhost" directory
16. Update wiki.xml with the following entry :
<Context path="/wiki"
         docBase="/var/lib/openshift/5426b6a3e0b8cdcf3b000791/confluence"
         debug="0"
         reloadable="true">
</Context>
17. git push (to github)
18. git push openshift


Changelog
============================
2014-09-27 Initial deployment
