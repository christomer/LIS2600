![logo-og.png](resources/CE263CB31DB34D5B3C7F753BAE70AF66.png)

**phpMyAdmin** is an open source tool written in PHP and designed to handle the administration of MySQL or MariaDB through the use of a Web browser. It can perform various tasks such as creating, modifying or deleting databases, tables, fields or rows; executing SQL statements; or managing users and permissions. The software, which is currently available in 78 languages, is maintained by The phpMyAdmin Project. 

Features provided by **phpMyAdmin** include:

* Web interface
* MySQL and MariaDB database management
* Import data from CSV and SQL
* Export data to various formats: CSV, SQL, XML, PDF (via the TCPDF library), ISO/IEC 26300 - OpenDocument Text and Spreadsheet, Word, Excel, LaTeX and others
* Administering multiple servers
* Creating PDF graphics of the database layout
* Creating complex queries using Query-by-Example (QBE)
* Searching globally in a database or a subset of it
* Transforming stored data into any format using a set of predefined functions, like displaying BLOB-data as image or download-link
* Live charts to monitor MySQL server activity like connections, processes, CPU/Memory usage, etc.
* Working with different operating systems.

(A `blob`, or binary large object, is a collection of binary data stored as a single entity in a database management system. Blobs are typically images, audio or other multimedia objects, though sometimes binary executable code is stored as a blob.)

MySQL was originally designed to be used from the command line, and it still fully supports this modality. However, owing to the complexities of relational databases, it is often easier to work with administrative tools that provide a visual interface; hence, the popularity of phpMyAdmin.

## Installing phpMyAdmin

![xampp.png](resources/A1964D9CD29143B0333603C028E1BA8B.png)

