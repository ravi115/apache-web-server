## This Tutorilas explains how to setup apache on linux machine.

**To check if apache is already installed on the machine**

        rpm -q httpd
        
**To install apache2**
  
        sudo apt-get install apache2 apache2-doc apache2-utils

 
**Directory structures: for httpd server a form of apache web server | in case of apache2 just replace httpd -> apache2** 
                  
               **File name**                             **Description**
              _________________                         _____________________________________________________________
              /usr/sbin/httpd                           server binary
              /etc/httpd                                directory containing server configuration files
              /etc/httpd/conf                           directory containing main configuration files
              /etc/httpd/conf.d                         directory containing configuration files for individually packaged  modules, like ssl, php, perl etc
              /etc/httpd/logs                           symbolic link to /var/log/httpd
              /etc/httpd/modules                        symbolic link to /usr/lib/httpd/modules
              /etc/httpd/run                            symbolic link to /var/run
              /usr/lib/httpd/modules                    server modules
              /var/log/httpd                            server log
              /var/run                                  runtime variables
              /var/run/httpd.pid                        server process ID
              /var/www/html                             public html files
     _______________________________________________________________________________________________________________________
  
**Main Configuration file is:**
    
      /etc/httpd/conf/httpd.conf
 1. this file already contains a large information of all kind of setting which is commented.
 2. we should always backup the original cnfig file if we are modifying into the same.
 
 **we can configure the hostname and corresponding ip address basically known as viurtual hosting**
 1. open the hosts file.
        
          /etc/hosts
 2. add the ip and corresponding name resoulution like below one.
 
         127.9.8.1    www.example.com
         
         
**content configuration**
1. **_/var/www/html_**: The actual web content, which by default only consists of the default Apache page you saw earlier, is served out of the /var/www/html directory. This can be changed by altering Apache configuration files.
  
**Server Configuration**

1. **_/etc/apache2_**: The Apache configuration directory. All of the Apache configuration files reside here.

2. **_/etc/apache2/apache2.conf_**: The main Apache configuration file. This can be modified to make changes to the Apache global configuration. This file is responsible for loading many of the other files in the configuration directory.
    
3. **_/etc/apache2/ports.conf_**: This file specifies the ports that Apache will listen on. By default, Apache listens on port 80 and additionally listens on port 443 when a module providing SSL capabilities is enabled.

4. **_/etc/apache2/sites-available/_**: The directory where per-site "Virtual Hosts" can be stored. Apache will not use the configuration files found in this directory unless they are linked to the sites-enabled directory (see below). Typically, all server block configuration is done in this directory, and then enabled by linking to the other directory with the a2ensite command.

5. **_/etc/apache2/sites-enabled/_**: The directory where enabled per-site "Virtual Hosts" are stored. Typically, these are created by linking to configuration files found in the sites-available directory with the a2ensite. Apache reads the configuration files and links found in this directory when it starts or reloads to compile a complete configuration.
    
6. **_/etc/apache2/conf-available/, /etc/apache2/conf-enabled/_**: These directories have the same relationship as the sites-available and sites-enabled directories, but are used to store configuration fragments that do not belong in a Virtual Host. Files in the conf-available directory can be enabled with the a2enconf command and disabled with the a2disconf command.
    
7. **_/etc/apache2/mods-available/, /etc/apache2/mods-enabled/_**: These directories contain the available and enabled modules, respectively. Files in ending in .load contain fragments to load specific modules, while files ending in .conf contain the configuration for those modules. Modules can be enabled and disabled using the a2enmod and a2dismod command.

**Server Logs**

1. **_/var/log/apache2/access.log_**: By default, every request to your web server is recorded in this log file unless Apache is configured to do otherwise.

2. **_/var/log/apache2/error.log_**: By default, all errors are recorded in this file. The LogLevel directive in the Apache configuration specifies how much detail the error logs will contain.

 
