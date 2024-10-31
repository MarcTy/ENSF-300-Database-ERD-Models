# EER Diagram

## Design Explanation

### Allergy

#### Entity Type
The Allergy is a weak entity type.

#### Relationship and participating entity types
The Allergy entity only interacts with the Student. The Allergy entity itself relies on an identifying relationship. The weak entity type has full participation with the relationship as it cannot exist without Student at least in the context of the database.

#### Attributes
The Allergy entity contains the Allergy name as a partial key and the procedures for the specified allergy (How to deal with the student's allergy).

#### Attribute Derivation
There are no derived attributes.

### Student

#### Entity type
The Student is a regular entity type.

#### Relationship and participating entity types
The entity types participating with Student are Teachers, Emergency Contact and Parent and Allergies.

Teacher has full participation with Student, as a Teacher is only a Teacher if they teach students. Students must be correlated to a Teacher. Students fully participate with teachers as Student must correlate with a Teacher. This relationship is defined with "teaches". Student has full participation with Emergency contact as students must always have an emergency contact when going on school trips and issues arise. Student have full participation with Parent as all students must have a parent whom registers them and provides permission for school trips. A Student may or may not have allergies. Therefore there is partial participation with the Allergy entity and student.

#### Attributes
The attributes for Student are Student Id which is the primary key defining the unique id for each student. Name which is a composite function composed of two attributes, FName and LName, First name and last name respectively. Then DOB or date of birth which is a composite attribute that contains, year, month and date that build the DOB attribute.

#### Attribute Derivation
There are no specific derived attributes in this entity class

### Parent

#### Entity type
The parent is a regular entity type. 

#### Relationship and participating entity types
The entity types participating with Parent are Student and Emergency Contact. 

Parent has partial participation with Emergency Contact as the emergency contact may not be the same as the Parent. This is denoted with 'is_a_contact' relationship to denote if a Parent is an Emergency Contact. Parent also participates in a full relationship with Student as all students must be registered with a parent. This relationship is denoted with require_permission, as students need permission to go on school trips.

#### Attributes
The Parent has attributes: LName for Last Name, Email which is used as a primary key for the Parent, as emails are usually unique, and the Phone number as a multivalued attribute since a Parent can have more than one number to reach them, for example, a work phone and a home phone.

#### Attribute Derivation
There are no derived attributes in the parent class

## EER Diagram
### Diagram: 

![EER Diagram Image](../models.drawio.svg)

### Explanation

Teacher: The teacher is an entity in our database model with 5 attributes and 2 relationships with other entities.
First name(Fname), Last name(Lname), ID, Preferred prefix and Grades they teach are the attributes of Teacher.
It has ID as its primary key attribute and Grades they teach as a Multivalued attribute.
ID is the primary key attribute because every teacher can have the same first name or last name and preferred prefix; but even if they do, in this situation they will all have uniqiue IDs.
It has Grades they teach because each Teacher could have various grades that they could teach.
It also has a subclass called Lead Teacher.
Each Lead Teacher manages several Teachers.
Teachers also have a relationship with students where they teach them.

Emergency Contact: The teacher is an entity in our database model with 3 attrubutes and 2 relationships with others entitites. 
First name(Fname), Last name(Lname) and Phone number are the attributes of Teacher.
It has its Primary key attribute as Phone number because you would need one phone number to call in time of emergencies.
It has a relationship with parent which shows that parents can be the emergency contact and they would be the ones to be contacted when those times arrive.
It also has a relationship with student where every student must have at least one emergency contact.

Lead Teacher: The Lead Teacher is another entity in our database model.
The Lead Teacher is a subclass of the teacher entity in our database model.
The Lead Teacher has all the attributes and relattionships that the Teacher entity posseses.
The Lead Teacher also has the attribute Managed teachers. This is a multivariable attribute that has a list of the Teachers' IDs that they manage. 
The Lead Teacher also has the unique relationship with the Teacher entity where 1 Lead Teacher manages multiple Teachers.
