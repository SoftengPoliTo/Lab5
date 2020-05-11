# Unit Testing Documentation template

Authors:Enrico Alberti

Date:2020-05-05

Version:1



# Contents

- [Black Box Unit Tests](#black-box-unit-tests)

  

# Black Box Unit Tests


### Ex 1 “order integers” - int orderIntegers(int v[])

```
The function int orderIntegers(int v[]) shall take as input an array of three integer numbers. The program shall output the greatest number among the elements of the array. The program shall order the elements of the array in decreasing order.
```


**Criteria**
	
- Array exists

- Sign of elements in array

- number of elements in array

  

**Predicates**

| Criteria                      | Predicate    |
| ------------------------------| ------------ |
| array exists                  | Y            |
|                               | N            |
| Sign of elements in array     | > 0          |
|                               | <=0          |
| Number of elements in array   | < 3          |
|                               | = 3          |
|                               | > 3          |



**Boundaries**:

| Criteria                      | Boundary values             |
| ----------------------------- | --------------------------- |
| Sign of elements in array     | Minint, 0, maxint           |
| Number of elements in array   | 0, 1, 2, 3, 4               |





 **Combination**

| Array exists | Number of elements in array | Sign of elements in array |  Valid/Invalid | Description of the test case                                               |
|------------- | --------------------------- | ------------------------- | -------------- | ------------------------------------------------------------------         |
|     N        | less than 3                 | Positive                  |    I           | --                                                                         |
|              |                             | Negative                  |    I           | --                                                                         |
|              | more than 3                 | Positive                  |    I           | --                                                                         |
|              |                             | Negative                  |    I           | --                                                                         |
|              | equals to 3                 | Positive                  |    I           | --                                                                         |
|              |                             | Negative                  |    I           | --                                                                         |
|     Y        | less than 3                 | Positive                  |    I           | --                                                                         |
|              |                             | Negative                  |    I           | --                                                                         |
|              | more than 3                 | Positive                  |    I           | --                                                                         |
|              |                             | Negative                  |    I           | --                                                                         |
|              | equals to 3                 | Positive                  |    V           | v[] = {1, 2, 3} <br>orderIntegers(int v[]) -> 3; v[] = {3, 2, 1}           |
|              |                             | Negative                  |    V           | v[] = {-1, -2, -3} <br>orderIntegers(int v[]) -> -1; v[] = {-1, -2, -3}    |





### Ex2 Calories    - boolean acceptableToEat( int carb, int protein, int fat);

```
The function receives the weight in grams of, respectively, carbohydrates, proteins, fats in a serving of food. It returns true if
the total amount of calories is < 1000
(carb + protein ) / fat > 1/2
boolean acceptableToEat( int carb, int protein, int fat);
ex. 
- acceptableToEat (100,100,100) ->  false (tot amount of calories = 100*4 + 100*4 + 100*9 > 1000)
- acceptableToEat (1,1,10) ->  false ( carb + protein / fat = 2/10)
- acceptableToEat (1,1,1)  ->  true ( carb + protein / fat = 2/1)
```


**Criteria**
	
- Sign of carbohydrates
  
- Sign of proteins
  
- Sign of fat

  

**Predicates**

| Criteria                      | Predicate    |
| ------------------------------| ------------ |
| Sign of carbohydrates         | < 0          |
|                               | >= 0         |
| Sign of proteins              | < 0          |
|                               | >= 0         |
| Sign of fat                   | < 0          |
|                               | = 0          |
|                               | > 0          |



**Boundaries**:

| Criteria                      | Boundary values             |
| ----------------------------- | --------------------------- |
| Sign of fat                   | Minint, 0, maxint           |



 **Combination**

| Sign of carbohydrates | Sign of proteins | Sign of fat  |  Valid/Invalid | Description of the test case                                               |
|---------------------- | ---------------- | ------------ | -------------- | -------------------------------------------------------------------------- |
| < 0                   |   -              |    -         | I              | -                                                                          |
| >= 0                  |   < 0            |    -         | I              | -                                                                          |
|                       |   >= 0           |    < 0       | I              | -                                                                          |
|                       |                  |    = 0       | I              | -                                                                          |
|                       |                  |    > 0       | V              | acceptableToEat (1,1,10) -> false                                          |
|                       |                  |              |                | acceptableToEat (10,10,5) -> true                                          |



## Ex3 parallelogram    - int parallelogram(int x1, int x2, int x3, int x4, int y1, int y2, int y3, int y4);

```
The function parallelogram(int x1, int x2, int x3, int x4, int y1, int y2, int y3, int y4) calculate the area of a parallelogram.
Requirements are:
- area is always strictly > 0;
- the parallelogram should stay in the first quadrant of the Cartesian plan;
- coordinates must have the following meaning:
In case of error or invalid input, -1 is returned.
P1(x1; y1) P2(x2; y2) ...
```


**Criteria**
	
- Sign of area
  
- sign of coordinates in Point

  

**Predicates**

| Criteria                      | Predicate         |
| ------------------------------| ----------------- |
| Sign of area                  | <= 0              |
|                               | > 0               |
| sign of coordinates in Point  |  x <= 0 & y <= 0  |
|                               |  x <= 0 & y > 0   |
|                               |  x > 0 & y <= 0   |
|                               |  x > 0 & y > 0    |


**Boundaries**:

| Criteria                      | Boundary values             |
| ----------------------------- | --------------------------- |
| sign of coordinates in Point  | x1= 0; y1 = 0               |



 **Combination**

| Sign of area | Sign of coordinates in Points |  Valid/Invalid | Description of the test case                                               |
|------------- | ----------------------------- | -------------- | -------------------------------------------------------------------------- |
| <= 0         |   -                           | I              | -                                                                          |
| > 0          |   x <= 0 & y <= 0             | I              | -                                                                          |
|              |   x <= 0 & y > 0              | I              | -                                                                          |
|              |   x > 0 & y <= 0              | I              | -                                                                          |
|              |   x > 0 & y > 0               | V              | P1(1, 1); p2(4,1); p3(3, 2); p4(5, 2)                                      |




## Ex4 inventory    -

```
A retail support system manages an inventory of items. Each item has a descriptor and the number of available items.

public class Item { // descriptor of items in inventory
    private String itemCode // aka bar code, unique identifier of item
    private int availability; // number of items available
    private String description; // description of item
    private String name; // name of item
}

public class Inventory{
    void addItem(Item i) throws ItemAlreadyExists // adds new descriptor
    Item searchItem (String itemCode) throws ItemNotExists; // returns item with given code

    public new Item(String itemCode,int quantity); // creates a new item
    int availabilityItem (String itemCode) throws ItemNotExists; // returns availability of item
    void subtractItem (String itemCode) throws ItemNotExists, ItemNotAvailable; // subtracts 1 to availability
    void addQtyToItem(String itemCode, int qty_to_add);
    void subtractQtyToItem(String itemCode, int qty_to_add);
}

```


**Criteria for method addItem**

- duplicate item

**Criteria for method subtractItem**

- item not exists
- item not available

**Criteria for method searchItem**

- item not exists

  

**Predicates for method addItem**

| Criteria                      | Predicate         |
| ------------------------------| ----------------- |
| duplicate item                | Y                 |
|                               | N                 |

**Predicates for method subtractItem**

| Criteria                      | Predicate         |
| ------------------------------| ----------------- |
| item not exists               | Y                 |
|                               | N                 |
| item not available            | Y                 |
|                               | N                 |

**Predicates for method searchItem**

| Criteria                      | Predicate         |
| ------------------------------| ----------------- |
| item not exists               | Y                 |
|                               | N                 |


**Boundaries**:

| Criteria                      | Boundary values                     |
| ----------------------------- | ----------------------------------- |
| availability                  |     0, 1, ... , max_int -1, max_int |



 **Combination for method addItem**

| duplicate item | Valid/Invalid | Description of the test case                                               |
|--------------- | ------------- | -------------------------------------------------------------------------- |
| Y              |  I            | -                                                                          |
| N              |  V            | Item i = new Item("mozzarella", 30); <br> addItem(i);                      |


 **Combination for method subtractItem**

| item not exists | item not available | Valid/Invalid | Description of the test case                                                                                   |
|---------------- | ------------------ | ------------- | -------------------------------------------------------------------------------------------------------------- |
| Y               |                    |  I            | -                                                                                                              |
| N               |  Y                 | I             | -                                                                                                              |
|                 |  N                 | V             | Item i = new Item("mozzarella", 30); <br> addItem(i);  <br>  subtractItem("mozzarella") -> i.availabiliy--     |


 **Combination for method searchItem**

| item not exists | Valid/Invalid | Description of the test case                                                                |
|---------------  | ------------- | ------------------------------------------------------------------------------------------- |
| Y               |  I            | -                                                                                           |
| N               |  V            | Item i = new Item("mozzarella", 30); <br> addItem(i);  <br>  searchItem("mozzarella") -> i  |



