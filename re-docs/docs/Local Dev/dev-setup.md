---
sidebar_position: 1
---

# Setup

The main project repo is located in Gitlab [Radioembolization Dosimetry Calculator](https://gitlab.com/bostonscientific.com/io/radioembolization-dosimetry-calculator)

Ensure you are running at least Node version: `v20.10.0`

```bash
git clone https://gitlab.com/bostonscientific.com/io/radioembolization-dosimetry-calculator.git
```

## Activity Calculator Frontend

The Activity Calculator Frontend is located in `frontend`

### Install

Naviagte to the `frontend` folder and run:

```bash
npm install
```

### Configuration

The frontend uses the following env vars to inject configuration values, create a .env file in the root of the `frontend` folder with the following content:

```
REACT_APP_MAX_TARGETS=4
REACT_APP_PUBLIC_SAMD_API_URL=http://localhost:4000
```

| Variable                      | Description                                                                                                                                      |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| REACT_APP_MAX_TARGETS         | The max number of targets allowed in the application (Should be set to 4 baesd on current requirements, defaults to `4` if no value is provided) |
| REACT_APP_PUBLIC_SAMD_API_URL | The base Url of the backend api to call (defaults to `http://localhost:4000` if no value is provided)                                            |

## Running the app

**Note:** At this point oyu can run the applicaiton, but you will also need the backend running locally for the frontend to be fully functional.

```bash
# development
$ npm run dev
```

## Running the Tests

You will need a `cypress.env.json` file in the `frontend` folder for the cypress E2E tests to execute. Make sure to fill in the missing property values below with the appropriate values.

```json
{
  "TEST_USER": "",
  "TEST_PASS": "",
  "LOGIN_DOMAIN": "stg.login2.bsci.com",
  "TEST_OIDC_AUTHORITY": "https://stg.login2.bsci.com/am/oauth2/",
  "TEST_OIDC_CLIENT_ID": "APP_THACQBEJ",
  "TEST_OIDC_CLIENT_ID_PROGRAMMATIC": ""
}
```

```bash
# unit tests
$ npm run test:coverage:ci

# cypress E2E tests
$ npm run test:e2e

```

## Activity Calculator Backend

The Activity Calculator Backend is located in `backend`

### Install

#### .npmrc configuration

**Note:** This repo contains an `.npmrc` file containing the configuration for connecting to the private package registry that contains the authentication module. This file expects you to have an environment variable `NPM_TOKEN` setup that contains an access token with the approprorate rights to access the registry in Gitlab. Without this configured you may experience an error trying to install.

Naviagte to the `backend` folder and run:

```bash
npm install
```

## Environment Config

You will need to create the .env file in the root of the backend folder for running the application. Make sure to fill in the missing property values below with the appropriate values (AUTHORIZED_USERS, INTROSPECT_CLIENT_SECRET).

```properties

# IO-Auth-Module Configuration #########################################################################
# Array of token groups to require, or blank
REQUIRED_ACCESS_GROUPS=
# Array of token roles to require, or blank
REQUIRED_ROLES=
# Logging on or off
AUTH_MODULE_LOGGING=false
# Array of authorized users (Global Unique Ids)
AUTHORIZED_USERS=
########################################################################################################


# Authentication Token Endpoints (CIP) #################################################################
ISSUER_URI=https://stg.login2.bsci.com:443/am/oauth2
JWKS_URI=https://stg.login2.bsci.com:443/am/oauth2/connect/jwk_uri
########################################################################################################


# Activity Calculator API Authentication Token (CIP) Introspection Configuration #######################
# if SKIP_INTROSPECTION is set to true introspection will not be performed
INTROSPECT_ENDPOINT=https://stg.login2.bsci.com/am/oauth2/introspect
INTROSPECT_CLIENT_ID=SAMD-Stage
INTROSPECT_CLIENT_SECRET=
# SKIP_INTROSPECTION=true
########################################################################################################

```

**Note:** You should update the `AUTHORIZED_USERS` value to include your [Global Unique ID](cip-guid) that is assigned by the CIP system.

.env.test file for additional test execution config

```properties
TEST_USER=radcals.e2e@gmail.com
TEST_PASS=<PASSWORD>
LOGIN_DOMAIN=https://stg.login2.bsci.com
TEST_OIDC_AUTHORITY=https://stg.login2.bsci.com/am/oauth2/
TEST_OIDC_CLIENT_ID=APP_THACQBEJ
TEST_OIDC_CLIENT_ID_PROGRAMMATIC=
```

## Running the app

**Note:** You will also need the backend running locally for the frontend to be functional.

```bash
# development
$ npm run dev
```

3

# Running the Tests

You will need a `env.test` file in the `backend` folder for the tests to execute. Make sure to fill in the missing property values below with the appropriate values.

```json
{
  "TEST_USER": "",
  "TEST_PASS": "",
  "LOGIN_DOMAIN": "stg.login2.bsci.com",
  "TEST_OIDC_AUTHORITY": "https://stg.login2.bsci.com/am/oauth2/",
  "TEST_OIDC_CLIENT_ID": "APP_THACQBEJ",
  "TEST_OIDC_CLIENT_ID_PROGRAMMATIC": ""
}
```

```bash
# unit tests
$ npm run test

# Pactum E2E tests
$ npm run test:e2e

```
