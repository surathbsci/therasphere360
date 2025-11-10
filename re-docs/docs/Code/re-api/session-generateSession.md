---
sidebar_position: 2
---

# session/generateSession

This api is intended to be used an external system that needs to pass data into the activity calculator.

**Description:**

This is the main controller method used to establish a link between and external sessionGUID and data being passed into the Activity Calculator.

- Accepts a sessionGUID to attach to the data.
- Optionally accepts Inputs and Results

## Input

CalculatorRequestDto

```json
{
  "inputs": {
    "targets": [
      {
        "desiredDose": 0,
        "targetName": "",
        "targetVolume": 0,
        "targetIndex": 0
      }
    ],
    "common": {
      "lungShuntFraction": 0,
      "previousLungDose": 0,
      "anticipatedResidualWaste": 0,
      "lungMass": 0
    }
  },
  "results": [
    {
      "requiredActivity_GBq": 0,
      "requiredActivity_mCi": 0,
      "doseToLungs": 0,
      "cumulativeDoseToLungs": 0,
      "inputs": {
        "lungShuntFraction": 0,
        "previousLungDose": 0,
        "anticipatedResidualWaste": 0,
        "lungMass": 0,
        "desiredDose": 0,
        "targetName": "",
        "targetVolume": 0
      }
    }
  ],
  "sessionGUID": ""
}
```

## Output

Returns a 200 resposne with no payload

## Errors

| Error | Description                                  |
| ----- | -------------------------------------------- |
| 400   | If any inputs are outside of expected ranges |
| 401   | Unauthorized                                 |
