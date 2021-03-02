# Linux-Shell-scripting-quick-notes

- # **if condition**

if condition which is used for decision making in shell script, If given condition is true then command1 is executed.

	if condition
	then
		command1 if condition is true or if exit status
		of condition is 0 (Zero)
	fi..
    
    
- # **test command or [ expr ]**

test command or [ expr ] is used to see if an expression is true, and if it is true it return zero(0), otherwise returns nonzero for false.

Syntax:
test expression OR [ expression ]


### **NOTE: == is equal, != is not equal.**

-eq = is equal to. 

-ne = is not equal to.

-lt = is less than.

-le = is less than or equal to.

-gt = greater than

-ge = is greater than or equal to.


string1 = string2 = string1 is equal to string2

string != string2 = string1 is NOT equal to string2

string1           = string1 is NOT NULL or not defined 

-n string1        = string1 is NOT NULL and does exist

-z string1        = string1 is NULL and does exist


! expression      = Logical NOT

expression1 -a expression2 = Logical AND

expression1 -o expression2 = Logical OR



- # **if...else...fi**

If given condition is true then command1 is executed otherwise command2 is executed.

Syntax:

	if condition
    then
    	condition is zero (true - 0)
        execute all commands upto else statement
	else
    	if condition is not true then
        execute all commands upto fi
  	fi
    

- # **Nested if-else-fi**

You can write the entire if-else construct within either the body of the if statement of the body of an else statement. This is called the nesting of ifs.


Note that Second if-else constuct is nested in the first else statement. If the condition in the first if statement is false the the condition in the second if statement is checked. If it is false as well the final else statement is executed.

Syntax:

	if condition
		then
			if condition
		then
			.....
			..
			do this
		else
			....
			..
			do this
	fi
		else
			...
			.....
			do this
	fi

- # **Multilevel if-then-else**

Syntax:

	if condition
	then
		condition is zero (true - 0)
		execute all commands up to elif statement
	elif condition1
	then
		condition1 is zero (true - 0)
		execute all commands up to elif statement
	elif condition2
	then
		condition2 is zero (true - 0)
		execute all commands up to elif statement
	else
		None of the above condtion,condtion1,condtion2 are true (i.e.
		all of the above nonzero or false)
		execute all commands up to fi
	fi
   
### **for Loop**


	for { variable name } in { list }
	do
		execute one for each item in the list until the list is
		not finished (And repeat all statement between do and done)
	done
    
    

### **while loop**

Loop is executed as long as given condition is true.

Syntax:

	while [ condition ]
	do
		command1
		command2
		command3
		..
		....
	done
    
    
### **The case Statement**

The case statement is good alternative to Multilevel if-then-else-fi statement. It enable you to match several values against one variable. Its easier to read and write.

Syntax:
	case $variable-name in
		pattern1) command
					...
					..
					command;;
		pattern2) command
					...
					..
					command;;
		patternN) command
					...
					..
					command;;
		*) command
					...
					..
					command;;
		esac
        
        
The $variable-name is compared against the patterns until a match is found. The shell then executes all the statements up to the two semicolons that are next to each other. The default is *) and its executed if no match is found.   




### **Conditional execution i.e. && and ||**

The control operators are && (read as AND) and || (read as OR). The syntax for AND list is as follows

Syntax:

	command1 && command2

command2 is executed if, and only if, command1 returns an exit status of zero.

The syntax for OR list as follows

Syntax:

	command1 || command2

command2 is executed if and only if command1 returns a non-zero exit status.

You can use both as follows
Syntax:

- command1 && comamnd2 if exist status is zero || command3 if exit status is non-zero

if command1 is executed successfully then shell will run command2 and if command1 is not successful then command3 is executed.



### **Functions**

Syntax:

	function-name ( )
	{
		command1
		command2
		.....
		...
		commandN
		return
	}	
    
Where function-name is name of you function, that executes series of commands. A return statement will terminate the function. 

Example:

Type SayHello() at $ prompt as follows

	$ SayHello()
	{
	echo "Hello $LOGNAME, Have nice computing"
	return
	}

To execute this SayHello() function just type it name as follows:

	$ SayHello

	Hello ec2-user, Have nice computing.
    
This way you can call function. Note that after restarting your computer you will loss this 

SayHello()

