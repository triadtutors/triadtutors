## Static Analysis by semgrep

semgrep (add to definitions/tools) is a static analysis tool. 

The below is an output from semgrep. There are 18 findings in 10 files, and 
when reviewing the findings below, the filename is first listed and then the 
violated rule is next marked by chevrons, and then a description of the 
problem. Jump to our [Discussion](#discussion) below.

``` linenums="1" hl_lines="1 10 27 76 86 97 115 122 134 151"
backend/chatbot_api/chatbot/settings.py
❯❱ python.django.security.audit.django-rest-framework.missing-throttle-config.missing-throttle-config
    Django REST framework configuration is missing default rate- limiting options. This could        
    inadvertently allow resource starvation or Denial of Service (DoS) attacks. Add                  
    'DEFAULT_THROTTLE_CLASSES' and 'DEFAULT_THROTTLE_RATES' to add rate-limiting to your application.
    Details: https://sg.run/vzBY                                                                     
                                                                                                    
    70┆ REST_FRAMEWORK = {

backend/chatbot_api/chatbot/views.py
❯❯❱ python.django.deserialization.tainted-json-django.tainted-json-django
    The application may convert user-controlled data into an object, which can lead to an insecure     
    deserialization vulnerability. An attacker can create a malicious serialized object, pass it to the
    application, and take advantage of the deserialization process to perform Denial-of-service (DoS), 
    Remote code execution (RCE), or bypass access control measures. To prevent this vulnerability,     
    leverage data formats such as JSON or XML as safer alternatives. If you need to deserialize user   
    input in a specific format, consider digitally signing the data before serialization to prevent    
    tampering. For more information, see: [Deserialization                                             
    prevention](https://cheatsheetseries.owasp.org/cheatsheets/Deserialization_Cheat_Sheet.html) Even  
    for a data-only serialization format such as JSON, a malicious string may cause the decoder to     
    consume considerable CPU and memory resources. Limiting the size of data to be parsed is           
    recommended.                                                                                       
    Details: https://sg.run/bY4Z                                                                       
                                                                                                        
    386┆ data = json.loads(request.body)

docker-compose.yaml
❯❱ yaml.docker-compose.security.no-new-privileges.no-new-privileges
    Service 'wpcli' allows for privilege escalation via setuid or setgid binaries. Add 'no-new-
    privileges:true' in 'security_opt' to prevent this.                                        
    Details: https://sg.run/0n8q                                                               
                                                                                                
    33┆ wpcli:

❯❱ yaml.docker-compose.security.writable-filesystem-service.writable-filesystem-service
    Service 'wpcli' is running with a writable root filesystem. This may allow malicious applications to
    download and run additional payloads, or modify container files. If an application inside a         
    container has to save something temporarily consider using a tmpfs. Add 'read_only: true' to this   
    service to prevent this.                                                                            
    Details: https://sg.run/e4JE                                                                        
                                                                                                        
    33┆ wpcli:

❯❱ yaml.docker-compose.security.no-new-privileges.no-new-privileges
    Service 'db' allows for privilege escalation via setuid or setgid binaries. Add 'no-new-
    privileges:true' in 'security_opt' to prevent this.                                     
    Details: https://sg.run/0n8q                                                            
                                                                                            
    63┆ db:

❯❱ yaml.docker-compose.security.writable-filesystem-service.writable-filesystem-service
    Service 'db' is running with a writable root filesystem. This may allow malicious applications to
    download and run additional payloads, or modify container files. If an application inside a      
    container has to save something temporarily consider using a tmpfs. Add 'read_only: true' to this
    service to prevent this.                                                                         
    Details: https://sg.run/e4JE                                                                     
                                                                                                    
    63┆ db:

❯❱ yaml.docker-compose.security.no-new-privileges.no-new-privileges
    Service 'nginx' allows for privilege escalation via setuid or setgid binaries. Add 'no-new-
    privileges:true' in 'security_opt' to prevent this.                                        
    Details: https://sg.run/0n8q                                                               
                                                                                                
    80┆ nginx:

❯❱ yaml.docker-compose.security.writable-filesystem-service.writable-filesystem-service
    Service 'nginx' is running with a writable root filesystem. This may allow malicious applications to
    download and run additional payloads, or modify container files. If an application inside a         
    container has to save something temporarily consider using a tmpfs. Add 'read_only: true' to this   
    service to prevent this.                                                                            
    Details: https://sg.run/e4JE                                                                        
                                                                                                        
    80┆ nginx:
                                        
frontend/src/Login.tsx
❯❯❱ typescript.react.security.react-insecure-request.react-insecure-request
    Unencrypted request over HTTP detected.
    Details: https://sg.run/1n0b           
                                            
    50┆ const response = await axios.post(local_endpoint, {
    51┆   username,
    52┆   password,
    53┆ });
                                                    
frontend/src/components/Drawer.tsx
❯❯❱ typescript.react.security.react-insecure-request.react-insecure-request
    Unencrypted request over HTTP detected.
    Details: https://sg.run/1n0b           
                                            
    161┆ const response = await axios.post('http://127.0.0.1:8000/options/', {
    162┆   // message_id but converted to an integer
    163┆   message: parseInt(node.id, 10),
    164┆   option_name: newOptionText
    165┆ });
                                                
frontend/src/views/LayoutFlow.tsx
❯❯❱ typescript.react.security.react-insecure-request.react-insecure-request
    Unencrypted request over HTTP detected.
    Details: https://sg.run/1n0b           
                                            
    176┆ fetch('http://localhost:8000/prompts/')
    ⋮┆----------------------------------------
    351┆ const request = await axios.post('http://127.0.0.1:8000/options/link/', {
    352┆   message: source,
    353┆   next_prompt: target,
    354┆ });
    ⋮┆----------------------------------------
    382┆ const response = await axios.post('http://127.0.0.1:8000/options/', {
    383┆   // message_id but converted to an integer
    384┆   message: parseInt(connectingNodeId.current, 10),
    385┆   option_name: 'New Option'
    386┆ });
                                                        
frontend/src/views/ResourceEditing.tsx
❯❯❱ typescript.react.security.react-insecure-request.react-insecure-request
    Unencrypted request over HTTP detected.
    Details: https://sg.run/1n0b           
                                            
    59┆ const response = await axios.get('http://localhost:8000/resources/');
                                        
nginx/conf.d/default.conf
❯❱ generic.nginx.security.alias-path-traversal.alias-path-traversal
    The alias in this location block is subject to a path traversal because the location path does not
    end in a path separator (e.g., '/'). To fix, add a path separator to the end of the path.         
    Details: https://sg.run/ZvNL                                                                      
                                                                                                    
    7┆ location /admin {
    8┆     alias /usr/share/nginx/html/;
    9┆     index admin.html;
    10┆     try_files $uri $uri/ /admin.html =404;
    11┆ }
                                            
plugin/docker-compose.yaml
❯❱ yaml.docker-compose.security.no-new-privileges.no-new-privileges
    Service 'db' allows for privilege escalation via setuid or setgid binaries. Add 'no-new-
    privileges:true' in 'security_opt' to prevent this.                                     
    Details: https://sg.run/0n8q                                                            
                                                                                            
    21┆ db:

❯❱ yaml.docker-compose.security.writable-filesystem-service.writable-filesystem-service
    Service 'db' is running with a writable root filesystem. This may allow malicious applications to
    download and run additional payloads, or modify container files. If an application inside a      
    container has to save something temporarily consider using a tmpfs. Add 'read_only: true' to this
    service to prevent this.                                                                         
    Details: https://sg.run/e4JE                                                                     
                                                                                                    
    21┆ db:
                                                            
plugin/plugin_src/prototypes/openIcon.html
❯❱ html.security.audit.missing-integrity.missing-integrity
    This tag is missing an 'integrity' subresource integrity attribute. The 'integrity' attribute allows
    for the browser to verify that externally hosted files (for example from a CDN) are delivered       
    without unexpected manipulation. Without this attribute, if an attacker can modify the externally   
    hosted resource, this could lead to XSS and other types of attacks. To prevent this, include the    
    base64-encoded cryptographic hash of the resource (file) you’re telling the browser to fetch in the 
    'integrity' attribute for all externally hosted files.                                              
    Details: https://sg.run/krXA                                                                        
                                                                                                        
    127┆ <script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>
```

### Discussion
semgrep was able to identify several security concerns in our application 
including in our Django application, Docker, nginx, and in http delivery. 

The Django error from Line 1 is about ensuring the application is resistant to
DOS and resource starvation attacks by setting up throttling.

The Django error from Line 10 highlights a problem where we deserialize the 
incoming request and an attacker could use that as a pathway for an attack.

The Docker error on Line 28, 44, 60, and 135 is about a risk with Docker where an
attacker may be able to gain elevated privileges within the system and cause
further damage. 

The Docker error on Line 35, 51, 67, and 142 is about a risk of having a writeable file
system. An attacker could potentially access our system and make use of this
fact to make an attack.

The Typescript error on Line 77, 87, 98, and 116 are about using HTTP. HTTP has
been mostly replaced by HTTPS these days because of the security issues around
plain-text transmission with HTTP.

The HTML error on Line 152 is about preventing an attacker from intercepting
the axios.min.js payload and replacing it with something else that could affect
the site. 

### Possible Fixes
We did not have time to address some of these fixes so we leave that as future
work to be completed. 

The first thing that should be addressed is migrating from HTTP to HTTPS. HTTP
is an unsecure protocol and moving to HTTPS will ensure that traffic is 
encrypted.

We can address the Django issue to prevent DOS attacks by implementing Django
settings that prevent this from happening.

The docker errors require some re-work of how we have Docker configured so that
writeable volumes are limited. We would have to architect this out a bit and
re-do the Docker design.

The HTML error is an easy fix. We just need to add a hash check to the page so
that we a certain that the files are what we expect them to be and haven't been
intercepted and substituted with a bad file. 