jenkins-rpm-build
=================

An RPM containing scripts to assist with configuring Jenkins RPM building projects


Usage
=================
Once this RPM has been built and installed on a Jenkins server you'd build RPM projects
as follows:

* Configure RPM source project version control (svn/git). If many RPMs are packaged into a single project consider
  using the File System SCM plugin to create individual RPM builds from a single project checkout
* Use the free-style software project to configure a new job to build the RPM project ensuring
  that the name of the Jenkins job is the same as the name of the rpm.
* In the Build section of the job configuration screen, click the Add build step drop-down and choose
  the Execute shell option. In this command window you'd add the /usr/local/bin/jenkins-build-rpm.sh script


Download
=================
Download [source](http://static-01.andyspohn.com/rpm/centos/6/jenkins-rpm-build-1.0.src.rpm) rpm
or binary (noarch) rpm for [CentOS 6](http://static-01.andyspohn.com/rpm/centos/6/jenkins-rpm-build-1.0.noarch.rpm)


Building
=================
Clone this project into PROJECT_DIR

    git clone https://github.com/spohnan/jenkins-rpm-build.git

Build the RPM

    rpmbuild \
        --define "release `date +%Y%m%d%H%M%S`" \
        --define "_topdir $PROJECT_DIR/jenkins-rpm-build" \
        -ba SPECS/jenkins-rpm-build.spec
