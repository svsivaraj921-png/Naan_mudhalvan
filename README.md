Implement Client Script & UI Policy for Incident Management
Project Overview
The Implement Client Script & UI Policy for Incident Management project is developed using the ServiceNow platform to improve data accuracy, field control, validation, and user interaction within Incident records.

In Incident Management, users may enter incomplete or incorrect information while creating or updating incidents. To reduce these errors, this project uses UI Policies, UI Policy Actions, and Client Scripts to dynamically control fields, automatically update values, validate user inputs, and restrict unwanted changes.

Project Objective
The main objective of this project is to implement client-side controls in the ServiceNow Incident Management module.

The project focuses on:

Improving the accuracy of Incident records.
Dynamically controlling Incident form fields.
Making fields mandatory based on specific conditions.
Automatically updating field values.
Validating user input before submitting an Incident.
Controlling field behavior based on Incident conditions.
Preventing unwanted changes through list editing.
Providing consistent Incident record handling.
Platform Used
Category	Details
Platform	ServiceNow
Module	Incident Management
Environment	ServiceNow Personal Developer Instance (PDI)
Table	Incident [incident]
Configuration	UI Policy, UI Policy Action, Client Script
Browser	Google Chrome / Microsoft Edge
Project Phases
The project was completed through the following eight phases:

Brainstorming & Ideation
Requirement Analysis
Project Design
Project Planning
Project Development
Project Testing
Project Documentation
Project Demonstration
Phase 1 – Brainstorming & Ideation
The project was started by identifying common data-entry and validation issues in ServiceNow Incident Management.

While creating or updating Incident records, users may leave important fields empty, enter inconsistent information, or make changes that should be restricted under certain conditions.

To address these issues, the project uses UI Policies and Client Scripts to provide dynamic control over Incident fields.

The main idea was to create a controlled Incident management process where field behavior changes automatically according to the values entered by the user.

Key Ideas
Dynamic field control.
Conditional mandatory fields.
Automatic field value updates.
Client-side validation.
Controlled Incident state changes.
Improved user experience.
Phase 2 – Requirement Analysis
The functional requirements were identified before starting the development.

Functional Requirements
Create a UI Policy for High Impact Incidents.
Make the Assignment Group field mandatory when Impact is High.
Make the Urgency field read-only when Impact is High.
Automatically set Urgency to High when Impact is High.
Prevent Incident submission when Assigned To is empty for High Impact incidents.
Prevent State changes through direct list editing.
Allow State changes through the Incident form.
Restore normal field behavior when the High Impact condition is no longer satisfied.
Software Requirements
ServiceNow Personal Developer Instance.
Web browser.
Incident Management module.
UI Policy.
UI Policy Action.
Client Scripts.
Phase 3 – Project Design
The project was designed around the Impact field of the Incident table.

The main workflow is:

Incident Form
      ↓
Impact = High
      ↓
UI Policy / Client Script
      ↓
Field Control & Validation
      ↓
Incident Submission
      ↓
Testing & Result Verification
UI Policy Design
A UI Policy is configured for the Incident table.

Condition
Impact is 1 - High
When the condition is satisfied:

Assignment Group becomes mandatory.
Urgency is controlled through the UI Policy Action.
The policy behavior is reversed when the condition becomes false.
Reverse if False
The Reverse if false option is used so that normal field behavior is restored when Impact changes from High to another value.

UI Policy Action
A UI Policy Action is configured for the Urgency field.

When the Incident Impact is High:

Urgency → Read-only
This prevents the user from directly modifying the Urgency field while the High Impact condition is active.

Client Script Design
The project uses Client Scripts to provide additional validation and automation.

1. onChange Client Script
Purpose
Automatically update Urgency when the Impact field changes.

Expected Behavior
When:

Impact = High
the system automatically sets:

Urgency = High
This reduces manual data entry and ensures consistent Incident information.

2. onSubmit Client Script
Purpose
Validate the Incident before it is submitted.

Condition
If:

Impact = High
AND
Assigned To is empty
the Incident submission is prevented.

Expected Result
The user receives a validation message and must provide the required information before submitting the Incident.

3. onCellEdit Client Script
Purpose
Prevent unwanted State changes through direct list editing.

When a user attempts to modify the State field directly from the Incident list:

State List Edit
      ↓
Client Script Validation
      ↓
Change Prevented
The user can still change the State through the Incident form.

Phase 4 – Project Planning
The project was planned as a sequence of configuration, development, and testing activities.

Development Tasks
Configure the Incident table.
Create the High Impact UI Policy.
Configure the UI Policy Action.
Create the onChange Client Script.
Create the onSubmit Client Script.
Create the onCellEdit Client Script.
Test each functionality.
Document the implementation and results.
Testing Plan
The following scenarios were planned:

High Impact field validation.
Automatic Urgency update.
Mandatory Assignment Group behavior.
Missing Assigned To validation.
Reverse UI Policy behavior.
State list-edit restriction.
State update through the Incident form.
Successful Incident submission.
Phase 5 – Project Development
Task 1 – High Impact Control
A UI Policy was created for the Incident table.

UI Policy
Name:

High Impact Control
Condition
Impact is 1 - High
Action
When the condition is true, the Assignment Group field becomes mandatory.

Task 2 – Urgency UI Policy Action
A UI Policy Action was created for the Urgency field.

Configuration
Field: Urgency
Read-only: True
When Impact is High, the Urgency field cannot be directly modified.

Task 3 – Automatically Set Urgency
An onChange Client Script was created for the Impact field.

Function
When the user selects High Impact, the script automatically sets Urgency to High.

