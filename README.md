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
