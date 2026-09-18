# AI-Assisted Test Scenario Generation Prompt

## Purpose

This prompt is designed to generate software test scenarios from the
**Hardware Shop POS --- Inventory Management Requirements**.

The prompt is intended for an AI-assisted QA portfolio project.

------------------------------------------------------------------------

## Prompt

You are a Senior Software QA Engineer with experience in functional
testing, requirements analysis, test design, inventory management
systems, and risk-based testing.

Your task is to analyze the provided **Hardware Shop POS Inventory
Management Requirements** and generate comprehensive, clear, and
traceable test scenarios.

### INPUT --- REQUIREMENTS

Use the Inventory Management Requirements provided below:

\[PASTE `hardware_shop_inventory_requirements.md` CONTENT HERE\]

------------------------------------------------------------------------

## OBJECTIVE

Convert each software requirement into appropriate test scenarios that
can later be used to create detailed test cases.

A test scenario should describe **what needs to be tested**, not provide
detailed execution steps.

------------------------------------------------------------------------

## TEST SCENARIO DESIGN INSTRUCTIONS

Analyze each requirement and identify applicable scenarios from the
following areas:

1.  Positive testing
2.  Negative testing
3.  Functional testing
4.  Validation testing
5.  Boundary Value Analysis
6.  Equivalence Partitioning
7.  Error handling
8.  Data integrity
9.  Authorization
10. Security
11. Stock calculation
12. Duplicate data
13. Empty/null input
14. Special-character input
15. Role-based access
16. Transaction consistency
17. Audit trail
18. Search and filtering
19. Reporting
20. Integration-related scenarios where the requirement supports them

Do not force every test type onto every requirement. Select only
scenarios that are relevant to the requirement.

------------------------------------------------------------------------

## IMPORTANT AI RULES

### Rule 1 --- Do Not Invent Requirements

Generate scenarios only from the provided requirements.

Do not introduce functionality that is not specified.

### Rule 2 --- Do Not Assume Missing Business Rules

For example, if the requirement does not specify:

-   Maximum product-name length
-   Minimum stock quantity
-   Maximum stock quantity
-   Password rules
-   Price limits
-   Decimal quantity rules
-   Allowed product-code characters

do not invent values.

Instead, identify the missing information as:

**Requirement Clarification Needed**

### Rule 3 --- Maintain Traceability

Every test scenario must have a valid Requirement ID.

Use the original Requirement IDs exactly as provided, for example:

-   REQ-INV-001
-   REQ-INV-002
-   REQ-INV-015

Do not create new requirement IDs.

### Rule 4 --- Avoid Duplicate Scenarios

Do not create multiple scenarios that test exactly the same behavior.

If two scenarios are similar but test different conditions, clearly
distinguish them.

### Rule 5 --- Cover Positive and Negative Conditions

Where applicable, include:

-   Valid behavior
-   Invalid behavior
-   Missing data
-   Incorrect data
-   Boundary conditions
-   Unauthorized behavior
-   Duplicate data
-   Failure conditions

### Rule 6 --- Consider Real Hardware Shop Usage

Use realistic inventory situations such as:

-   Adding a hammer
-   Receiving electrical cable
-   Selling a box of screws
-   Adjusting physical stock
-   Reaching reorder level
-   Product becoming out of stock
-   Deactivating a discontinued product

Use these examples only to clarify the scenario and do not create new
business rules.

------------------------------------------------------------------------

# OUTPUT FORMAT

Generate the scenarios in the following table:

| Scenario ID \| Requirement ID \| Test Scenario \| Test Type \|
  Priority \| Preconditions \| Requirement Clarification \|

### Scenario ID Format

Use:

TS-INV-001\
TS-INV-002\
TS-INV-003\
...

Continue the numbering sequentially.

### Test Type

Use appropriate values such as:

-   Positive
-   Negative
-   Functional
-   Validation
-   Boundary
-   Security
-   Authorization
-   Data Integrity
-   Error Handling
-   Reporting
-   Search
-   Audit

