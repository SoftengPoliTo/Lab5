# Unit Testing, Exercise 3

Authors:

Andrea Bruno, s269705

Date:

05/05/2020

Version:

1.0 (Black box)


# Contents

- [Black Box Unit Tests](#black-box-unit-tests)



- [White Box Unit Tests](#white-box-unit-tests)

  

# Black Box Unit Tests

The function parallelogram(int x1, int x2, int x3, int x4, int y1, int y2, int y3, int y4) calculate the area of a
parallelogram.
Requirements are:
- area is always strictly > 0;
- the parallelogram should stay in the first quadrant of the Cartesian plan;
- coordinates must have the following meaning:
In case of error or invalid input, -1 is returned.


**Criteria:**
	

- Sign of input
- Parallelogram validity
- Area of parallelogram

  

**Predicates:**

| Criteria                  | Predicate    |
| ------------------------- | ------------ |
| Sign of input             | >= 0         |
|                           | <0           |
|Parallelogram validity| Yes (x1<=x2,x3<=x4, x3-x1=x4-x2, y3-y1=y4-y2 )|
||No|
| Area of parallelogram     | >0 (x1!=x2 && y1!=y3)      |
||=0|



**Boundaries:**

| Criteria            | Boundary values             |
| ------------------- | --------------------------- |
| Sign of input       | minint, minint-1, -1, 0, 1, maxint-1, maxint      |



 **Combination of predicates:**
 //correct(1,2,1,2,1,1,2,2)->-1
| Sign of input             |Parallelogram validity| Area of parallelogram     | Valid/Invalid|Description of the test case|
|--|--|--|--|--|
|<0|-|-|I (all negative)|(-1,-1,-1,-1,-1,-1,-1,-1)->-1|
||||I (only one point negative)|(1,2,1,-1,1,1,2,-1)->-1|
|>=0|No|-|I (x1>x2)|(2,1,1,2,1,1,2,2)->-1|
||||I (x3>x4)|(1,2,2,1,1,1,2,2)->-1|
||||I (x3-x1!=x4-x2)|(1,2,1,3,1,1,2,2)->-1|
||||I (y3-y1=y4-y2)|(1,2,1,2,1,1,2,3)->-1|
||Yes|=0|I (x1=x2)|(1,1,1,1,1,1,2,2)->-1|
||||I (y1=y3)|(1,2,1,2,1,1,1,1)->-1|
|||>0|V|(1,3,1,3,1,1,3,3)->4|
|||>0|V(edges not parallel to the axes)|(1,3,2,4,1,2,3,4)->4|
||||V (many values at 0, but still valid)|(0,3,0,3,0,0,3,3)->9|


# White Box Unit Tests

### Test cases definition

```
<Report here all the created JUnit test cases, and the units/classes they test >
```

| Unit name | JUnit test case                              |
| --------- | -------------------------------------------- |
| Converter | com.polito.converter.<br />whiteboxtests.tc1 |
| Converter | com.polito.converter.<br />blackboxtests.tc2 |
|           |                                              |

### Code coverage report

```
<Add here the screenshot report of the code and branch coverage obtained using
the Jacoco tool. >
```

### Loop coverage analysis

```
<Identify significant loops in the units and reports the test cases
developed to cover zero, one or multiple iterations >
```

| Unit name | Loop rows | Number of iterations | JUnit test case                              |
| --------- | --------- | -------------------- | -------------------------------------------- |
| Converter | 7-11      | 0                    | com.polito.converter.<br />whiteboxtests.tc1 |
|           |           | 1                    | com.polito.converter.<br />whiteboxtests.tc2 |
|           |           | 2+                   | com.polito.converter.<br />whiteboxtests.tc4 |
| ...       | ...       | ...                  | ...                                          |

