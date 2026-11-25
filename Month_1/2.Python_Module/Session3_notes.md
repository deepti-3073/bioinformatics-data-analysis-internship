# Module 3: Python Programming

## Session 3: Core Data Structures

## 1. Objectives

- Create and manipulate lists.
- Work with dictionaries using key-value pairs.
- Perform common string operations.
- Use tuples for fixed and immutable data structures.
- Use sets to manage unique elements and perform membership checks.
- Select appropriate data structures based on the use case and efficiency requirements.

---

# PART A: LISTS

## 2. Lists

### Definition

- A list is an ordered collection of elements.
- Lists are created using square brackets `[]`.
- They can store elements belonging to different data types.
- Lists are mutable, meaning their elements can be modified after creation.
- Lists allow duplicate values.

### Characteristics of Lists

1. **Ordered:** Elements maintain their position in the list.
2. **Mutable:** Elements can be added, removed or modified.
3. **Heterogeneous:** A list can contain different data types.
4. **Duplicates allowed:** The same value can appear multiple times.
5. **Indexed:** Elements can be accessed using their positions.

### Basic Syntax

```python
my_list = [element1, element2, element3]
```

### Example 1: Creating a List

```python
fruits = ["apple", "banana", "cherry", "watermelon"]

print(fruits)
```

**Output:**

```text
['apple', 'banana', 'cherry', 'watermelon']
```

### Example 2: Creating a List with Different Data Types

```python
mixed_list = [1, 10.6, "Hello", False]

print(mixed_list)
```

**Output:**

```text
[1, 10.6, 'Hello', False]
```

**Explanation:**

The list contains:
- `1` – Integer
- `10.6` – Float
- `"Hello"` – String
- `False` – Boolean

A list can store different data types together.

---

## 3. Accessing List Elements (Indexing)

### Definition

- Indexing is used to access individual elements in a list.
- Python uses zero-based indexing.
- This means the first element is at index `0`.
- The second element is at index `1`, and so on.
- Negative indexing allows elements to be accessed from the end of the list.

### Example

```python
fruits = ["apple", "banana", "cherry", "watermelon"]
```

| Element | apple | banana | cherry | watermelon |
|---|---:|---:|---:|---:|
| Positive index | 0 | 1 | 2 | 3 |
| Negative index | -4 | -3 | -2 | -1 |

### Accessing the First Element

```python
print(fruits[0])
```

**Output:**

```text
apple
```

### Accessing the Third Element

```python
print(fruits[2])
```

**Output:**

```text
cherry
```

### Accessing the Last Element

```python
print(fruits[-1])
```

**Output:**

```text
watermelon
```

### Important Points

- Positive indexing starts from the beginning.
- Negative indexing starts from the end.
- Indexing starts from `0`, not `1`.
- Accessing an index that does not exist produces an `IndexError`.

---

## 4. Common List Operations

List operations are used for:

- Adding elements.
- Removing elements.
- Accessing and modifying elements.
- Counting elements.
- Sorting and reversing the list.
- Checking the contents of a list.

The common list methods covered in this session include:

| Operation | Method / Function | Purpose |
|---|---|---|
| Adding | `append()` | Adds one element at the end |
| Adding | `insert()` | Adds an element at a specified index |
| Adding | `extend()` | Adds multiple elements from another iterable |
| Removing | `remove()` | Removes a specified value |
| Removing | `pop()` | Removes and returns an element |
| Removing | `clear()` | Removes all elements |
| Sorting | `sort()` | Sorts the list |
| Reversing | `reverse()` | Reverses the order of elements |
| Counting | `count()` | Counts occurrences of a value |
| Accessing | `index()` | Finds the index of a value |
| Utility | `len()` | Returns the number of elements |

---

## 5. Adding Elements to a List

### 1. append()

**Definition:**

- `append()` adds a single element to the end of a list.
- It modifies the original list.
- It does not create a separate list.

