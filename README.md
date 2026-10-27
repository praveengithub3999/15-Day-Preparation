# 15-Day-Preparation
A 15-day preparation journey focused on strengthening Python programming skills, practicing coding problems, revising core concepts, and improving problem-solving abilities through consistent daily practice.

# 15-Day Preparation – Day 1 Assignment
Name: Bellamkonda Praveen Kumar
Date: 26/10/2026
Day: 1

## 1. Coding Problem: First Non-Repeating Character

### Approach:
1. Removing all spaces from the input string.
2. Use a dictionary to count the frequency of each character.
3. Traverse the string again in its original order.
4. Return the first character whose frequency is 1.
5. If no such character exists, return `"No non-repeating character found"`.

The solution is case-sensitive, so uppercase and lowercase letters are treated as different characters.

### Code:

def first_non_repeating(text):

    text = text.replace(" ", "")
    
    freq = {}
    
    for char in text:
        freq[char] = freq.get(char, 0) + 1
        
    for char in text:
        if freq[char] == 1:
            return char
            
    return "No non-repeating character found"

print(first_non_repeating("programming"))
print(first_non_repeating("aabbcdd"))
print(first_non_repeating("aabbcc"))
print(first_non_repeating(""))
print(first_non_repeating("a A"))

### Test Inputs and Outputs

| Input | Expected output |
| "programming" | p |
| "aabbcdd" | c |
| "aabbcc"| No non-repeating character found |
| "" | No non-repeating character found|
| "a A" | a |

### Time and Space Complexity

**Time complexity:** O(n), because the string is traversed twice.
**Extra space complexity:** O(k), where k is the number of distinct non-space characters stored in the dictionary.

## 2. Concept Question: List, Tuple, Set and Dictionary

| Data structure | Ordered? | Mutable? | Allows duplicates? | Example use |
|---|---|---|---|---|
| List | Yes | Yes | Yes | Storing a list of student names |
| Tuple | Yes | No | Yes | Storing fixed coordinates |
| Set | No guaranteed order | Yes | No | Storing unique student IDs |
| Dictionary | Insertion order preserved | Yes | Keys must be unique | Storing student profile fields |

### Scenario 1: Unique Student IDs

**Answer:** I would use a set because it stores only unique values. If the same student ID is added more than once, the set keeps only one copy.

student_ids = {101, 102, 103, 101}
print(student_ids)

Output:{101, 102, 103}

### Scenario 2: Student Profile Fields

**Answer:** I would use a dictionary because it stores data as key-value pairs. Each field, such as name, age, and student ID, can be accessed using its key.

student = {
    "name": "Anil",
    "age": 21,
    "student_id": 101
}

print(student["name"])
print(student["age"])
print(student["student_id"])

#Output:
Anil
21
101

## 3. Debugging Challenge: Student Search

### Issue
The original code prints `"Student not found"` inside the loop's `else` block. Therefore, it prints the message for every student whose name is not `"Kiran"`, even when Kiran appears later in the list.

### Incorrect Code:

students = ["Ravi", "Anil", "Kiran", "Suresh"]

for i in range(len(students)):
    if students[i] == "Kiran":
        print("Student found:", students[i])
    else:
        print("Student not found")

### Fixed Code

students = ["Ravi", "Anil", "Kiran", "Suresh"]

for student in students:
    if student == "Kiran":
        print("Student found:", student)
        break
else:
    print("Student not found")

### Output when Kiran exists

Student found: Kiran

### Output when Kiran does not exist

For example, if the list is ["Ravi", "Anil", "Suresh"]:

Student not found

### Explanation
The `break` statement stops the loop once Kiran is found. In Python, the `else` block associated with a `for` loop executes only when the loop finishes normally without encountering `break`. Therefore, the program prints exactly one correct message.

I also avoided `range(len(students))` because directly iterating over the student names is simpler and more readable.



# 15-Day Preparation — Day 2 Assignment

**Name:** Bellamkonda Praveen Kumar 
**Date:** 27/10/2026  
**Day:** 2

## 1. Duplicate-Removal Problem

### Approach

1. Create an empty set named `seen` to track elements already encountered.
2. Create an empty list named `result` to store unique elements in their original order.
3. Traverse the input list one element at a time.
4. If an element is not in `seen`, add it to both `seen` and `result`.
5. Return `result` after processing all elements.

This approach preserves the order of first occurrence and does not use a one-line shortcut.

### Code

def unique_in_order(items):
    seen = set()
    result = []

    for item in items:
        if item not in seen:
            seen.add(item)
            result.append(item)

    return result


print(unique_in_order([]))
print(unique_in_order([5]))
print(unique_in_order([2, 2, 2]))
print(unique_in_order([3, 1, 3, 2, 1]))
print(unique_in_order(["apple", "banana", "apple"]))
print(unique_in_order([1, 2, 3, 4]))

### Test Inputs and Outputs

| Input | Expected output |
|---|---|
| `[]` | `[]` |
| `[5]` | `[5]` |
| `[2, 2, 2]` | `[2]` |
| `[3, 1, 3, 2, 1]` | `[3, 1, 2]` |
| `["apple", "banana", "apple"]` | `["apple", "banana"]` |
| `[1, 2, 3, 4]` | `[1, 2, 3, 4]` |

### Time and Space Complexity

