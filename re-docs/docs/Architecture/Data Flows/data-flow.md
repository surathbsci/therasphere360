---
sidebar_position: 1
---

# SaMD and Non-SaMD Interactions

There are 3 main systems in play in the end to end solution:

1. Therasphere 360 Portal (Non-SaMD)
1. Activity Calculator (SaMD)
1. MDDS APIs / Database (Non-SaMD)
1. TOP - Therasphere Ordering Platform

The Therasphere 360 Portal is intended to provide the overall user experience.

The Activity Calculator is meant to perform activity calculations

The MDDS APIs and database are meant to store data related to treatment drafts, orders and activity calculations.

Top is the existing solution that is in place to allow for ordering of Therasphere vials. The intention is the system will be extended for this product to allow for ordering through the treatment drafts.

## High Level Data Flow Diagram

![High Level Data Flow Diagram](/DFD/DFD-diagram.svg "High Level Data Flow Diagram")

Therasphere 360 Portal will provide the Activity Calculator the following data:

| Data                          | Description                                                                            |
| ----------------------------- | -------------------------------------------------------------------------------------- |
| TreatmentFacilityTimezone     | TOP Treatment Facility Timezone for the current Treatment Draft `America/New_York`     |
| ManufacturingFacilityTimezone | TOP Manufacturing Facility Timezone for the current Treatment Draft `America/New_York` |
| TreatmentFacilityId           | TOP Treatment Facility Id for the current Treatment Draft `Format TBD`                 |
| Data                          | JSON Payload of calculation inputs and results                                         |

The above data will come in via a call to the `session/generateSession` Activity Calculator Backend Endpoint in the `user` attribute.

The Therasphere 360 Portal can optionally send a payload in the `data` attribute to pre-load data that was previously "calculated".

![Inital Session Creation with Option Data](/DFD/P2.svg "Inital Session Creation with Option Data")

The `TreatmentFacilityTimezone` and `ManufacturingFacilityTimezone` will be used to calculate the necessary offset for the MIRD calculation.

The user interacts with the Activity Calculator Frontend, adding common inputs and 1 or more sets of target inputs.

The Activity Calculator Frontend performs validation of user inputs and handles messaging to the user.

The Activity Calculator Frontend sends the inputs to the Activity Calculator Backend to perform the necessary calculations.

The Activity Calculator Frontend displays the results calculated from the backend payload.

The Activity Calculator Frontend (If embedded in an iFrame) notifies the parent window that a calculator result is ready.

The Therasphere 360 Portal calls the Activity Calculator Backend to retrieve the results of the calculation

![Retrieve Activity Calculator Results](/DFD/P3a.svg "Retrieve Activity Calculator Results")

The user will leave the context of the Activity Calculator window at this point to use other functions in the portal.

If the user comes back the Activity Calculator or the Vial Selector, the Therasphere 360 Portal will provide the Activity Calculator with teh data above including the data payload that was stored in MDDS.

The Portal will pass the SessionGUID in the querystring of the iFrame to allow SaMD to link the data in cache to the reqeust and pre-load any necessary data.