### Syntax

```python
list_name.append(element)
```

### Example

```python
fruits = ["apple", "banana"]

fruits.append("cherry")

print(fruits)
```

**Output:**

```text
['apple', 'banana', 'cherry']
```

**Explanation:**

- Initially, the list contains apple and banana.
- `append("cherry")` adds cherry at the end.
- The original list is updated.

### 2. insert()

**Definition:**

- `insert()` adds an element at a particular index.
- It allows an element to be placed at a specific position rather than only at the end.

### Syntax

```python
list_name.insert(index, element)
```

### Example

```python
fruit = ["apple", "banana", "cherry"]

fruit.insert(1, "orange")

print(fruit)
```

**Output:**

```text
['apple', 'orange', 'banana', 'cherry']
```

**Explanation:**

- `1` specifies the index.
- `"orange"` is the element being inserted.
- The element is placed at index 1.
- The other elements shift to the right.

### 3. extend()

**Definition:**

- `extend()` adds multiple elements from another iterable to the end of a list.
- It is commonly used to combine the contents of two lists.
- Unlike `append()`, it adds the individual elements rather than adding the entire second list as one nested element.

### Syntax

```python
list_name.extend(iterable)
```

### Example

```python
list_1 = [1, 2, 3]
list_2 = [4, 5]

list_1.extend(list_2)

print(list_1)
```

**Output:**

```text
[1, 2, 3, 4, 5]
```

**Explanation:**

- `list_1` initially contains 1, 2 and 3.
- `list_2` contains 4 and 5.
- `extend()` adds both elements to the end of `list_1`.

### Difference Between append(), insert() and extend()

| Method | Purpose | Example |
|---|---|---|
| `append()` | Adds one element at the end | `fruits.append("mango")` |
| `insert()` | Adds an element at a specified position | `fruits.insert(1, "mango")` |
| `extend()` | Adds multiple elements from another iterable | `fruits.extend(["mango", "grapes"])` |

---

## 6. Removing Elements from a List

### 1. remove()

**Definition:**

- `remove()` removes a specified value from the list.
- It removes the first occurrence of that value.
- If the value does not exist, Python raises a `ValueError`.

### Syntax

```python
list_name.remove(value)
```

### Example

```python
numbers = [10, 20, 30, 20]

numbers.remove(20)

print(numbers)
```

**Output:**

```text
[10, 30, 20]
```

**Explanation:**

- The value 20 occurs twice.
- `remove(20)` removes only the first occurrence.
- The second occurrence remains in the list.

### 2. pop()

**Definition:**

- `pop()` removes and returns an element from the list.
- By default, it removes the last element.
- An index can be specified to remove an element from a particular position.

### Syntax

```python
list_name.pop()
```

Or:

```python
list_name.pop(index)
```

### Example 1: Removing the Last Element

```python
items = ["a", "b", "c", "d"]

last_item = items.pop()

print(items)
print(last_item)
```

**Output:**

```text
['a', 'b', 'c']
d
```

**Explanation:**

- `pop()` removes the last element, `"d"`.
- The removed element is returned and stored in `last_item`.
- The original list now contains only `"a"`, `"b"` and `"c"`.

### Example 2: Removing an Element Using an Index

```python
items = ["a", "b", "c", "d"]

removed_item = items.pop(1)

print(items)
print(removed_item)
```

**Output:**

```text
['a', 'c', 'd']
b
```

### 3. clear()

**Definition:**

- `clear()` removes all elements from a list.
- The list itself continues to exist.
- After clearing, the list becomes empty.

### Syntax

```python
list_name.clear()
```

### Example

```python
data = [1, 2, 3]

data.clear()

print(data)
```

**Output:**

```text
[]
```

**Explanation:**

- All elements are removed.
- The list still exists, but it contains no elements.

### Difference Between remove(), pop() and clear()

