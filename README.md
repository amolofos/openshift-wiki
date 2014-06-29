openshift-wiki
============================
The OpenShift `diy` cartridge documentation can be found at:

http://openshift.github.io/documentation/oo_cartridge_guide.html#diy

Build
============================
Assuming that user has a openshift account and has setup already the command line tools.

1. rhc app create wiki diy-0.1
2. rhc cartridge-add mysql-5.5    --app wiki
3. rhc cartridge-add phpmyadmin-4 --app wiki
4. git clone https://github.com/amolofos/openshift-wiki.git wiki
5. cd wiki
6. git remote add openshift ssh://53afff1f4382ecc5de000451@wiki-needingmeds.rhcloud.com/~/git/wiki.git/
7. git fetch openshift
8. git merge openshift/master
9. git add new files/commit
10. git push (to github)
11. git push openshift

Changelog
============================
2014-06-29 Initial deployment


