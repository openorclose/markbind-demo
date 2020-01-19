# Project Duke

<div class="lead">

<pic add-class="float-left border mr-2 mt-2 p1 bg-white" src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/5d/Duke_%28Java_mascot%29_waving.svg/226px-Duke_%28Java_mascot%29_waving.svg.png" width="60">

<small><small>**Duke**, the Java Mascot<br>[[credit: Wikipedia](https://en.wikipedia.org/wiki/File:Duke_(Java_mascot)_waving.svg)]</small></small>
</pic>

**Project Duke is a educational software project designed to take you through the steps of building a small software _incrementally_**, while applying as many Java and SE techniques as possible along the way.
</div>

**The project aims to build a product named _Duke_, a Personal Assistant Chatbot that helps a person to keep track of various things.** %%The name _Duke_ was chosen as a placeholder name, in honor of [Duke, the Java Mascot](https://www.oracle.com/java/duke.html).%% **You may give it any other name or personality you wish.**

Here is a sample interaction with Duke:
```
    ____________________________________________________________
      ____        _        
     |  _ \ _   _| | _____ 
     | | | | | | | |/ / _ \
     | |_| | |_| |   <  __/
     |____/ \__,_|_|\_\___|

     Hello! I'm Duke
     What can I do for you?
    ____________________________________________________________

list
    ____________________________________________________________
     Here are the tasks in your list:
     1.[T][✓] read book
     2.[D][✗] return book (by: June 6th)
     3.[E][✗] project meeting (at: Aug 6th 2-4pm)
     4.[T][✓] join sports club
    ____________________________________________________________

todo borrow book
    ____________________________________________________________
     Got it. I've added this task: 
       [T][✗] borrow book
     Now you have 5 tasks in the list.
    ____________________________________________________________


deadline return book /by Sunday
    ____________________________________________________________
     Got it. I've added this task: 
       [D][✗] return book (by: Sunday)
     Now you have 6 tasks in the list.
    ____________________________________________________________

done 2
    ____________________________________________________________
     Nice! I've marked this task as done: 
       [D][✓] return book (by: June 6th)
    ____________________________________________________________

blah
    ____________________________________________________________
     ☹ OOPS!!! I'm sorry, but I don't know what that means :-(
    ____________________________________________________________

bye
    ____________________________________________________________
     Bye. Hope to see you again soon!
    ____________________________________________________________

```
<div id="increments_summary">

The project consists of the following _increments_:
* **Levels**: A series of features, meant to be added to Duke in the given order, although some can be skipped. These have been named `Level 1` to `Level 10` to indicate how the features make the product progressively "level up".
* **Extensions:**
  * <big><span class="badge badge-pill badge-primary">Category A</span></big> These are internal/feature enhancements meant to help you practice a specific Java or an SE technique.  
  * <big><span class="badge badge-pill badge-info">Category B</span></big> These are enhancements related to task tracking.
  * <big><span class="badge badge-pill badge-success">Category C</span></big> These are enhancements, not specifically related to task tracking.
  * <big><span class="badge badge-pill badge-danger">Category D</span></big> Each of these adds the ability to track another type of entities.
</div>
</div>

## <div class="text-white bg-dark p-1">Levels</div>

<div id="level1">

<thumbnail text=":fas-comments:" font-color="white" add-class="float-left bg-dark mr-2 mt-2" size="80"/>

### Level 1. Greet, Echo, Exit

In this initial _skeletal_ version of Duke, it starts by greeting the user, simply  echos commands entered by the user, and exits when the user types `bye`.
<br>
Example:
```
    ____________________________________________________________
     Hello! I'm Duke
     What can I do for you?
    ____________________________________________________________

list
    ____________________________________________________________
     list
    ____________________________________________________________

blah
    ____________________________________________________________
     blah
    ____________________________________________________________

bye
    ____________________________________________________________
     Bye. Hope to see you again soon!
    ____________________________________________________________

```
* The indentation and horizontal lines are optional.

</div><hr><!-- ================================================================================================ -->
<div id="level2">

<thumbnail text=":fas-list:" font-color="white" add-class="float-left bg-dark mr-2 mt-2" size="80"/>

### Level 2. Add, List

Add the ability to store whatever text entered by the user and display them back to the user when requested.

Example:
```
    ____________________________________________________________
     Hello! I'm Duke
     What can I do for you?
    ____________________________________________________________

read book
    ____________________________________________________________
     added: read book
    ____________________________________________________________

return book
    ____________________________________________________________
     added: return book
    ____________________________________________________________

list
    ____________________________________________________________
     1. read book
     2. return book
    ____________________________________________________________
bye
    ____________________________________________________________
     Bye. Hope to see you again soon!
    ____________________________________________________________

```

* There is no need to save the data to the hard disk.
* Assume there will be no more than 100 tasks. If you wish, you may use a fixed size array (e.g., `String[100]`) to store the items.
</div><hr><!-- ================================================================================================ -->
<div id="level3">

<thumbnail text=":fas-check:" font-color="white" add-class="float-left bg-dark mr-2 mt-2" size="80"/>

### Level 3. Mark as Done

Add the ability to mark tasks as _done_.<br><br>

```
list
    ____________________________________________________________
     Here are the tasks in your list:
     1.[✓] read book
     2.[✗] return book
     3.[✗] buy bread
    ____________________________________________________________

done 2
    ____________________________________________________________
     Nice! I've marked this task as done: 
       [✓] return book
    ____________________________________________________________
```

{{ icon_tip | safe }} When implementing this feature, you are also recommended to implement the following extension as collections classes (e.g., `ArrayList`) have methods to easily delete an item at a specified location:

<panel header="**Extension: `A-Classes`**">

### <span class="badge badge-pill badge-primary">A-Classes</span>
{{ indented_arrow | safe }} **Use a class to represent tasks**</span>

While it is possible to represent a task list as a multi-dimensional array containing <tooltip content="`String`, `int`, `boolean` etc.">primitive values</tooltip>, the more natural approach is to use a `Task` class to represent tasks.

<panel type="seamless" header="Partial solution" minimized>

```java
public class Task {
    protected String description;
    protected boolean isDone;

    public Task(String description) {
        this.description = description;
        this.isDone = false;
    }

    public String getStatusIcon() {
        return (isDone ? "\u2713" : "\u2718"); //return tick or X symbols
    }

    //...
}
```

```java
Task t = new Taks("read book");
t.markAsDone()
```
</panel>
</panel>

</div><hr><!-- ================================================================================================ -->
<div id="level4">

<thumbnail text=":fas-business-time:" font-color="white" add-class="float-left bg-dark mr-2 mt-2" size="80"/>

### Level 4. ToDos, Events, Deadlines

Add support for tracking three types of tasks:
<br>
<br>

1. **ToDos**: tasks without any date/time attached to it %%e.g., _visit new theme park_%%
2. **Deadlines**: tasks that need to be done before a specific date/time %%e.g., _submit report by 11/10/2019 5pm_%%
3. **Events**: tasks that start at a specific time and ends at a specific time %%e.g., _team project meeting on 2/10/2019 2-4pm_%%

Example:
```
todo borrow book
    ____________________________________________________________
     Got it. I've added this task: 
       [T][✗] borrow book
     Now you have 5 tasks in the list.
    ____________________________________________________________

list
    ____________________________________________________________
     Here are the tasks in your list:
     1.[T][✓] read book
     2.[D][✗] return book (by: June 6th)
     3.[E][✗] project meeting (at: Aug 6th 2-4pm)
     4.[T][✓] join sports club
     5.[T][✗] borrow book
    ____________________________________________________________

deadline return book /by Sunday
    ____________________________________________________________
     Got it. I've added this task: 
       [D][✗] return book (by: Sunday)
     Now you have 6 tasks in the list.
    ____________________________________________________________

event project meeting /at Mon 2-4pm
    ____________________________________________________________
     Got it. I've added this task: 
       [E][✗] project meeting (at: Mon 2-4pm)
     Now you have 7 tasks in the list.
    ____________________________________________________________
```

At this point, dates/times can be treated as strings; there is no need to convert them to actual dates/times.

Example:
```

deadline do homework /by no idea :-p
    ____________________________________________________________
     Got it. I've added this task: 
       [D][✗] do homework (by: no idea :-p)
     Now you have 6 tasks in the list.
    ____________________________________________________________
```

{{ icon_tip | safe }} When implementing this feature, you are also recommended to implement the following extension as collections classes (e.g., `ArrayList`) have methods to easily delete an item at a specified location:

<panel header="**Extension: `A-Inheritance`**">

### <span class="badge badge-pill badge-primary">A-Inheritance</span>
{{ indented_arrow | safe }} **Use Inheritance to support multiple task types**</span>

As there are multiple types of tasks that have some similarity between them, you can implement classes `Todo`, `Deadline` and `Event` classes to inherit from a `Task` class.

Furthermore, use polymorphism to store all tasks in a data structure containing `Task` objects e.g., `Task[100]`.

<panel type="seamless" header="Partial solution" minimized>

```java
public class Deadline extends Task {

    protected String by;

    public Deadline(String description, String by) {
        super(description);
        this.by = by;
    }

    @Override
    public String toString() {
        return "[D]" + super.toString() + " (by: " + by + ")";
    }
}
```

```java
Task[] tasks = new Task[100];
task[0] = new Deadline("return book", "Monday");
```

</panel>

</panel>

</div><hr><!-- ================================================================================================ -->
<div id="level5">

<thumbnail text=":fas-exclamation-triangle:" font-color="white" add-class="float-left bg-dark mr-2 mt-2" size="80"/>

### Level 5. Handle Errors

Teach Duke to deal with errors such as incorrect inputs entered by the user.
<br>
<br>

Example:
```
todo
    ____________________________________________________________
     ☹ OOPS!!! The description of a todo cannot be empty.
    ____________________________________________________________

blah
    ____________________________________________________________
     ☹ OOPS!!! I'm sorry, but I don't know what that means :-(
    ____________________________________________________________
```

{{ icon_tip | safe }} When implementing this feature, you are also recommended to implement the following extension as collections classes (e.g., `ArrayList`) have methods to easily delete an item at a specified location:

<panel header="**Extension: `A-Exceptions`**">

### <span class="badge badge-pill badge-primary">A-Exceptions</span>
{{ indented_arrow | safe }} **Use Exceptions to handle errors**</span>

Use exceptions to handle errors. For example, define a class `DukeException` to represent exceptions specific to Duke.

</panel>

* **Minimal**: handle at least the two types of errors shown in the example above.
* **Stretch goal**: handle all possible errors in the current version. As you evolve Duke, continue to handle errors related to the new features added. 

</div><hr><!-- ================================================================================================ -->
<div id="level6">

<thumbnail text=":fas-trash-alt:" font-color="white" add-class="float-left bg-dark mr-2 mt-2" size="80"/>

### Level 6. Delete

Add support for deleting tasks from the list.
<br>
<br>

Example:
```
list
    ____________________________________________________________
     Here are the tasks in your list:
     1.[T][✓] read book
     2.[D][✓] return book (by: June 6th)
     3.[E][✗] project meeting (at: Aug 6th 2-4pm)
     4.[T][✓] join sports club
     5.[T][✗] borrow book
    ____________________________________________________________

delete 3
    ____________________________________________________________
     Noted. I've removed this task: 
       [E][✗] project meeting (at: Aug 6th 2-4pm)
     Now you have 4 tasks in the list.
    ____________________________________________________________
```

{{ icon_tip | safe }} When implementing this feature, you are also recommended to implement the following extension as collections classes (e.g., `ArrayList`) have methods to easily delete an item at a specified location:

<panel header="**Extension: `A-Collections`**">

<variable name="extStyle">primary</variable>

### <span class="badge badge-pill badge-{{ extStyle }}">A-Collections</span>
{{ indented_arrow | safe }} **Use Java Collections classes**</span>

Use Java Collections classes for storing data. For example, you can use an `ArrayList<Task>` to store the tasks.

</panel>

</div><hr><!-- ================================================================================================ -->
<div id="level7">

<thumbnail text=":fas-save:" font-color="white" add-class="float-left bg-dark mr-2 mt-2" size="80"/>

### Level 7. Save

Save the tasks in the hard disk automatically whenever the task list changes. Load the data from the hard disk whe Duke starts up. You may hard-code the file name and location %%e.g., `[project_root]/data/duke.txt`%%

The format of the file is up to you. Example:
```
T | 1 | read book
D | 0 | return book | June 6th
E | 0 | project meeting | Aug 6th 2-4pm
T | 1 | join sports club
```

</div><hr><!-- ================================================================================================ -->
<div id="level8">

<thumbnail text=":fas-clock:" font-color="white" add-class="float-left bg-dark mr-2 mt-2" size="80"/>


### Level 8. Dates and Times

Teach Duke to understand dates and times. For example, if the command is `deadline return book /by 2/12/2019 1800`, Duke understands `2/12/2019 1800` as _2nd of December 2019, 6pm_, instead of storing it simply as a String.

* **Minimal**: Store deadline dates as a `java.time.LocalDate` in your task objects. Accept dates in a format such as `yyyy-mm-dd` format (e.g., `2019-10-15`)  and print in a different format such as `MMM d yyyy` e.g., (`Oct 15 2019`).
* **Stretch goal**: Use dates and times in more meaningful ways. e.g., add a command to print deadlines/events occurring on a specific date. 

<panel header="Using dates/times in Java" minimized >

A code snippet using the `LocalDate` class:
```java
import java.time.LocalDate;
import java.time.format.DateTimeFormatter;
import java.time.temporal.ChronoUnit;

public class Main {
    public static void main(String[] args) {
        //create dates from strings
        LocalDate d1 = LocalDate.parse("2019-12-01");
        LocalDate d2 = LocalDate.parse("2019-12-02");
        LocalDate d3 = LocalDate.parse("2019-12-02");
        
        //compare dates
        System.out.println(d1.isBefore(d2)); // -> true
        System.out.println(d1.isAfter(d2)); // -> false
        System.out.println(d2.equals(d3)); // -> true
        
        //work with dates
        System.out.println(d1.getDayOfWeek()); // -> SUNDAY
        System.out.println(d1.getMonth()); // -> DECEMBER
        System.out.println(d1.plus(1, ChronoUnit.YEARS));  // -> 2020-12-01
        
        // get today's date and print it in a specific format
        LocalDate d4 = LocalDate.now();
        System.out.println(d4); // -> 2019-10-15
        System.out.println(d4.format(DateTimeFormatter.ofPattern("MMM d yyyy"))); // -> Oct 15 2019
    }
}
```

* [A tutorial from https://www.baeldung.com/](https://www.baeldung.com/java-8-date-time-intro)
</panel>

</div><hr><!-- ================================================================================================ -->
<div id="level9">

<thumbnail text=":fas-search:" font-color="white" add-class="float-left bg-dark mr-2 mt-2" size="80"/>

### Level 9. Find

Give users a way to find a task by searching for a keyword.
<br>
<br>

Example:
```
find book
    ____________________________________________________________
     Here are the matching tasks in your list:
     1.[T][✓] read book
     2.[D][✓] return book (by: June 6th)
    ____________________________________________________________
```

</div><hr><!-- ================================================================================================ -->