| Method | Purpose |
|---|---|
| `remove(value)` | Removes the first occurrence of a specified value |
| `pop(index)` | Removes and returns an element at a specified index; defaults to the last |
| `clear()` | Removes all elements from the list |

---

## 7. Sorting a List

### sort()

**Definition:**

- `sort()` arranges the elements of a list in ascending order by default.
- It modifies the original list.
- It can also sort in descending order using `reverse=True`.

### Syntax

```python
list_name.sort()
```

### Example: Ascending Order

```python
numbers = [5, 2, 9, 1]

numbers.sort()

print(numbers)
```

**Output:**

```text
[1, 2, 5, 9]
```

### Example: Descending Order

```python
numbers = [5, 2, 9, 1]

numbers.sort(reverse=True)

print(numbers)
```

**Output:**

```text
[9, 5, 2, 1]
```

**Explanation:**

- By default, `sort()` arranges elements from smallest to largest.
- `reverse=True` arranges them from largest to smallest.

---

## 8. Reversing a List

### reverse()

**Definition:**

- `reverse()` reverses the current order of elements in a list.
- It modifies the original list.
- It does not sort the elements.

### Syntax

```python
list_name.reverse()
```

### Example

```python
letters = ["a", "b", "c"]

letters.reverse()

print(letters)
```

**Output:**

```text
['c', 'b', 'a']
```

**Explanation:**

The original order is reversed.

**Important difference:**

- `sort()` arranges elements according to their values.
- `reverse()` simply reverses their existing order.

---

## 9. Counting Elements in a List

### len()

**Definition:**

- `len()` returns the total number of elements in a list.
- It counts the elements present in the list.

### Syntax

```python
len(list_name)
```

### Example

```python
scores = [95, 76, 81, 93]

print(len(scores))
```

**Output:**

```text
4
```

There are four elements in the list.

### count()

**Definition:**

- `count()` returns the number of times a specified value occurs in a list.
- It is useful when duplicate values are present.

### Syntax

```python
list_name.count(value)
```

### Example

```python
numbers = [1, 2, 2, 3, 2, 4]

print(numbers.count(2))
```

**Output:**

```text
3
```

The value 2 occurs three times.

---

## 10. Finding the Index of an Element

### index()

**Definition:**

- `index()` returns the position of the first occurrence of a specified value.
- It is useful for locating an element in a list.

### Syntax

```python
list_name.index(value)
```

### Example

```python
letters = ["a", "b", "c", "d"]

print(letters.index("c"))
```

**Output:**

```text
2
```

The element `"c"` is located at index 2.

If the value is not present, Python raises a `ValueError`.

---

## 11. List Indexing and Slicing

### Indexing

Indexing accesses an individual element.

```python
letters = ["a", "b", "c", "d", "e"]

print(letters[0])
print(letters[-1])
```

**Output:**

```text
a
e
```

### Slicing

Slicing extracts a portion of the list.

### Syntax

```python
list_name[start:end]
```

- `start` specifies the starting index.
- `end` specifies the stopping index.
- The ending index is excluded.

### Example

```python
letters = ["a", "b", "c", "d", "e"]

print(letters[1:4])
```

**Output:**

```text
['b', 'c', 'd']
```

The elements at indices 1, 2 and 3 are returned.

---

## 12. Calculations Using Lists

Lists can store numerical values that can be used for mathematical calculations.

### Example: Calculating Average Marks

```python
marks = [85, 90, 78, 92]

total = sum(marks)

average = total / len(marks)

print("Average:", average)
```

**Output:**

```text
Average: 86.25
```

### Explanation

1. `marks` stores the numerical values.
2. `sum(marks)` calculates the total of all values.
3. `len(marks)` calculates the number of elements.
4. The total is divided by the number of elements to calculate the average.
5. `print()` displays the result.

### Where Lists Are Useful

- When the order of elements matters.
- When the data may change.
- When duplicate values are allowed.
- When storing multiple observations or measurements.

