# Unit Testing Documentation template

Authors: Bolla Alessandro   

Date: 08/05/2020

Version: 1.0



# Contents

- [Black Box Unit Tests](#black-box-unit-tests)
  

# Black Box Unit Tests

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