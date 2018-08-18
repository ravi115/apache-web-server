## This tutorials explains server configuration component.

**There are two types of containers**
1. The first type cotainer evaluates for each request.
   - The enclosed directory are applied to only for those request that match the containers.
   - The <IfDefine>, <IfModule>, and <IfVersion> containers.
    
2. The second type containers evalautes only at startup and restart.
   - if their conditions are true at startup then the enclosed directory will be applied to all the requests and vice-versa.
   
**Contaniers directives:-**

  1. **_IfDefine_**:-
    a. this directive will directives that will only be applied if an appropriate parameter is defined on the httpd command line.
    b. For example, with the following configuration, all requests will be redirected to another site only if the server is started using httpd -DClosedForNow:
    
             <IfDefine ClosedForNow>
                  Redirect "/" "http://otherserver.example.com/"
             </IfDefine>
    
  2. **_IfModule_**:-
    a. this directive is only applied if a particular module is available in the server.
    
          <IfModule mod_mime_magic.c>
              MimeMagicFile "conf/magic"
          </IfModule>
          
  3. **_IfVersion_**:-
    a. it encloses directives that will only be applied if a particular version of the server is executing.
    
          <IfVersion >= 2.4>
              # this happens only in versions greater or
              # equal 2.4.0.
          </IfVersion>
          
  4. we can "!" symbol to evalutes the above directives on negative condition.
  
  
**Filesystem Containers**

   1. **_Directory_**:
      a. Directives enclosed in a <Directory> section apply to the named filesystem directory and all subdirectories of that directory (as well as the files in those directories).
      b. we can also user regex to find the filesystem directory.
   
               <Directory "/var/web/dir1">
                   Options +Indexes
               </Directory>
               
   2. **_Files_**:
      a. Directives enclosed in a <Files> section apply to any file with the specified name, regardless of what directory it lies in.
               
               <Files "private.html">
                     Require all denied
               </Files>
               
               
   3. we can even combine Directory and Files to achieve more useful results.
   
               <Directory "/var/web/dir1">
                     <Files "private.html">
                           Require all denied
                     </Files>
               </Directory>
               
**Webspace Containers**:-
   1. **_LocationMatch_**:
      a. it allows perl-compatible regular expressions to be used in choosing the matches.
      
            <LocationMatch "^/private">
                  Require all denied
            </LocationMatch>
            
   2. **_Location_**:
      a. The <Location> directive need not have anything to do with the filesystem. For example, the following example shows how to map a particular URL to an internal Apache HTTP Server handler provided by mod_status. No file called server-status needs to exist in the filesystem.
   
               <Location "/server-status">
                     SetHandler server-status
               </Location>
               

**Boolean expressions**:
   1. **_If_**:
      a. The <If> directive change the configuration depending on a condition which can be expressed by a boolean expression. For example, the following configuration denies access if the HTTP Referer header does not start with "http://www.example.com/".
   
                  <If "!(%{HTTP_REFERER} -strmatch 'http://www.example.com/*')">
                         Require all denied
                  </If>
   
