openshift-wiki
============================
The OpenShift `jbossews` cartridge documentation can be found at:

http://openshift.github.io/documentation/oo_cartridge_guide.html#tomcat

Build
============================
Assuming that user has a openshift account and has setup already the command line tools.

1. rhc app-create -a wiki -g MEDIUM -t jbossews-2.0
2. rhc cartridge-add -c  postgresql-9.2 -a wiki
4. git clone https://github.com/amolofos/openshift-wiki.git wiki
5. cd wiki
6. git remote add openshift ssh://5426b6a3e0b8cdcf3b000791@wiki-needingmeds.rhcloud.com/~/git/wiki.git/
7. git fetch openshift
8. git merge openshift/master
9. git add new files/commit
10. git push (to github)
11. git push openshift

Changelog
============================
2014-09-27 Initial deployment
