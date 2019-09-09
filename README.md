# Integration Testing Study

* [What is Integration Testing Study?](#)
* [What is an integration test?](#)
* [How do you implement an integration test?](#)
   * [STEP 1: Install chai-http to your dev-dependencies](#)
   * [STEP 2: Require "chai" and "chai-http](#)
   * [STEP 1: Require "chai" and "chai-http](#)
   * [STEP 1: Require "chai" and "chai-http](#)


<br>

## What is Integration Testing Study?
The "Integration Testing Study" is a further study of unit testing with Mocha and Chai


## What is an integration test?
An **integration test** is a logical extension of *unit testing*, which tests smaller and more independant peices of code. When two or more units 
are combined, they form an *interface*, and when two or more interfaces are combined they form a *component*.

An *integration test* determines if independently developed units work correctly when they are connected to one another.  Integration tests also 
help identify problems that occur at the interface level and test the HTTP layer and how clients interact with your API.  Additionally, integration tests also 
ensures that the functional, performance, and reliability between units are integrated and working properly.

## How do you implement an integration test?

### STEP 1: Install chai-http to your dev-dependencies
First, you need to install the chai-http npm package to your dev-dependencies in your package.json file.
```
    npm install chai-http --save-dev
```

### STEP 2: Require "chai" and "chai-http"
In your test file (which will follow naming conventions outlined in the unit testing study), you want to first require chai and chai-http.  **Chai** is a "test expectation"
library that helps you make assertions by providing functions and methods to compare output of tests with expected values.  **Chai-http** gives you access to methods such as ```chai.request()``` which you can use to make arbitrary requests to a server and then assert about the results of the request.
```JavaScript
    const chai = require("chai");
    const chaiHttp = require("chai-http");
```

### STEP 3: Import

