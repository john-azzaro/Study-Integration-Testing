# Integration Testing Study

* [What is Integration Testing Study?](#)
* [What is an integration test?](#)
* [How do you implement a basic (GET) integration test](#)
   * [STEP 1: Install chai-http to your dev-dependencies](#)
   * [STEP 2: Require "chai" and "chai-http](#)
   * [STEP 3: Create a middleware for chai-http](#)
   * [STEP 4: Import server.js](#)
   * [STEP 5: Setup your test suite](#)


<br>

## What is Integration Testing Study?
The "Integration Testing Study" is a further study of unit testing with Mocha and Chai

<br>

## What is an integration test?
An **integration test** is a logical extension of *unit testing*, which tests smaller and more independant peices of code. When two or more units 
are combined, they form an *interface*, and when two or more interfaces are combined they form a *component*.

An *integration test* determines if independently developed units work correctly when they are connected to one another.  Integration tests also 
help identify problems that occur at the interface level and test the HTTP layer and how clients interact with your API.  Additionally, integration tests also 
ensures that the functional, performance, and reliability between units are integrated and working properly.

<br>

## How do you implement a basic (GET) integration test?

### STEP 1: Install chai-http to your dev-dependencies
First, you need to install the chai-http npm package to your dev-dependencies in your package.json file.
```
    npm install chai-http --save-dev
```

### STEP 2: Require "chai" and "chai-http"
In your test file (which will follow naming conventions outlined in the unit testing study), you want to first require chai and chai-http.  **Chai** is a "test expectation"
library that helps you make assertions by providing functions and methods to compare output of tests with expected values.  **Chai-http** gives you access to methods such as ```chai.request()``` which you can use to make arbitrary requests to a server and then assert about the results of the request.  Additionally, you want to declare a variable for "expect" from chai import.
```JavaScript
    const chai = require("chai");
    const chaiHttp = require("chai-http");
    const expect = chai.expect;
```

### STEP 3: Create a middleware for chai-http
To use chai with chai-http every time there is a request, create a middleware function what will be used every time the app recieves a request.
```JavaScript
    const chai = require("chai");
    const chaiHttp = require("chai-http");
    const expect = chai.expect;

    chai.use(chaiHttp);                      // chai-http middleware
```

### STEP 4: Import server.js
Of course, you will need to import and create variables for certain parts of server.js since the object of the integration test is to test the http layer.  In the example below,
we import server.js and use destructing to create multiple variables, specifically: server.app, server.runServer, and server.closeServer.  To see more on this, check out the server.js
file in the study files above.
```JavaScript
    const chai = require("chai");
    const chaiHttp = require("chai-http");
    const expect = chai.expect;

    chai.use(chaiHttp);

    const {app, runServer, closeServer} = require('../server');       // 3 variables created from server.js
```

### STEP 5: Setup your test suite
Use "describe" to group your tests.  *Describe* takes a string and a callback In the case of this test, the string will be set to "Users".
```JavaScript
    describe('Users', function() {
        ...
    }); 
```

### STEP 6: Add "before" and "after" functions BEFORE any tests
Before any of your tests run, you use the "before" hook to run the server.  In this example, the "runServer" function in the example *asynchronously* starts the server and returns a promise, which is returned with "return runServer".  After the tests run (in case there are other test modules to run), you use the "after" hook to close the server.  Remember, if there are other as well because if the server is already running, it will error out.
```JavaScript
    describe('Users', function() {

        before(function() {                  // "before" with callback to run the server.
            return runServer();
        });
        after(function() {                   // "after" with the callback to close the server.
            return closeServer();
        });

    });
```
