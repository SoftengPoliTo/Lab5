# Unit Testing Documentation template

Author: Fabio Bertone

Date: 2020-05-05

Version: 1



# Contents

- [Black Box Unit Tests](#black-box-unit-tests)

	+ [Order Integers](#order-integers)
	+ [Calories](#calories)
	+ [Parallelogram](#parallelogram)
	+ [Inventory](#inventory)

 

# Black Box Unit Tests


## Order Integers


**Criteria for function Order Integers:**
	
- Length of the array

- Signs of array elements

- Null/not null pointer
  

**Predicates for function Order Integers:**

| Criteria                  | Predicate      |
| ------------------------- | ---------------|
| Length of the array       | ==1            | 
|                           | > 1            |
| Type of data              | Integers > 0   |
|                           | Integers < 0   |
|                           | Both < and > 0 |
| Null pointer              | Yes            |
|                           | No             |

**Combination of predicates for function Order Integers**

| Null pointer | Length of the array | Type of data | Valid/Invalid | Description of the test case |
|:------------:|:-------------------:|:------------:|:-------------:|:----------------------------:|
|   Yes        |     -               |     -        |       I       | orderIntegers(null) -> -1    |
|   No         |     1            | positive int    |       V       | orderIntegers([42]) -> 42      |
|              |                  | negative int    |       V       | orderIntegers([-7]) -> -1      |
|              |     >1              | positive int |       V       | orderIntegers([9,0,2]) -> 9    |
|              |                     | negative int |       V       | orderIntegers([-7,-2,-3]) ->-2 |
|              |          |positive and negative int|       V       | orderIntegers([4,-2,0]) -> 4   |


## Calories


**Criteria for function acceptableToEat:**
	
- Sing of proteins

- Sign of carbohydrates

- Sign of fats
  

**Predicates for function acceptableToEat:**

| Criteria                  | Predicate      |
| ------------------------- | ---------------|
| Proteins                  | < 0            | 
|                           | >=0            |
| Carbohydrates             | < 0            | 
|                           | >=0            |
| Fats                      | < 0            | 
|                           | ==0            |
|                           | >0             |

**Combination of predicates for function acceptableToEat**

*(some test case description is reported below)*

| Proteins | Carbohydrates | Fats     | Valid/Invalid | Description of the test case      |
|:--------:|:-------------:|:--------:|:-------------:|:---------------------------------:|
|    >=0   |      >=0      |   > 0    |       V       |     test case (a)                 |
|          |               |   > 0    |       V       |     test case (b)                 |
|          |               |   > 0    |       V       |     test case (c)                 |
|          |               |   > 0    |       V       |     test case (d)                 |
|          |               |   = 0    |       I       | acceptableToEat(10,10,0) -> false |                           
|          |               |   < 0    |       I       | acceptableToEat(10,10,-1) -> false|
|          |      < 0      |   > 0    |       I       | acceptableToEat(10,-1,10) -> false|
|          |               |   = 0    |       I       | acceptableToEat(10,-1,0) -> false |
|          |               |   < 0    |       I       | acceptableToEat(10,-1,-1) -> false|
|   < 0    |      >=0      |   > 0    |       I       | acceptableToEat(-1,10,10) -> false|
|          |               |   = 0    |       I       | acceptableToEat(-1,10,0) -> false |                          
|          |               |   < 0    |       I       | acceptableToEat(-1,10,-1) -> false| 
|          |      < 0      |   > 0    |       I       | acceptableToEat(-1,-1,10) -> false| 
|          |               |   = 0    |       I       | acceptableToEat(-1,-1,0) -> false | 
|          |               |   < 0    |       I       | acceptableToEat(-1,-1,-1) -> false|


1g carbohydrates = 4 kcal

1g proteins = 4 kcal

1g fats = 9 kcal

#### (a) acceptableToEat(40,20,10)

-> 160+80+90 = 330 kcal < 1000

-> (40+20)/10 = 6 > 1/2

-> return true

#### (b) acceptableToEat(20,20,90)

-> 80+80+810 = 970 kcal < 1000

-> (20+20)/90 < 1/2

-> return false

#### (c) acceptableToEat(20,20,100)

-> 80+80+900 = 1060 kcal > 1000

-> (20+20)/100 < 1/2

-> return false

#### (d) acceptableToEat(80,70,70)

-> 320+280+630 = 1230 kcal > 1000

-> (80+70)/70 > 1/2

-> return false


## Parallelogram


**Criteria for function Parallelogram:**
	
- Area > 0 -> not all coordinates with the same value

- Parallelogram in the first quadrant -> all coordinates > 0

- Valid coordinates value 
  

**Predicates for function Parallelogram:**

| Criteria                            | Predicate                               |
| ----------------------------------- | ----------------------------------------|
| Area > 0                            | ! (x1==x2==x3==x4==y1==y2==y3==y4)      | 
| Parallelogram in the first quadrant | x1>=0 & x2>0 & x3>0 & x4>0 & y1>=0 & y2>=0 & y3 >0 & y4>0 |
| Valid coordinates value             | x3>x1 & x4>x2 & x2>x1 & x4>x3 & y3>y1 & y4>y2 & y2==y1 & y4==y3 |


**Combination of predicates for function Parallelogram**

| x1 | x2 | x3 | x4 | y1 | y2 | y3 | y4 | Valid/Invalid | Description of the test case |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:-------------:|:----------------------------:|
| >=0| >0 | >0 | >0 | >=0| >=0| >0 | >0 |       V       | parallelogram(10,20,30,40,0,0,50,50) -> 500 |
|    |    |    |    |    |    |    |    |       I       | parallelogram(1,1,1,1,1,1,1,1) -> -1 |     
|    |    |    |    |    |    |    |    |       I       | parallelogram(2,1,1,1,0,0,10,10) -> -1 |
|    |    |    |    |    |    |    |    |       I       | parallelogram(1,2,4,3,0,0,10,10) -> -1 |     
|    |    |    |    |    |    |    |    |       I       | parallelogram(1,2,3,4,0,1,10,10) -> -1 |     
|    |    |    |    |    |    |    |    |       I       | parallelogram(2,1,1,1,10,10,0,0) -> -1 |     
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,40,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,40,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,30,40,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,40,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,40,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,30,40,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,40,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,40,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,20,30,40,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,40,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,40,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,30,40,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,40,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,40,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,30,40,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,40,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,40,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |       I       | parallelogram(10,20,30,40,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,40,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,40,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,30,40,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,40,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,40,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,30,40,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,40,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,40,-1,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,20,30,40,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,40,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,40,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,30,40,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,40,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,40,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,30,40,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,40,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,40,-1,-1,-1,0) -> -1 |
|    |    |    | =0 | >=0| >=0| >0 | >0 |       I       | parallelogram(10,20,30,0,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,0,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,0,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,30,0,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,0,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,0,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,30,0,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,0,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,0,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,20,30,0,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,0,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,0,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,30,0,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,0,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,0,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,30,0,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,0,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,0,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |       I       | parallelogram(10,20,30,0,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,0,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,0,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,30,0,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,0,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,0,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,30,0,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,0,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,0,-1,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,20,30,0,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,0,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,0,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,30,0,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,0,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,0,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,30,0,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,0,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,0,-1,-1,-1,0) -> -1 |
|    |    |    | <0 | >=0| >=0| >0 | >0 |       I       | parallelogram(10,20,30,-1,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,-1,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,-1,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,30,-1,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,-1,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,-1,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,30,-1,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,-1,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,-1,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,20,30,-1,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,-1,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,-1,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,30,-1,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,-1,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,-1,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,30,-1,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,-1,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,-1,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |       I       | parallelogram(10,20,30,-1,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,-1,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,-1,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,30,-1,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,-1,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,-1,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,30,-1,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,-1,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,-1,-1,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,20,30,-1,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,-1,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,-1,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,30,-1,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,-1,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,-1,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,30,-1,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,30,-1,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,30,-1,-1,-1,-1,0) -> -1 |
|    |    | =0 | >0 | >=0| >=0| >0 | >0 |       I       | parallelogram(10,20,0,40,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,40,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,40,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,0,40,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,40,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,40,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,0,40,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,40,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,40,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,20,0,40,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,40,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,40,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,0,40,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,40,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,40,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,0,40,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,40,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,40,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |       I       | parallelogram(10,20,0,40,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,40,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,40,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,0,40,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,40,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,40,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,0,40,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,40,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,40,-1,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,20,0,40,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,40,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,40,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,0,40,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,40,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,40,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,0,40,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,40,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,40,-1,-1,-1,0) -> -1 |
|    |    |    | =0 | >=0| >=0| >0 | >0 |       I       | parallelogram(10,20,0,0,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,0,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,0,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,0,0,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,0,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,0,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,0,0,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,0,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,0,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,20,0,0,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,0,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,0,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,0,0,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,0,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,0,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,0,0,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,0,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,0,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |       I       | parallelogram(10,20,0,0,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,0,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,0,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,0,0,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,0,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,0,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,0,0,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,0,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,0,-1,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,20,0,0,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,0,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,0,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,0,0,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,0,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,0,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,0,0,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,0,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,0,-1,-1,-1,0) -> -1 |
|    |    |    | <0 | >=0| >=0| >0 | >0 |       I       | parallelogram(10,20,0,-1,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,-1,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,-1,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,0,-1,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,-1,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,-1,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,0,-1,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,-1,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,-1,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,20,0,-1,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,-1,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,-1,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,0,-1,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,-1,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,-1,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,0,-1,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,-1,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,-1,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |       I       | parallelogram(10,20,0,-1,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,-1,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,-1,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,0,-1,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,-1,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,-1,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,0,-1,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,-1,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,-1,-1,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,20,0,-1,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,-1,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,-1,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,0,-1,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,-1,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,-1,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,0,-1,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,0,-1,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,0,-1,-1,-1,-1,0) -> -1 |
|    |    | <0 | >0 | >=0| >=0| >0 | >0 |       I       | parallelogram(10,20,-1,40,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,40,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,40,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,-1,40,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,40,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,40,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,-1,40,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,40,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,40,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,20,-1,40,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,40,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,40,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,-1,40,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,40,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,40,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,-1,40,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,40,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,40,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |       I       | parallelogram(10,20,-1,40,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,40,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,40,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,-1,40,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,40,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,40,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,-1,40,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,40,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,40,-1,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,20,-1,40,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,40,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,40,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,-1,40,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,40,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,40,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,-1,40,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,40,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,40,-1,-1,-1,0) -> -1 |
|    |    |    | =0 | >=0| >=0| >0 | >0 |       I       | parallelogram(10,20,-1,0,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,0,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,0,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,-1,0,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,0,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,0,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,-1,0,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,0,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,0,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,20,-1,0,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,0,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,0,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,-1,0,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,0,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,0,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,-1,0,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,0,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,0,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |       I       | parallelogram(10,20,-1,0,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,0,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,0,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,-1,0,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,0,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,0,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,-1,0,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,0,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,0,-1,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,20,-1,0,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,0,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,0,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,-1,0,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,0,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,0,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,-1,0,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,0,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,0,-1,-1,-1,0) -> -1 |
|    |    |    | <0 | >=0| >=0| >0 | >0 |       I       | parallelogram(10,20,-1,-1,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,-1,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,-1,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,-1,-1,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,-1,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,-1,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,-1,-1,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,-1,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,-1,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,20,-1,-1,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,-1,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,-1,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,-1,-1,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,-1,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,-1,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,-1,-1,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,-1,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,-1,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |       I       | parallelogram(10,20,-1,-1,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,-1,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,-1,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,-1,-1,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,-1,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,-1,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,-1,-1,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,-1,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,-1,-1,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,20,-1,-1,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,-1,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,-1,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,20,-1,-1,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,-1,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,-1,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,20,-1,-1,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,20,-1,-1,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,20,-1,-1,-1,-1,-1,0) -> -1  |
|    | =0 | >0 | >0 | >=0| >=0| >0 | >0 |       I       | parallelogram(10,0,30,40,0,0,50,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,40,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,40,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,30,40,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,40,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,40,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,30,40,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,40,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,40,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,0,30,40,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,40,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,40,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,30,40,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,40,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,40,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,30,40,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,40,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,40,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |       I       | parallelogram(10,0,30,40,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,40,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,40,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,30,40,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,40,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,40,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,30,40,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,40,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,40,-1,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,0,30,40,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,40,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,40,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,30,40,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,40,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,40,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,30,40,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,40,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,40,-1,-1,-1,0) -> -1 |
|    |    |    | =0 | >=0| >=0| >0 | >0 |       I       | parallelogram(10,0,30,0,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,0,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,0,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,30,0,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,0,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,0,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,30,0,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,0,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,0,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,0,30,0,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,0,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,0,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,30,0,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,0,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,0,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,30,0,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,0,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,0,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |       I       | parallelogram(10,0,30,0,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,0,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,0,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,30,0,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,0,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,0,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,30,0,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,0,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,0,-1,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,0,30,0,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,0,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,0,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,30,0,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,0,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,0,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,30,0,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,0,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,0,-1,-1,-1,0) -> -1 |
|    |    |    | <0 | >=0| >=0| >0 | >0 |       I       | parallelogram(10,0,30,-1,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,-1,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,-1,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,30,-1,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,-1,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,-1,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,30,-1,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,-1,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,-1,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,0,30,-1,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,-1,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,-1,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,30,-1,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,-1,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,-1,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,30,-1,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,-1,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,-1,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |       I       | parallelogram(10,0,30,-1,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,-1,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,-1,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,30,-1,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,-1,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,-1,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,30,-1,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,-1,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,-1,-1,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,0,30,-1,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,-1,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,-1,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,30,-1,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,-1,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,-1,-1,-1,0,0) -> -1  |
|    |    | =0 | >0 | >=0| >=0| >0 | >0 |       I       | parallelogram(10,0,30,-1,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,30,-1,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,30,-1,-1,-1,-1,0) -> -1 |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,0,40,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,40,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,40,0,0,50,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,0,40,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,40,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,40,0,0,0,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,0,0,40,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,40,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,40,0,0,-1,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,0,40,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,40,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,40,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,0,40,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,40,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,40,0,-1,0,0) -> -1  |
|    |    |    |    | <0 | >=0| >0 | >0 |       I       | parallelogram(10,0,0,40,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,40,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,40,0,-1,-1,0) -> -1 |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,0,40,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,40,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,40,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,0,40,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,40,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,40,-1,0,0,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,0,0,40,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,40,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,40,-1,0,-1,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,0,40,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,40,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,40,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,0,40,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,40,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,40,-1,-1,0,0) -> -1  |
|    |    |    | =0 | >=0| >=0| >0 | >0 |       I       | parallelogram(10,0,0,40,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,40,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,40,-1,-1,-1,0) -> -1 |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,0,0,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,0,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,0,0,0,50,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,0,0,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,0,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,0,0,0,0,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,0,0,0,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,0,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,0,0,0,-1,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,0,0,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,0,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,0,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,0,0,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,0,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,0,0,-1,0,0) -> -1  |
|    |    |    |    | <0 | >=0| >0 | >0 |       I       | parallelogram(10,0,0,0,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,0,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,0,0,-1,-1,0) -> -1 |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,0,0,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,0,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,0,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,0,0,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,0,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,0,-1,0,0,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,0,0,0,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,0,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,0,-1,0,-1,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,0,0,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,0,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,0,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,0,0,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,0,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,0,-1,-1,0,0) -> -1  |
|    |    |    | <0 | >=0| >=0| >0 | >0 |       I       | parallelogram(10,0,0,0,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,0,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,0,-1,-1,-1,0) -> -1 |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,0,-1,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,-1,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,-1,0,0,50,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,0,-1,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,-1,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,-1,0,0,0,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,0,0,-1,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,-1,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,-1,0,0,-1,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,0,-1,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,-1,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,-1,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,0,-1,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,-1,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,-1,0,-1,0,0) -> -1  |
|    |    |    |    | <0 | >=0| >0 | >0 |       I       | parallelogram(10,0,0,-1,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,-1,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,-1,0,-1,-1,0) -> -1 |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,0,-1,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,-1,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,-1,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,0,-1,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,-1,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,-1,-1,0,0,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,0,0,-1,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,-1,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,-1,-1,0,-1,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,0,-1,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,-1,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,-1,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,0,-1,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,-1,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,-1,-1,-1,0,0) -> -1  |
|    |    | <0 | >0 | >=0| >=0| >0 | >0 |       I       | parallelogram(10,0,0,-1,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,0,-1,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,0,-1,-1,-1,-1,0) -> -1 |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,-1,40,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,40,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,40,0,0,50,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,0,-1,40,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,40,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,40,0,0,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,-1,40,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,40,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,40,0,0,-1,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,-1,40,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,40,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,40,0,-1,50,0) -> -1  |
|    |    |    |    | <0 | >=0| >0 | >0 |       I       | parallelogram(10,0,-1,40,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,40,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,40,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,-1,40,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,40,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,40,0,-1,-1,0) -> -1 |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,-1,40,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,40,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,40,-1,0,50,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,0,-1,40,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,40,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,40,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,-1,40,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,40,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,40,-1,0,-1,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,-1,40,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,40,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,40,-1,-1,50,0) -> -1  |
|    |    |    | =0 | >=0| >=0| >0 | >0 |       I       | parallelogram(10,0,-1,40,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,40,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,40,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,-1,40,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,40,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,40,-1,-1,-1,0) -> -1 |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,-1,0,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,0,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,0,0,0,50,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,0,-1,0,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,0,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,0,0,0,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,-1,0,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,0,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,0,0,0,-1,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,-1,0,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,0,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,0,0,-1,50,0) -> -1  |
|    |    |    |    | <0 | >=0| >0 | >0 |       I       | parallelogram(10,0,-1,0,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,0,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,0,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,-1,0,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,0,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,0,0,-1,-1,0) -> -1 |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,-1,0,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,0,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,0,-1,0,50,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,0,-1,0,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,0,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,0,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,-1,0,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,0,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,0,-1,0,-1,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,-1,0,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,0,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,0,-1,-1,50,0) -> -1  |
|    |    |    | <0 | >=0| >=0| >0 | >0 |       I       | parallelogram(10,0,-1,0,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,0,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,0,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,-1,0,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,0,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,0,-1,-1,-1,0) -> -1 |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,-1,-1,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,-1,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,-1,0,0,50,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,0,-1,-1,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,-1,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,-1,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,-1,-1,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,-1,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,-1,0,0,-1,0) -> -1  |
|    |    |    |    | <0 | >=0| >0 | >0 |       I       | parallelogram(10,0,-1,-1,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,-1,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,-1,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,-1,-1,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,-1,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,-1,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,-1,-1,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,-1,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,-1,0,-1,-1,0) -> -1 |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,0,-1,-1,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,-1,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,-1,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,0,-1,-1,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,-1,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,-1,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,0,-1,-1,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,0,-1,-1,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,0,-1,-1,-1,0,-1,0) -> -1  |				   
|    | <0 | >0 | >0 | >=0| >=0| >0 | >0 |       I       | parallelogram(10,-1,30,40,0,0,50,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,40,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,40,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,30,40,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,40,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,40,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,30,40,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,40,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,40,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,-1,30,40,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,40,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,40,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,30,40,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,40,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,40,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,30,40,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,40,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,40,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |       I       | parallelogram(10,-1,30,40,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,40,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,40,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,30,40,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,40,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,40,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,30,40,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,40,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,40,-1,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,-1,30,40,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,40,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,40,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,30,40,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,40,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,40,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,30,40,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,40,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,40,-1,-1,-1,0) -> -1 |
|    |    |    | =0 | >=0| >=0| >0 | >0 |       I       | parallelogram(10,-1,30,0,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,0,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,0,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,30,0,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,0,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,0,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,30,0,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,0,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,0,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,-1,30,0,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,0,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,0,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,30,0,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,0,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,0,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,30,0,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,0,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,0,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |       I       | parallelogram(10,-1,30,0,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,0,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,0,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,30,0,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,0,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,0,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,30,0,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,0,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,0,-1,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,-1,30,0,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,0,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,0,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,30,0,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,0,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,0,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,30,0,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,0,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,0,-1,-1,-1,0) -> -1 |
|    |    |    | <0 | >=0| >=0| >0 | >0 |       I       | parallelogram(10,-1,30,-1,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,-1,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,-1,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,30,-1,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,-1,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,-1,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,30,-1,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,-1,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,-1,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,-1,30,-1,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,-1,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,-1,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,30,-1,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,-1,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,-1,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,30,-1,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,-1,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,-1,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |       I       | parallelogram(10,-1,30,-1,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,-1,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,-1,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,30,-1,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,-1,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,-1,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,30,-1,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,-1,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,-1,-1,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,-1,30,-1,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,-1,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,-1,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,30,-1,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,-1,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,-1,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,30,-1,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,30,-1,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,30,-1,-1,-1,-1,0) -> -1 |
|    |    | =0 | >0 | >=0| >=0| >0 | >0 |       I       | parallelogram(10,-1,0,40,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,40,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,40,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,0,40,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,40,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,40,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,0,40,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,40,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,40,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,-1,0,40,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,40,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,40,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,0,40,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,40,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,40,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,0,40,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,40,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,40,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |       I       | parallelogram(10,-1,0,40,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,40,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,40,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,0,40,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,40,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,40,-1,0,0,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,-1,0,40,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,40,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,40,-1,0,-1,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,0,40,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,40,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,40,-1,-1,50,0) -> -1  |
|    |    |    | =0 | >=0| >=0| >0 | >0 |       I       | parallelogram(10,-1,0,40,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,40,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,40,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,0,40,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,40,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,40,-1,-1,-1,0) -> -1 |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,0,0,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,0,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,0,0,0,50,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,-1,0,0,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,0,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,0,0,0,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,0,0,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,0,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,0,0,0,-1,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,0,0,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,0,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,0,0,-1,50,0) -> -1  |
|    |    |    |    | <0 | >=0| >0 | >0 |       I       | parallelogram(10,-1,0,0,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,0,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,0,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,0,0,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,0,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,0,0,-1,-1,0) -> -1 |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,0,0,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,0,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,0,-1,0,50,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,-1,0,0,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,0,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,0,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,0,0,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,0,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,0,-1,0,-1,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,0,0,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,0,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,0,-1,-1,50,0) -> -1  |
|    |    |    | <0 | >=0| >=0| >0 | >0 |       I       | parallelogram(10,-1,0,0,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,0,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,0,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,0,0,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,0,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,0,-1,-1,-1,0) -> -1 |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,0,-1,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,-1,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,-1,0,0,50,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,-1,0,-1,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,-1,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,-1,0,0,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,0,-1,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,-1,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,-1,0,0,-1,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,0,-1,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,-1,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,-1,0,-1,50,0) -> -1  |
|    |    |    |    | <0 | >=0| >0 | >0 |       I       | parallelogram(10,-1,0,-1,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,-1,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,-1,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,0,-1,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,-1,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,-1,0,-1,-1,0) -> -1 |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,0,-1,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,-1,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,-1,-1,0,50,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,-1,0,-1,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,-1,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,-1,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,0,-1,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,-1,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,-1,-1,0,-1,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,0,-1,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,-1,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,-1,-1,-1,50,0) -> -1  |
|    |    | <0 | >0 | >=0| >=0| >0 | >0 |       I       | parallelogram(10,-1,0,-1,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,-1,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,-1,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,0,-1,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,0,-1,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,0,-1,-1,-1,-1,0) -> -1 |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,-1,40,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,40,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,40,0,0,50,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,-1,-1,40,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,40,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,40,0,0,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,-1,40,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,40,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,40,0,0,-1,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,-1,40,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,40,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,40,0,-1,50,0) -> -1  |
|    |    |    |    | <0 | >=0| >0 | >0 |       I       | parallelogram(10,-1,-1,40,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,40,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,40,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,-1,40,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,40,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,40,0,-1,-1,0) -> -1 |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,-1,40,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,40,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,40,-1,0,50,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,-1,-1,40,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,40,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,40,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,-1,40,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,40,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,40,-1,0,-1,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,-1,40,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,40,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,40,-1,-1,50,0) -> -1  |
|    |    |    | =0 | >=0| >=0| >0 | >0 |       I       | parallelogram(10,-1,-1,40,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,40,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,40,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,-1,40,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,40,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,40,-1,-1,-1,0) -> -1 |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,-1,0,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,0,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,0,0,0,50,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,-1,-1,0,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,0,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,0,0,0,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,-1,0,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,0,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,0,0,0,-1,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,-1,0,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,0,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,0,0,-1,50,0) -> -1  |
|    |    |    |    | <0 | >=0| >0 | >0 |       I       | parallelogram(10,-1,-1,0,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,0,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,0,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,-1,0,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,0,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,0,0,-1,-1,0) -> -1 |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,-1,0,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,0,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,0,-1,0,50,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,-1,-1,0,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,0,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,0,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,-1,0,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,0,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,0,-1,0,-1,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,-1,0,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,0,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,0,-1,-1,50,0) -> -1  |
|    |    |    | <0 | >=0| >=0| >0 | >0 |       I       | parallelogram(10,-1,-1,0,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,0,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,0,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,-1,0,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,0,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,0,-1,-1,-1,0) -> -1 |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,-1,-1,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,-1,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,-1,0,0,50,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,-1,-1,-1,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,-1,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,-1,0,0,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,-1,-1,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,-1,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,-1,0,0,-1,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,-1,-1,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,-1,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,-1,0,-1,50,0) -> -1  |
|    |    |    |    | <0 | >=0| >0 | >0 |       I       | parallelogram(10,-1,-1,-1,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,-1,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,-1,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,-1,-1,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,-1,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,-1,0,-1,-1,0) -> -1 |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,-1,-1,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,-1,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,-1,-1,0,50,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |       I       | parallelogram(10,-1,-1,-1,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,-1,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,-1,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |       I       | parallelogram(10,-1,-1,-1,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,-1,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,-1,-1,0,-1,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |       I       | parallelogram(10,-1,-1,-1,-1,-1,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |       I       | parallelogram(10,-1,-1,-1,-1,-1,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |       I       | parallelogram(10,-1,-1,-1,-1,-1,-1,0) -> -1  |
| <0 | >0 | >0 | >0 | >=0| >=0| >0 | >0 |      I        | parallelogram(-1,20,30,40,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,40,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,40,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,30,40,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,40,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,40,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,30,40,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,40,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,40,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,20,30,40,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,40,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,40,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,30,40,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,40,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,40,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,30,40,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,40,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,40,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |      I        | parallelogram(-1,20,30,40,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,40,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,40,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,30,40,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,40,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,40,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,30,40,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,40,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,40,-1,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,20,30,40,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,40,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,40,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,30,40,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,40,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,40,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,30,40,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,40,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,40,-1,-1,-1,0) -> -1 |
|    |    |    | =0 | >=0| >=0| >0 | >0 |      I        | parallelogram(-1,20,30,0,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,0,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,0,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,30,0,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,0,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,0,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,30,0,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,0,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,0,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,20,30,0,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,0,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,0,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,30,0,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,0,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,0,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,30,0,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,0,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,0,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |      I        | parallelogram(-1,20,30,0,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,0,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,0,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,30,0,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,0,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,0,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,30,0,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,0,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,0,-1,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,20,30,0,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,0,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,0,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,30,0,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,0,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,0,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,30,0,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,0,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,0,-1,-1,-1,0) -> -1 |
|    |    |    | <0 | >=0| >=0| >0 | >0 |      I        | parallelogram(-1,20,30,-1,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,-1,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,-1,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,30,-1,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,-1,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,-1,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,30,-1,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,-1,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,-1,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,20,30,-1,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,-1,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,-1,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,30,-1,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,-1,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,-1,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,30,-1,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,-1,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,-1,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |      I        | parallelogram(-1,20,30,-1,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,-1,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,-1,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,30,-1,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,-1,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,-1,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,30,-1,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,-1,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,-1,-1,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,20,30,-1,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,-1,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,-1,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,30,-1,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,-1,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,-1,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,30,-1,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,30,-1,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,30,-1,-1,-1,-1,0) -> -1 |
|    |    | =0 | >0 | >=0| >=0| >0 | >0 |      I        | parallelogram(-1,20,0,40,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,40,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,40,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,0,40,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,40,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,40,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,0,40,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,40,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,40,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,20,0,40,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,40,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,40,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,0,40,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,40,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,40,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,0,40,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,40,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,40,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |      I        | parallelogram(-1,20,0,40,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,40,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,40,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,0,40,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,40,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,40,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,0,40,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,40,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,40,-1,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,20,0,40,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,40,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,40,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,0,40,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,40,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,40,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,0,40,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,40,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,40,-1,-1,-1,0) -> -1 |
|    |    |    | =0 | >=0| >=0| >0 | >0 |      I        | parallelogram(-1,20,0,0,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,0,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,0,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,0,0,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,0,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,0,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,0,0,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,0,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,0,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,20,0,0,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,0,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,0,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,0,0,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,0,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,0,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,0,0,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,0,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,0,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |      I        | parallelogram(-1,20,0,0,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,0,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,0,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,0,0,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,0,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,0,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,0,0,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,0,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,0,-1,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,20,0,0,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,0,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,0,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,0,0,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,0,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,0,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,0,0,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,0,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,0,-1,-1,-1,0) -> -1 |
|    |    |    | <0 | >=0| >=0| >0 | >0 |      I        | parallelogram(-1,20,0,-1,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,-1,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,-1,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,0,-1,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,-1,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,-1,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,0,-1,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,-1,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,-1,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,20,0,-1,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,-1,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,-1,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,0,-1,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,-1,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,-1,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,0,-1,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,-1,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,-1,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |      I        | parallelogram(-1,20,0,-1,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,-1,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,-1,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,0,-1,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,-1,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,-1,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,0,-1,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,-1,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,-1,-1,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,20,0,-1,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,-1,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,-1,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,0,-1,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,-1,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,-1,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,0,-1,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,0,-1,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,0,-1,-1,-1,-1,0) -> -1 |
|    |    | <0 | >0 | >=0| >=0| >0 | >0 |      I        | parallelogram(-1,20,-1,40,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,40,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,40,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,-1,40,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,40,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,40,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,-1,40,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,40,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,40,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,20,-1,40,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,40,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,40,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,-1,40,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,40,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,40,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,-1,40,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,40,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,40,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |      I        | parallelogram(-1,20,-1,40,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,40,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,40,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,-1,40,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,40,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,40,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,-1,40,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,40,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,40,-1,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,20,-1,40,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,40,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,40,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,-1,40,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,40,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,40,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,-1,40,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,40,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,40,-1,-1,-1,0) -> -1 |
|    |    |    | =0 | >=0| >=0| >0 | >0 |      I        | parallelogram(-1,20,-1,0,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,0,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,0,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,-1,0,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,0,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,0,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,-1,0,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,0,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,0,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,20,-1,0,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,0,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,0,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,-1,0,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,0,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,0,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,-1,0,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,0,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,0,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |      I        | parallelogram(-1,20,-1,0,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,0,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,0,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,-1,0,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,0,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,0,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,-1,0,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,0,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,0,-1,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,20,-1,0,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,0,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,0,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,-1,0,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,0,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,0,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,-1,0,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,0,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,0,-1,-1,-1,0) -> -1 |
|    |    |    | <0 | >=0| >=0| >0 | >0 |      I        | parallelogram(-1,20,-1,-1,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,-1,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,-1,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,-1,-1,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,-1,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,-1,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,-1,-1,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,-1,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,-1,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,20,-1,-1,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,-1,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,-1,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,-1,-1,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,-1,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,-1,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,-1,-1,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,-1,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,-1,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |      I        | parallelogram(-1,20,-1,-1,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,-1,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,-1,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,-1,-1,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,-1,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,-1,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,-1,-1,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,-1,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,-1,-1,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,20,-1,-1,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,-1,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,-1,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,20,-1,-1,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,-1,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,-1,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,20,-1,-1,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,20,-1,-1,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,20,-1,-1,-1,-1,-1,0) -> -1  |
|    | =0 | >0 | >0 | >=0| >=0| >0 | >0 |      I        | parallelogram(-1,0,30,40,0,0,50,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,40,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,40,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,30,40,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,40,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,40,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,30,40,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,40,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,40,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,0,30,40,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,40,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,40,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,30,40,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,40,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,40,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,30,40,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,40,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,40,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |      I        | parallelogram(-1,0,30,40,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,40,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,40,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,30,40,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,40,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,40,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,30,40,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,40,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,40,-1,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,0,30,40,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,40,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,40,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,30,40,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,40,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,40,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,30,40,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,40,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,40,-1,-1,-1,0) -> -1 |
|    |    |    | =0 | >=0| >=0| >0 | >0 |      I        | parallelogram(-1,0,30,0,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,0,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,0,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,30,0,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,0,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,0,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,30,0,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,0,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,0,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,0,30,0,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,0,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,0,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,30,0,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,0,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,0,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,30,0,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,0,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,0,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |      I        | parallelogram(-1,0,30,0,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,0,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,0,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,30,0,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,0,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,0,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,30,0,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,0,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,0,-1,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,0,30,0,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,0,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,0,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,30,0,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,0,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,0,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,30,0,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,0,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,0,-1,-1,-1,0) -> -1 |
|    |    |    | <0 | >=0| >=0| >0 | >0 |      I        | parallelogram(-1,0,30,-1,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,-1,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,-1,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,30,-1,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,-1,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,-1,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,30,-1,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,-1,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,-1,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,0,30,-1,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,-1,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,-1,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,30,-1,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,-1,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,-1,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,30,-1,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,-1,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,-1,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |      I        | parallelogram(-1,0,30,-1,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,-1,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,-1,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,30,-1,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,-1,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,-1,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,30,-1,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,-1,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,-1,-1,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,0,30,-1,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,-1,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,-1,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,30,-1,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,-1,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,-1,-1,-1,0,0) -> -1  |
|    |    | =0 | >0 | >=0| >=0| >0 | >0 |      I        | parallelogram(-1,0,30,-1,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,30,-1,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,30,-1,-1,-1,-1,0) -> -1 |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,0,40,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,40,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,40,0,0,50,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,0,40,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,40,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,40,0,0,0,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,0,0,40,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,40,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,40,0,0,-1,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,0,40,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,40,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,40,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,0,40,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,40,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,40,0,-1,0,0) -> -1  |
|    |    |    |    | <0 | >=0| >0 | >0 |      I        | parallelogram(-1,0,0,40,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,40,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,40,0,-1,-1,0) -> -1 |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,0,40,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,40,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,40,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,0,40,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,40,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,40,-1,0,0,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,0,0,40,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,40,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,40,-1,0,-1,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,0,40,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,40,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,40,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,0,40,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,40,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,40,-1,-1,0,0) -> -1  |
|    |    |    | =0 | >=0| >=0| >0 | >0 |      I        | parallelogram(-1,0,0,40,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,40,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,40,-1,-1,-1,0) -> -1 |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,0,0,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,0,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,0,0,0,50,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,0,0,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,0,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,0,0,0,0,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,0,0,0,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,0,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,0,0,0,-1,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,0,0,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,0,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,0,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,0,0,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,0,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,0,0,-1,0,0) -> -1  |
|    |    |    |    | <0 | >=0| >0 | >0 |      I        | parallelogram(-1,0,0,0,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,0,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,0,0,-1,-1,0) -> -1 |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,0,0,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,0,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,0,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,0,0,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,0,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,0,-1,0,0,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,0,0,0,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,0,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,0,-1,0,-1,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,0,0,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,0,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,0,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,0,0,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,0,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,0,-1,-1,0,0) -> -1  |
|    |    |    | <0 | >=0| >=0| >0 | >0 |      I        | parallelogram(-1,0,0,0,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,0,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,0,-1,-1,-1,0) -> -1 |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,0,-1,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,-1,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,-1,0,0,50,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,0,-1,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,-1,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,-1,0,0,0,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,0,0,-1,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,-1,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,-1,0,0,-1,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,0,-1,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,-1,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,-1,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,0,-1,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,-1,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,-1,0,-1,0,0) -> -1  |
|    |    |    |    | <0 | >=0| >0 | >0 |      I        | parallelogram(-1,0,0,-1,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,-1,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,-1,0,-1,-1,0) -> -1 |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,0,-1,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,-1,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,-1,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,0,-1,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,-1,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,-1,-1,0,0,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,0,0,-1,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,-1,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,-1,-1,0,-1,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,0,-1,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,-1,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,-1,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,0,-1,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,-1,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,-1,-1,-1,0,0) -> -1  |
|    |    | <0 | >0 | >=0| >=0| >0 | >0 |      I        | parallelogram(-1,0,0,-1,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,0,-1,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,0,-1,-1,-1,-1,0) -> -1 |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,-1,40,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,40,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,40,0,0,50,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,0,-1,40,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,40,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,40,0,0,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,-1,40,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,40,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,40,0,0,-1,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,-1,40,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,40,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,40,0,-1,50,0) -> -1  |
|    |    |    |    | <0 | >=0| >0 | >0 |      I        | parallelogram(-1,0,-1,40,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,40,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,40,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,-1,40,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,40,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,40,0,-1,-1,0) -> -1 |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,-1,40,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,40,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,40,-1,0,50,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,0,-1,40,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,40,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,40,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,-1,40,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,40,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,40,-1,0,-1,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,-1,40,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,40,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,40,-1,-1,50,0) -> -1  |
|    |    |    | =0 | >=0| >=0| >0 | >0 |      I        | parallelogram(-1,0,-1,40,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,40,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,40,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,-1,40,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,40,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,40,-1,-1,-1,0) -> -1 |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,-1,0,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,0,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,0,0,0,50,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,0,-1,0,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,0,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,0,0,0,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,-1,0,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,0,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,0,0,0,-1,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,-1,0,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,0,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,0,0,-1,50,0) -> -1  |
|    |    |    |    | <0 | >=0| >0 | >0 |      I        | parallelogram(-1,0,-1,0,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,0,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,0,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,-1,0,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,0,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,0,0,-1,-1,0) -> -1 |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,-1,0,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,0,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,0,-1,0,50,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,0,-1,0,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,0,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,0,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,-1,0,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,0,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,0,-1,0,-1,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,-1,0,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,0,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,0,-1,-1,50,0) -> -1  |
|    |    |    | <0 | >=0| >=0| >0 | >0 |      I        | parallelogram(-1,0,-1,0,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,0,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,0,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,-1,0,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,0,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,0,-1,-1,-1,0) -> -1 |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,-1,-1,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,-1,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,-1,0,0,50,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,0,-1,-1,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,-1,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,-1,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,-1,-1,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,-1,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,-1,0,0,-1,0) -> -1  |
|    |    |    |    | <0 | >=0| >0 | >0 |      I        | parallelogram(-1,0,-1,-1,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,-1,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,-1,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,-1,-1,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,-1,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,-1,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,-1,-1,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,-1,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,-1,0,-1,-1,0) -> -1 |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,0,-1,-1,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,-1,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,-1,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,0,-1,-1,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,-1,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,-1,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,0,-1,-1,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,0,-1,-1,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,0,-1,-1,-1,0,-1,0) -> -1  |				   
|    | <0 | >0 | >0 | >=0| >=0| >0 | >0 |      I        | parallelogram(-1,-1,30,40,0,0,50,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,40,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,40,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,30,40,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,40,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,40,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,30,40,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,40,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,40,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,-1,30,40,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,40,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,40,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,30,40,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,40,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,40,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,30,40,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,40,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,40,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |      I        | parallelogram(-1,-1,30,40,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,40,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,40,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,30,40,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,40,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,40,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,30,40,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,40,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,40,-1,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,-1,30,40,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,40,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,40,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,30,40,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,40,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,40,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,30,40,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,40,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,40,-1,-1,-1,0) -> -1 |
|    |    |    | =0 | >=0| >=0| >0 | >0 |      I        | parallelogram(-1,-1,30,0,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,0,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,0,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,30,0,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,0,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,0,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,30,0,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,0,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,0,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,-1,30,0,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,0,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,0,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,30,0,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,0,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,0,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,30,0,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,0,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,0,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |      I        | parallelogram(-1,-1,30,0,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,0,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,0,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,30,0,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,0,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,0,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,30,0,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,0,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,0,-1,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,-1,30,0,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,0,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,0,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,30,0,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,0,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,0,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,30,0,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,0,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,0,-1,-1,-1,0) -> -1 |
|    |    |    | <0 | >=0| >=0| >0 | >0 |      I        | parallelogram(-1,-1,30,-1,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,-1,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,-1,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,30,-1,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,-1,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,-1,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,30,-1,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,-1,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,-1,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,-1,30,-1,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,-1,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,-1,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,30,-1,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,-1,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,-1,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,30,-1,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,-1,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,-1,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |      I        | parallelogram(-1,-1,30,-1,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,-1,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,-1,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,30,-1,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,-1,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,-1,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,30,-1,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,-1,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,-1,-1,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,-1,30,-1,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,-1,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,-1,-1,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,30,-1,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,-1,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,-1,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,30,-1,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,30,-1,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,30,-1,-1,-1,-1,0) -> -1 |
|    |    | =0 | >0 | >=0| >=0| >0 | >0 |      I        | parallelogram(-1,-1,0,40,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,40,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,40,0,0,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,0,40,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,40,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,40,0,0,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,0,40,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,40,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,40,0,0,-1,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,-1,0,40,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,40,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,40,0,-1,50,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,0,40,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,40,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,40,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,0,40,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,40,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,40,0,-1,-1,0) -> -1 |
|    |    |    |    | <0 | >=0| >0 | >0 |      I        | parallelogram(-1,-1,0,40,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,40,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,40,-1,0,50,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,0,40,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,40,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,40,-1,0,0,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,-1,0,40,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,40,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,40,-1,0,-1,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,0,40,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,40,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,40,-1,-1,50,0) -> -1  |
|    |    |    | =0 | >=0| >=0| >0 | >0 |      I        | parallelogram(-1,-1,0,40,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,40,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,40,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,0,40,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,40,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,40,-1,-1,-1,0) -> -1 |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,0,0,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,0,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,0,0,0,50,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,-1,0,0,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,0,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,0,0,0,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,0,0,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,0,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,0,0,0,-1,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,0,0,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,0,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,0,0,-1,50,0) -> -1  |
|    |    |    |    | <0 | >=0| >0 | >0 |      I        | parallelogram(-1,-1,0,0,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,0,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,0,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,0,0,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,0,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,0,0,-1,-1,0) -> -1 |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,0,0,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,0,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,0,-1,0,50,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,-1,0,0,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,0,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,0,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,0,0,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,0,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,0,-1,0,-1,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,0,0,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,0,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,0,-1,-1,50,0) -> -1  |
|    |    |    | <0 | >=0| >=0| >0 | >0 |      I        | parallelogram(-1,-1,0,0,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,0,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,0,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,0,0,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,0,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,0,-1,-1,-1,0) -> -1 |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,0,-1,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,-1,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,-1,0,0,50,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,-1,0,-1,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,-1,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,-1,0,0,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,0,-1,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,-1,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,-1,0,0,-1,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,0,-1,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,-1,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,-1,0,-1,50,0) -> -1  |
|    |    |    |    | <0 | >=0| >0 | >0 |      I        | parallelogram(-1,-1,0,-1,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,-1,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,-1,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,0,-1,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,-1,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,-1,0,-1,-1,0) -> -1 |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,0,-1,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,-1,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,-1,-1,0,50,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,-1,0,-1,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,-1,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,-1,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,0,-1,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,-1,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,-1,-1,0,-1,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,0,-1,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,-1,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,-1,-1,-1,50,0) -> -1  |
|    |    | <0 | >0 | >=0| >=0| >0 | >0 |      I        | parallelogram(-1,-1,0,-1,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,-1,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,-1,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,0,-1,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,0,-1,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,0,-1,-1,-1,-1,0) -> -1 |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,-1,40,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,40,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,40,0,0,50,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,-1,-1,40,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,40,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,40,0,0,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,-1,40,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,40,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,40,0,0,-1,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,-1,40,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,40,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,40,0,-1,50,0) -> -1  |
|    |    |    |    | <0 | >=0| >0 | >0 |      I        | parallelogram(-1,-1,-1,40,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,40,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,40,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,-1,40,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,40,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,40,0,-1,-1,0) -> -1 |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,-1,40,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,40,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,40,-1,0,50,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,-1,-1,40,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,40,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,40,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,-1,40,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,40,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,40,-1,0,-1,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,-1,40,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,40,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,40,-1,-1,50,0) -> -1  |
|    |    |    | =0 | >=0| >=0| >0 | >0 |      I        | parallelogram(-1,-1,-1,40,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,40,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,40,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,-1,40,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,40,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,40,-1,-1,-1,0) -> -1 |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,-1,0,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,0,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,0,0,0,50,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,-1,-1,0,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,0,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,0,0,0,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,-1,0,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,0,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,0,0,0,-1,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,-1,0,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,0,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,0,0,-1,50,0) -> -1  |
|    |    |    |    | <0 | >=0| >0 | >0 |      I        | parallelogram(-1,-1,-1,0,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,0,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,0,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,-1,0,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,0,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,0,0,-1,-1,0) -> -1 |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,-1,0,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,0,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,0,-1,0,50,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,-1,-1,0,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,0,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,0,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,-1,0,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,0,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,0,-1,0,-1,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,-1,0,-1,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,0,-1,-1,50,-5) -> -1  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,0,-1,-1,50,0) -> -1  |
|    |    |    | <0 | >=0| >=0| >0 | >0 |      I        | parallelogram(-1,-1,-1,0,-1,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,0,-1,-1,0,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,0,-1,-1,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,-1,0,-1,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,0,-1,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,0,-1,-1,-1,0) -> -1 |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,-1,-1,0,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,-1,0,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,-1,0,0,50,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,-1,-1,-1,0,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,-1,0,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,-1,0,0,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,-1,-1,0,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,-1,0,0,-1,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,-1,0,0,-1,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,-1,-1,0,-1,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,-1,0,-1,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,-1,0,-1,50,0) -> -1  |
|    |    |    |    | <0 | >=0| >0 | >0 |      I        | parallelogram(-1,-1,-1,-1,0,-1,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,-1,0,-1,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,-1,0,-1,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,-1,-1,0,-1,-1,10) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,-1,0,-1,-1,-1) -> -1 |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,-1,0,-1,-1,0) -> -1 |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,-1,-1,-1,0,50,50) -> -1 |
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,-1,-1,0,50,-5) -> -1  |
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,-1,-1,0,50,0) -> -1  |
|    |    |    |    |    | <0 | >0 | >0 |      I        | parallelogram(-1,-1,-1,-1,-1,0,0,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,-1,-1,0,0,-1) -> -1 |  
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,-1,-1,0,0,0) -> -1  |
|    |    |    |    |    |    | =0 | >0 |      I        | parallelogram(-1,-1,-1,-1,-1,0,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,-1,-1,0,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,-1,-1,0,-1,0) -> -1  |
|    |    |    |    |    |    | <0 | >0 |      I        | parallelogram(-1,-1,-1,-1,-1,-1,-1,50) -> -1 | 
|    |    |    |    |    |    |    | <0 |      I        | parallelogram(-1,-1,-1,-1,-1,-1,-1,-1) -> -1 | 
|    |    |    |    |    |    |    | =0 |      I        | parallelogram(-1,-1,-1,-1,-1,-1,-1,0) -> -1  |
                                               


## Inventory


**Criteria for Inventory:**
	
- Code -> Alphanumeric String

- Code -> String lenght > 0

-  Stricly positive quantitity

** Buondaries **
- Quantitity == 0
  

**Predicates for Inventory:**

| Criteria                            | Predicate                               |
| ----------------------------------- | ----------------------------------------|
| Alphanumeric String                 | each char in {a-z,A-Z,0-9}	     		| 
| String lenght > 0					  | code.lenght > 0						    |
| Stricly positive quantitity         | quantitity > 0                          |


**Combination of predicates for Inventory**

| Alphanumeric | Length | Quantitity | Valid/Invalid | Description of the test case |
|:------------:|:------:|:----------:|:-------------:|:-----------------------------|
|    yes	   |  >0    |    >0      |     V         | "prod4362" , 5               |
|        	   |        |    =0      |     I         | "prod4362" , 0               |
|        	   |        |    <0      |     I         | "prod4362" , -1              |
|     No       |  =0    |    >0      |     I         | "",8                         |
|              |        |    =0      |     I         | "",0                         |
|              |        |    =0      |     I         | "",-2                        |