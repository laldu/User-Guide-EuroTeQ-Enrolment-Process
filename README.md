# User Guide for EuroTeQ Enrolment Process
This is a user guide for the EuroTeQ Enrolment Automation System

_Note_: To see the table of contents click on the outline button in the top-right corner

## Login
### Go to Remote Desktop Connection
<img width="1283" height="818" alt="image" src="https://github.com/user-attachments/assets/ff6ac2f4-e9d2-45d2-b88f-ee4a29c93070" />

### Input server name and username and press "Connect" and enter password
<ins>Production server name:</ins> AIT-PWEBEUT02.win.dtu.dk\
<ins>Test server name:</ins> ait-dwebeut01.win.dtu.dk

  _Remember to place "WIN\" before the username_

<img width="1130" height="654" alt="image" src="https://github.com/user-attachments/assets/de1df6c5-99fe-48ab-8317-dc136a6fcb0d" />

### After the remote desktop starts open PGAdmin 4

<img width="864" height="512" alt="image" src="https://github.com/user-attachments/assets/77a837e5-57e2-469b-95c9-921188ec2957" />

## Entering the Enrolment Environment

### To access the host enrolment environment (incoming students)
1. After opening PG admin wait for it to load
2. Click the dropdown button on "Servers" under "Object Explorer"
3. Under databases, click on the database titled: "student_mobility_enrollment_reciever_business"
4. Go under "schemas" and there should be a section labeled "tables"
5. That is where you will be enrolling students

<img width="551" height="574" alt="pgAdminDropdown" src="https://github.com/user-attachments/assets/c870933e-bbde-4582-98c9-779bb83965f9" />

### To access the home enrolment environment (outgoing students)
1. After opening PG admin wait for it to load
2. Click the dropdown button on "Servers" under "Object Explorer"
3. Under databases, click on the database titled: "student_mobility_home_institution"
4. Go under "schemas" and there should be a section labeled "tables"
5. That is where you will be enrolling students

<img width="475" height="512" alt="pgAdmin_openingHomeMiljøDropdown" src="https://github.com/user-attachments/assets/d9f19343-17ea-4174-be38-3e9121b0ec5c" />
  
## How to make enrolment decisions on incoming students

### Making an enrolment decision as the host university

1. Right click on the table labeled as "enrolment_business_decision", click on "View/Edit Data, click on "all rows"
    - Each row within that table is a separate enrolment.
    - The "status" column is where you will change the enrolment decision to one of the [enrolment states](#enrolment-states).
    - When first seeing the table any enrolments that we have not made a decision on should be labeled as "NOT_CONSIDERED".

2. Double-click on the status of the enrolment, type in a new enrolment status, and click "OK"
    - _Remember_: the status can only be input in upper-case
    - If you would like to see more information regarding the student and the enrolment see the following [section](#seeing-more-incoming-student-information).

3. If you are certain about the decision, change the "send_status_to_home" field to _true_
    - Click on the checkbox until it changes to a checkmark, then it will be true

4. Click on the button labeled as "Save Data Changes"


https://github.com/user-attachments/assets/24781cac-3a3e-4011-84bf-7702286fb327



### Seeing more incoming student information

In order to see more information on an incoming student you must go to the "person" table in the database. There you will see each enrolment associated with an ID. Each row is a separate enrolment, you can find the enrolment you are looking for by matching the **id** from the "enrolment-business-decision" table with the **enrolment_business_decision_id** in the "person" table. Within this table you should be able to see the basic information needed in order to make an enrolment decision.

<img width="1426" height="231" alt="image" src="https://github.com/user-attachments/assets/5ef1f7ca-f160-4d15-b3c6-782df570485c" />
<img width="1414" height="189" alt="image" src="https://github.com/user-attachments/assets/4e7645ca-2cee-44d7-aa1b-e0a00be8d38c" />

### Sending emails to incoming students

1. In order to send an email to an incoming student you must mark the **send_status_to_home** field as _true_ in the "enrolment_business_decision" table.
2. Then click on the button labeled as "Save Data Changes"
    - This will automatically send an email updating the student of his enrolment status.
    - If you would like to know more about the automated email system read [here](#Automated-Email).

## How to make enrolment decisions on outgoing DTU students

### Making an enrolment decision as the home university
1. Right click on the table labeled as "associations", click on "View/Edit Data, click on "all rows"
     - Each row is an enrolment
2. Go to the state column and double click on the state
     - The **state** column is the status that DTU sets for their outgoing students
     - The **remote state** column is the status that DTU recieves from the partner university who is hosting their student
3. Type in the enrolment state and click "OK"
     - _Remember_: the state is case sensitive and must be in upper-case
5. Click on the button labeled as "Save Data Changes"


https://github.com/user-attachments/assets/586e675c-e606-4c0d-8d1e-70e3b0ee3e25


### Seeing more information

In order to see more information on an outgoing student you must go to the "user_object" table in the database. There you will see each student has a **uuid**. Each row in the "user_object" table is a separate student, not a separate enrolment. You can find the outgoing student you are looking for by matching the **person_id** from the "associations" table with the **uuid** in the "user_object" table. Within the "user_object" table you should be able to see the basic information needed in order to make an enrolment decision.

<img width="1428" height="305" alt="image" src="https://github.com/user-attachments/assets/452a5caf-8d6b-4ec0-9fa9-8a62656483cc" />
<img width="1419" height="129" alt="image" src="https://github.com/user-attachments/assets/10224fab-dd16-4c0a-a210-03a942d2952d" />



## Appendix

### Enrolment States

1. NOT_CONSIDERED
   - This state means that the application has been recieved and that a DTU admin has not changed its status.
   - While in this state the partner university sees the status as "pending".
2. ASSOCIATED
   - This state means that the enrolment has been accepted.
3. DENIED
   - This means that the enrolment has been denied.
   - Denials may occur automatically via various checks.
4. PENDING
   - This means a decision has not been made on the enrolment
5. CANCELED
   - This means that the student has withdrawn their application
   - This should only occur for incoming students via the cancellation link, which incoming students recieve in the emails from DTU
6. QUEUED
   - This is used when the student has been placed in a waiting list.
   - This status is not in use as of Fall 2025.

### Automated Email

The automated email system is currently under works.