---

# PART B: TUPLES

## 13. Tuples

### Definition

- A tuple is an ordered collection of elements.
- Tuples are created using parentheses `()`.
- They can store different data types.
- Tuples are immutable, meaning their elements cannot be modified after creation.
- Tuples allow duplicate values.

### Characteristics of Tuples

1. **Ordered:** Elements maintain their position.
2. **Immutable:** Elements cannot be changed after creation.
3. **Heterogeneous:** Different data types can be stored together.
4. **Duplicates allowed:** Repeated values are permitted.
5. **Indexed:** Elements can be accessed using their positions.

### Basic Syntax

```python
my_tuple = (element1, element2, element3)
```

### Example

```python
values = (10, 20, 30)

print(values)
```

**Output:**

```text
(10, 20, 30)
```

### Accessing Tuple Elements

Tuple elements can be accessed through indexing, just like lists.

```python
values = (10, 20, 30)

print(values[0])
```

**Output:**

```text
10
```

### Accessing the Last Element

```python
values = (10, 20, 30)

print(values[-1])
```

**Output:**

```text
30
```

### Important: Immutability

Tuples cannot be modified after creation.

For example:

```python
values = (10, 20, 30)

values[0] = 50
```

This produces a `TypeError` because tuple elements cannot be reassigned.

### Difference Between Lists and Tuples

| Feature | List | Tuple |
|---|---|---|
| Brackets | `[]` | `()` |
| Ordered | Yes | Yes |
| Mutable | Yes | No |
| Duplicate values | Allowed | Allowed |
| Different data types | Allowed | Allowed |
| Elements can be modified | Yes | No |

### When to Use Tuples

- When the data should not change.
- When a fixed collection of values is required.
- When the structure of the data should remain unchanged.

---

# PART C: DICTIONARIES

## 14. Dictionaries

### Definition

- A dictionary stores data in key-value pairs.
- Each key is associated with a corresponding value.
- Dictionaries are mutable, meaning values can be added, removed or updated.
- Dictionary keys must be unique.
- Dictionaries allow fast lookup of values using their keys.

### Characteristics of Dictionaries

1. **Key-value pairs:** Each entry contains a key and its corresponding value.
2. **Mutable:** Values can be modified.
3. **Unique keys:** Duplicate keys are not allowed.
4. **Access through keys:** Values are retrieved using their keys rather than positional indexing.
5. **Ordered:** Dictionaries preserve insertion order.

### Basic Syntax

```python
my_dictionary = {
    "key1": "value1",
    "key2": "value2"
}
```

### Example: Creating a Dictionary

```python
student = {
    "name": "Aman",
    "age": 21
}

print(student)
```

**Output:**

```text
{'name': 'Aman', 'age': 21}
```

### Explanation

- `"name"` is a key.
- `"Aman"` is its corresponding value.
- `"age"` is another key.
- `21` is its corresponding value.

---

## 15. Accessing Dictionary Values

Dictionary values can be accessed using their keys.

### Method 1: Using Keys

### Syntax

```python
dictionary_name["key"]
```

### Example

```python
student = {
    "name": "Aman",
    "age": 21
}

print(student["name"])
```

**Output:**

```text
Aman
```

### Method 2: Using get()

**Definition:**

- `get()` retrieves the value associated with a specified key.
- It is another way to access dictionary values.
- If the key does not exist, it returns `None` by default instead of raising a `KeyError`.

### Syntax

```python
dictionary_name.get("key")
```

### Example

```python
student = {
    "name": "Aman",
    "age": 21
}

print(student.get("age"))
```

**Output:**

```text
21
```

### Example: Accessing a Missing Key

```python
print(student.get("course"))
```

**Output:**

```text
None
```

### Difference Between Square Brackets and get()

| Method | Behaviour when key is missing |
|---|---|
| `dictionary["key"]` | Raises a `KeyError` |
| `dictionary.get("key")` | Returns `None` by default |

