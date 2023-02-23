The following are instructions for installing Apache Maven and Java 8 on an Amazon EC2 instance. These are required for the Amazon Neptune Signature Version 4 authentication samples.

## Steps To Install Apache Maven and Java 8 on your EC2 instance

1. Connect to your Amazon EC2 instance with an SSH client.

2. Install Apache Maven on your EC2 instance. First, enter the following to add a repository with a Maven package.

    ``sudo wget https://repos.fedorapeople.org/repos/dchen/apache-maven/epel-apache-maven.repo -O /etc/yum.repos.d/epel-apache-maven.repo``

- Enter the following to set the version number for the packages.

    `sudo sed -i s/\$releasever/6/g /etc/yum.repos.d/epel-apache-maven.repo`
- Then you can use yum to install Maven.

    `sudo yum install -y apache-maven`

    mvn -emp admin
    {O4OsKtFoBCMH6Enyv1w7crgEv2AT+88mDxwT+fYIr64=}


    sudo su
  b. cd /root
  c. mkdir .m2
  cd .m2

    nano settings-security.xml

    add the content to above file after change above password from line 6

<?xml version="1.0"?>
<settingsSecurity>
     <master>{O4OsKtFoBCMH6Enyv1w7crgEv2AT+88mDxwT+fYIr64=}</master>
</settingsSecurity>

7. We have to encrypt nexus password and update it in 9
a. mvn -ep admin
{masbUk+Bov8HcIX0k9C5TZ0qvuPOlwusW7WUSn8kCLQ=}
8. create settings.xml file
a. nano settings.xml


9. above file below content after change above password from line 6

<?xml version="1.0" encoding="UTF-8"?>

<settings xmlns="http://maven.apache.org/POM/4.0.0"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">

 <localRepository>/var/lib/jenkins/.m2/repository</localRepository>

<servers>
   <server>
        <id>nexus</id>
        <username>admin</username>
        <password>{masbUk+Bov8HcIX0k9C5TZ0qvuPOlwusW7WUSn8kCLQ=}</password>
  </server>
</servers>

<mirrors>
<mirror>
<id>nexus</id>
<name>nexus</name>
<url>http://13.235.132.119:8081/repository/maven_project/</url>
<mirrorOf>*</mirrorOf>
</mirror>
</mirrors>
</settings>



10. move above two files to /var/lib/jenkins/.m2
a. mv settings.xml /var/lib/jenkins/.m2
b. mv settings-security.xml /var/lib/jenkins/.m2
11. To check
a. ls /var/lib/jenkins/.m2
12. Get into the folder
cd /var/lib/jenkins/.m2
13. Change ownership of the 2 files
a. chown jenkins:jenkins settings.xml settings-security.xml
14. Change permissions of the 2 files
a. chmod 755 settings.xml settings-security.xml
    
3. The Gremlin libraries require Java 8. Enter the following to install Java 8 on your EC2 instance.

    `sudo yum install java-1.8.0-devel`
4. Enter the following to set Java 8 as the default runtime on your EC2 instance.

    `sudo /usr/sbin/alternatives --config java`
- When prompted, enter the number for Java 8.

5. Enter the following to set Java 8 as the default compiler on your EC2 instance.

    `sudo /usr/sbin/alternatives --config javac`
- When prompted, enter the number for Java 8.

6. Verify your maven version
    `mvn -v`

### Project Preparation
7. Create the `.m2` directory in the home directory of your current user
    `mkdir ~/.m2`

8. Create the Settings file inside of the `~/.m2` directory
    `cd ~/.m2/`
    `mv demo/settings.xml ~/.m2/`
