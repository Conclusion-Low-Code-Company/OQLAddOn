# OQLAddOn


## Description
Adding list parameter support, loading records via either call dataset document from Studio or statement

## Typical usage scenario
Use this module if you want to create OQL statements with an `IN`-operator. 

## Features and limitations
Features
- Add a list of objects to your OQL-statements with support for the `IN`-operator (https://docs.mendix.com/refguide/oql-operators/):
  - `IN` Matches any value in a subquery or a list of expression values.	
    - `City IN (SELECT Name FROM City WHERE Country = 'Gelre')`
    - `City IN ('Losdun', 'Die Haghe', 'Haagambacht')`

- Load records instead of creating new instances via either a dataset - and thus leveraging the consistency check - within Studio Pro or create a statement manually.

## Dependencies
- v1.0.0 for MX 8.18.23 or higher

- OQL module (https://marketplace.mendix.com/link/component/66876) - Build upon the working of the OQL module. 
  - This module is required due to the fact that the stack of parameters for the OQL query is build on-top-of the method of the OQL module. We are seeking into options to make these actions part of the OQL module or extend this module further so the dependency is removed.

## Installation
Download the module and add it to your project.

## Configuration

**1. Constant value**
- Configure the constant to the values that you will use in your project. Set the value in your project configuration and cloud deployment environment.

1. `AddListParameterDefaultMember` - The default member of the list parameter. If you set it to empty when calling the activity, it will fallback to the value of this constant. If this constant is also left blank, the module will use the ID / GUID of the object as the member to include in the `IN`-operator.

**2. Apply in your model **
- Include the activities `Add list parameter` to your microflow to build the stack of parameters like you always do when using the OQL module. Keep in mind that this will only work with the next two activities
- Add `Execute OQL Dataset - Load records` or `Execute OQL Statement - Load records` into your microflow to execute the query, load the records from your OQL.