Expected Behavior
Impact = High
       ↓
Urgency = High
Task 4 – Prevent Submission Without Assigned To
An onSubmit Client Script was created to validate the Incident before submission.

Validation
IF Impact = High
AND Assigned To is empty
THEN
    Prevent submission
This ensures that important Incident information is completed before the record is saved.

Task 5 – Prevent State Changes Through List Editing
An onCellEdit Client Script was created for the State field.

When a user attempts to modify State directly from the Incident list, the script prevents the change and displays a notification.

State changes can still be performed through the Incident form.

Phase 6 – Project Testing
The implemented functionality was tested using different Incident scenarios.

Test Case 1 – High Impact Validation
Scenario
Create or update an Incident with:

Impact = High
Assigned To = Empty
Expected Result
The system prevents submission and displays the appropriate validation message.

Status
Passed

Test Case 2 – Successful Incident Submission
Scenario
Provide the required Assigned To information and submit the Incident.

Expected Result
The Incident is saved successfully.

Status
Passed

Test Case 3 – Automatic Urgency Update
Scenario
Change Impact to High.

Expected Result
Urgency is automatically set to High.

Status
Passed

Test Case 4 – Reverse Condition
Scenario
Change Impact from High to Medium.

Expected Result
Assignment Group is no longer forced to be mandatory by the policy.
Urgency becomes editable.
Normal Incident behavior is restored.
Status
Passed

Test Case 5 – State List Edit
Scenario
Attempt to directly modify State from the Incident list.

Expected Result
The State change is prevented.

Status
Passed

Test Case 6 – State Form Update
Scenario
Open an Incident through the Incident form and change State.

Expected Result
The State change is allowed and saved successfully.

Status
Passed

Testing Summary
Test Case	Functionality	Result
TC01	High Impact validation	Passed
TC02	Successful Incident submission	Passed
TC03	Automatic Urgency update	Passed
TC04	Reverse UI Policy condition	Passed
TC05	State list-edit restriction	Passed
TC06	State change through form	Passed
Phase 7 – Project Documentation
The complete implementation and testing process was documented.

The documentation includes:

Project overview.
Problem statement.
Project objectives.
Functional requirements.
Project design.
UI Policy configuration.
UI Policy Action configuration.
Client Script implementation.
Testing scenarios.
Testing results.
Screenshots.
Final project outcome.
Phase 8 – Project Demonstration
The project demonstration covers the complete implementation of the ServiceNow Incident Management controls.

Demonstration Flow
Introduction to the project.
Open ServiceNow Incident Management.
Demonstrate the Incident form.
Demonstrate the High Impact UI Policy.
Demonstrate the UI Policy Action.
Demonstrate the onChange Client Script.
Demonstrate the onSubmit Client Script.
Demonstrate the onCellEdit Client Script.
Perform the testing scenarios.
Show the final results.
Project Benefits
The project provides several benefits:

Improves Incident data accuracy.
Reduces incomplete Incident submissions.
Automates repetitive field updates.
Provides dynamic field control.
Validates important information before submission.
Reduces incorrect data entry.
Prevents unwanted list-based State changes.
Maintains consistent Incident handling.
Improves the user experience within Incident Management.
Future Enhancements
The project can be extended with additional ServiceNow capabilities.

Possible Enhancements
Automated Incident assignment based on category.
Automatic priority calculation.
SLA monitoring and notifications.
Email notifications for important Incident updates.
Automated escalation for critical Incidents.
Integration with external monitoring systems.
Dashboard for Incident statistics.
Automated Incident categorization.
AI-assisted Incident classification.
Automated resolution recommendations.
Integration with ServiceNow Flow Designer.
Integration with ServiceNow Business Rules.
Project Structure
Implement-Client-Script-UI-Policy-Incident/
│
├── README.md
│
├── PROJECT REPORT.pdf
│
├── screenshots/
│   ├── incident-form.png
│   ├── ui-policy.png
│   ├── ui-policy-action.png
│   ├── onchange-client-script.png
│   ├── onsubmit-client-script.png
│   ├── oncelledit-client-script.png
│   ├── validation-output.png
│   └── final-output.png
│
└── documentation/
    └── PROJECT_DOCUMENTATION.md
Project Documentation
The complete project report containing the project implementation, testing, screenshots, and results can be added to this repository.

Project Report: PROJECT REPORT.pdf

Project Demonstration Video
The complete project demonstration video can be added below:

Demonstration Video: (https://drive.google.com/file/d/1pWvA9scICC7YBoPaz-YAhvhrQJc7JweU/view?usp=sharing)

Final Output
The project successfully demonstrates the use of ServiceNow UI Policies, UI Policy Actions, and Client Scripts to control Incident records.

The implementation provides:

Dynamic Field Control
        +
Automatic Field Updates
        +
Client-side Validation
        +
List Edit Restriction
        +
Controlled Incident Management
These configurations help improve the consistency and accuracy of Incident records while providing users with controlled and meaningful interactions.

Conclusion
The Implement Client Script & UI Policy for Incident Management project demonstrates how ServiceNow client-side configuration can be used to improve Incident Management.

By combining UI Policies, UI Policy Actions, and Client Scripts, the project provides conditional field control, automatic value updates, validation before submission, and restrictions on unwanted list-based changes.

The project covers the complete development lifecycle from brainstorming and requirement analysis through implementation, testing, documentation, and demonstration.

Technologies Used
ServiceNow
Incident Management
UI Policies
UI Policy Actions
Client Scripts
JavaScript
ServiceNow Personal Developer Instance (PDI)
License
This project is created for educational and demonstration purposes.
