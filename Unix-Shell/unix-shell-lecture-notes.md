## Introduction

Instructor notes for the [Unix shell lesson of the Software Carpentry](http://swcarpentry.github.io/shell-novice/). These lecture notes were used as a reference for teaching Unix Shell in the [Software Carpentry workshop at TU Delft](https://4turesearchdata-carpentries.github.io/2021-04-06-Delft/) on April 6th 2021 held in an online format. 

The teaching style in these lecture notes has been derived from the [Software Carpentry](https://software-carpentry.org/). The lecture notes make use of the [Unix Shell lesson material of software carpentry](http://swcarpentry.github.io/shell-novice/) distributed under the [CC By 4.0 license](https://creativecommons.org/licenses/by/4.0/).


## Program

[13:30 PM - 13:40 PM] Introducing the Shell <br/>
[13:40 PM - 14:00 PM] Navigating files and directories <br/>
[14:00 PM - 14:20 PM] Working with files and directories <br/>
[14:20 PM - 14:35 PM] Coffee break <br/>
[14:35 PM - 14:37 PM] Breakout room exercise briefing <br/>
[14:37 PM - 15:57 PM] Exercises in breakout rooms <br/>
[14:57 PM - 15:20 PM] Pipes and filters <br/>
[15:20 PM - 15:35 PM] Shell script part 1 <br/>
[15:35 PM - 15:50 PM] Coffee break <br/>
[15:50 PM - 16:15 PM] Shell script part 2 + for loops <br/>
[16:15 PM - 16:17 PM] Breakout session 2 exercise briefing <br/>
[16:17 PM - 16:40 PM] Exercises in breakout rooms <br/>
[16:40 PM - 16:45 PM] Buffer for covering exercise solutions in the main room <br/> 
[16:45 PM - 16:48 PM] Summary and pointers on where to go from here? <br/>
[16:48 PM - 17:00 PM] Feedback from the learners + Q&A <br/>

The lesson is delivered mainly as a type along with the learners. Slides are used only to facilitate the lesson introduction and as an aid to explain the key concepts using figures. There are dedicated helpers to assist the learners in the breakout rooms
during the exercise session and answer their questions on the chat in the main room. You can learn more about the role of a helper in this workshop in [this document](https://doi.org/10.5281/zenodo.4730727).

### Introducing the Shell [10 min]

#### Part 1: Introduction from the slides [5 min] 

- What is Unix shell and why should I use it?
- Go through the learning goals for the workshop

#### Part 2: Launch the shell together with the learners [5 min]

- After telling the learners how to launch the shell, the instructor sets up command history as per the instructions borrowed from the [command history set up documentation
provided by the 4TUResearchData](https://github.com/4TUResearchData-Carpentries/documentation/blob/master/command-history.md). The explanation of this terminal history is not part of the lesson.

On the main terminal
```
export PROMPT_COMMAND="history -a;$PROMPT_COMMAND"
```
On a new terminal where the history will be recorded.
```
tail -f ~/.bash_history
```
- Briefly tell the first view of the shell window, tell what does the `$` sign mean, mention the terminologies - command line, terminal, shell

- There are Windows as well as Mac users. The idea is to get them to the home directory when they launch the shell. For windows users using git bash this is possible if we ask them to launch git bash from the start menu. 
For mac users - ask the learners to launch the terminal from the search bar by typing terminal. Default shell is zsh

- Backup: In case learners are not in the home directory to start with, ask them to execute `cd` or `cd ~`. Explain the meaning of the commands in the respective section later. 


### Navigating files and directories [20 min]


#### Intro [1 min]

- How can I move around on my computer? 
- How can I see what files and directories I have?
- How can I specify the location of a file or directory on my computer?


#### pwd [2 min]

- Prints working directory
- Typealong - execute pwd on the terminal, explain the output by explaining the file system in Unix using the diagram in the slides.


#### ls [5 min]

- Lists files in the current directory.

- Explain the general syntax of a shell command using an example. The below piece of text from the Software carpentry lesson material is a good reference. 
 
```
ls -F / 
```
*ls is the command, with an option -F and an argument /. Options change the behaviour of a command, arguments tell the command what to operate on (e.g. files and directories). A command can be called with more than one option and more than one argument: but a command doesn’t always require an argument or an option.*

- **Note**: `ls` and `ls -F` show the same output for Windows users. 

- **Note**: General syntax of shell command is an important concept. Make sure to go over this concept each time when typing a command or reading a command, go over how a command is formed using multiple options and arguments.

-Use `--help` option to find the usage information of a shell command

- Typealong: List the contents of the data shell directory on Desktop
```
ls -F Desktop/data-shell
```
**Remark**: The files can be accessed in a hierarchical way (refer to the file system diagram in the slides). It is not possible to jump the path and go to a different folder. 



#### cd [10 min]

- Changes working directory
- Use `..` to go to the parent directory. 
- `ls -a` shows `..` and `.`
- `.` means the current directory, its usage will be discussed later in the lesson.
- Each file and folder on the PC is addressed via either absolute or relative path.

- Typealong: Go back to the home directory using `cd` without an argument and then we try to move to the `data` folder inside the `data- shell` directory with one command. This is a relative path. You can go to any other folder also if you specify the path of the folder from the root of the file system.


### Working with files and directories [20 min]

#### Intro [1 min]

- How can I create, copy, and delete files and directories?
- How can I edit files?
 
**Note**: The idea to keep in mind while introducing a command is to try and convince the learners that doing operations on the command line is efficient and faster than GUI. 


#### mkdir [2 min]

- Creates a new empty directory in the current directory. 
```
mkdir <new-directory>
```
- Also possible to create nested directories. 
```
mkdir -p data/data-nested
```

#### nano [1 min]

- Basic text editor for writing/editing files.
- Use `Ctrl+O` to save the file  `Ctrl+X` to exit the text editor.

#### mv [5 min]

- mv is short for move, moves files and directories from one location to another. Same as cut and paste operation.
- Also works on directories
- Give an example of using `mv` with multiple files 

#### cp [5 min]

- Short for copy. Copies files and directories from one location to another. Similar to copy and paste operation.
- use `-r` flag for copying directories
```
cp -r <dir> <path>
```
- When copying multiple files, the last argument must be the destination.
```
cp <file1>, <file2> <file3> <path>
```

#### rm [1 min]

- (permanently) deletes file and directories.
- use the `-r` flag for deleting directories.


#### Wildcards [5 min]

- used to filter out multiple files at once
- `*` matches zero or more characters
- `?` matches exactly one character
- What happens when the shell sees a wildcard? - it expands it at the command line to see the matching files
- Use case (1/2) - copying/moving bunch of files in one go
- Use case (2/2) - Filtering not possible with GUI


********* **Coffee break at 14:20 PM** ************


### Break out session 1 briefing [2 min]

Give a brief overview of the exercises and how the learners must approach them.

### Exercises in breakout rooms [20 min]

Four exercises from the Software Carpenty's Unix shell lesson material are chosen.

- Exercise 1: [Relative Path resolution](https://swcarpentry.github.io/shell-novice/02-filedir/index.html#relative-path-resolution)
- Exercise 2: [List filenames matching a pattern](https://swcarpentry.github.io/shell-novice/03-create/index.html#list-filenames-matching-a-pattern)
- Exercise 3: [Organizing Directories and Files](https://swcarpentry.github.io/shell-novice/03-create/index.html#organizing-directories-and-files)
- Exercise 4: [Reproduce a folder structure](https://swcarpentry.github.io/shell-novice/03-create/index.html#reproduce-a-folder-structure)


### Pipes and Filters [25 min]

### Intro
How can I combine existing commands to do new things?

#### Note for instructor on the teaching flow
- Introduce the commands individually - wc, >, sort, head, tail, etc.
- Summarize what we did in the last 5 mins - “we saw some commands that can help filter and arrange content in the files. You noticed that we made use of a file as a placeholder to capture the output of one command then used that file as an input for another command. But we can get rid of these intermediate files and be more efficient. Let's see how...”
- Show one example on the terminal for each of the below commands.

#### wc [2 min]

Counts the no. of words in the file and outputs on the console window

#### cat [1 min]

- Prints the contents of a file on the console window
- Used as sneak peak, can fill your entire screen with the content
- Use `less` if you want to see less output

#### sort [2 min]

- Sorts the output in alphanumeric order
- Add `-n` option to sort the content in numerical order

#### > (redirect) [1 min]

- Redirects the output to a file
- Creates the file if it doesn’t exist

#### >> [1 min]

Appends to a file

#### echo [1 min]

Prints the text passed on the console window

#### head [2 min]

Prints the top 10 lines of the text
```
head -n 5 file.txt
```

#### tail [2 min]

Prints the last few lines of the text
```
tail -n file.txt
```

#### | (pipe) [10 min]

- Explain basic philosophy behind pipes
- Avoid the use of temporary files when using multiple commands together. 
- Use case - extract block of lines in between a file
```
head -n 10 file.txt | tail -n 5 file.txt
```
- Example - Putting it all together
```
wc -l *.pdb | sort -n | head -n 10 | tail -n 5
```


### Shell scripts part 1 [15 min] 

#### Intro
- How can I save and re-use commands?
- So far we have been typing commands on the console window, but now it’s time to save them in a file so that we can (re)use them later. 
- Shell script is a collection of commands saved in a file. This file has an extension of ‘.sh’
- Why use it? - make your workflow reproducible
- How does it work - Once we have saved the .sh file, we can ask the shell to execute the commands it contains. Our shell is called bash, so we run the following command
```
bash script.sh
```

#### Typealong

- Give basic example - a simple head tail command operating on a specific file, then run that script
```
head -n 10 octane.pdb | tail -n 5
```
- So we did the same thing as before but took an extra step of executing the commands from a file, we did not see a great benefit here. However, we will shortly see the benefits.

- Advantage of scripts (1/3): make script versatile to operate on multiple files.
Replace octane.pdb with a special variable `$1`

- Advantage of scripts (2/3): make script versatile to change its functionality via command line arguments.

Example: Replace 10 and 5 with variables that are populated by command line arguments.
```
head -n $2 $1 | tail -n $3
```
**Note**: make sure to pass the arguments in the correct order as you specified in the script. 



****************** **Coffee break (15:35 - 15:50 PM)** *********************


### Shell scripts part 2 + for loops [25 min]

#### Intro

How can I perform the same actions on many different files?

#### For loops

- Explain the for loop operation using the diagram in slides. 
- The below text from Software Carpentry's Unix Shell lesson is a good reference for explaining the for loop

*When the shell sees the keyword for, it knows to repeat a command (or group of commands) once for each item in a list. Each time the loop runs (called an iteration), an item in the list is assigned in sequence to the variable, and the commands inside the loop are executed, before moving on to the next item in the list. Inside the loop, we call for the variable’s value by putting $ in front of it. The $ tells the shell interpreter to treat the variable as a variable name and substitute its value in its place, rather than treat it as text or an external command.
In this example, the list is three filenames: basilisk.dat, minotaur.dat, and unicorn.dat. Each time the loop iterates, it will assign a file name to the variable filename and run the head command. The first time through the loop, $filename is basilisk.dat. The interpreter runs the command head on basilisk.dat and pipes the first two lines to the tail command, which then prints the second line of basilisk.dat. For the second iteration, $filename becomes minotaur.dat. This time, the shell runs head on minotaur.dat and pipes the first two lines to the tail command, which then prints the second line of minotaur.dat. For the third iteration, $filename becomes unicorn.dat, so the shell runs the head command on that file, and tail on the output of that. Since the list was only three items, the shell exits the for loop.*


- Advantage of scripts (3/3): Reproducible workflow - add comments explaining your script for the **future you** and others


Examples to cover:

- For loop to echo files
```
for filename in *.pdb
do      echo $filename
done
```

- For loop to do head tail operation. Print the filename on which the operation is being done so that you have an idea


### Breakout session 2 exercise briefing [1 min] 

The objective of the 2 exercises in this breakout session is to learn how to read someone else’s shell script and understand what it is doing, something that you will come across often, and then practice writing one of your own. You may or may not use these exact scripts in your work but the idea is to get you some hands-on experience with reading and writing shell scripts which is a handy skill to have!

### Exercise in Breakout room [20 min]

- Exercise 1: [Variables in Shell Scripts](https://swcarpentry.github.io/shell-novice/06-script/index.html#variables-in-shell-scripts)

- Exercise 2: [Find the longest file file with a given extension](https://swcarpentry.github.io/shell-novice/06-script/index.html#find-the-longest-file-with-a-given-extension)

### Summary and pointers on where to go from here? [3 min]

- Summary from slides
- Seeking help on the internet

### Feedback from learners and Q&A [12 min]

********************************* The End ************************************************

