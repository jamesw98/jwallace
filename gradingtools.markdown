---
layout: page
title: GradingTools
permalink: /projects/gradingtools
parent: Projects
nav_order: 1
---

# GradingTools
## Purpose
GradingTools is a Python program written for Virginia Tech for grading student coding assignments for the courses, [CS3304](https://cs.vt.edu/Undergraduate/courses/CS3304.html) and [CS2505](https://courses.cs.vt.edu/~cs2505/) for professor David McPherson. This tool was actively used for both of these classes during the two summer 2021 semesters. Since it is used for Virginia Tech, I cannot link the code here, but I have a similar proof of is listed on this site.
## Description
The program reads info from a JSON info file that the instructor writes that provides all the necessary info used for grading, such as Canvas course ID, what language the project uses, files relevant for a reference solution, etc. (below is an example of a JSON file used for CS2505)  
The program will then download all new or updated submissions from Canvas and grade them based on the info provided. It then updates the grade in Canvas for each student and attaches a file for feedback.  
This is an on going project, I am always trying to improve it and make it support different types of assignments.   
### Examples and Output
Here is an example of the JSON info file used for CS2505 C05:
```json 
{
    "assignment_id": <ID>,
    "external_grading": true,
    "timeout": 20,
    "build_step_command": ["cmake", "."],
    "compile_step_command": ["make"],
    "run_step_command": ["./Rectangles", "input.txt", "results.txt"],
    "student_filename": "Intersection.c",
    "required_files": [
        "CMakeLists.txt",
        "driver.c", 
        "Intersection.h", 
        "checkAnswer.o", 
        "checkAnswer.h", 
        "Generator.o", 
        "Generator.h"
    ],
    "file_with_grade": "results.txt",
    "files_to_upload": ["results.txt"],
    "total_points": 600
}
```
Here is the command used for running the grader on C03:
```
./gradingtools.py c03_grades/ c03.json
```  
and the output from this command:
```
Downloading submission for Test-Student...
Grading Test-Student's submission... [600/600]

Uploading feedback for Test-Student...
Finished!
Grades have been updated in Canvas and feedback has been uploaded

              Check /home/ugrads/nonmajors/jamesw98/gradingtools/c03_grades/results.csv for grades

Stats:
New/Updated Submissions:         1
Total Submissions:               1
Average Score (for new/updated): 2000.0/2000
```
