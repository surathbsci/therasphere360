---
sidebar_position: 3
---

# TOP (Therasphere Ordering Platform)

For our vial selection flow when a user has already selected a treatmetn date, we will need to pull in inventory data from TOP if the treatment date is within `X` business days of today.

TOP's APIs are GraphQL based. They will be building a new endpoint for us, but it will be closely modeled off of the existing [`portalVialSearch`](https://top-desnd.netlify.app/therasphereportalapidocs/#query-portalVialSearch) endpoint.

# DRAFT Proposal:

![TOP Integration](/DFD/TOP.svg "TOP Integration")

## Inputs

We will pass the following params to TOP:

| Property                     | Description                                                   | Example    |
| ---------------------------- | ------------------------------------------------------------- | ---------- |
| TreatmentDate                | The date of the scheduled Treatment in user's timezone        | 2024-05-28 |
| TreatmentTime                | The time of the scheduled Treatment in user's timezone        | 18:30      |
| TreatmentFacilityId          | The treatment facility id associated with the treatment draft | 10001      |
| desiredActivitiesAtTreatment | TBD                                                           | [2]        |

## Response

```json
{
  "data": {
    "portalVialSearch": {
      "vials": [
        {
          "2.0": [
            {
              "available": 0,
              "dosage": 3.5,
              "region_code": "US",
              "surplus": false,
              "optimum_ship_date": "2024-05-23",
              "deviation": -3.45,
              "treatment_activity": 1.93,
              "calibration_date": "2024-05-26",
              "calibration_week": 1
            }
          ]
        }
      ],
      "__typename": "PortalVialResult"
    }
  }
}
```
