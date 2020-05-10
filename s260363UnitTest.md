# Unit Testing Documentation template

Authors:

Date:

Version:



# Contents

- [Black Box Unit Tests](#black-box-unit-tests)



- [White Box Unit Tests](#white-box-unit-tests)



# Black Box Unit Tests: Exercise 1

 
**Criteria for method orderIntegers(int v[]):**


- Length of the input vector (number of its integer components) 

- Type of parameter passed to orderIntegers (integers, all other types)




**Predicates for method orderIntegers(int v[]):**

| Criteria                  | Predicate    |
| ------------------------- | ------------ |
| Length of the input vector          | different from 3         |
|                           | =3          |
| Type of parameter passed to orderIntegers         | integers     |
|                           | all other types        |




**Boundaries for method orderIntegers(int v[]):**

| Criteria            | Boundary values             |
| ------------------- | --------------------------- |
| Length of the input vector     | 0, 1, 2, 3, 4, maxsize-1, maxsize|
| Type of parameter passed to orderIntegers | |





 **Combination of predicates for method orderIntegers(int v[])**

| Lenght of input vector | Type of parameter passed to orderIntegers | Valid/Invalid | Description of the test case| JUnit test case     |
| ---------------- | ---------------- | ------------------------- | ------------------- | ------------- |
| Different form 3          | -        | I     |  int v[]=[1,2,3,4];<br /> orderIntegers(v)--> Exception     | com.polito.exercise1.blackboxtests.tc1     | 
| = 3          | integer        | V    |  int v[]=[5,-2,8];<br /> orderIntegers(v) --> [8,5,-2] , 8     | com.polito.exercise1.blackboxtests.tc2     |
|              | all other types        | I  |  double v[]=[1.3,2.3,3.4];<br /> orderIntegers(v) --> Exception     | com.polito.exercise1.blackboxtests.tc3     |  


<br />

# Black Box Unit Tests: Exercise 2

**Criteria for method acceptableToEat:**


- Type of parameters passed to acceptableToEat

- Total amount of calories

- Constraint (carb + protein ) / fat
<br />

<br />

**Predicates for method acceptableToEat:**

| Criteria                  | Predicate    |
| ------------------------- | ------------ |
| Type of parameters for acceptableToEat         | integer          |
|                           | all other types          |
| Signs of input parameters  | all Positive |
|                            |at least one negative|
| Total amount of calories  | <1000      |
|                           | >=1000         |
| Constraint (carb + protein ) / fat| >0.5          |
|                           | <=0.5           |



<br />

**Boundaries for method acceptableToEat**:

| Criteria            | Boundary values             |
| ------------------- | --------------------------- |
| Type of parameters for acceptableToEat    | |
| Signs of input parameters  | 0, -1, 1 |
| Total amount of calories| 0,1, 999,1000,1001, maxint-1, maxint|
| Constraint (carb + protein ) / fat| 0, 0.01, 0.49 0.50, 0.51, maxdouble-0.01, maxdouble|

**REMARK**: i assumed that the precision of last constraint is 0.01, because in the text of exercise 2, there isn't nothing about this fact.

<br />

 **Combination of predicates for method acceptableToEat**

| Type of parameters for acceptableToEat | Signs of input parameters|Total amount of calories | Constraint (carb + protein ) / fat | Valid/Invalid | Description of the test case | JUnit test case |
| ---------------- | ---------------- | ------------------------- | ------------------- | ------------- | ------------------------------------------------------------ |----|
| Integer          |  All positive| <1000         |  >0.5         | V          | acceptableToEat(1,1,1) --> true                                     | com.polito.exercise2.blackboxtests.tc1 |
|      | |       |  <=0.5         | V            | acceptableToEat(1,1,10) --> false | com.polito.exercise2.blackboxtests.tc2 |
|      ||>=1000        |  -       | V            | acceptableToEat(100,100,100) --> false | com.polito.exercise2.blackboxtests.tc3 |
|      |at least one negative|-        |  -       | I            | acceptableToEat(-1,1,1) --> Exception | com.polito.exercise2.blackboxtests.tc4 |
| All other types        |-| -         |  -        | I | acceptableToEat(98.2,34.4,76.3) --> Exception|com.polito.exercise2.blackboxtests.tc5 |


# Black Box Unit Tests: Exercise3

**Criteria for method parallelogram:**


- Type of parameters passed to parallelogram

- Sign of input parameters



<br />

**Predicates for method parallelogram:**

| Criteria                  | Predicate    |
| ------------------------- | ------------ |
| Type of parameters passed to parallelogram         | Integer          |
|                           | all other types          |
| Signs of input parameters          |All positive      |
|                           | at least one negative         |
| (slope of P1P3)= (slope od P2P3) and <br /> (slope of P1P2) = (slope od P3P4)      |yes      |
|                           | no        |
|All four points are different| yes|
|                             | no|

**REMARK**: the points P1, P2, P3, P4 are the same of the exercise 3 picture, so: P1(x1,y1), P2(x2,y2), P3(x3,y3), P1(x4,y4).  <br /> Moreover the slopes above mentioned are defined as follow:  <br />
slope of P1P3=(y3-y1)/(x3-x1) <br />
slope of P2P3=(y3-y2)/(x3-x2) <br />
slope of P1P2=(y2-y1)/(x2-x1) <br />
slope of P3P4=(y4-y3)/(x4-x3) <br />
Finally i have assumed that the square is a particular case of parallelogram.


<br />

**Boundaries for method parallelogram**:

| Criteria            | Boundary values             |
| ------------------- | --------------------------- |
|Type of parameters passed to parallelogram   |           |
| Signs of input parameters  | 0, -1, 1 |
| (slope of P1P3)= (slope od P2P3) and <br /> (slope of P1P2) = (slope od P3P4)      ||


<br />
<br />

 **Combination of predicates for method parallelogram**

| Type of parameters passed to parallelogram  | Signs of input parameters|All four points are different|(slope of P1P3)= (slope od P2P3) and <br /> (slope of P1P2= slope od P3P4)| Valid/Invalid | Description of the test case | JUnit test case |
| ---------------- | ---------------- | ------------------------- | ------------------- | ------------- | -------- |-----|
| Integer          | All positive      |yes|yes|  V             | parallelogram(0,3,1,4,0,0,6,6) --> 18| com.polito.exercise3.<br />blackboxtests.tc1 |
|         |       ||no|  V             | parallelogram(0,3,0,2,0,0,3,2) --> -1| com.polito.exercise3.<br />blackboxtests.tc2 |
|           |       |no|-|  V             |parallelogram(0,3,0,0,0,0,3,0) --> -1| com.polito.exercise3.<br />blackboxtests.tc3 |
|           | at least one negative      |-||V             |parallelogram(0,0,0,-2,0,3,3,2) --> -1 | com.polito.exercise3.<br />blackboxtests.tc4 |
| All other types          | -       |-| |V             | parallelogram(1.2,4.3,5.6,2.4,6.7,2.5,3.6,2.7) --> -1| com.polito.exercise3.<br />blackboxtests.tc5 |

