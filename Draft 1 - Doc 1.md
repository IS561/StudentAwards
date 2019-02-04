# Overview

The following work is the collaborative effort of Amit Gandhi, Alexis Kim, Pranali Mane, Han Wang, Xiaoxin Wang and Bo Zhao. We tried to do a detailed study on our topic, Students Awards and Prizes as it had complex rules and information, in order to build a simple, scalable data model. An information system based on these modelling options, would help a University’s Financial Services department handle Student Awards and Prizes system smoothly.
As per the constraints of this assignment, we have limited out total entity classes and relationships to 20, with minimum 5 of each. Following are our recommended classes and relationships and the rationale behind them:

# Entities and classes

### Student
A registered member of the university that takes classes, usually in pursuit of a degree. Students are recipients of awards (awardee).

#### Student Attributes
* ID: Unique determiner of a student in case of shared names.
* Name: Key in determining how to adress the funds to the awardee. May also be used if award is presented publicly.
* Department: Responsible for maintaining records for students housed under its field. Cardholder in department is responsible for awarding to students.

### Department
A division of a university that students belong to. It requests for awards for its students to the concerned personnel. The responsibility of the department is to check the guidelines and send the award request to proper officials.

#### Department attributes
* Name: name of the department. For example: Statistics department
* Number of Award: No of awards received by the department’s students

### Award
Award is the entity which is awarded to the student based on his achievements. Award class explains the type of the award given, the amount of award and the form in which it was awarded. Considering all these attributes, it is necessary to consider award as a class.

#### Attributes
* Award: Name of the Award 
* Student ID: represents the ID of the Student who got the award
* Award Value: Represents the amount/value of the award
* Approved By: Represents who approved the Award (Dean, Provost, President)
* Department:  Represents the Department to which the student belongs

### Guidelines
A reference which defines the amount of cash awards and the level of approval. A department checks the guidelines while requesting awards for its students. Other organizations (Provost office, Admin office and President/Dean/President) are referred to by the guidelines for approval.

#### Guideline attributes
* Category No: guideline category; there are 3 categories of funds.
* Level of approval: to determine who have the right to approve the award, for example: Dean, Provost, President.
* Award amount: Amount of the award, for instance: $50, $500, $1000
* Special approval: Boolean, in category 3, the value of award which is less than $1000 and greater than $50 is special approved by the respective officials.

### Admin office
High level offices within the University that oversee general action and are responsible for maintaining order in accordance to University policy. The Admin office consists of the Deans, Directors, and other miscellaneous officers. The Admin office also checks completion of forms and documentation.

#### Admin office Attributes
* Employee type: Refers to the employees specific position which may affect their ability to give clearance to awards of larger amounts. For example, the Dean is part of administration and can approve some awards that the general office cannot.
* Name: Represents the employees name.
* Employee ID: Unique determiner of an employee in case of shared names.

### Student Financial Aid Office
Student financial aid is an office that has necessary employees who have 2 main responsibilities: processing student forms to review all the payments and adjusting student financial aid records according to the award and prize they received. 

#### Attributes
* Student ID: represents a unique identifier for a student who received/will receive the award
* Financial aid amount: represents the amount of award the student received

### President
President is a position of importance, with 1 President in power at a time. He/She is responsible for specially approving awards that are exceed $50 as per the award guidelines.

#### Attributes
* President ID: a unique key for each President in case that some of them may have the same names
* Name: represents individual President’s name

### Accounts Payable Services Office/University Financial Services
An office that is responsible for some approval processes. Applications of awards need to be reviewed here. The issuance of Student Payment Procurement Cards is approved by this office. Besides, it processes payments and sends copies of them to the Office of Student Financial Aid. For purposes of this scenario, University Financial Services and Accounts Payable Services Office have similar work, hence we have considered them as 1 class.

#### Attributes of Accounts Payable Services Office
* Transaction Number: the unique ID of transactions
* Account Number: the unique ID of accounts
* Student ID: the student that the award is given to
* Amount Payable: the approved amount of award

### Provost Office
Provost Office is the office which is responsible for maintaining the list of all the approved awards. This helps to track awards were given to students and the department of the student it was awarded.

#### Attributes
* ID: A unique key representing each record of approved award
* Student ID: ID, representing the student who was given the award
* Department: represents the department the student belonged to
* Approved Award Amount: Represents the amount of the given award

