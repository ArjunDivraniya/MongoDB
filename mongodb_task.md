
---

### **MongoDB Tasks**

#### **Task 1: Add more students to the `students` collection**  
- Add at least 5 new students to the `students` collection with unique names, roll numbers, and course enrollments.

```js 
db.students.insertMany([
  {
    name: "Priya Sharma",
    rollNumber: 106,
    courses: ["MATH101", "CS202", "ENG101"]
  },
  {
    name: "Raj Patel",
    rollNumber: 107,
    courses: ["PHYS101", "MATH101", "HIST201"]
  },
  {
    name: "Simran Kaur",
    rollNumber: 108,
    courses: ["CHEM101", "BIO201", "MATH101"]
  },
  {
    name: "Amit Verma",
    rollNumber: 109,
    courses: ["CS202", "PHYS101", "MATH101"]
  },
  {
    name: "Neha Gupta",
    rollNumber: 110,
    courses: ["ENG101", "HIST201", "ECON101"]
  }
]);

```


#### **Task 2: Insert a new course into the `courses` collection**  
- Add a new course with the following details:  
  - Course Code: `CS202`  
  - Name: `Data Structures`  
  - Credits: 3  
  - Instructor: `Prof. Krishna`

  ```
 db.courses.insertMany([
  {
    courseCode: "CS202",
    name: "Data Structures",
    credits: 3,
    instructor: "Prof. Krishna",
    semester: "Spring 2025",
    description: "This course covers fundamental data structures and their applications in computer science."
  },
  {
    courseCode: "MATH101",
    name: "Calculus I",
    credits: 4,
    instructor: "Dr. Meera Shah",
    semester: "Fall 2025",
    description: "An introductory course on calculus, focusing on limits, derivatives, and integrals."
  },
  {
    courseCode: "PHYS101",
    name: "Physics I",
    credits: 3,
    instructor: "Dr. Ravi Nair",
    semester: "Fall 2025",
    description: "Covers fundamental concepts in mechanics, thermodynamics, and waves."
  },
  {
    courseCode: "ENG101",
    name: "Introduction to Literature",
    credits: 2,
    instructor: "Prof. Anjali Desai",
    semester: "Spring 2025",
    description: "Explores key literary works and develops critical reading and writing skills."
  },
  {
    courseCode: "CS301",
    name: "Operating Systems",
    credits: 4,
    instructor: "Dr. Amit Singh",
    semester: "Winter 2025",
    description: "Introduction to operating system concepts, including process management and memory allocation."
  }
]);

```

#### **Task 3: Fetch a specific student's record by roll number**  
- Use `find()` to fetch a student's information using their roll number (`CS1002`).

```
db.students.find({ rollNumber: 106 });
```

#### **Task 4: Query all students who are enrolled in a particular course**  
- Retrieve all students who are enrolled in "MATH101".

```
db.students.find({ courses: "MATH101" });
```


#### **Task 5: Update a student's courses**  
- Update the student with roll number `CS1001` to enroll in an additional course "CS202".


```
CS1002
```

#### **Task 6: Remove a course from a student's courses list**  
- Remove the course `MATH101` from the student `Mahir`'s list of enrolled courses.

```
db.students.updateOne(
  { name:"Raj Patel" },
  { $pull: { courses: "MATH101" } }
);
```


#### **Task 7: Find all courses with 3 credits**  
- Query the `courses` collection to find all courses where the `credits` field equals 3.

```
db.courses.find({credits:3})

```


#### **Task 8: Find students who have enrolled in more than 2 courses**  
- Use `$size` operator to query students who are enrolled in more than 2 courses.

#### **Task 9: Use the `$in` operator to find students enrolled in multiple courses**  
- Use the `$in` operator to find students who are enrolled in either `CS101` or `MATH202`.

```
db.students.find(
{$or:[{courses:"PHYS101"},{courses:"MATH101"}]})
```

#### **Task 10: Fetch all students from a specific department (e.g., CSE)**  
- Use a query to find all students in the `CSE` department.

```
db.students.find({department: "CSE"})
```


#### **Task 11: Query students who are in their 3rd year**  
- Retrieve students who are in the `3rd` year using the `year` field.

```
db.students.find({year:4})
```


#### **Task 12: Query students using a range for their year**  
- Find all students who are in `2nd` or `3rd` year by using the `$gte` operator.

```
db.students.find({year:{$gte:2,$lte:3}})
```

#### **Task 13: Count the total number of students in each department**  
- Use the `$group` stage of aggregation to group students by department and count them.

```


#### **Task 14: Group courses by credits**  
- Group courses by their credit value and count how many courses there are for each credit value.

```
db.students.aggregate([
  { $match: { department: "CSE" } },
  { $group: { _id: "$year", totalStudents: { $sum: 1 } } }
]);
```


#### **Task 15: Find the highest credit course**  
- Query for the course with the highest number of credits using the `$sort` operator.

```


#### **Task 16: Use the `$and` operator for filtering students**  
- Find all students who belong to the `CSE` department and are enrolled in more than 2 courses.

```


#### **Task 17: Add a new field to all documents in the `students` collection**  
- Add a new field `activeStatus` and set it to `true` for all students.
```
db.students.updateMany({},{$push:{activestatus:"true"}})
```


#### **Task 18: Use `$rename` to rename a field**  
- Rename the `coursesEnrolled` field in the `students` collection to `enrolledCourses`.

```


