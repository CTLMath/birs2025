# Strategies for Implementation

We will explore different systems of varying complexity to share, collect, grade and return computational documents. The simplest workflow involves Syzygy, a learning management system (LMS) and manual grading. We will also describe a workflow involving Syzygy, LMS, nbgrader and LMS API to manage, autograde and upload grades and feedback for thousands of students.

## File exchanges without extra tools

You will need to plan out how to deliver notebooks to students, how the students will work in the notebooks, how you will grade their notebooks, and how the students will view the feedback on their notebooks.

### 1. Posting the notebook
The easiest place to post the notebook is wherever you usually post files for students, probably your LMS or course website. The notebooks can be posted and accessed like any other file, but instructions for the students on how to use this new file type is helpful. Along with the notebook file, you may wish to include:

* Instructions on how to open the .ipynb file (ex. download from here and then upload to Syzygy)
* Instructions for how to complete the activity in the notebook
* Instructions for submitting their completed notebook
* General resources for help with Python, Jupyter notebooks, Syzygy, etc.
* More specific resources for help with this particular activity
* Where to go for additional support (ex. office hours, drop-in tutoring)
* Any relevant dates

### 2. Students complete the notebook
Once students have access to the notebook, they will need to work on it either locally on their own machine or a web-based platform for Jupyter notebooks. We recommend Syzygy. Here are two sample workflows for students: 

**Working locally:**
* Students download the blank notebook from LMS to their computer
* Students open the blank notebook in the Jupyter notebook interface (or other local editor)
* Students complete the notebook and save the file
* Students upload the complete notebook to LMS submission page

**Syzygy:**
* Students download the blank notebook from LMS to their computer
* Students upload the blank notebook to Syzygy
* Students complete the notebook and save the file in Syzygy
* Students download the notebook to their computer
* Students upload the complete notebook to LMS submission page

### 3. Notebook grading and feedback
There are two main options for delivering feedback to students: putting feedback directly in their notebook and using whatever feedback options exist for your LMS. These two options can be mixed, although it should be made clear to students where they need to look to find all of their feedback. The final grade for the notebook (if it is graded) will need to be recorded somewhere other than the notebook (eg. LMS or grade spreadsheet). Without batch downloading and uploading, you will need to download and grade, then potentially re-upload, each student's notebook one at a time. The method(s) you choose for feedback delivery will guide your grading workflow, so we will discuss potential grading workflows as well.

#### 3.1 Feedback within the notebook
Feedback in the notebook can exist in code cells or markdown cells. Including any feedback in the notebook itself means re-uploading the notebook for each student as part of the grading process.

**Code cells:** 

Feedback in code cells are tests to check if an answer has a correct value or has some desired properties. You can use the `assert` function to print a custom message if a test doesn't pass. See the examples page for examples of assignments with tests that use this function.

Here are some other useful functions for a few test types:

* Check if the answer is the right data type:
    * `callable`: check if an answer is a callable function.
    * `isinstance`: check if an answer matches a given data type, eg. `np.ndarray`, `bool`.
* Check if the answer has the right properties, eg. matches an initial condition.
    * `np.allclose`: check if an answer takes on the correct values.
    * `__.shape`: check the dimensions of an array/matrix. 
    * `len`: check length of an array.

Without automated grading, you will need to copy-paste in tests from your solutions file to each notebook by hand as you grade them. You may also wish to include some tests in the notebook that is given to students so they can get feedback as they work.

**Markdown cells:**

Feedback in markdown cells is very freeform and can look however you want, including rendering mathematical expressions using Tex. Here is where you can type in customized feedback for each student. You may also want to keep track of common comments in your solutions file so you can copy-paste some comments in for efficiency.

#### 3.2 Feedback in LMS grading tools

Depending on the grading tool you use, there are some options for feedback within your LMS. Rubrics, comment boxes and annotations can all be useful tools for delivering feedback to students that they can see without downloading any additional files or leaving the LMS. Grading the notebooks using this method will mean working in at least two windows/tabs simultaneously: running the student's notebook in one window, potentially pasting in tests to the notebook from another window, and entering their feedback in the grading tool in another window. However, if you do not include any feedback in the notebook, you will not need to re-upload the notebook as part of the grading process.

**Rubrics:**

* For each problem, list the tests and marks associated with it
* You can include aspects of good coding practice that you want to highlight (ex. used a particular function, included comments, etc)
* Check off passed/failed tests and any other rubric items as you go

**Comment boxes:**

* Similar to markdown cells (described above)
* Write in any comments in the comments box of the grading tool:
    * Free form customized feedback
    * Paste in commonly used comments
    * Paste in any tests that failed

**Annotations:**

If your grading tool allows annotating a pdf or html file and viewing it within the LMS without downloading an additional file, then you may wish to ask students to upload a pdf/html version of their notebook (as well as the .ipynb file). Writing or putting annotations directly on their work can be a more efficient way to give feedback on specific aspects of their work. If you want to run the notebook, you will still need to download the .ipynb file. 

## Using nbgrader and Canvas API

*Under construction*