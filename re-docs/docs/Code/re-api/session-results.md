---
sidebar_position: 3
---

# session/results

This api is intended to be used an external system that needs to retrieve data from the activity calculator.

**Description:**

This is the main controller method used to establish a link between and external sessionGUID and data being passed into the Activity Calculator.

- Returns the results for the requested sessionGUID

## Input

CalculatorRequestDto

```json
{
  "sessionGUID": ""
}
```

## Output

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

## Errors

| Error | Description  |
| ----- | ------------ |
| 401   | Unauthorized |
