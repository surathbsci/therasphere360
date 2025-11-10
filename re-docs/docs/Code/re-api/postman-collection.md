---
sidebar_position: 4
---

# Postman

The postman collection has the following structure:

- Activity Calculator
  - CIP User Auth
    - Step 1
    - Step 2
    - Step 3
  - Session
    - 1. generateSession
    - 2. results
    - 3. checkAuth
  - Calculate
    - Calculate 1 Target
    - Calculate 2 Targets
    - Calculate 4 Targets
    - Calculate 4 Targets

## Use

### Configuration

1. Import the [collection](/re-api/Activity-Calculator.postman_collection.json) into Postman
2. Open the collection level variables tab and update teh current value of both `test-username` and `test-password` to valid user credentials

### Making Calls

1. Always begin by running the entire folder `CIP User Auth` to get a valid token based on the credentials you added in configuration step 2. (Right click and run folder, keep defaults and click Run)
2. Choose any of the other calls in `Session` or `Calculate`, they should inhert the token that was captured by running the `CIP User Auth` you can always check the collection variables if you think something is not working. `AuthCode_AccessToken` should be populated with a valid token.
