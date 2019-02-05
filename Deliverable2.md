This document is a joint effort of all members of the group. We have tried to recall and put in all the discussions, arguments, contributions that occured during the course of the assignment.

# Group Rationale

Some of the changes that took place from our first to final understanding of the assignment are as follows:
#### Initial understanding of the classes:
![Initial classes](https://github.com/IS561/StudentAwards/blob/master/im1.jpg)

#### Final understanding (upon consulting the TA):
![Final Classes](https://github.com/IS561/StudentAwards/blob/master/im2.jpg)

We identified that although the offices considered in this scenario have similar attributes (they perform some function, are answerable to some other offices), their work is different from each other and they can be broken down into individual entities. Hence, in our final understanding all offices are counted as separate classes.
We can add in more classes to make the information system full-proof, but due to the constraints of this assignment, we have limited entities and relationships to 20.

Some of the questions we faced were:
#### Is the student to award relationship 1-to-1 or 1-to-M?
While finding out the cardinality between classes, the relationship between student and award led to long controversies. Half of the group was of the notion that the relationship should be many to many, i.e. many students can receive multiple awards during a given year and while the other half felt it should be one to one, as the resources or funds available are limited to give out multiple award to same individual. But we went back to the guidelines and policies, where there wasn’t a mention related to the funds or that how the award should be given out. Also, it is possible that one student achieved or performed exceptionally at multiple things and deserves multiple awards related to his work. Further, there may be a possibility that a group of students performed well at a single activity and all should get the same award and not just a single person. Thus, it led us to conclude that the award to student follows a many to many relationship.

#### Should guidelines be a separate class?
When we read through the guidelines which give information about how certain funds and awards should be dealt with, we were unsure as to whether we can include that as a class or not. Amit and Han talked to the TA regarding the same and got it clarified, so we decided to go with guidelines as a separate class. We identified that there are 3 categories into which the awards can be divided, each going through an approval either from the Dean, the President or the Provost. Hence the attributes we decided to go forward with are: Category No, Level of approval, Award amount and Special approval (binary).

#### What attributes should be included in different offices and what does individuals and arity mean?
As we discussed about, the responsibility of different offices (Admin office, President and Provost) is according to the guidelines, different type of awards should be approved by different offices accordingly. Since each class should contain at least 2 attributes, we wondered about what attributes should be included. There are 2 employee types (Director and Dean) in admin office, so we add the employee type for admin office class. Apart from this, Pranali brought up the thought that imagine we should build a database for this scenario, we should make every class have its unique key, so we add the employee ID for these offices and add name for further convenience.

#### What is domain and codomain?
From the instruction of this assignment, we are asked to describe the arity, cardinality, domain and codomain of each relationship. After going through all the reading materials, however, we still could not find the exact explanations of these terms. We went to online office hours but even the TA said she had no idea about these concepts. On Friday, Han and Amit went to ask TAs face to face. It was surprised that two TAs gave us different answers. One said that domain is like a subject in a sentence and codomain is the object, thus here the relationship is like the verb. On the other hand, another TA said codomain is a part of domain. At first, we could not decide which one was correct here. But after a long discussion, we began to think that both of them may be correct. It depends on the what we are actually talking about, like in relationships and in classes they could have different definitions. Since the instruction asked us to discuss the domain and codomain in a relationship, we finally decided to use the explanation given by the first TA.

What’s more, we talked about what’s the difference between individuals and entity classes. We figured out that individuals are like different rows in a database. For example, for entity class “student”, the according individuals are studentA, studentB and so on.

When we try to finish our own part, we are not sure about what arity means, Han gave us the screenshot of Professor Dubin’s example and make us understand that arity is exactly that how many things participate in an instance of relationship.

### Conclusion
When we started this project as a group, we were unsure. Unsure who we were working with, unsure of our end-point and even unsure of some of the instructions. However, over the past week on this first section, we have worked together both in person and online for approximately over ten hours. During this time, we have found our roles in the group and are now working together more cohesively. Pranali is good at leading charge when decisions need to be made; Han steps in to gather or explain information whenever needed; Bo is alert and genial to other teammates communications; Amit has extra tech savvy to share; Alexis coordinates team meeting and efforts; Xiaoxin makes sure new information is clarified. We have found that it's not always easy to step in a argue a point with a teammate-- and for some it's easier to assert themselves. But we are trying to stay conscious of when a teammate has been quiet and may have an unanswered question they feel uncomfortable asking or when it is time to concede a point. Although 
