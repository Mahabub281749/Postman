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
