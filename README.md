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

3. If you are certain about the decision, change the "send_status_to_home" field to __true__
    - Click on the checkbox until it changes to a checkmark, then it will be true

4. Click on the button labeled as "Save Data Changes"

https://github.com/user-attachments/assets/24781cac-3a3e-4011-84bf-7702286fb327


### Seeing more incoming student information

In order to see more information on an incoming student you must go to the "persons" table in the database. 

## How to make enrolment decisions on outgoing DTU students

### Making an enrolment decision as the home university
1. Go to the table labeled "associations"
2. Each row is an enrolment
3. Under the "state" column you can see the enrolment status from DTU
4. Under the "remote-state" column you can see the enrolment status from the host university

### Seeing more information 

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