### Priority

Use:

-   High
-   Medium
-   Low

Assign priority based on the business impact of the requirement.

Do not describe a scenario as high priority merely because it is a
negative test.

------------------------------------------------------------------------

# SCENARIO WRITING RULES

Each scenario should:

-   Begin with an action or behavior to verify.
-   Be specific and testable.
-   Be independent where possible.
-   Clearly relate to one requirement.
-   Avoid detailed test steps.
-   Avoid expected-result details that belong in the test case.
-   Avoid implementation-specific details unless stated in the
    requirement.

### Example

Requirement:

**REQ-INV-015 --- Prevent Negative Stock**

"The system shall prevent the available stock quantity from becoming
negative."

Good scenarios:

-   Verify that stock cannot be reduced below zero.
-   Verify that a stock reduction equal to the available quantity
    results in zero stock.
-   Verify that a stock reduction greater than the available quantity is
    rejected.

Avoid:

-   Verify that the system displays a red error message saying
    "Insufficient Stock."

The exact message is not specified by the requirement.

------------------------------------------------------------------------

# COVERAGE REQUIREMENTS

After generating the scenarios, perform a coverage analysis.

Create a second table:

| Requirement ID \| Requirement Description \| Scenario Count \|
  Coverage Status \|

Use:

-   Covered
-   Partially Covered
-   Not Covered

A requirement is:

### Covered

When one or more appropriate scenarios adequately test the requirement.

### Partially Covered

When scenarios exist but important applicable conditions are missing.

### Not Covered

When no scenario has been created for the requirement.

------------------------------------------------------------------------

# REQUIREMENT CLARIFICATION ANALYSIS

Create a separate table:

| Requirement ID \| Missing Information \| Why It Matters for Testing \|
  Suggested Clarification \|

Only identify clarification points that are supported by the
requirements.

Use the clarification section already provided in the requirements
document.

Do not invent additional business rules.

------------------------------------------------------------------------

# FINAL QA ANALYSIS

After generating all test scenarios, provide:

## 1. Scenario Summary

Report:

-   Total requirements analyzed
-   Total test scenarios generated
-   Positive scenarios
-   Negative scenarios
-   Boundary scenarios
-   Validation scenarios
-   Security scenarios
-   Authorization scenarios
-   Data integrity scenarios

## 2. Requirement Coverage

Report:

-   Covered requirements
-   Partially covered requirements
-   Not covered requirements
-   Requirement coverage percentage

Calculate:

**Requirement Coverage % = (Number of Covered Requirements / Total
Requirements) × 100**

Clearly state how the percentage was calculated.

## 3. Potential Duplicate Scenarios

Identify scenarios that may duplicate other scenarios.

## 4. Missing Test Coverage

Identify requirements that need additional scenarios.

## 5. Requirement Clarifications

List requirements where additional information is required before
reliable test cases can be created.

## 6. QA Review Notes

Identify any scenario where the AI had to avoid making assumptions.

------------------------------------------------------------------------

# TRACEABILITY RULE

The final output must allow the following relationship:

Requirement → Test Scenario

The generated Scenario IDs will later be used to create:

Requirement → Test Scenario → Test Case → Test Data

Do not create test cases or test data in this task.

The purpose of this prompt is **test scenario generation only**.

------------------------------------------------------------------------

# FINAL QUALITY CHECK

Before completing the response, verify:

-   Every original requirement was analyzed.
-   Every generated scenario has a valid Requirement ID.
-   No requirement IDs were invented.
-   No business rules were invented.
-   Missing information is clearly identified.
-   Positive and negative scenarios are included where applicable.
-   Boundary testing is used only where meaningful.
-   Security and authorization scenarios are included where applicable.
-   Duplicate scenarios are minimized.
-   Requirement coverage is reported.
-   Scenario IDs are sequential.
-   The output is suitable for importing into Excel or a QA management
    tool.