---

## 16. Adding and Updating Dictionary Values

### Definition

- Dictionaries are mutable.
- New key-value pairs can be added.
- Existing values can be updated by assigning a new value to their keys.

### Example: Updating an Existing Value

```python
student = {
    "name": "Aman",
    "age": 21
}

student["age"] = 20

print(student)
```

**Output:**

```text
{'name': 'Aman', 'age': 20}
```

The age value is updated from 21 to 20.

### Example: Adding a New Key-Value Pair

```python
student["grade"] = "A"

print(student)
```

**Output:**

```text
{'name': 'Aman', 'age': 20, 'grade': 'A'}
```

The new key `"grade"` and its value `"A"` are added to the dictionary.

---

## 17. Dictionary Operations

### 1. pop()

**Definition:**

- `pop()` removes a specified key from a dictionary.
- It also returns the value associated with the removed key.

### Syntax

```python
dictionary_name.pop("key")
```

### Example

```python
student = {
    "name": "Shyam",
    "age": 21,
    "grade": "A"
}

removed_value = student.pop("age")

print("Removed:", removed_value)
print("Updated values:", student)
```

**Output:**

```text
Removed: 21
Updated values: {'name': 'Shyam', 'grade': 'A'}
```

**Explanation:**

- `"age"` is the key being removed.
- `pop()` removes the key-value pair.
- The value associated with `"age"` is returned and stored in `removed_value`.
- The updated dictionary no longer contains the age entry.

### 2. keys()

**Definition:**

- `keys()` returns all the keys present in a dictionary.
- It is useful when we need to retrieve or examine the dictionary's keys.

### Example

```python
student = {
    "name": "Shyam",
    "age": 21,
    "grade": "A"
}

all_keys = student.keys()

print("Keys:", all_keys)
```

**Output:**

```text
Keys: dict_keys(['name', 'age', 'grade'])
```

### 3. values()

**Definition:**

- `values()` returns all the values present in a dictionary.
- It is useful when we want to examine the stored values without retrieving the keys.

### Example

```python
student = {
    "name": "Shyam",
    "age": 21,
    "grade": "A"
}

all_values = student.values()

print("Values:", all_values)
```

**Output:**

```text
Values: dict_values(['Shyam', 21, 'A'])
```

### 4. items()

**Definition:**

- `items()` returns the key-value pairs in a dictionary.
- Each pair is returned as a tuple containing the key and its corresponding value.

### Example

```python
student = {
    "name": "Shyam",
    "age": 21,
    "grade": "A"
}

print(student.items())
```

**Output:**

```text
dict_items([('name', 'Shyam'), ('age', 21), ('grade', 'A')])
```

---

## 18. Iterating Through a Dictionary

### Definition

- Iteration means accessing elements one at a time.
- A dictionary can be traversed using a `for` loop.
- The `items()` method allows both keys and values to be accessed together.

### Example

```python
student = {
    "name": "Shyam",
    "age": 21,
    "grade": "A"
}

for key, value in student.items():
    print(key, ":", value)
```

**Output:**

```text
name : Shyam
age : 21
grade : A
```

### Explanation

- `student.items()` provides the key-value pairs.
- `key` stores the current key.
- `value` stores the corresponding value.
- The `for` loop processes each pair one at a time.
- `print()` displays the key and its value.

### When to Use Dictionaries

- When data has labels or identifiers.
- When there is a relationship between values and their names.
- When fast lookup using keys is required.

---

# PART D: SETS

## 19. Sets

### Definition

- A set is an unordered collection of unique elements.
- Sets are created using curly brackets `{}`.
- Sets are mutable, meaning elements can be added or removed.
- Duplicate values are not allowed.
- Sets do not support indexing.

### Characteristics of Sets

