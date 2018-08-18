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
  
  