- **Time complexity:** O(n) on average, where n is the number of elements in the input list.
- **Extra space complexity:** O(n), because the set and result list may store up to n elements.


## 2. Sliding-Window Problem: Maximum Sum of a Contiguous Window

### Approach

1. Validate that `k` is greater than zero and does not exceed the length of the list.
2. Calculate the sum of the first `k` elements.
3. Store this sum as the initial maximum sum.
4. Move the window one position at a time by subtracting the element leaving the window and adding the new element entering it.
5. Update the maximum whenever a larger window sum is found.
6. Return the maximum sum.

The sliding-window technique avoids recalculating the sum of every window from scratch.

### Code

def max_window_sum(numbers, k):
    if k <= 0 or k > len(numbers):
        raise ValueError("k must be between 1 and the list length")

    window_sum = sum(numbers[:k])
    max_sum = window_sum

    for i in range(k, len(numbers)):
        window_sum = window_sum - numbers[i - k] + numbers[i]

        if window_sum > max_sum:
            max_sum = window_sum

    return max_sum


print(max_window_sum([2, 1, 5, 1, 3, 2], 3))
print(max_window_sum([1, 2, 3, 4, 5], 2))
print(max_window_sum([-2, -1, -5], 2))
print(max_window_sum([10], 1))

### Test Inputs and Outputs

| Input | Expected output |
|---|---|
| `max_window_sum([2, 1, 5, 1, 3, 2], 3)` | `9` |
| `max_window_sum([1, 2, 3, 4, 5], 2)` | `9` |
| `max_window_sum([-2, -1, -5], 2)` | `-3` |
| `max_window_sum([10], 1)` | `10` |
| `max_window_sum([], 1)` | Raises `ValueError` |
| `max_window_sum([1, 2, 3], 0)` | Raises `ValueError` |
| `max_window_sum([1, 2, 3], 4)` | Raises `ValueError` |

### Edge Cases

- Empty list: raises `ValueError`.
- `k = 0`: raises `ValueError`.
- `k` greater than the list length: raises `ValueError`.
- A list containing one element with `k = 1`: returns that element.
- Negative numbers: works correctly because the maximum is initialized using the first window's sum rather than zero.

### Time and Space Complexity

- **Time complexity:** O(n), because each element is processed at most once after the initial window calculation.
- **Extra space complexity:** O(1), because only a fixed number of variables are used, excluding the input list.

## 3. Debugging Challenge: Incorrect “Not Found” Message

### Issue

The original program prints `"Not found"` for every number that does not match the target. If the target exists later in the list, the program can print both `"Not found"` and `"Found"`.

### Incorrect Code

numbers = [4, 8, 12]
target = 7

for number in numbers:
    if number == target:
        print("Found")
    else:
        print("Not found")

### Fixed Code

numbers = [4, 8, 12]
target = 7

for number in numbers:
    if number == target:
        print("Found")
        break
else:
    print("Not found")


### Output

Not found

If `target = 8`, the output is:

Found


### Explanation

The original `else` belongs to the `if` statement inside the loop. Therefore, it executes for every number that does not match the target.

In the corrected program, the `else` belongs to the `for` loop. Python executes this `else` only if the loop finishes without encountering `break`.

When the target is found, `break` stops the loop and prevents the `"Not found"` message from appearing. Thus, the program prints exactly one correct result.

## 4. Data-Structure Comparison: List, Set, and Dictionary

| Feature | List | Set | Dictionary |
|---|---|---|---|
| Order | Preserves insertion order | No guaranteed iteration order | Preserves insertion order of keys |
| Duplicates | Allowed | Duplicate elements are not allowed | Keys must be unique; values can repeat |
| Membership | `x in list` | `x in set` | `x in dict` checks keys |
| Typical membership time | O(n) | O(1) average | O(1) average for keys |
| Common use | Ordered collections | Unique values | Key-value data |

### Realistic Backend Examples

**1. List — Storing expense records**

A backend API can return a list of expenses in chronological order.

expenses = [
    {"category": "Food", "amount": 250},
    {"category": "Travel", "amount": 500},
    {"category": "Food", "amount": 150}
]

print(expenses)


A list is useful here because it preserves the records' order and allows repeated categories.

**2. Set — Tracking unique student IDs**

A backend service can use a set to track unique IDs during data validation.

student_ids = {101, 102, 103, 101}

print(student_ids)
print(102 in student_ids)

The repeated ID `101` is stored only once.

**3. Dictionary — Storing a student profile**

A backend API can represent a student's details as key-value pairs.

student = {
    "id": 101,
    "name": "Anil",
    "course": "Python"
}

print(student["name"])
print(student["course"])

A dictionary is suitable because each field can be accessed directly through its key.

## 5. What I Learned:

I learned how to remove duplicate elements from a list while preserving their first-seen order using a set and a list. I also learned how the sliding-window technique efficiently calculates the maximum sum of a contiguous subarray of size `k`. Additionally, I understood how Python's `for/else` construct and `break` statement help correct loop-related debugging errors. I practised choosing appropriate data structures for different backend programming tasks.

## 6. What I Found Difficult:

Initially, I found it difficult to understand how to preserve the original order while removing duplicates. I also needed practice understanding how the sliding window updates its sum by removing the outgoing element and adding the incoming element. Debugging the `"Not found"` message helped me understand the difference between an `if/else` block and a `for/else` block.
