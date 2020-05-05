# Unit Testing, Exercise 4

Authors:

Andrea Bruno, s269705

Date:

05/05/2020

Version:

1.0 (Black box)


# Contents

- [Black Box Unit Tests](#black-box-unit-tests)

	+ [addItem](#addItem)

	+ [searchItem](#searchItem)

	+ [new Item](#new-Item)

	+ [availabilityItem](#availabilityItem)

	+ [subtractItem](#subtractItem)

	+ [addQtyToItem](#addQtyToItem)

	+ [subtractQtyToItem](#subtractQtyToItem)



- [White Box Unit Tests](#white-box-unit-tests)

  

# Black Box Unit Tests
A retail support system manages an inventory of items. Each item has a descriptor and the number of
available items.

public class Item { // descriptor of items in inventory

 private String itemCode // aka bar code, unique identifier of item

 private int availability; // number of items available

 private String description; // description of item

 private String name; // name of item

}

public class Inventory{

void addItem(Item i) throws ItemAlreadyExists // adds new descriptor

 Item searchItem (String itemCode) throws ItemNotExists; // returns item 
 with given code

public new Item(String itemCode,int quantity); // creates a new item

 int availabilityItem (String itemCode) throws ItemNotExists; // returns availability of item

 void subtractItem (String itemCode) throws ItemNotExists, ItemNotAvailable;
 // subtracts 1 to availability

 void addQtyToItem(String itemCode, int qty_to_add);

 void subtractQtyToItem(String itemCode, int qty_to_add);

}

## addItem
**Criteria:**
	
- Null state of item
- Validity of itemCode
- Existence of item

**Predicates:**

| Criteria                  | Predicate    |
| ------------------------- | ------------ |
| Null state of item| Null|
||Not Null|
|Validity of itemCode|Not valid|
||Valid|
|Existence of item|Existent|
||New|

**Boundaries:**

| Criteria            | Boundary values             |
| ------------------- | --------------------------- |
| Validity of itemCode| Null, ""|

 **Combination of predicates:**

 Existent items: I1 (itemCode="I1")
|Null state of item|Validity of itemCode|Existence of item|Valid/Invalid|Test cases|
|--|--|--|--|--|
|Null|-|-|I|(null)-> no update|
|Not Null|Not valid|-|I (Null)|(I(itemCode=Null))-> no update|
| |||I ("")|(I(itemCode=""))-> no update|
||Valid|Existent|I|(I(itemCode="I1"))-> throws ItemAlreadyExixts|
|||New|V|(I(itemCode="I2")-> update|

 ## searchItem

 **Criteria:**
	
- Validity of itemCode
- Existence of item

**Predicates:**

| Criteria                  | Predicate    |
| ------------------------- | ------------ |
|Validity of itemCode|Not valid|
||Valid|
|Existence of item|Existent|
||New|



**Boundaries:**
| Criteria            | Boundary values             |
| ------------------- | --------------------------- |
| Validity of itemCode| Null, ""|

 **Combination of predicates:**
 
 Existent items: I1 (itemCode="I1")
|Validity of itemCode|Existence of item|Valid/Invalid|Test cases|
|--|--|--|--|
|Not valid|-|I (Null)|(Null)->throws ItemNotExixts|
| ||I ("")|("")-> throws ItemNotExixts|
|Valid|Not existent|I|("I2")-> throws ItemNotExixts|
||Existent|V|("I1")-> I1|

 ## new Item

 **Criteria:**
	
- Validity of quantity
- Validity of itemCode
- Existence of itemCode

**Predicates:**

| Criteria                  | Predicate    |
| ------------------------- | ------------ |
|Validity of quantity|<0|
||>=0|
|Validity of itemCode|Not valid|
||Valid|
|Existence of itemCode|Existent|
||New|



**Boundaries:**
| Criteria            | Boundary values             |
| ------------------- | --------------------------- |
| Validity of quantity|minint, minint+1, -1,0,1,maxint-1, maxint|
| Validity of itemCode| Null, ""|

 **Combination of predicates:**
 
 Existent items: I1 (itemCode="I1")
|Validity of quantity|Validity of itemCode|Existence of itemCode|Valid/Invalid|Test cases|
|--|--|--|--|--|
|<0|-|-|I|("I2",-1)->no insertion|
|>=0|Not valid|-|I (null)|(null, 1)->no insertion|
||||I ("")|("",1)->no insertion|
||Valid|Existent|I|("I1",1)->no insertion|
|||New|V|("I2",1)->insertion|

 ## availabilityItem

 **Criteria:**
	
- Validity of itemCode
- Existence of item

**Predicates:**

| Criteria                  | Predicate    |
| ------------------------- | ------------ |
|Validity of itemCode|Not valid|
||Valid|
|Existence of item|Existent|
||New|



**Boundaries:**
| Criteria            | Boundary values             |
| ------------------- | --------------------------- |
| Validity of itemCode| Null, ""|

 **Combination of predicates:**
 
 Existent items: I1 (itemCode="I1", quantity=5)
|Validity of itemCode|Existence of item|Valid/Invalid|Test cases|
|--|--|--|--|
|Not valid|-|I (Null)|(Null)->throws ItemNotExixts|
| ||I ("")|("")-> throws ItemNotExixts|
|Valid|Not existent|I|("I2")-> throws ItemNotExixts|
||Existent|V|("I1")-> 5|

 ## subtractItem

 **Criteria:**
	
- Validity of itemCode
- Existence of item
- Previous quantity of item

**Predicates:**

| Criteria                  | Predicate    |
| ------------------------- | ------------ |
|Validity of itemCode|Not valid|
||Valid|
|Existence of item|Existent|
||New|
|Previous quantity of item| 0|
||>0|



**Boundaries:**
| Criteria            | Boundary values             |
| ------------------- | --------------------------- |
| Validity of itemCode| Null, ""|
|Previous quantity of item|0, 1, maxint-1, maxint|

 **Combination of predicates:**
 
 Existent items: I1 (itemCode="I1", quantity=5),I2 (itemCode="I2", quantity=0)
|Validity of itemCode|Existence of item|Previous quantity of item|Valid/Invalid|Test cases|
|--|--|--|--|--|
|Not valid|-|-|I (Null)|(Null)->throws ItemNotExixts|
| |||I ("")|("")-> throws ItemNotExixts|
|Valid|Not existent|-|I|("I3")-> throws ItemNotExixts|
||Existent|0|I|("I3")-> throws ItemNotAvailable|
|||>0|V|("I1")-> I1.quantity is now 4|

 ## addQtyToItem

 **Criteria:**
	
- Validity of itemCode
- Existence of item
- Validity of qty_to_add
- Previous quantity of item

**Predicates:**

| Criteria                  | Predicate    |
| ------------------------- | ------------ |
|Validity of itemCode|Not valid|
||Valid|
|Existence of item|Existent|
||New|
|Validity of qty_to_add|<0|
||>=0|
|Previous quantity of item| <maxint-qty_to_add|
||>maxint-qty_to_add|



**Boundaries:**
| Criteria            | Boundary values             |
| ------------------- | --------------------------- |
| Validity of itemCode| Null, ""|
| Validity of qty_to_add|minint, minint+1,-1, 0, 1, maxint-1, maxint|
|Previous quantity of item|0, 1, maxint-qty_to_sub, maxint-1, maxint|

 **Combination of predicates:**
 
 Existent items: I1 (itemCode="I1", quantity=5),I2 (itemCode="I2", quantity=maxint-1)
|Validity of itemCode|Existence of item|Validity of qty_to_sub|Previous quantity of item|Valid/Invalid|Test cases|
|--|--|--|--|--|--|
|Not valid|-|-|-|I (Null)|(Null, 2)->no update|
| ||||I ("")|("", 2)-> no update|
|Valid|Not existent|-|-|I|("I3", 2)->no update|
||Existent|<0|-|I|("I2", -3)->no update|
|||>=0|<maxint-qty_to_add|I|("I2", 2)-> no update|
||||>=maxint-qty_to_add|V|("I1", 2)->I1.quantity is now 7|

## subtractQtyToItem

 **Criteria:**
	
- Validity of itemCode
- Existence of item
- Validity of qty_to_sub
- Previous quantity of item

**Predicates:**

| Criteria                  | Predicate    |
| ------------------------- | ------------ |
|Validity of itemCode|Not valid|
||Valid|
|Existence of item|Existent|
||New|
|Validity of qty_to_sub|<0|
||>=0|
|Previous quantity of item| <qty_to_sub|
||>qty_to_sub|



**Boundaries:**
| Criteria            | Boundary values             |
| ------------------- | --------------------------- |
| Validity of itemCode| Null, ""|
| Validity of qty_to_sub|minint, minint+1,-1, 0, 1, maxint-1, maxint|
|Previous quantity of item|0, 1, qty_to_sub-1, qty_to_sub, qty_to_sub+1, maxint-1, maxint|

 **Combination of predicates:**
 
 Existent items: I1 (itemCode="I1", quantity=5),I2 (itemCode="I2", quantity=1)
|Validity of itemCode|Existence of item|Validity of qty_to_sub|Previous quantity of item|Valid/Invalid|Test cases|
|--|--|--|--|--|--|
|Not valid|-|-|-|I (Null)|(Null, 2)->no update|
| ||||I ("")|("", 2)-> no update|
|Valid|Not existent|-|-|I|("I3", 2)->no update|
||Existent|<0|-|I|("I2", -3)->no update|
|||>=0|<qty_to_sub|I|("I2", 2)-> no update|
||||>=qty_to_sub|V|("I1", 2)->I1.quantity is now 3|

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

