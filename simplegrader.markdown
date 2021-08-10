---
layout: page
title: Simple Grader
permalink: /projects/simplegrader
parent: Projects
nav_order: 2
---
# Simple Grader
## Github
[github.com/jamesw98/simple-grader](http://github.com/jamesw98/simple-grader)
## Purpose
This is the proof of concept program that eventually lead to VT [GradingTools](/projects/gradingtools).
## Description
I wrote this to be tool that could be used to grade any type of coding assignment, in essentially any language in any format (single file, zip, tar, etc). It is kind of rough around the edges, and definitely a work in progress, since my focus turned to GradingTools and an internship. It uses essentially the same tools and logic as GradingTools, but without Canvas integration. The biggest difference between GradingTools and SimpleGrader is that SimpleGrader can be set up with multiple "tests" to be run on each student submission, instead of just running one large test. My GitHub has a wiki if you want to read more about it, but below are some examples of the JSON info files, commands to run the tool, and output  
### Examples and Output
JSON info file for a Haskell coding assignment with randomized input and a reference solution:
```json
{
    "language": "haskell",
    "stdout": false,
    "student_output": "output.txt",
    "generator_info": {
        "generator": "forth_generator.py",
        "generator_args": ["input.txt"], 
        "reference_solution": "p2_ref"
    },
    "tests": {
        "test_basic": {
            "input_filename": "input.txt",
            "expected_output_filename": "output_ref.txt",
            "points": 250,
            "points_off_per_wrong_line": 10,
            "max_points_off": 250
        }
    }
}
```
Here is how to run the grader on a group of submissions (only working way at the moment):
```
./grader.py <json file name> -d <dir to grade>
```
Here is some output for a a submission that fails some tests, but passes one:
```
Tests to be run:
0. test_basic
   Points: 40
   Input File: test.txt
1. test_ryan
   Points: 90
   Input File: test_2.txt
2. test_gman
   Points: 90
   Input File: test_3.txt

========== Running test: test_basic ==========

No errors! Congratulations!

Your score: 40/40
Your percent: 100.0%

========== Running test: test_ryan ==========

FATAL: Your program crashed or didn't compile! No points earned!
Command '['./student_exe', 'test_2.txt']' died with <Signals.SIGSEGV: 11>.

========== Running test: test_gman ==========

FATAL: Your program crashed or didn't compile! No points earned!
Command '['./student_exe', 'test_3.txt']' died with <Signals.SIGSEGV: 11>.

========== Results of All Tests ==========

Your score 40/220
Your percent 18.18%
```