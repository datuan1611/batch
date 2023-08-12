BATCH CODE
https://ss64.com/nt/
https://youtube.com/playlist?list=PLCHXYO09JUKlwRyiUvNFKu6i99r8hcArb

#1. echo, cls, tag, pause
title <title name of cmd window>
rem <content of comment>
::<content of comment>
@echo off
	-> hide cmd "echo off" with "@" 
	-> hide every prompt with "echo off"
echo <string>
	-> print string on cmd screen
pause
	-> pause until enter any key
timeout /t <number of seconds>
	-> timeout in number of seconds
:<name of label>
goto <name of label>
	-> goto position of label
goto :eof
	-> goto end of script -> exit
call [drive:][path]filename [parameters]
call :label [parameters]
call internal_cmd
	-> at the end of the subroutine, an EXIT /B will return to the position where you used CALL
call :<name of label>
	-> call a subroutine (:label)
cls
	-> clear cmd screen
color <character:0->9 or A->F>
	-> change color of text in cmd screen
color /?
	-> check color value by below command in cmd window

#2. set variable
set <name of variable 01>=<number 01>
set /a <name of variable 02>=<number 02>
	-> define a variable
set /p <name of variable 03>="Input number:"
	-> input variable from keyboard
echo %<name of variable>%
	-> use value of variable in cmd echo

#3. create a file
echo <string AAA> > <filename01.txt>
	-> ">" create new file/ overwrite exist file with content <string AAA>
echo <string BBB> >> <filename01.txt>
	-> ">>" insert content <string BBB> into exist file <filename01.txt>

#4. create file to creat/check password
if [/i] [not] <condition> (command) else (command)
	-> if: cmd to check condition, and decide actione after that
	-> if not: perform if condition is false
	-> ==: compare equal
	-> compare operator:
		EQU : equal
		NEQ : not equal
		LSS : less than <
		LEQ : less than or equal <=
		GTR : greater than >
		GEQ : greater than or equal >=
	-> test if string is null
		if not define %string% (command)
		if define %string% (command)
	-> test if file/folder is exist
		if exist <filename> (command)
	-> pipe: if condition is true, command_01 run, and its output will be piped to command_02
		if <condition> (command_01 | command_02)
	-> AND condition
		if condition_01 (
			if condition_02 (
				command_AAA
			)
		)
	-> OR condition
		if condition_01 (command_AAA)
		if condition_02 (command_AAA)

for /f "delims=" %%a in (<filename.txt>) do (
	<do anything>
)
	-> for: start a for loop to read from beginning to the end of a file
	-> "delims": if read a character, stop
	-> /f: handle to file
	-> %%a: temporary variable to save value that is read in file
	-> in: in a file

syntax-FOR-Files
	FOR %%parameter IN (set) DO command
syntax-FOR-Files-Rooted at Path
	FOR /R [[drive:]path] %%parameter IN (set) DO command
syntax-FOR-Folders
	FOR /D %%parameter IN (folder_set) DO command
syntax-FOR-List of numbers
	FOR /L %%parameter IN (start,step,end) DO command
syntax-FOR-File contents
	FOR /F ["options"] %%parameter IN (filenameset) DO command
	FOR /F ["options"] %%parameter IN ("Text string to process") DO command
syntax-FOR-Command Results
	FOR /F ["options"] %%parameter IN ('command to process') DO command

#5. copy, move, rename a file

copy [option] source_01 [+ source_02] destination

copy C:\src.txt C:\dest.txt
	-> copy content from file src.txt to file dest.txt

copy C:\src01.txt + C:\src02.txt C:\combine.txt
	-> combine file src01.txt, src02.txt to combine.txt

xcopy C:\src.txt C:\dest.txt
	-> copy file with prompt to overwrite or not

xcopy /y C:\src.txt C:\dest.txt
xcopy /n C:\src.txt C:\dest.txt
	-> copy file with default overwrite [Yes] or not [No]

move C:\src.txt D:
	-> move file src.txt from folder C: to D:

move C:\src.txt C:\new.txt
	-> rename file src.txt to new.txt

del C:\*.txt
	-> delete all TXT file in folder C: