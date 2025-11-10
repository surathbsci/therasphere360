---
sidebar_position: 1
---

# CIP Application Configuration

CIP is our customer identity management platform. It is what is used to authenticate all of our external users, but it also handles the hand off of employee logins with the "Employee Login" just below the login button.

Openid Config: https://stg.login2.bsci.com/am/oauth2/.well-known/openid-configuration

## ClientID: App_THACQBEJ

Redirect URIs:

- https://re.internal.dev.apps.bsci.com/redirect
- http://localhost:3000/redirect
- https://re.dev.apps.bsci.com/redirect
- https://re.stage.apps.bsci.com/redirect

## ClientID: TP_TestHarness

- http://localhost:3001/redirect
- https://re-harness.internal.dev.apps.bsci.com/redirect
- https://re-harness.dev.apps.bsci.com/redirect
- https://re-harness.stage.apps.bsci.com/redirect
