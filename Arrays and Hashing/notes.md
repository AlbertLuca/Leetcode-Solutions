## Set()
A built-in function used to create a set. A set is an unordered collection of unique elements, meaning that is does not allow duplicate values.
Sets are useful when you need to store and operate on unique items without caring about their order. 

You can create a set:
my_set = ([1,2,3,4])
my_set = {1, 2, 3, 4}

# Properties of a Set
- Unordered: The elements in a set are not stored in any particular order
- Unique: A set cannot contain duplicate elements

# Common Set Operations
1. Adding Elements: 
my_set.add(5)

2. Removing elements:
my_set.remove(3)

3. Set Union:
Combines elements from two sets, removing duplicates:
set1 = {1, 2, 3}
set2 = {3, 4, 5}

union_set = set1._union(set2)

4. Set intersection:
Returns elements that are common in both sets.
intersection_Set = set1.intersection(set2)

print(intersection_set)

output: 
{3}

5. Set difference:
Returns elements that are in one set but not in the other
difference_set = set1.difference(set2)

print(difference_set)
{1,2}

6. Set symmetric Difference:
Returns elements that are in either set but not in both
sym_diff_set = set1.symmetric_difference(set2)

print(sym_diff_set)

output: 
{1,2,4,5}

# When to use sets
- Removing duplicates: if you have a list with duplicates and you need a collection with unique
elements, a set is ideal

- Membership tests: Sets are optimized for checking if an elements is part of the set (`O(1)` time complexity)

- Set operations: For mathematical operations like union, intersection, amd difference, sets provide built-in methods



# Are sets hash tables?
Yes, sets in Python are implemented using hash tables, which is why they have some of the characteristics associated with hash tables, such as:

- **Fast Lookups:** Elements in a set can be checked for membership (e.g., `x in my_set`) in average constant time, `O(1)`, due to the underlying hash table.
  
- **Unique Elements:** Each element in a set must be unique, which is enforced by the hash table. If you try to add a duplicate element, it will simply overwrite the existing entry.

- **Unordered Collection:** Sets do not maintain any order of elements because the underlying hash table does not store elements in a sorted manner. The order in which elements are stored in a hash table is determined by the hash function and is generally non-deterministic.

### How Hash Tables Work in Sets

A hash table is a data structure that stores key-value pairs, but in the case of sets, it stores only keys (the values are implicit). When you add an element to a set:

1. **Hashing:** The element is passed through a hash function, which converts it into a fixed-size integer value known as a hash code.
   
2. **Indexing:** This hash code is then used as an index to place the element in the hash table. If two different elements produce the same hash code (a collision), Python handles this using techniques like open addressing or chaining.

3. **Uniqueness Check:** If the hash code already exists in the table (meaning the element is already in the set), the new element will not be added, ensuring uniqueness.

### Example

Here's an example that shows how sets leverage hashing:

```python
my_set = {"apple", "banana", "cherry"}
print("banana" in my_set)  # This check is very fast because of the hash table.
```

In this example, checking whether `"banana"` is in `my_set` is efficient due to the hash table's ability to quickly locate the element based on its hash code.

### Comparison with Hash Tables (Dictionaries)

While sets are implemented using hash tables, they are simpler than dictionaries (which are also hash-table-based) because:

- **Sets store only keys, not key-value pairs.**
- **Dictionaries use hash tables to map keys to values**, allowing for fast lookups, insertions, and deletions.

So, to summarize: sets in Python **are** based on hash tables, which explains their efficiency and their constraints like uniqueness and lack of order.

# Sort()
The `sort()` method is used to sort the elements of list in place, meaning it modifies the original list. The sorting is done in ascening order by default,
but you can customize it with optional parameters


In Python, the sort() method is used to sort the elements of a list in place, meaning it modifies the original list. The sorting is done in ascending order by default, but you can customize it with optional parameters.

## Basic Usage
Here’s an example of sorting a list of numbers:

numbers = [3, 1, 4, 1, 5, 9, 2, 6]
numbers.sort()
print(numbers)

Output:

[1, 1, 2, 3, 4, 5, 6, 9]

## Sorting in Descending Order
To sort a list in descending order, use `reverse` parameter:

numbers = [3, 1, 4, 1, 5, 9, 2, 6]
numbers.sort(reverse=True)
print(numbers)

Output:

[9, 6, 5, 4, 3, 2, 1, 1]

## Sorting with a Custom Key
You can customize the sort order by providing a key function. This function is applied to each element in the list before comparison.

For example, to sort a list of strings by their length:

words = ["apple", "banana", "cherry", "date"]
words.sort(key=len)
print(words)

Output:
['date', 'apple', 'banana', 'cherry']

## Important points:
In-Place Sorting: The sort() method modifies the original list. If you need a new sorted list and want to keep the original list unchanged, use the sorted() function instead, which returns a new sorted list.

original_list = [3, 1, 4, 1, 5, 9, 2, 6]
sorted_list = sorted(original_list)
print(sorted_list)  # [1, 1, 2, 3, 4, 5, 6, 9]
print(original_list)  # [3, 1, 4, 1, 5, 9, 2, 6]

Stability: Python's sort() is stable, meaning that when two records have the same key, their original order is preserved.

Time Complexity: Python's sort() uses Timsort, which has a time complexity of O(n log n) in the average and worst case.

Summary of Parameters
reverse: If True, the list elements are sorted as if each comparison were reversed (descending order).
key: A function that serves as a key for the sort comparison.