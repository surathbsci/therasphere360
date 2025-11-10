---
sidebar_position: 1
---

# calculate

This api is intended to be used only by the internal SaMD application to initiate an activity calculation.

**Description:**

This is the main controller method used to perform a calculation.

- Validates the payload passed in to ensure data inputs are within expected ranges.
- Makes a call to the logging module to record the call
- Calls calculator service's calculate method to perform actual calculation
- **TODO**: Need to call to encrypt the data before storing in Cache
- Calls cacheManager to store the results in Cache

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
  "sessionGUID": ""
}
```

## Output

CalculatorResponseDto

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

| Error | Description                                  |
| ----- | -------------------------------------------- |
| 400   | If any inputs are outside of expected ranges |
| 401   | Unauthorized                                 |

![Activity Calculator Backend](/re-api/Activity-Calculator-Backend.svg "Activity Calculator Backend")
