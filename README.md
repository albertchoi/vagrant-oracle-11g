# Vagrant Oracle 11g + SSL

Vagrant script to install Oracle Database 11g with SSL enabled.

Forked from: [paykin/vagrant-oracle-11g](https://github.com/paykin/vagrant-oracle-11g), for which detailed instructions are at [http://java.paykin.info/install-oracle-database-vagrant-puppet/](http://java.paykin.info/install-oracle-database-vagrant-puppet/).

## Prerequisites

- Vagrant
- VirtualBox

## Instructions

1. Clone this repo

		$ git clone https://github.com/albertchoi/vagrant-oracle-11g.git
		
2.  Download [Oracle 11g Release 2 64-bit for Linux](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/112010-linx8664soft-100572.html) (Oracle login required).  The two files should be:

	- linux.x64_11gR2_database_1of2.zip
	- linux.x64_11gR2_database_2of2.zip
	

3.  Copy the two zip files into `modules/oracles/files` in this repo.

4.  Start the VM.

		$ cd vagrant-oracle-11g
		$ vagrant up
		
5.  Coffee break!

6.  A file called `certificate.txt` should be created in the current directory.  This should be imported as a trusted certificate into truststore of your JVM to enable JDBC connections.  E.g.

		$ keytool -import -alias myOracle -file certificate.txt -keystore <JAVA_HOME>/jre/lib/security/cacerts -storepass changeit

7.  Connect to the database via port 1521 for unencrypted connections and port 2484 for SSL connctions.  The password for the `system` user is `password`.





