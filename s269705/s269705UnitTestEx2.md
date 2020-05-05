# Unit Testing, Exercise 2

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

The function receives the weight in grams of, respectively, carbohydrates, proteins, fats in a serving of
food. It returns true if
the total amount of calories is < 1000
(carb + protein ) / fat > 1/2
boolean acceptableToEat( int carb, int protein, int fat);
ex. acceptableToEat (100,100,100)  false (tot amount of calories = 100*4 + 100*4 + 100*9 > 1000)
 acceptableToEat (1,1,10)  false ( carb + protein / fat = 2/10)
 acceptableToEat (1,1,1)  true ( carb + protein / fat = 2/1) 

**Criteria:**
	

- Range of carb 

- Range of prot

- Range of fat

- Total calories

- Ratio

  

**Predicates:**

| Criteria                  | Predicate    |
| ------------------------- | ------------ |
|Range of carb	|<0|
|	|>=0|
|Range of prot|	<0|
|	|>=0|
|Range of fat|	<0|
|	|>=0|
|Total calories|	<1000|
|	|>=1000|
|Ratio|	<=0.5|
|	|>0.5|




**Boundaries:**

| Criteria            | Boundary values             |
| ------------------- | --------------------------- |
|Range of carb|minint, minint+1, -1, 0, 1, maxint-1, maxint|
|Range of prot | minint, minint+1, -1, 0, 1, maxint-1, maxint|
|Range of fat|  minint, minint+1, -1, 0, 1, maxint-1, maxint|
|Total calories | 0, 1, maxint-1, maxint|
|Ratio |0, 0.1, 0.4, 0.5, 0.6, maxdouble-0.1, maxdouble|






 **Combination of predicates**

|Range of carb	|Range of prot	|Range of fat	|Total calories	|Ratio|	Valid Invalid	|Test cases|
| --------------|-------------- | --------|----|----|----|------- |
|<0	|-	|-	|-	|-	|I	|(-1, 1,1)->error
|>=0|<0	|-	|-	|-	|I	|(1,-1,1)->error
|	|>=0|<0	|-	|-	|I	|(1,1,-1)->error
|	|	|>=0|>=1000	|-	|V	|(500,500,500)->false
|	|	|	|<1000	|<1/2	|V	|(1,1,5)->false
|	|	|	|	|>1/2	|V	|(1,1,1)->true

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