1. **Unordered:** Elements do not have fixed positional indices.
2. **Unique elements:** Duplicate values are automatically removed.
3. **Mutable:** Elements can be added or removed.
4. **No indexing:** Individual elements cannot be accessed using positions.
5. **Membership checking:** Sets are useful for checking whether an element exists.

### Basic Syntax

```python
my_set = {element1, element2, element3}
```

### Example: Creating a Set

```python
my_set = {1, 2, 3}

print(my_set)
```

**Output:**

```text
{1, 2, 3}
```

### Example: Duplicate Values

```python
data = {1, 2, 2, 3, 4}

print(data)
```

**Output:**

```text
{1, 2, 3, 4}
```

**Explanation:**

- The value 2 is entered twice.
- Sets automatically remove duplicate values.
- Therefore, each value appears only once.

**Important:** Sets are unordered. The displayed order of elements is not guaranteed.

---

## 20. Set Operations

### 1. add()

**Definition:**

- `add()` inserts a single element into a set.
- If the element is already present, no duplicate is created.

### Syntax

```python
set_name.add(element)
```

### Example

```python
numbers = {1, 2, 3}

numbers.add(4)

print(numbers)
```

**Output:**

```text
{1, 2, 3, 4}
```

### Adding an Existing Element

```python
numbers = {1, 2, 3}

numbers.add(2)

print(numbers)
```

**Output:**

```text
{1, 2, 3}
```

The value 2 is already present, so another copy is not added.

### 2. remove()

**Definition:**

- `remove()` removes a specified element from a set.
- If the element does not exist, Python raises a `KeyError`.

### Syntax

```python
set_name.remove(element)
```

### Example

```python
numbers = {1, 2, 3, 4}

numbers.remove(2)

print(numbers)
```

**Output:**

```text
{1, 3, 4}
```

The value 2 is removed from the set.

---

## 21. Membership Checking in Sets

### Definition

- Membership checking determines whether an element is present in a set.
- Python uses the `in` operator to check membership.
- It returns a Boolean result: `True` or `False`.

### Example

```python
numbers = {1, 2, 3, 4}

print(2 in numbers)
print(5 in numbers)
```

**Output:**

```text
True
False
```

### Explanation

- `2 in numbers` checks whether 2 is present.
- Since 2 exists in the set, the result is `True`.
- `5 in numbers` checks whether 5 exists.
- Since 5 is absent, the result is `False`.

### Where to Use

- Checking whether a gene is present in a gene list.
- Identifying whether a sample identifier exists.
- Checking membership of unique elements.
- Comparing collections of values.

---

## 22. Why Sets Do Not Support Indexing

Sets are unordered collections and do not maintain fixed positional indices.

Therefore, indexing cannot be used to access individual elements.

### Example

```python
numbers = {1, 2, 3, 4}

print(numbers[0])
```

This produces a `TypeError` because sets do not support indexing.

**Important distinction:**

- Lists and tuples support indexing because their elements are ordered.
- Sets do not support indexing because they do not have fixed positions.

---

# PART E: COMPARISON OF DATA STRUCTURES

## 23. Difference Between Lists, Tuples, Dictionaries and Sets

| Feature | List | Tuple | Dictionary | Set |
|---|---|---|---|---|
| Syntax | `[]` | `()` | `{key: value}` | `{}` |
| Ordered | Yes | Yes | Yes | No |
| Mutable | Yes | No | Yes | Yes |
| Allows duplicates | Yes | Yes | Keys must be unique | No |
| Access method | Index | Index | Key | Membership checking |
| Main purpose | Ordered collection | Fixed collection | Key-value storage | Unique elements |

### When to Use Each Data Structure

**Lists:**
- When order matters.
- When data may change.
- When duplicate values are allowed.

**Tuples:**
- When data should not change.
- When a fixed collection of values is required.

**Dictionaries:**
- When data has labels or identifiers.
- When relationships between keys and values need to be stored.
- When fast lookup using keys is required.

