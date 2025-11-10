---
sidebar_position: 1
---

# ActivityCalculatorView

The main Activity Calculator view for Single Compartment Dosemitry.

## Screen Design

Figma Design Link: [3.0.0 - Activity Calculator](https://www.figma.com/design/m37PhNdPoSBs0xamPVI2m9/Production?node-id=1996-52510&t=YwgyOoaoJswkilFA-4)

Image Export as of 16-May-2024.

**Note:** The vertical menu is not part of the SaMD application and is currently managed by the Therasphere 360 Portal.

![Activity Calculator](/docs/views/ActivityCalculatorView/ActivityCalculator-SCD-design.svg)

## Implementation

### State

| Variable           | Description                                                                                                                                            |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| commonInputs       | holds the values entered in the common inputs panel                                                                                                    |
| commonErrors       | holds any errors that have been triggered on the common inputs                                                                                         |
| targetData         | holds the values entered on each target                                                                                                                |
| calculationResults | holds the calculation results returned by the backend api                                                                                              |
| triggerValidation  | a boolean that is used to trigger validation of form fields                                                                                            |
| tabsToRemove       | holds the calculated numebr of tabs to remove when modal is presented                                                                                  |
| tabsDiff           | holds the difference between current tabs and what user wants to change the total number of tabs too for setting the active tab after a change in tabs |

### Refs

| Ref            | Description                                    |
| -------------- | ---------------------------------------------- |
| childRefTarget | A reference passed into the `TargetTabsView`   |
| childRefCommon | A reference passed into the `CommonInputPanel` |
| modalRef       | A reference passed into the `Modal`            |

### Methods

#### addTarget

Used to add a new target to the current targetData state

#### removeTarget

Used to remove the last target in the array of targets and update current targetData state

#### setTargetCount

Used to change the number of taregts to add or removed based on the numebr of targets passed into the method. Also handles the logic on if we should display a modal to the user if they are attempting to delete taregts that contain data.

#### removeModalConfirm

Method called when a user confirms they want to delete a target or targets tha contain data. Handles removing the targets from the data and setting the active tab to the last tab in the list of tabs that remains.

#### triggerCalculation

Used to synchronously call the `validateAllTargetInputs` function in the `TargetTabsView` child view and upon completion set the `triggerValidation` state value to `true`.

#### confirmValidation

Used to loop each target in `targetData` and check for any errors associated with the fields in the target, if no errors exist this method makes a call to the backend api to perform the calculation. The method also sets the calculationResults state value based on what is returned from the api.

#### closeModal

Used to close the modal when a user clicks cancel or close on the presented modal

### Hooks

- When commonInputs are changed, target results are cleared
- When calculationResults are updated, targetData is updated
- When calculationResults are updated, a message is sent to the parent window

## Dependency Graph

![Main Dependency Graph](/docs/views/ActivityCalculatorView/ActivityCalculatorView.svg "ActivityCalculatorView")
