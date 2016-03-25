RPM-Example Project Example
==========================
	
### Configuration 
Builds RPM package from war file. Two files are included in this folder.

1. rpm.spec - spec file used by the RPMBUILD command
2. rpmbuild - executed from Jenkins to set up the rpmbuild directory for the rpm.spec
3. Jenkins is running on Centos or Redhat OS.  
4. Tomcat is installed on /usr/local/tomcat7/webapps

### Jenkins Configuration  
1. Create a freestype project and enable Generic-Artifactory Integration
2. Enter in "Published Artifacts" ${WORKSPACE}/rpmbuild/RPMS/noarch/*rpm -- location of the rpm file from rpmbuild
3. Enter in "Resolved Artifacts" <location of war file>=>$WORKSPACE/$JOB_NAME/SOURCE
4. For the Build Step - Execute shell with the following commands 
  * cd $WORKSPACE/$JOB_NAME
  * bash rpmscript.sh <rpm-name> $BUILD_NUMBER

   where rpm-name is the name of the webapp to be deployed in /tomcat7/webapps directory 

### Future work 
1. Run RPMBUILD in a Jenkin Slave with Centos or Redhat OS. 
