---
title: Normal forms
author: Sahil Ahuja
categories: [nitt]
tags:
  - database
date: 2007-06-04 10:47:00
---

Sitting here in Morgan Stanley, it's hard to find free time. Things are always on the run.

But one day, I did find free time, and did what I had wanted to do for a very long time - learn about Normal forms in RDBMS.

Here is what I gathered from these websites :

*   [http://www.serverwatch.com/tutorials/article.php/1549781](http://www.blogger.com/post-create.g?blogID=27948672#%20http://www.serverwatch.com/tutorials/article.php/1549781)
*   [http://en.wikipedia.org/wiki/Database_normalization](http://en.wikipedia.org/wiki/Database_normalization)
*   [http://www.datamodel.org/NormalizationRules.html](http://www.datamodel.org/NormalizationRules.html)
## [1st Normal Form](http://en.wikipedia.org/wiki/First_normal_form):

1. **No multivalued attribute**
    
    |StudID|Course|
    |---|---|
    |12345|3100,3600,3900|
    |54321|1300,2300,3400|
    (Wrong)
    
1. **No repeating group**

    |StudID|Course1|Course2|Course3|
    |---|---|---|---|
    | 12345 | 3100 | 3600 | 3900 |
    |54321 | 1300 | 2300 | 3400 |
    (Wrong)
    
1. **Presence of atleast one unique identifier (addn of ID field)**

    | StudID|Course |
    |---|---|
    |12345 | 3100|
    |12345 | 3600|
    |54321 | 1300|
    |54321 | 2300|
    (Right)
    
There needs to be one composite key atleast. (One or more fields that can be used to distinguish every row uniquely). In the above example, if it was possible for the same student to take the same course twice, then we would have to add another uID field to bring the DB to the first normal form.

## [2nd Normal Form](http://en.wikipedia.org/wiki/Second_normal_form):

The DB is in this if all non-prime attributes are completely dependent on a candidate key. (and not on a part of it).

i.e. no repetition of key detail in one detail

| StudID  CourseID | StudNm  ProfID  ProfName |
|---|---|
|123456 310000 | April00 6789  David|
|123456 410000 | April00 2345  David|
|123456 210000 | April00 6789  David|

Candidate Key = StidID + CourseID

But StudNm (student name) depends only on StudID (and not on StudID + CourseID)
Had prof been just a function of course, even that would have to be removed.
Hence it is not in 2nd NF.
The ProfName-ProfID dependency is removed in the 3rd NF (where no attribute can be dependent on a non-key attribute in that table).
No part key dependencies can exist in 2nd NF.

None of the non-prime attributes of the table are functionally dependent on a part (proper subset) of a candidate key; in other words, all functional dependencies of non-prime attributes on candidate keys are full functional dependencies. For example, in an "Employees' Skills" table whose attributes are Employee ID, Employee Address, and Skill, the combination of Employee ID and Skill uniquely identifies records within the table. Given that Employee Address depends on only one of those attributes – namely, Employee ID – the table is not in 2NF.

*   **Candidate key**: A [candidate key](http://en.wikipedia.org/wiki/Candidate_key "Candidate key") is a minimal superkey, that is, a superkey for which we can say that no proper subset of it is also a superkey. {Employee Id, Skill} would be a candidate key for the "Employees' Skills" table.
*   **uperkey**: A [superkey](http://en.wikipedia.org/wiki/Superkey "Superkey") is an attribute or set of attributes that uniquely identifies rows within a table; in other words, two distinct rows are always guaranteed to have distinct superkeys. {Employee ID, Employee Address, Skill} would be a superkey for the "Employees' Skills" table; {Employee ID, Skill} would also be a superkey.
*   **Non-prime attribute**: A non-prime attribute is an attribute that does not occur in any candidate key. Employee Address would be a non-prime attribute in the "Employees' Skills" table.
*   **Primary key**: Most [DBMSs](http://en.wikipedia.org/wiki/Database_management_system "Database management system") require a table to be defined as having a single unique key, rather than a number of possible unique keys. A [primary key](http://en.wikipedia.org/wiki/Primary_key "Primary key") is a candidate key which the database designer has designated for this purpose.
Some thoughts :

*   In and after 2nd NF, all tables have only one candidate key. -&gt; FALSE
*   All candidate keys in a table map to each other one to one. -&gt; TRUE
*   What normalization stage ensures that only one candidate key is remaining?

    *   None. Beacause [normalization](http://en.wikipedia.org/wiki/Database_normalization) aims at reducing data duplication and inconsistencies. Candidate keys in a table causes no redundency.

*   If a table in 1st NF has no composite candidate keys (candidate keys consisting of more then one attributes), then it is automatically in 2nd NF.

## [3rd Normal Form](http://en.wikipedia.org/wiki/Third_normal_form):

No non-transitive dependencies:
A non-transitive dependency is one in which an attribute is dependent on a non-key attribute in that table.
For example, in the ProfID example given above, to bring it to 3rd normal form, ProfName and ProfID would have to brought to a separate table. Because ProfName is a non-transitive dependency.

*   In 2nd Normal form, all candidate keys become mutually independent. FALSE
*   In 2nd Normal form, any candidate key is a candidate key (i.e. is a sufficient and necessary dependency) for all other attributes. FALSE - this happens in 3rd NF.
*   In 3rd Normal form, non-prime attributes become dependent on a candidate key. TRUE