**Sets:**
- When only unique elements are required.
- When duplicate values should be removed.
- When membership checking is needed.

---

## 24. Quick Revision: Important Methods

### List Methods

| Method / Function | Purpose |
|---|---|
| `append()` | Adds one element at the end |
| `insert()` | Adds an element at a specified position |
| `extend()` | Adds multiple elements |
| `remove()` | Removes the first occurrence of a value |
| `pop()` | Removes and returns an element |
| `clear()` | Removes all elements |
| `sort()` | Sorts the list |
| `reverse()` | Reverses the list |
| `count()` | Counts occurrences of a value |
| `index()` | Finds the index of a value |
| `len()` | Returns the number of elements |

### Tuple Operations

| Operation | Purpose |
|---|---|
| Indexing | Accesses an individual element |
| Slicing | Extracts a portion of the tuple |
| `len()` | Returns the number of elements |

### Dictionary Methods

| Method | Purpose |
|---|---|
| `get()` | Retrieves a value using a key |
| `pop()` | Removes a key-value pair and returns its value |
| `keys()` | Returns all keys |
| `values()` | Returns all values |
| `items()` | Returns key-value pairs |

### Set Methods

| Method / Operator | Purpose |
|---|---|
| `add()` | Adds an element |
| `remove()` | Removes an element |
| `in` | Checks whether an element exists |

---

## 25. Important Concepts to Remember

1. What is a list?
2. What are the characteristics of lists?
3. How do you create a list?
4. What is the difference between positive and negative indexing?
5. What is the difference between indexing and slicing?
6. What is the purpose of `append()`?
7. What is the difference between `append()`, `insert()` and `extend()`?
8. What is the difference between `remove()` and `pop()`?
9. What is the purpose of `clear()`?
10. What is the difference between `sort()` and `reverse()`?
11. What is the purpose of `len()`, `count()` and `index()`?
12. What is a tuple?
13. Why are tuples called immutable?
14. What is the difference between a list and a tuple?
15. What is a dictionary?
16. What are key-value pairs?
17. How can dictionary values be accessed?
18. What is the difference between `get()` and square-bracket access?
19. How can dictionary values be added or updated?
20. What is the purpose of `pop()`, `keys()`, `values()` and `items()`?
21. How can you iterate through a dictionary?
22. What is a set?
23. Why do sets not allow duplicate values?
24. Why do sets not support indexing?
25. What is the purpose of `add()` and `remove()`?
26. What is membership checking?
27. When should lists, tuples, dictionaries and sets be used?

---

## 26. Session 3 Completion Checklist

### Lists

- [ ] Understand lists and their characteristics.
- [ ] Create lists.
- [ ] Access elements using indexing.
- [ ] Use positive and negative indexing.
- [ ] Perform slicing.
- [ ] Add elements using `append()`, `insert()` and `extend()`.
- [ ] Remove elements using `remove()`, `pop()` and `clear()`.
- [ ] Sort and reverse lists.
- [ ] Use `len()`, `count()` and `index()`.

### Tuples

- [ ] Understand tuples and their characteristics.
- [ ] Create tuples.
- [ ] Access elements using indexing.
- [ ] Understand immutability.
- [ ] Differentiate between lists and tuples.

### Dictionaries

- [ ] Understand key-value pairs.
- [ ] Create dictionaries.
- [ ] Access values using keys.
- [ ] Use `get()`.
- [ ] Add and update values.
- [ ] Remove entries using `pop()`.
- [ ] Retrieve keys, values and items.
- [ ] Iterate through dictionaries.

### Sets

- [ ] Understand sets and their characteristics.
- [ ] Create sets.
- [ ] Understand duplicate removal.
- [ ] Add elements using `add()`.
- [ ] Remove elements using `remove()`.
- [ ] Perform membership checking.
- [ ] Understand why sets do not support indexing.

---

**End of Session 3: Core Data Structures**