#### **Task 19: Set default values for new fields in all student documents**  
- Add a field `graduationYear` with a default value for all students.

```


#### **Task 20: Use the `$push` operator to add a new course to a student’s course list**  
- Add the course "CS303" to `Mahir`’s `coursesEnrolled` list.

```
db.students.updateMany(
  {name:"Raj Patel"},
  {$push:{courses:"CS303"}})
  
  
```



#### **Task 21: Use `$pull` to remove a course from a student's courses list**  
- Remove the course `CS101` from `Jenil`’s list.

```
db.students.updateMany(
  {name:"Priya Sharma"},
  {$pull:{courses:"CS202"}})

```

#### **Task 22: Remove a student from the `students` collection**  
- Delete the student record with roll number `CS1004`.

```
db.students.deleteOne({rollNumber:108})
```


#### **Task 23: Find students who are enrolled in both `CS101` and `MATH202`**  
- Use `$all` operator to find students who are enrolled in both courses.

```
db.students.find({$and:[{courses:"MATH101"},{courses:"PHYS101"}]})
```


#### **Task 24: Use `$regex` to search for students whose name starts with "A"**  
- Use regular expressions to search for students whose names begin with the letter "A".

#### **Task 25: Use `$exists` to find students with enrolled courses**  
- Query students who have an entry in the `coursesEnrolled` array.

#### **Task 26: Add a field to store students' grades for each course**  
- Add a new field `grades` to the `students` collection and store an array of grades for each course.

```
db.students.updateMany(
  {},
  {
    $set: {
      grades: [
        { course: "CS101", grade: "A" },
        { course: "MATH101", grade: "B" },
        { course: "PHYS101", grade: "A-" }
      ]
    }
  }
);
```

#### **Task 27: Use `$elemMatch` to query students enrolled in specific courses**  
- Find students enrolled in `CS101` and have the grade `A`.

#### **Task 28: Use `$size` operator to query students with exactly 2 courses enrolled**  
- Query students who have enrolled in exactly two courses.

#### **Task 29: Perform a text search for a course title**  
- Use text indexing to search for the course `Digital Electronics` in the `courses` collection.

#### **Task 30: Create a compound index on department and year**  
- Create a compound index on the fields `department` and `year` for better querying performance.

#### **Task 31: Use `$sort` to order students by their roll number**  
- Sort the students in ascending order of their roll number.

```
db.students.find().sort({rollNumber:1})

```


#### **Task 32: Create a unique index on the roll number**  
- Create a unique index to ensure that the roll numbers in the `students` collection are unique.

#### **Task 33: Update the course name in the `courses` collection**  
- Update the name of the course `CS101` to `Intro to Programming`.

```
db.courses.updateMany({courseCode:"CS301"},
                      {$set:{courseCode:"Intro to Programming"}})

```



#### **Task 34: Create a backup of the `CodingGitaStudents` database**  
- Use `mongodump` to back up the entire `CodingGitaStudents` database.

#### **Task 35: Restore the `CodingGitaStudents` database from the backup**  
- Use `mongorestore` to restore the database after a backup.

#### **Task 36: Use `$project` to reshape data in aggregation**  
- Project only the `name` and `department` of students using an aggregation query.

#### **Task 37: Use `$unwind` to deconstruct the courses array**  
- Use `$unwind` to split the `coursesEnrolled` array into individual documents.

#### **Task 38: Use `$limit` to retrieve only the first 3 students**  
- Use `$limit` to limit the result to the first 3 students in the `students` collection.

```
db.students.find().limit(3)
```


#### **Task 39: Use `$skip` to skip the first 2 students and get the rest**  
- Use `$skip` to fetch all students except the first two.

```
db.students.find().skip(2)
```


#### **Task 40: Use `$lookup` to join student data with courses**  
- Use `$lookup` to fetch the course information for students.

#### **Task 41: Create a new collection for storing `studentFeedback`**  
- Create a collection `studentFeedback` with fields: `studentRollNumber`, `feedbackText`, `date`.

```
db.createCollection("studentsfeedback")
```

```
db.studentsfeedback.insertMany([
  {
    studentRollNumber: "CS1001",
    feedbackText: "The course content is excellent and very engaging.",
    date: "2025-01-05"
  },
  {
    studentRollNumber: "CS1002",
    feedbackText: "The assignments were challenging but helpful for understanding concepts.",
    date: "2025-01-04"
  },
  {
    studentRollNumber: "CS1003",
    feedbackText: "More practical examples would be great for better understanding.",
    date: "2025-01-06"
  },
  {
    studentRollNumber: "CS1004",
    feedbackText: "I appreciate the instructor's efforts in clarifying doubts promptly.",
    date: "2025-01-03"
  },
  {
    studentRollNumber: "CS1005",
    feedbackText: "The online resources provided were very useful for revisions.",
    date: "2025-01-02"
  }
]);
```



#### **Task 42: Query the `studentFeedback` collection to find feedback from a specific student**  
- Use `find()` to retrieve feedback from `Jenil`.

#### **Task 43: Use `$set` to update multiple fields at once**  
- Use the `$set` operator to update the `department` and `coursesEnrolled` fields for `Arjun`.

#### **Task 44: Create a custom index on the `coursesEnrolled` field**  
- Create an index on the `coursesEnrolled` array for faster querying.

#### **Task 45: Perform a query on nested documents in `students` collection**  
- Query for students who have grades `A` in their courses.

---