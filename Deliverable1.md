# Overview

The following work is the collaborative effort of Amit Gandhi, Alexis Kim, Pranali Mane, Han Wang, Xiaoxin Wang and Bo Zhao. We tried to do a detailed study on our topic, Students Awards and Prizes as it had complex rules and information, in order to build a simple, scalable data model. An information system based on these modelling options, would help a University’s Financial Services department handle Student Awards and Prizes system smoothly.
As per the constraints of this assignment, we have limited out total entity classes and relationships to 20, with minimum 5 of each. Following are our recommended classes and relationships and the rationale behind them:

# Entities and classes

### Student
A registered member of the university that takes classes, usually in pursuit of a degree. Students are recipients of awards (awardee).

#### Attributes
* ID: Unique determiner of a student in case of shared names.
* Name: Key in determining how to adress the funds to the awardee. May also be used if award is presented publicly.
* Degree level: a qualification awarded to students upon successful completion of a course of study such as bachelor's, master's and doctorates.
* Sex: female, male, etc. Some awards may be specially given to a specific gender.
* Date of birth: basic information of a student.

### Department
A division of a university that students belong to. It requests for awards for its students to the concerned personnel. The responsibility of the department is to check the guidelines and send the award request to proper officials.

#### Attributes
* Department ID: primary key, this attibute is necessary because the department name may be changed.
* Name: name of the department. For example: Statistics department
* Cardholder name: name of the person who is responsible for card issues
* Card number: bank account number for purchasing gifts and awarding students

### Award
Award is the entity which is awarded to the student based on his achievements. Award class explains the type of the award given, the amount of award and the form in which it was awarded. Considering all these attributes, it is necessary to consider award as a class.

#### Attributes
* Award ID: primary key, for ongoing awards, use ID to distinguish different awards and different years(such as 1002018 to represent award1 in 2018 and 1002017 for award1 in 2017)
* Award name: name of the Award
* Award Value: represents the amount/value of the award

### Guidelines
A reference which defines the amount of cash awards and the level of approval. A department checks the guidelines while requesting awards for its students. Other organizations (Provost office, Admin office and President/Dean/President) are referred to by the guidelines for approval.

#### Attributes
* Category No: guideline category; there are 3 categories of funds.
* Level of approval: to determine who have the right to approve the award, for example: Dean, Provost, President.
* Award amount: amount of the award, for instance: $50, $500, $1000
* Special approval: boolean, in category 3, the value of award which is less than $1000 and greater than $50 is special approved by the respective officials.

### Admin office
High level offices within the University that oversee general action and are responsible for maintaining order in accordance to University policy. The Admin office consists of the Deans, Directors, and other miscellaneous officers. The Admin office also checks completion of forms and documentation.

#### Attributes
* Employee ID: unique determiner of an employee in case of shared names.
* Employee type: refers to the employees specific position which may affect their ability to give clearance to awards of larger amounts. For example, the Dean is part of administration and can approve some awards that the general office cannot.
* Employee name: represents the employees name.
* Special approval: represents what kind of special award the employee could aprrove.

### Financial Services
To store transaction information.

#### Attributes
* Transaction ID: the unique ID of transactions
* Award amount: the approved amount of award

### Provost Office
Provost Office is the office which is responsible for maintaining the list of all the approved awards. This helps to track awards were given to students and the department of the student it was awarded.

#### Attributes
* Employee ID: a unique key representing each record of approved award
* Employee name: represents the employees name.

### PRD(payment request document)
A document that includes payment information of the award

#### Attributes
* Invoice number: the unique number of each transaction's invoice
* Document number: primary key, to identity each payment document
* Source of funds: record the where the funds come from such as unrestriced general funds, self-supporting and restricted gifts

### Application
A form which is needed in the approval processes. For departments who are willing to purchase gifts or pay cash to a student, an application form is needed.

### Attributes
* Description: a description of the program
* Reason: the reson or purpose for the reward
* Criteria: the criteria for selecting the recipients
* Award type: the type of award(plaque, gift, cash, etc.)
* Award limit: the dollar limit or value of the award
* Source of funds: record the where the funds come from such as unrestriced general funds, self-supporting and restricted gifts

# Relationships

### Belongs to
* Scope note: A relationship between Student and Department. Students housed in a department will need to meet individual department criteria for awards. That department's cardholder is the relevant purchaser of awards.
* Domain: Student
* Codomain: Department
* Arity: 2
* Cardinality: M-to-M

### Approves
* Scope note: A relationship between Admin office and Award. For an award to be approved, an administration office needs to process the appropriate documents and make sure that proper criteria are followed. Then approval is given for the award to be distributed.
* Domain: Admin office, Provost
* Codomain: Award
* Arity: 3
* Cardinality: 1-to-M

### Audits
* Scope note: A relationship between Provost Office and Financial Services. The Provost Office will maintain a file of approved awards that Financial Services will use for auditing purposes.
* Domain: Financial Services
* Codomain: Provost Office
* Arity: 2
* Cardinality: 1-to-1

### Processes
* Scope note: A relationship between Financial Services and PRD. The documents of Payment Request Document (PRD) is processed by Financial Services.
* Domain: Financial Services
* Codomain: PRD
* Arity: 2
* Cardinality: 1-to-M

### Refer to:
* Scope note: A relationship between application and guidelines, when students fill out the application form, they should refer to the guidelines to figure out the category of the award
* Domain: Application
* Codomain: Guideline
* Arity:2
* Cardinality:M-to-1


### Guide:
* Scope note: A relationship between guidelines and admin office or provost office, according to the guideline, if the award amount is more than $50 in Category I and Category II, Provost would be responsible for specially approving this award. Also, if greater than 500$ in Category III, Provost would be responsible for approving this award.
* Domain: Guideline
* Codomain: Admin office, Provost office
* Arity:3
* Cardinality:1-to-1


### Submit:
* Scope note: A relationship between department and application, departments need to submit the application form based on guidelines
* Codomain: Application
* Arity:2
* Cardinality:1-to-M


### Submit Details
* Scope note: A relationship between Admin office or Provost and Financial Services. Admin office or Provost office  submit application details to the Financial Services
* Domain: Admin office, Provost office
* Codomain: Financial Services
* Arity: 3
* Cardinality: 1-to-M

### Maintain
* Scope note: A relationship between Provost office and Award. Provost office should maintain a list of approved award.
* Domain: Provost office
* Codomain: Award
* Arity: 2
* Cardinality: 1-to-M

### Award to
* Scope note: A relationship between Student and Award. the award is awarded to the students.
* Domain: Award
* Codomain: Student
* Arity: 2
* Cardinality: M-to-M
