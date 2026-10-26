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