**[XAMPP](https://www.apachefriends.org/index.html)** is an open source, cross-platform Web server package developed by Apache Friends, consisting mainly of the Apache HTTP Server, MariaDB database, and interpreters for scripts written in the PHP and Perl programming languages. (Since XAMPP 5.5.30 and 5.6.14, XAMPP ships MariaDB instead of MySQL. The commands and tools are the same for both. MariaDB is a community-developed fork of the MySQL relational database management system. The MariaDB community is led by the original developers of MySQL, who forked it due to concerns over MySQL's acquisition by Oracle.) XAMPP stands for Cross-Platform (X), Apache (A), MariaDB (M), PHP (P) and Perl (P). It is a lightweight Apache distribution that makes it easy for developers to create a local Web server for testing and deployment purposes. Everything needed to set up a Web server – server application (Apache), database (MariaDB), and scripting language (PHP) – is included in an extractable file. Since most actual Web server deployments use the same components as XAMPP, it makes transitioning from a local test server to a live server easy as well. Officially, XAMPP's designers intended it for use only as a development tool, to allow website designers and programmers to test their work on their own computers without any access to the Internet. To make installation as simple as possible, many important security features are disabled by default. XAMPP has the ability to serve web pages on the World Wide Web. A special tool is provided to password-protect the most important parts of the package.

At present, XAMPP includes versions that support PHP 5 and PHP 7, respectively. The version using PHP 5 should be used in this course.

![xampp\_setup.png](resources/9F5FF81CA8181968B1352C4847CCCD84.png)

![xampp\_setup\_2.png](resources/7236D36E1409302604C5F9BAAD6E3AFD.png)

![xampp\_setup\_3.png](resources/7E3C4541EC6AE7A19BF0A4C53B36B9C9.png)

![xampp\_setup\_4.png](resources/545F2FAAE669040B04244FB15EB063E2.png)

![xampp\_setup\_5.png](resources/E511CF15FB5802A98416C02734545333.png)

![xampp\_setup\_complete.png](resources/26A95B50E0E09019A132E628F45E0A1D.png)

This is the XAMPP Control Panel, running as a desktop application.

![xampp\_control\_panel\_1.png](resources/04C2F9B49F883625F9FF3D39BB35515C.png)

![xampp\_manage\_servers.png](resources/C65EC671233889E3A346B2CA581066BE.png)

A couple of related notes: phpMyAdmin will be fully functional in the XAMPP configuration only if the MySQL server is running. The ProFTPD application is of incidental importance in the database-oriented exercises, but it will be of vital importance in the event that the XAMPP installation is used subsequently for Web design. 

---

![phpmyadmin\_1.png](resources/179F93C6CF398FD6E797DADF1A21C958.png)

Below is another view of the XAMPP Control Panel. Note that in this instance that FileZilla, Mercury, and Apache Tomcat have been included in this version.

![aid4772-728px-Install-phpMyAdmin-on-Your-Windows-PC-Step-7.png](resources/4024C3A742E2CBCA70364E996A3F9437.png)

### An Alternative to XAMPP: MAMP

![mamp\_1.png](resources/3ADA000B7F099CD5CC969047A77934F1.png)

[MAMP](https://www.mamp.info/en/) is an alternative to XAMPP. There are two significant differences. The first difference is that MAMP continues to support MySQL, and the second one is that MAMP is available in two editions: the first one is based exclusively on open source software and available for free, whereas the second edition incorporates proprietary management software and is available under a commercial license.

To use the MAMP under OS X, your system must meet the following requirements:

* Operating system: Apple OS X 10.6.6 or later
* Mac with 64-Bit CPU from Intel (x84)
* User account that allows to administer the computer (Administrator)

For systems running Microsoft Windows — MAMP is officially supported on Windows 7, Windows 8 , and Windows 8.1 — the requirements are:

* 1GB RAM
* .NET Framework 4.0

![mamp\_2.png](resources/17858E7C3D268B0A0B2DE350BC70DF6F.png)

### Installing phpMyAdmin on a Linux System

If you are using a Linux system or a virtual machine running a standard Linux distribution such as Debian or Ubuntu, installing phpMyAdmin is a straightforward process. It begins from the command line with this instruction:

`sudo apt-get install phpmyadmin`

(If you're using Ubuntu 7.10 (Gutsy) or later, select Apache2 from the "Configuring phpmyadmin" dialog box.)

To set up under Apache all you need to do is include the following line in /etc/apache2/apache2.conf: 

`Include /etc/phpmyadmin/apache.conf`

Once phpMyAdmin is installed point your browser to `http://localhost/phpmyadmin` to start using it. You should be able to login using any users you've setup in MySQL. If no users have been setup, use admin with no password to login. 

You may also install phpmyadmin from source code. Since this method circumvents the package manager, you will need to install updates yourself. 

To install it from source, open the console and `cd` to the www directory using:

`cd /var/www/`

Then download it using `svn` by writing:

`sudo svn checkout https://phpmyadmin.svn.sourceforge.net/svnroot/phpmyadmin/tags/STABLE/phpMyAdmin phpMyAdmin`

([Apache Subversion](https://subversion.apache.org/), often abbreviated SVN, after the command name `svn`, is a software versioning and revision control system distributed as free software under the Apache License. Software developers use Subversion to maintain current and historical versions of files such as source code, web pages, and documentation. Its goal is to be a mostly compatible successor to the widely used Concurrent Versions System (CVS). The free software community has used Subversion widely: for example in projects such as Apache Software Foundation, Free Pascal, FreeBSD, GCC, Mono and SourceForge. CodePlex offers access to Subversion as well as to other types of clients.)

Then cd to phpMyAdmin:

`cd phpMyAdmin`

Create the directory config:

`sudo mkdir config`

Change the permissions of the `config` directory:

`sudo chmod o+rw config`

Navigate to `http://localhost/phpmyadmin/scripts/setup.php` in your Web browser and follow the instructions for setting up phpMyAdmin.

Or you may download the latest stable version of the PhpMyAdmin software at [http://www.phpmyadmin.net/home_page/downloads.php](http://www.phpmyadmin.net/home_page/downloads.php). If you are working from the Linux command line, use the utility called `wget to download phpMyAdmin:

`wget www.phpmyadmin.net/home_page/downloads.php`

Then, extract the archive file on your computer. In the Linux environment, the following command will extract phpMyAdmin to a folder:

`unzip phpMyAdmin-4.6.0-all-languages.zip`

If `unzip` is not installed, the following command will download and install it:

`sudo apt-get install unzip`

The simplest approach to download the file phpMyAdmin-4.6.0-all-languages.zip to `/var/www/html' and extract it there. Then, load the PhpMyAdmin page with your Web browser, using the corresponding URL (for example `http://www.yourdomainname.com/phpMyAdmin/scripts/setup.php`, where you should substitute www.yourdomainname.com with your actual domain name).

### Webmin: an Alternative to phpMyAdmin

**Webmin** is a Web-based system configuration tool for UNIX-like systems, although recent versions can also be installed and run on Windows. With it, it is possible to configure operating system internals, such as users, disk quotas, services or configuration files, as well as modify and control open source apps, such as the Apache HTTP Server, PHP or MySQL.

Webmin is largely based on Perl, running as its own process and Web server. It defaults to TCP port 10000 for communicating, and can be configured to use SSL if OpenSSL is installed with additional required Perl Modules.

Webmin is built around modules, which have an interface to the configuration files and the Webmin server. Webmin can be expanded by installing modules. This makes it easy to add new functionality. It is also possible for a programmer to write plugins for desktop configuration. Webmin allows for controlling many machines through a single interface.

Webmin is released under the BSD license.

![Webmin-Screenshot.png](resources/6C49A06BFB736AEEC825B685E82A7613.png)

This is the basic Webmin interface above. The interface of the module affording access to the MySQL server is illustrated below.

![mysql-database-server.png](resources/4E3CD1010E8120C32CB2EBA1FEBB670F.png)

## Logging into phpMyAdmin

![2.jpg](resources/88DD7C8B0FFC06A3201F60288810DB54.jpg)

The default username of phpMyAdmin is "root" and the password is "admin". If phpMyadmin is installed on a computer to which other users have access, both the administrative userID and password should be changed during the first session.

In the view below, phpMyAdmin is being used to review the fields in a database table.

![phpmyadmin-screenshot-02.png](resources/7F6421537555A6EF7D5FEA1B46E12BDF.png)

phpMyAdmin enables an administrator to create users (as well as databases) and assign them privileges — read, write, create and delete, etc.

![users.png](resources/A90465292A770743A8D33AC2DCF5856B.png)



