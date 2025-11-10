---
sidebar_position: 1
---

# Activity Calculator FE

The intention is to embed the Activity Calculator Frontend application in an iFrame in the overall Therasphere (TS) 360 Portal experience.

The SaMD Team has created a "Simulated" Therasphere 360 portal solution while we wait for development to ramp up on the portal.

https://re-harness.dev.apps.bsci.com

Currently we have 2 different applications setup in the CIP system for authentication purposes:

1. TS 360 Portal (Test Harness): `TP_TestHarness`
1. Activity Calculator Frontend: `App_THACQBEJ`

If both of the applications are hoested under the same domain, then authentication should seamlessly work between the applications.

If a user "Authenticates" on the `TS 360 Portal` and then the `Activity Calculator Frontend` is loaded in the iFrame, the iFrame should automatically authenticate the user and display the Activity Calculator.

Login:

![Login Screen](/embedding/RedirectToLogin.png "Login Screen")

After Login:

![After Login](/embedding/AfterLogin.png "After Login")

## Notifications to Parent

The Activity Calcualator will need to routinely communicate with the parent window to send notifications about what is heppening within the Activity Calculator.

### Calculation Complete Notification

When a user fills out the Activity Calculator fields and sucessfully performs a calculation, the Activity Calculator will need to send a `CALCULATION_READY` message to the parent window if running in embedded mode. The portal can use this notification to then retireve the results and then mark the menu for Activity Calculator as completed.

### Calculation Partial Notification

When a user fills out the Activity Calculator fields and sucessfully performs a calculation for a subset of targets, the Activity Calculator will need to send a `CALCULATION_PARTIAL_READY` message to the parent window if running in embedded mode.

This will let the portal know that they user still has additional target details that were not sucessfully calculated, which drives an indicator in the Portal menu.
