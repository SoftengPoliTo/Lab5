# Unit Testing Documentation template

Authors: Bolla Alessandro   

Date: 08/05/2020

Version: 1.0



# Contents

- [Black Box Unit Tests Ex1](#black-box-unit-tests-ex1)
- [Black Box Unit Tests Ex2](#black-box-unit-tests-ex2)
  

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