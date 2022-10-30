---
layout: page
title: User Guide
---
{:toc}

## Introduction

### About GREWZ
Tired of opening multiple applications for your teaching needs? Look no further!

GREWZ is your all-in-one **address book desktop application designed for university teaching assistants** to manage their personal homework and their students. It manages attendance of your students, organises your contacts and keeps track of your own homework!

GREWZ boasts a timeless, compartmentalised Graphical User Interface(GUI) while utilising a clean Command Line Interface(CLI) - this means that the faster you can type, the faster you can get your work done.

Hopefully our application has grown on you! 

### Navigation
The aim of this User Guide is to provide you with all the information needed to fully utilise GREWZ. We understand the steep difficulty curve when learning Command Line Interface (CLI) programs and have tried our best to ease you in. 

If you need help setting up GREWZ, jump over to [Quick start](#quick-start) to continue.

If you want to find out more about GREWZ features and commands, jump over to [Features](#features).

If you want the quick overview of GREWZ commands, jump over to [Command Summary](#command-summary)

Take note of the following symbols and formatting used in this document:


--------------------------------------------------------------------------------------------------------------------

## Quick start

1. Ensure you have Java `11` or above installed in your Computer.

2. Download the latest `GREWZ.jar` from [here](https://github.com/AY2223S1-CS2103T-W12-4/tp/releases).

3. Copy the file to the folder you want to use as the _home folder_ for your GREWZ.

4. Double-click the file to start the app. The GUI similar to the below should appear in a few seconds. Note how the app contains some sample data.<br>
   ![Ui](images/Ui.png)

5. Type the command in the command box and press Enter to execute it. e.g. typing **`help`** and pressing Enter will open the help window.<br>
   Some example commands you can try:

   * **`list`** : Lists all students.

   * **`add`**`n/student p/98765432 i/e0778123 [e/student@example.com] [p/91251211]` : Adds a student named `John Doe` to the student list.

   * **`delete`**`3` : Deletes the 3rd student shown in the current list.

   * **`clear`** : Deletes all students.

   * **`exit`** : Exits the app.

1. Refer to the [Features](#features) below for details of each command.

--------------------------------------------------------------------------------------------------------------------

## Features

<div markdown="block" class="alert alert-info">

**:information_source: Notes about the command format:**<br>

* Words in `UPPER_CASE` are the parameters to be supplied by the user.<br>
  e.g. in `add n/NAME`, `NAME` is a parameter which can be used as `add n/John Doe`.

* Items in square brackets are optional.<br>
  e.g `n/NAME [t/TAG]` can be used as `n/John Doe t/friend` or as `n/John Doe`.

* Items with `…`​ after them can be used multiple times including zero times.<br>
  e.g. `[t/TAG]…​` can be used as ` ` (i.e. 0 times), `t/friend`, `t/friend t/family` etc.

* Parameters can be in any order.<br>
  e.g. if the command specifies `n/NAME p/PHONE_NUMBER`, `p/PHONE_NUMBER n/NAME` is also acceptable.

* If a parameter is expected only once in the command but you specified it multiple times, only the last occurrence of the parameter will be taken.<br>
  e.g. if you specify `p/12341234 p/56785678`, only `p/56785678` will be taken.

* Extraneous parameters for commands that do not take in parameters (such as `help`, `list`, `exit` and `clear`) will be ignored.<br>
  e.g. if the command specifies `help 123`, it will be interpreted as `help`.

</div>

### Viewing help : `help`

Shows a message explaning how to access the help page.

![help message](images/helpMessage.png)

Format: `help`

### Exiting the program : `exit`

Exits the program.

Format: `exit`

# Student Contact Commands
---


### Adding a student: `add`

Adds a student to the class list.

Format: `add n/NAME i/STUDENT_ID [p/PHONE_NUMBER] [e/EMAIL] [c/CLASS_GROUP] [t/TAG]…​`


* ~~Compulsory~~ Optional Fields to Fill in (Fields in Square Bracket are Optional).
* The fields can be written in any order.
* ***Only*** Name and Student ID are a must.
* Name must only consist of alphanumeric characters.
* Student ID must take the format of e0XXXXXX where X is a digit from 0 to 9.
* A student can have any number of tags (including 0).


Examples:
* `add n/John Doe i/e0123456`
* `add n/Betsy Crowe i/e0321456 e/betsycrowe@example.com p/1234567 t/criminal`

### Listing all students : `list`

Shows a list of all students in the student list.

Format: `list`

### Adding a class field to a student: `class`

Add the class group to the specified student from the student list.

Format: `class 1 c/CLASS`

* Edits the student at the specified INDEX. The index refers to the index number shown in the displayed student list. The index must be a positive integer 1, 2, 3, …
* Existing class group will be updated to the input values.
* You can remove a student's class group by typing `c/` without specifying any value after it.

Examples:
* ```class 1 c/CS2030S Lab 32``` Edits the class group of the 1st student in the list to be CS2030S Lab 32.
* ```class 1 c/ ``` Clears the class group of the 1st student in the list.

### Uploading/ Changing student profile picture: `upload-pic`

GREWZ allows you to upload image of your students into your application. The following steps will help you upload photos of your students into the student list.

Format: `upload-pic INDEX`

* Uploads a picture for the student at the specified `INDEX`. The index refers to the index number shown in the displayed student list. The index **must be a positive integer** 1, 2, 3, …​
* A window will open to allow you to select a file from your computer. The file **must** be of .JPG format.
* If no picture exists for the student specified, the selected picture will be assigned to the student.
* Existing picture will be updated to the input file picture.

<div markdown="span" class="alert alert-warning">:information_source: **Note:**
You are recommended to select an image of dimensions ratio of about 1:1 otherwise the selected picture may not appear nicely.
</div>

### Editing student information : `edit`

Edits an existing student in the student list.

Format: `edit INDEX [n/NAME] [p/PHONE] [e/EMAIL] [c/CLASS] [i/STUDENT_ID] [t/TAG]…​`

* Edits the student at the specified `INDEX`. The index refers to the index number shown in the displayed student list. The index **must be a positive integer** 1, 2, 3, …​
* At least one of the optional fields must be provided.
* Existing values will be updated to the input values.
* When editing tags, the existing tags of the student will be removed i.e adding of tags is not cumulative.
* You can remove all the student’s tags by typing `t/` without
    specifying any tags after it.
* This command does not offer editing a student's profile picture. To do this, refer to [upload](#uploading-changing-student-profile-picture-upload-pic)

Examples:
*  `edit 1 p/91234567 e/studentEmail@example.com` Edits the phone number and email of the 1st student in the list to be `91234567` and `studentEmail@example.com` respectively.
*  `edit 2 n/Jackie Chan t/` Edits the name of the 2nd student to be `Jackie Chan` and clears all existing tags.

### Locating students by name: `find`

Finds students whose student details contain any of the given keywords.

Format: `find KEYWORD [MORE_KEYWORDS]`

* The search is case-insensitive. e.g hans will match Hans
* The order of the keywords does not matter. e.g. Hans Bo will match Bo Hans
* All fields are searched - `NAME`, `STUDENT_ID`, `PHONE`, `CLASS`, `EMAIL`.
* Partial words will also be matched e.g. Han will match Hans
* Students matching at least one keyword will be returned (i.e. OR search).
  e.g. `find Hans Bo` will return `Hans Gruber`, `Bo Yang`

Examples:
* `find Jack` returns `jack tan` and `Jack Lee`
* `find alex dav` returns `Wong Alex, David Lim`


### Deleting a student : `delete`

Deletes the specified student from the student list.

Format: `delete INDEX`

* Deletes the student at the specified `INDEX`.
* The index refers to the index number shown in the displayed student list.
* The index **must be a positive integer** 1, 2, 3, …​

Examples:
* `list` followed by `delete 2` deletes the 2nd student in the student list.
* `find Betsy` followed by `delete 1` deletes the 1st student in the results of the `find` command.

### Clearing all entries : `clear`

Clears all entries from the student list.

Format: `clear`

## Attendance commands
To aid teaching assistants in keeping track of attendance, we developed a feature to add an attendance list of a maximum of 12 lessons. Afterwards, teaching assistants can mark/unmark attendance of their students. Currently, we have only one class of attendance for students.

### Adding an attendance list to a student: `attendance add`

Adds an attendance list to a student in the contact list. 

Format: `attendance add INDEX c/CLASS s/ATTENDANCE_SIZE`

<div markdown="span" class="alert alert-primary">:bulb: **Additional information:**
Maximum attendance list size is 12, if the size is 0, the attendance list will be N.A. 
There can only be one attendance list for each student for ease of command.
</div>

Examples:
```attendance add 1 c/CS2030 s/10```
```attendance add 1 c/CS2040 s/1```

### Marking attendance of student: `attendance mark`

Marks attendance of given student in class list. In this case, we use 0 for absent and 1 for present because it is faster for CLI users to type numerical values instead of ```"absent"``` or ```"present"```.

Format: `attendance mark INDEX l/LESSON m/ATTENDANCE_VALUE`

<div markdown="span" class="alert alert-primary">:bulb: **Additional information:**
Lesson number starts from 1.
Attendance value is 0 for absent, 1 for present.
</div>

Examples:
`attendance mark 1 l/1 m/1`
`attendance mark 1 l/1 m/0`

### Deleting attendance to student: `attendance delete`

Deletes entire attendance list of student in class list

Format: `attendance delete INDEX`

Examples:
`attendance delete 1`
`attendance delete 2`

# Task Commands
---

### Adding a Task : `task`

Adds a task to the Task List.
There is two different types of Task - ***ToDo*** and ***Deadline***.

#### Adding a ToDo

Adds a ***ToDo*** (A type of Task) to the Task List.

Format: `task t/TITLE d/DESC`

* A ToDo should always include a title and description and should not be left blank.
* Both title and description should consist of only alphanumeric characters.

Examples:
* `task t/Prepare slides for studio d/Topic Environment Model`
* `task t/Collect robot d/At MakersLab`

#### Adding a Deadline

Adds a ***Deadline*** (A type of Task) to the Task List.

Format: `task t/TITLE d/DESC by/YYYY-MM-DD`

* A Deadline should always include a title, description and date and should not be left blank.
* Both title and description should consist of only alphanumeric characters.
* A date should strictly follow the format of YYYY-MM-DD.

Examples:
* `task t/Prepare slides for studio d/Topic Environment Model by/2020-12-12`
* `task t/Collect robot d/At MakersLab by/2019-09-10`

### Removing a Task

Removes a specified task from the Task List (Can be a ToDo and a Deadline).

Format: `remove-task INDEX`

* Deletes the task at the specified `INDEX`.
* The index refers to the index number shown in the displayed task list.
* The index **must be a positive integer** 1, 2, 3, …​

Examples:
* `remove-task 2` deletes the 2nd student in the task list.

### Navigating User Input History: `↑`, `↓`

Adapted from [senior](https://github.com/AY2122S2-CS2103T-W13-3/tp)

Allows user to quickly retrieve their previous inputs from current session by using the up and down arrow keys.

Format: `↑`, `↓`

### Saving the data

GREWZ data are saved in the hard disk automatically after any command that changes the data. There is no need to save manually.

### Editing the data file

GREWZ data are saved as a JSON file `[JAR file location]/data/addressbook.json`. Advanced users are welcome to update data directly by editing that data file.

<div markdown="span" class="alert alert-warning">:exclamation: **Caution:**
If your changes to the data file makes its format invalid, GREWZ will discard all data and start with an empty data file at the next run.
</div>

### Creating Assignment Tasks

Adds an ***Assignment*** (A type of Task) to the Task List.

Format: `task t/TITLE d/DESCRIPTION addStu/STUDENT_1, STUDENT_2`

* An Assignment task should always include a title, description that should not be left blank.
* The `addStu/` **MUST** be present for the task to be an assignment.
* The number of students input is zero or more, and each student is separated by a `,` comma, thus student names should not contain commas.
* Both title and description should consist of only alphanumeric characters.

Examples:
* `task t/Assignment 1 d/Description here addStu/Adam Tan, Wong Zhu Yi, Robin Hood`
* `task t/Midterm Assignment d/This is a challenging assignment addStu/Alvin, Simon, Theodore`

### Editing Tasks

Edits an existing tasks in the task list.

Format: `edit-task [t/TITLE] [d/DESCRIPTION] [deleteStu/STUDENT_1, STUDENT_2]`

* Edits the task at the specified `INDEX`. The index refers to the index number shown in the displayed task list. The index **must be a positive integer** 1, 2, 3, …​
* At least one of the optional fields must be provided.
* For task specific fields `by/`, `addStu/`, and `deleteStu/`, can only be edited if the task is of the correct type.
    * `by/` is only accepted while editing a Deadline Task. The date follows the same format as [deadline tasks](#creating-deadline-tasks).
    * `addStu/` and `deleteStu/` are only accepted while editing an Assignment Task.
    * `addStu/` adds the student names to the assignment while `deleteStu/` deletes students names if the exact name is already in the assignment task's student list.
* Existing values will be updated to the input values.

Examples:
* `edit-task 1 t/Assignment 1 d/Topics: Recursion addStu/Adam Lee, Ben Tang deleteStu/Zack Yu, Xenia Ng`
  Edits the title, description and student list of the 1st task in the task list, provided that it is an assignment task, to be `Assignment 1`, `Topics: Recursion` and `Adam Lee, Ben Tang` respectively.
* `edit-task 2 deleteStu/Jackie Chan` Edits the student list of the 2nd task in the task list to delete the name `Jackie Chan`. All other students in the student list of the task are not affected.
* `edit-task 3 t/Mark Lab Worksheets d/CS2030S by/2022-10-30` Edits the title, description and deadline of the 3rd task
  in the task list, provided that it is a deadline task, to be `Mark Lab Worksheets`, `CS2030S` and `Oct 30 2022` respectively.

--------------------------------------------------------------------------------------------------------------------

## FAQ

**Q:** Do I have to retype the command every single time even if they are similar?
<br />
**A:** You can use our [input history feature](#navigating-user-input-history--) and simply use the UP `↑` and DOWN `↓` arrow keys to  access your older commands.

**Q:** What is the difference between the different types of tasks?
<br />
**A:** All the three tasks essentially have a task title and description. What differentiate them is that a deadline task has date property where you can set its deadline and an assignment task has a student property where you can add a list of student who are yet to complete the assignment task. Lastly, the todo task doesn't have either of these fields.

**Q:** How to add a student if I do not have their student ID?
<br />
**A:** Unfortunately we need the name and student ID of the student minimally as we are using this fields to distinguish the students in the student list.

**Q:** How to add a deadline to an existing toDo task?
<br />
**A:** Remove the existing toDo task, then add the same task with your given deadline.

**Q:** How to edit an existing task?
<br />
**A:** Remove the existing task, then add the same task with the change that you want to make.

**Q:** How do I transfer my data into another computer?
<br />
**A:** Install the app in the other computer. From your current computer, transfer the "data" folder from GREWZ to your new GREWZ folder.


--------------------------------------------------------------------------------------------------------------------

## Command summary

| Action                | Format                                                                                                  | Examples                                                                                                          |
|-----------------------|-------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|
| **Add**               | `add n/NAME  i/STUDENT_ID [t/TAG] [e/EMAIL] [p/PHONE_NUMBER] [c/CLASS]…​`                                         | `add n/James Ho i/e0823115 p/22224444 e/jamesho@example.com t/friend t/colleague`                                 |
| **Attendance Add**    | `attendance add INDEX c/CLASS s/ATTENDANCE_SIZE`                                                                   | `attendance add 1 c/CS2030 s/10`                                                                                  |
| **Attendance Delete** | `attendance delete INDEX`                                                                                         | `attendance delete 1`                                                                                             |
| **Attendance Mark**   | `attendance mark INDEX l/LESSON m/ATTENDANCE_VALUE`                                                                | `attendance mark 1 l/1 m/1`                                                                                       |
| **Clear**             | `clear`                                                                                                           |                                                                                                                   |
| **Delete**            | `delete INDEX`                                                                                                    | `delete 3`                                                                                                        |
| **Edit**              | `edit INDEX [n/NAME] [i/STUDENT_ID] [p/PHONE_NUMBER] [e/EMAIL] [i/STUDENT_ID] [t/TAG]…​`                          | `edit 2 n/James Lee e/jameslee@example.com`                                                                       |
| **Find**              | `find KEYWORD [MORE_KEYWORDS]`                                                                                    | `find James Jake`                                                                                                 |
| **List**              | `list`                                                                                                            |                                                                                                                   |
| **Task**              | `task t/TITLE d/DESC [by/YYYY-MM-DD]`                                                                             | `task t/Collect robot d/At MakersLab`, `task t/Prepare slides for studio d/Topic Environment Model by/2020-12-12` |
| **Edit Task**         | `edit-task [t/TITLE] [d/DESC] [by/YYYY-MM-DD] [addStu/STUDENT_1,STUDENT_2...] [deleteStu/STUDENT_1,STUDENT_2...]` | `edit-task 1 t/Mark Lab Worksheets d/CS2030S by/2022-10-30`                                                       | 
| **Remove Task**       | `remove-task INDEX`                                                                                               | `remove-task 1`                                                                                                   |
| **Upload**            | `upload-pic INDEX`                                                                                                | `upload-pic 1`                                                                                                    |
| **Help**              | `help`                                                                                                            |                                                                                                                   |


--------------------------------------------------------------------------------------------------------------------

## Glossary


