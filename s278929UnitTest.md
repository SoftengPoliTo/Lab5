# Unit Testing Documentation template

Authors: Giacomo Brusamolin

Date: 05/05/2020

Version: 1



# Contents

- [Unit Testing Documentation template](#unit-testing-documentation-template)
- [Contents](#contents)
- [Black Box Unit Tests](#black-box-unit-tests)
  - [Ex 1 order integers](#ex-1-order-integers)
  - [Ex 2 calories](#ex-2-calories)
  - [Ex 3 parallelogram](#ex-3-parallelogram)
  - [Ex 4 inventory](#ex-4-inventory)
- [White Box Unit Tests](#white-box-unit-tests)
    - [Test cases definition](#test-cases-definition)
    - [Code coverage report](#code-coverage-report)
    - [Loop coverage analysis](#loop-coverage-analysis)

- [White Box Unit Tests](#white-box-unit-tests)

  

# Black Box Unit Tests

## Ex 1 order integers


**Criteria**

- Validity of the array
- Number of elements in the array


**Predicates**

| Criteria                  | Predicate    |
| ------------------------- | ------------ |
| Validity of the array     | Yes          |
|                           | No           |
| Number of elements in the array | 3      |
|                           | <=2 and >=4  |


**Boundaries**:

| Criteria            | Boundary values             |
| ------------------- | --------------------------- |
| Number of elements in the array | 0, 1, 2, 3, 4   |


 **Combination of predicates**

| Validity of the array | Number of elements in the array | Valid/Invalid | Description of the test case |
| -- | -- | -- | -- | -- |
| Yes    | 3   | V    | T1(orderIntegers([1,2,3])) -> [3,2,1] -> 3 |
|        | <=2 and >=4 | I    | T2(orderIntegers([1,2])) -> error |
| No     | -   | I    | T3(orderIntegers(NULL)) -> error |


## Ex 2 calories


**Criteria**

- Number of parameter
- Total amount of calories
- Calories ratio


**Predicates**

| Criteria                  | Predicate    |
| ------------------------- | ------------ |
| Number of parameter       | 3            |
|                           | <=2 and >=4  |
| Total amount of calories  | <1000 and >0 |
|                           | >=1000       |
|                           | <=0          |
| Calories ratio            | (carb + protein ) / fat > 1/2 |
|                           | (carb + protein ) / fat <= 1/2 |


**Boundaries**:

| Criteria            | Boundary values             |
| ------------------- | --------------------------- |
| Total amount of calories | 0, 1, 999, 1000, 1001  |
| Calories ratio      | 0.499, 0.5, 0.501 |


 **Combination of predicates**

| Number of parameter  | Total amount of calories | Calories ratio | Valid/Invalid | Description of the test case |
| -- | -- | -- | -- | -- | -- |
| 3    | <1000 and >0   | (carb + protein ) / fat > 1/2 | V    | T1(acceptableToEat(300, 200, 200)) -> TRUE |
|      | <1000 and >0   | (carb + protein ) / fat <= 1/2 | I    | T2(acceptableToEat(100, 100, 500)) -> FALSE |
|      | >=1000   | - | I    | T3(acceptableToEat(300, 400, 500)) -> FALSE |
|      | <=0   | - | I    | T4(acceptableToEat(0, 0, 0)) -> FALSE |
| <=2 and >=4     | -  | - | I    | T5(acceptableToEat(200, 300)) -> FALSE |


## Ex 3 parallelogram


**Criteria**

- Number of parameter
- Sign of coordinates
- Lengh of the bases
- Lengh of the sides


**Predicates**

| Criteria                  | Predicate    |
| ------------------------- | ------------ |
| Number of parameter       | 8            |
|                           | <=7 and >=9  |
| Sign of coordinates       | All positive >=0 |
|                           | All negative <0 |
|                           | Mixed        |
| Lengh of the bases | sqrt[ (x2-x1)^2 + (y2-y1)^2 ] = sqrt[ (x4-x3)^2 + (y4-y3)^2 ] != 0 |
|                    | sqrt[ (x2-x1)^2 + (y2-y1)^2 ] != sqrt[ (x4-x3)^2 + (y4-y3)^2 ] |
|                    | sqrt[ (x2-x1)^2 + (y2-y1)^2 ] = 0 or sqrt[ (x4-x3)^2 + (y4-y3)^2 ] = 0 |
| Lengh of the sides | sqrt[ (x3-x1)^2 + (y3-y1)^2 ] = sqrt[ (x4-x2)^2 + (y4-y2)^2 ] != 0 |
|                    | sqrt[ (x3-x1)^2 + (y3-y1)^2 ] != sqrt[ (x4-x2)^2 + (y4-y2)^2 ] |
|                    | sqrt[ (x3-x1)^2 + (y3-y1)^2 ] = 0 or sqrt[ (x4-x2)^2 + (y4-y2)^2 ] = 0 |


**Boundaries**:

| Criteria            | Boundary values             |
| ------------------- | --------------------------- |
| Sign of coordinates | -0.001, 0, 0.001  |
| Lengh of the bases  | 0, 0.001 |
| Lengh of the sides  | 0, 0.001 |


 **Combination of predicates**

| Number of parameter | Sign of coordinates | Lengh of the bases | Lengh of the sides | Valid/Invalid | Description of the test case |
| -- | -- | -- | -- | -- | -- | -- |
| 8    | All positive >=0 | sqrt[ (x2-x1)^2 + (y2-y1)^2 ] = sqrt[ (x4-x3)^2 + (y4-y3)^2 ] != 0 | sqrt[ (x3-x1)^2 + (y3-y1)^2 ] = sqrt[ (x4-x2)^2 + (y4-y2)^2 ] != 0 | V    | T1(parallelogram(1, 3, 2, 4, 0, 0, 1, 1)) -> 2 |
| 8    | All positive >=0 | sqrt[ (x2-x1)^2 + (y2-y1)^2 ] = sqrt[ (x4-x3)^2 + (y4-y3)^2 ] != 0 | sqrt[ (x3-x1)^2 + (y3-y1)^2 ] != sqrt[ (x4-x2)^2 + (y4-y2)^2 ] | V    | T2(parallelogram(1, 3, 2, 4, 0, 0, 1, 0.5)) -> -1 |
| 8    | All positive >=0 | sqrt[ (x2-x1)^2 + (y2-y1)^2 ] = sqrt[ (x4-x3)^2 + (y4-y3)^2 ] != 0 | sqrt[ (x3-x1)^2 + (y3-y1)^2 ] = 0 or sqrt[ (x4-x2)^2 + (y4-y2)^2 ] = 0 | V    | T3(parallelogram(1, 3, 2, 4, 0, 0, 1, 0)) -> -1 |
| 8    | All positive >=0 | sqrt[ (x2-x1)^2 + (y2-y1)^2 ] != sqrt[ (x4-x3)^2 + (y4-y3)^2 ] | - | V    | T4(parallelogram(1, 3, 2, 5, 0, 0, 1, 1)) -> -1 |
| 8    | All positive >=0 | sqrt[ (x2-x1)^2 + (y2-y1)^2 ] = 0 or sqrt[ (x4-x3)^2 + (y4-y3)^2 ] = 0 | - | V    | T5(parallelogram(1, 1, 2, 4, 0, 0, 1, 1)) -> -1 |
| 8    | All negative <0 | - | - | V    | T6(parallelogram(-1, -1, -2, -4, -1, -3, -2, -1)) -> -1 |
| 8    | Mixed | - | - | V    | T7(parallelogram(1, -1, 2, 4, 1, 3, 2, 1)) -> -1 |
| 7    | - | - | - | V    | T7(parallelogram(1, 1, 2, 4, 1, 3, 2)) -> -1 |


## Ex 4 inventory


**Criteria**

- Unique itemCode
- Availability number


**Predicates**

| Criteria                  | Predicate    |
| ------------------------- | ------------ |
| Unique itemCode           | unique and not NULL |
|                           | non unique or NULL  |
| Availability number       | >0 |
|                           | 0  |
|                           | <0  |


**Boundaries**:

| Criteria            | Boundary values             |
| ------------------- | --------------------------- |
| Availability number | -1, 0, 1  |


 **Combination of predicates**

| Unique itemCode  | Availability number | Valid/Invalid | Description of the test case |
| -- | -- | -- | -- | -- |
| unique and not NULL | >0 | V    | T1(addItem(i)) -> OK |
| unique and not NULL | 0  | V    | T2(subtractItem(i)) -> ItemNotAvailable |
| unique and not NULL | <0  | I    | T2 |
| non unique or NULL  | >=0 | I    | T3(availabilityItem(i)) -> ItemNotExists |
| non unique or NULL  | 0  | I    | T3 |
| non unique or NULL  | <0 | I    | T3 |


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
