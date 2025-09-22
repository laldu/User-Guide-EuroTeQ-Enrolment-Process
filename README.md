# User Guide EuroTeQ Enrolment Process
This is a user guide for the EuroTeQ Enrolment Automation System

-- Table of contents --

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

## How to make enrolment decisions on outgoing DTU students









