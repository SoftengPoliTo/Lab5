# Unit Testing Documentation template

Authors: Bolla Alessandro   

Date: 08/05/2020

Version: 1.0



# Contents

- [Black Box Unit Tests Ex1](#black-box-unit-tests-ex1)
- [Black Box Unit Tests Ex2](#black-box-unit-tests-ex2)
- [Black Box Unit Tests Ex3](#black-box-unit-tests-ex3)
  

# Black Box Unit Tests Ex1

```
<Define here criteria, predicates and the combination of predicates for each function of each class.
Define test cases to cover all equivalence classes and boundary conditions.
In the table, report the description of the black box test case and the correspondence with the JUnit black box test case name/number>
```
The function int orderIntegers(int v[]) shall take as input an array of three integer numbers. The program shall output the greatest number among the elements of the array. The program shall order the elements of the array in decreasing order.

### Class EventsQueue 



**Criteria:**
	
- Length of the array
- Validity of the array

  

**Predicates:**

| Criteria                  | Predicate    |
| ------------------------- | ------------ |
| Length of array           | > 3          |
|                           | <=3          |
|                           | 3            |
| Validity of the array | Y
|| N |




**Boundaries**:

| Criteria            | Boundary values             |
| ------------------- | --------------------------- |
| Length array        | no element                  |
| Values | All equal values |
|| max int, min int|





 **Combination of predicates**

| Length of the array | Vality/Invality | Description of test case |  
| ------------- | -------------- | ------------- |
| < 3 | V | [1,2] -> error |
|  | I | [1,F] -> error |
|  |  | [] -> error |
| > 3 | V | [1,2,3,4] -> error |
|  | I | [1,2,3,F] -> error |
| = 3 | V | [4,2,9] -> 9, array [9,4,2] |
|  |  | [minint,0,maxint] -> maxint, array [maxint,0,minint] |
|  |  | [7,7,7] -> 7, array [7,7,7] |
|  | I | [5,3,I] -> error|

# Black Box Unit Tests Ex2

The function receives the weight in grams of, respectively, carbohydrates, proteins, fats in a serving of food. It returns true if the total amount of calories is < 1000.   
(carb + protein ) / fat > 1/2  

boolean acceptableToEat( int carb, int protein, int fat);   
ex. acceptableToEat (100,100,100) -> false (tot amount of calories = 100*4 + 100*4 + 100*9 > 1000)   
acceptableToEat (1,1,10) -> false ( carb + protein / fat = 2/10)   
acceptableToEat (1,1,1) -> true ( carb + protein / fat = 2/1)

### Class EventsQueue 

**Criteria:**
- Number of elements
- Values of calories
- Validity of elements

**Predicates:**

| Criteria                  | Predicate    |
| ------------------------- | ------------ |
| Number of elements       | <> 3          |
|                           | =3          |
| Values of calories | > 1000 |
|| < 1000 |
| Validiy of elements | Y |
|| N |

**Boundaries**:

| Criteria            | Boundary values             |
| ------------------- | --------------------------- |
| Values of calories        | 1000                  |
|| < 0 |
| Validity of elements | Negative numbers |
|| fat = 0 |
|| null numbers |

 **Combination of predicates**

 | Number of Elements | Calories value | Vality/Invality | Description of test case |  
| ------------- | -------------- | ------------- | ------------------ | 
| <> 3 | > 1000 | I | [100,100,-100,15] -> error |
|  |  | V |  [100,100,100,15] -> error |
|  |  > 0 && <= 1000 | I | [100,100,-10,10] -> error |
||| V | [100,100,10,10] -> error |
| = 3 | > 1000 | I | [100,100,-100] -> error |
||| V | [100,100,100] -> false |
|| > 0 && <= 1000 | I | [10,10,-10] -> error |
||| V | [10,10,10] -> true |
|||| [1,1,10] -> false |

# Black Box Unit Tests Ex3

The function parallelogram(int x1, int x2, int x3, int x4, int y1, int y2, int y3, int y4) calculate the area of a parallelogram.
Requirements are:
- area is always strictly > 0; 
- the parallelogram should stay in the first quadrant of the Cartesian plan; 
- coordinates must have the following meaning:  

In case of error or invalid input, -1 is returned.

### Class EventsQueue 

**Criteria:**
- Number of coordinates
- Validity of elements
- Sign of points
- Value of points

**Predicates:**

| Criteria                  | Predicate    |
| ------------------------- | ------------ |
| Number of coordinates       | <> 8          |
|                           | = 8       |
| Validity of elements | Y |
|| N |
| Sign of points | " + " |
| Value of points | y1 = y2, y3 = y4 ==> x1 < x2, x3 < x4 |
|| x1 = x2, x3 = x4 ==> y1 < y2, y3 < y4 |

**Boundaries**:

| Criteria            | Boundary values             |
| ------------------- | --------------------------- |
| Number of coordinates | 0                  |
| Sign of points | 0 |
| | " - " |
| Incremental value | x1 = x2, x3 = x4 |
|| y1 = y2, y3 = y4 |
| Value of points | if y1 = y2 && y3 = y4 ==> x1 = x3, x2 = x4 |
|| if x1 = x3 && x2 = x4 ==> y1 = y2, y3 = y4|


 **Combination of predicates**

 | Number of Elements | Sign of points | Vality/Invality | Description of test case |  
| ------------- | -------------- | ------------- | ------------------ | 
| <> 8 | - | I | [1,5,3,8,-1,-1,A,A,A] -> -1 |
|  |  | V | [1,5,3,8,1,1,5,5,9,9] -> -1 |
|| + | I | [1,5,3,8,1,1,5,5,!,?] -> -1 |
||| V | [1,5,3,8,1,1,5,5,3,3] -> -1 |
| = 8 | - | I | [1,5,3,8,-1,-1,T,Z] -> -1 |
||| V | [1,5,3,8,1,1,-5,-5] -> -1 |
|| + | I | [1,5,3,8,%,%,5,5] -> -1 |
||| V | [1,5,3,7,1,1,5,5] -> 16 |
|||| [1,5,3,8,1,10,5,5] -> -1|
|||| [1,1,3,8,1,1,5,5] -> -1 |
|||| [6,5,3,7,1,1,5,5] -> -1 |
||||[1,5,1,5,1,1,5,5] -> -1 |

# Black Box Unit Tests Ex4

A retail support system manages an inventory of items. Each item has a descriptor and the number of available items.

### Class EventsQueue 

**Criteria:**
- Unique identity code
- Availability item
- Existance of an item
- Valid item

**Predicates:**

| Criteria                  | Predicate    |
| ------------------------- | ------------ |
| Unique identity code | Unique |
| | Not unique or null |
| Existance of an item | Exist |
|| Not exist |
| Availability item | > 0 |
|| = 0 |
|| < 0 |
| Valid item | Y |
|| N |
**Boundaries**:

| Criteria            | Boundary values             |
| ------------------- | --------------------------- |
| Availability Item | < 0 |
|| 0 |


 **Combination of predicates**

 | Unique identity code | Existance | Validity | Description of test case |  
| ------------- | -------------- | ------------- | ------------------ | 
| Not unique | Not exist | N | addItem(i) -> notAvailable |
|  |  | Y | addiItem(i) -> notAvailable |
|| Exist | Y | addiItem(i) -> notAvailable |
||| N | addiItem(i) -> notAvailable |
| Unique | Notexist | N | addiItem(i) -> notAvailable |
|| Exist | Y | addiItem(i) -> notAvailable |
|| Not exist | Y | addiItem(i) -> Ok | 