function, since its created for current session only. To overcome this problem and to add you own
function to automate some of the day today life task, add your function to /etc/bashrc file. To add function to this file you must logon as root. Following is the sample /etc/bashrc file with today() function, which is used to print formatted date. First logon as root or if you already logon with your name (your login is not root), and want to move to root account, then you can type following command , when asked for password type root (administrators) password.




**Cut Utility**

General Syntax of cut utility:

	cut -f{field number} {file-name}


Use of Cut utility: Selecting portion of a file.



**Paste Utility**

General Syntax of paste utility:

	paste {file1} {file2}

Use of paste utility: Putting lines together.


**Join Utility**

Syntax:
	
    join {file1} {file2}
    
Use of join utility: The join utility joins, lines from separate files.


**tr utility**

Syntax:

	tr {pattern-1} {pattern-2}
    
Use of tr utility: To translate range of characters into other range of characters.


**Data manipulation using awk utility**

General Syntax of awk utility:

	awk pattern action {file-name}
    

**sed utility - Editing file without using editor**

Syntax:

 	sed {expression} {file}
    
    
Use of sed utility: sed is used to edit (text transformation) on given stream i.e a file or may be input from a pipeline.


**Removing duplicate lines using uniq utility**

General Syntax of uniq utility:

	uniq {file-name}
    


**Finding matching pattern using grep utility**

Syntax:

	grep word-to-find {file-name}
    
    
Grep will locate all the words mentioned in the syntax


**Getting started with ex**

You can start the ex editor by typeing ex at shell prompt:

Syntax:

	ex {file-name}
    
Example:

	$ ex demofile


**Printing text on-screen**

First open the our demofile as follows:

	ex demofile
    

Entering Ex mode. Type "visual" to go to Normal mode.

Now type 'p' in front of : as follow and press enter
    
    
- NOTE By default p command will print current line, in our case its the last line of above text file.

- Now if you want to print 1st line to next 5 line (i.e. 1 to 5 lines) then give command
	
    :1,5 p
    
NOTE Here 1,5 is the address. if single number is used (e.g. 5 p) it indicate line number and if two numbers are separated by comma its range of line.

- Printing particular line

To print 2nd line from our file give command
	
    :2 p

- Printing entire file on-screen

	`:1,$ p`
    
NOTE Here 1 is 1st line and $ is the special character of ex which mean last-line character. So 1,$ means print from 1st line to last-line character (i.e. end of file). Here p stands print.

- Printing line number with our text

	`:set number`
	`:1,3 p`


NOTE This command prints number next to each line. If you don't want number you can turn off
numbers by issuing following command

	:set nonumber
	:1,3 p
    
**Deleting lines**

Give command
	
    :1, d
    

NOTE Here 1 is 1st line and d command indicates deletes (Which deletes the 1st line).

You can even delete range of line by giving command as

	:1,5 d

**Copying lines**

Give command as follows
	
    :1,4 co $
	:1,$ p
    
    
NOTE Here 1,4 means copy 1 to 4 lines; co command stands for copy; $ is end of file. So it mean copy first four line to end of file. You can delete this line as follows
	
    :18,21 d    


**Searching the words**

(a) Give following command
	
    :/linux/ p
    
Note In ex you can specify address (line) using number for various operation. This is useful if you know the line number in advance, but if you don't know line number, then you can use contextual address to print line on-screen. In above example /linux/ is contextual address which is constructed by surrounding a regular expression with two slashes. And p is print command of ex.

**Quitting the ex**

Give command
	
    :q


**Find and Replace (Substituting regular expression)**

Give command as follows
	
    :8 p
    
  :8 s/lerarns/learn/ 
	
    :p

![Screen Shot 2021-03-02 at 9.16.33 AM.png]({{site.baseurl}}/Screen Shot 2021-03-02 at 9.16.33 AM.png)


Note Using above command, you are substituting the word "currently" to "now"

Above command can be explained as follows:

- 3 - go to line 3 
- s - substitute
- currently - Target pattern
- now - If target found replace with now.


![Screen Shot 2021-03-02 at 9.20.09 AM.png]({{site.baseurl}}/Screen Shot 2021-03-02 at 9.20.09 AM.png)


Using above command, you are substituting all lines i.e. s command will find all of the address line for the pattern "Linux" and if pattern "Linux" found substitute pattern "Unix".    

- :1,$ - Substitute for all line
- s - substitute
- /Linux - target pattern
- Unix - Substitute to the target.