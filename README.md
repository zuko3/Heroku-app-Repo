# Heroku-app-repo
This repository acts as source repository for Heroku app deployment.

# Steps for deployment of JS(Angular 5) app  in Heroku:

# 1. Install Express as dependency.
D:\ANGULAR\recipieBook>npm install express
  
# 2. Build your app
Building the app is easy run below command <br/><br/>
D:\ANGULAR\recipieBook>ng build --prod --aot                               
Date: 2018-01-04T12:46:12.081Z                                                                                
Hash: 9eb127024970c30f769d                                                                                    
Time: 64579ms                                                                                                 
chunk {0} 0.91a1e46c1b7f1cf47610.chunk.js () 972 bytes  [rendered]                                            
chunk {1} main.4bc2a673676fa421a98a.bundle.js (main) 911 kB [initial] [rendered]                              
chunk {2} polyfills.5600db1c56078c4ea7cb.bundle.js (polyfills) 61 kB [initial] [rendered]                     
chunk {3} styles.176e4d821cc3a21887b2.bundle.css (styles) 115 kB [initial] [rendered]                         
chunk {4} inline.74516ca29352d5044f4b.bundle.js (inline) 1.47 kB [entry] [rendered] 
<br><br>You’ll see builds file generated  in the ‘dist’ folder with a single index.html file which can be served using a web server.

# 3.  Modifyin package.json file
 a)  Move below dependency from dev dependencies section to dependencies section.<br>
 "typescript": "~2.4.2"<br>
 "@angular/cli": "1.6.0"<br>
 "@angular/compiler-cli": "^5.0.0"<br><br>
 b)  Replace your start script<br>
 ```
 "scripts": {
        ...
        "start": "node server.js",<br>
         ...
  }
```
# 4.  Adding server.js file for start script.
```
var express = require('express');
var path = require('path');
var serveStatic = require('serve-static');
app = express();
app.use(serveStatic(__dirname));
var port = process.env.PORT || 5000;
app.listen(port);
console.log('server started '+ port);
```

# 5.  Stucture your files and commit in your git account:
Arrange your dist, package.json file and server.js file in below structure.
```
--dist
--package.json
--server.js
```

# 6. Create New Heroku App and Manual deployment steps.
1.  Login to your Heroku account and click on the ‘New’ button located at top right corner and then click on ‘Create New App’.<br>
Provide your application name and click create app.<br>
2.  Heroku will ask you the deployment method. Here, select the Github button and authenticate your GitHub account.
type your repository name where code is placed. Select the git branch and click connect.<br>
3.  After connecting to your github repository, select the Github branch (by default master) under manual deploy(skipping automatic deploy tab) a and click on Deploy Branch button. Wait few seconds and you will see the success screen once the code is deployed in Heroku instance.<br>
4.  click View button to see your deployed application