### Documents
Documents is a class represents the documentation which is needed in the approval processes. For departments who are willing to purchase gifts or pay cash to a student, a payment request document is needed. For each transaction, a document that contains information about awards or purchase is needed.

#### Attributes of a Document
* Document Type: what kind of document it is
* Processed By: the office that processed this document
* Issued By: the office that issued this document

# Relationships

### Belongs to
* Scope note: A relationship between Student and Department. Students housed in a department will need to meet individual department criteria for awards. That department's cardholder is the relevant purchaser of awards.
* Domain: Student
* Codomain: Department
* Arity: 2
* Cardinality: 1-to-M

### Approves
* Scope note: a relationship between Admin office and Award. For an award to be approved, an administration office needs to process the appropriate documents and make sure that proper criteria are followed. Then approval is given for the award to be distributed.
* Domain: Admin office
* Codomain: Award
* Arity: 2
* Cardinality: 1-to-M

### Approves
* Scope note: : A relationship between President and Guidelines, which represents a special approval case which allows the President to approve award amounts more than $50.
* Domain: President
* Codomain: Award
* Arity:2
* Cardinality: M-to-1

### Approves: 
* Scope note: a relationship between Provost Office and Award. Provost is the one who approves the award when the Award lies in the Category III (Restricted Gifts) and when the award amount is greater than 500$.Also, he is responsible for preapproval of the award lying in the Category I and Category II of the Guidelines when the award price is greater than 50$.
* Domain: Provost Office
* Codomain: Award
* Arity:2
* Cardinality: 1-to-M
It has a one-to-many relationship(process) with the award codomain. This means the Provost office can approve multiple awards lying in different categories at a time.

### Audits
* Scope note: A relationship between Provost Office and University Financial Services/Accounts Payable Services Office. The Provost Office will maintain a file of approved awards that Accounts Payable Services will use for auditing purposes.
* Domain: Provost Office
* Codomain: Accounts Payable Services Office
* Arity: 2
* Cardinality: 1-to-1

### Processes
* Scope note: A relationship between Accounts Payable Services Office and Documents. The documents of Payment Request Document (PRD) is processed by Accounts Payable Services Office.
* Domain: Accounts Payable Services Office
* Codomain: Documents
* Arity: 2
* Cardinality: 1-to-1

### Processes
* Scope note: A relationship between Office of Student Financial Aid and Documents. All documents of transactions need to be reviewed by Office of Student Financial Aid.
* Domain: Office of Student Financial Aid
* Codomain: Documents
* Arity: 2
* Cardinality: 1-to-1

### Processes
* Scope note: a relationship between student financial aid office and document. Student financial aid office should process student document about award application to review the payments made to ensure proper handling of the same.
* Domain: Student financial aid
* Codomain: Document
* Arity:2
* Cardinality: 1-to-1
Student Financial Aid office has a one-to-one relationship with the Document class as each student will have a separate payment transaction details and hence documentation that will be needed to be processed individually.  

### Refer to:
* Scope note: a relationship between Provost and guidelines, which represents according to the guideline, if the award amount is more than $50 in Category I and Category II, Provost would be responsible for specially approving this award. Also, if greater than 500$ in Category III, Provost would be responsible for approving this award. 
* Domain: Guideline
* Codomain: Provost Office
* Arity:2
* Cardinality: 1-to-1
Based on the guideline, one award is referred to the Provost at a time. That is, an award of Category I will be forwarded to Provost one at a time depending on whether it is greater than 50$.

### Refer to
* Scope note: A relationship between President and Guidelines, which represents that the President can give a special approval for an award to be more than a certain amount in the guidelines.
* Domain: Guideline
* Codomain: President
* Arity:2
* Cardinality: 1-to-1

### Refer to
* Scope note: A relationship between Guidelines and Admin office. These offices refer to the guidelines to determine the guideline category, the amount of award and who oversees approval. 
* Domain: Guideline
* Codomain: Admin office
* Arity: 2
* Cardinality: 1-to-1

### Checks
* Scope note: A relationship between Department and Guideline. Department checks the guidelines and sent the award request to appropriate officials.
* Domain: Department
* Codomain: Guideline
* Arity: 2 
* Cardinality: 1-to-M
