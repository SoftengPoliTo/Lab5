# Unit Testing, Exercise 1

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

The function int orderIntegers(int v[]) shall take as input an array of three integer numbers. The program
shall output the greatest number among the elements of the array. The program shall order the elements of
the array in decreasing order.


**Criteria:**
	

- Length of array

  

**Predicates:**

| Criteria                  | Predicate    |
| ------------------------- | ------------ |
| Length of array           | <3		   |
|                           | >3           |
|                           |  3           |



**Boundaries:**

| Criteria            | Boundary values             |
| ------------------- | --------------------------- |
|  Length of array    | 0 elements in array |
| Values |all equal values, minint, minint+1, maxint-1, maxint|





 **Combination of predicates:**

|Length of array	|Valid Invalid	|Test cases|
| ------------------- | -------------|-------------- |
|<3|	I	|[1,2] -> error|
|	|	|[]->error|
|>3|	I|	[3,1,15, 6, 5]->error|
|3|	V	|[3,1,2]->3 (array after [1,2,3])|
|	|	|[3, minint, 2]->3 (array after [minint, 2, 3])|
|	|	|[3, minint+1, 2]->3 (array after [minint+1, 2, 3])|
|	|	|[3, maxint-1, 2]->maxint-1 (array after [2, 3,maxint-1])|
|	|	|[3, maxint, 2]-> maxint (array after [2, 3,maxint])|
|	|	|[3,3,3]->3 (array after [3, 3, 3]|




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

