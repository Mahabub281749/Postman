##### Data Driving Test #####
Req URL (Post): http://www.dummy.restapiexample.com/create

    1. Create a single entry in database:
          Request Body/ Request Payload:
          {
              "name": "mahabub",
              "salary":"4500",
              "age":"31"
          }
          
          test point:
              1. tests["check status code"] = responseCode.code = 200;
              2. tests["check status in response"] = responseBody.has("success")

              3. var response = JSON.parse(responseBody);
                 tests["check status in exact position"] = response.status == "success"

              4. pm.test("check Content-Type header", function()
                  {
                    pm.response.to.be.header("Content-Type","application/json");
                  })
                  
                 
    2. Multiple Entry:
    
          Data fiormat: csv, JSON
          Request Body/ Request Payload:
          {
              "name":"{{name}}",
              "salary":"{{salary}}",
              "age":"{{age}}"
          }
          
    3. How to run single collection which includes multiple requests:
            > Go to runner > Select Collection requests > Run
            
    4. Running postman requets from command line:
        
        Pre-requisites:
            1. Download & install node.js (npm)
                Open the cmd and write 
                
                node -v (to check node.js version)
                npm -v (to check npm version)
                
            2. Install newman
                npm install -g newman
                
            3. To generate html report
                npm install newman-reporter-html
                
            4. Export collection and then run from CMD
            
         How many ways we can run collection through CMD:
         
         Method 1:
         Syntax: newman run <<exported collection file.json>>
         Example: C:\apitestdata\>newman run EmployeeAPIS.postman_collection.json
         
         Method 2: generating html report
         Syntax: newman run <<exported collection file.json>> -r html
         Example: C:\apitestdata\>newman run EmployeeAPIS.postman_collection.json -r html
         
         Method 3: Excuting collection remotely
         Shared the collection and get the URL
         Syntax: newman run <<shared URL>> -r html


##### Fake API Creation & Testing #####

    1. Install NodeJs
    2. After Installation give below command in cmd:
        node --version
    3. npm comes with NodeJs
    4. Check version
        npm --version
    5. Install Json server
        npm install -g json-server
    6. Create info.json file with sample data (Json format)
    7. Run the below command to make your API's up and running
        json-server info.json

        GET   http://localhost:3000/users
        GET         http://localhost:3000/users/1
        POST http://localhost:3000/users
        PUT http://localhost:3000/users/4
        DELETE http://localhost:3000/users/4


##### Variables #####

    1. Collection variables
    2. Environment variables/Global variables

    Collection variables:
    Right click on -- Collection - Edit - Variables - Define varaibles (Key,value)- Update
    Usage: {{Key}}

    (Or) postman.setGlobalVariable("key","value");
    postman.clearGlobalVariable("key");

    Environment variables/Global variables:
    Manage Environments - Global-Key,Value--Save
    Usage: {{Key}}


##### Workflow #####

    postman.setNextRequest("Request Name");
    postman.setNextRequest("null")

#### Chain API ####

    1) Create Get Request (Listing all users)
        https://reqres.in/api/users?page=2
 
    2) Create Global variable "username" is xyz at collection level
 
    3) Write Test script in Request1 to update  "username"

            jsonData=JSON.parse(responseBody)
            value=jsonData.data[0].first_name
            pm.globals.set("username", value);

    4) Create Put Request (Update user by Name)
        https://reqres.in/api/users/2

    5) Parameterize username varaible in to 2nd request(PUT)
            "name": "{{username}}"
 
    6) Run Collection which contains both the requests


#### Authorization ####

    1) Basic Auth:
    https://postman-echo.com/basic-auth
    username: postman
    password: password

    2) API Key Auth
    Get Request: https://api.openweathermap.org/data/2...
    API Key/appid: fe9c5cddb7e01d747b4611c3fc9eaf2c

    3) Bearer Token / OAuth 2.0
    API Reference URL: https://developer.github.com/v3/repos/
    Post Request: https://api.github.com/user/repos


#### Pre-Request Script ####


    Pre-Request Script  -- Request---Response-- Test Script

    Collection
        Folder
            Requests

    Pre-Request Script: console.log("")
    Test Script: console.log("")


#### Postman Scripting ####

    Postman Scripting using JavaScript and Chai BDD
    ------------------------------------------------
    Reference Link : https://learning.postman.com/docs/writing-scripts/test-scripts/