# Unit Testing, Exercise 4

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

```
<Define here criteria, predicates and the combination of predicates for each function of each class.
Define test cases to cover all equivalence classes and boundary conditions.
In the table, report the description of the black box test case and the correspondence with the JUnit black box test case name/number>
```

**Criteria:**
	

- Sign of timeTag

- Type of timeTag

- There are equal time tags

- Number of time tags

  

**Predicates:**

| Criteria                  | Predicate    |
| ------------------------- | ------------ |
| Sign of time tag          | > 0          |
|                           | <=0          |
| Type of time tag          | Integer      |
|                           | Char         |
|                           | String       |
|                           | Float        |
| There are equal time tags | Yes          |
|                           | No           |
| Number of time tags       | 0 to 100.000 |
|                           | > 100.000    |



**Boundaries:**

| Criteria            | Boundary values             |
| ------------------- | --------------------------- |
| Sign of time tag    | Minint, 0, maxint           |
| Number of time tags | 0, 1, 99999, 100000, 100001 |





 **Combination of predicates:**


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

