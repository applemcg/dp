
NAME
====

+ dp -- Dot Prof
 		
SYNOPSIS
========

+ source dp_app -- loads the DP functions
+ dp -- 
  + on first use in a directory: installs a **.prof** in the current directory
  + subsequent: sources the .prof, executing user-defined commands in the file
+ dp _subfunction_ see the list of options

DESCRIPTION
===========

Manage and execute a **.prof** file.

A developer's  main use is editing shell functions into the .prof file and
test them with commands later in the file.  See the companion **Workflow** paper

OPTIONS
=======
The abstract table, produced by the *dp abstracts* command:

    name        	abstract
    ----        	--------
    dp          	do Dot Prof
    dp abstracts	write the Table for DP function ABSTRACTS
    dp all      	all the functions in the DP family
    dp diff     	diff LIB and .prof versions of functions
    dp example  	dotprof usage examples
    dp funs     	list all function and their Dot Prof file
    dp init     	bring along its utillib
    dp install  	move the run-time components into place
    dp profs    	list the active Dot-Profs
    dp root     	the development, think ~/src/... directory for source control
    dp test     	home for DP testing, "it's shaping up in the FALSE block
    dp tolibrary	write dot prof functions to their primary directory
    dp utilities	functions used by dplib functions
    dp version  	print the version


FILES
=====

* **dplib** -- the function library of the DP family of functions
* **dp_app** -- the DP application, sourced to load the functionality, containing
   all the supporting (and otherwised undocumented) functions

COMPONENTS
==========

Routinely used 
--------------

### dp 

The most used command. Part of a iterative developement cycle

    dp
	.. user inspects results
	.. updates, adds dot prof functions, test execution code
	dp 
	....
	
### dp profs

When there are more than one directory with a .prof, list the directories
with .profs .

With mulitple function librairies, a given function may, but rarely should
be updated in more than one .prof.

### dp funs

Used with dp profs, lists each function in the directories with .prof files
	
EXAMPLES
========

### dp example

    dp_example () 
    { 
        : dotprof usage examples;
        : date: 2022-08-19;
        foreach dp_funs $(dp_profs) 1>&2;
        echo . . . .;
        foreach dp_funs $(dp_profs) | field 2 | sort -u;
        echo . . . .;
        declare -f $(myname)
    }

INSTALL
=======

* clone DP from github
* pull dp
* *optional* export DP_ROOT=/pick/a/source/directory
* source bin/dp\_app


AUTHOR
======

Marty McGowan: martymcgowan AT mit DOT alum DOT edu

SEE ALSO
========

* The Only Backup You'll Ever Need:
   http://mcgowans.org/pubs/marty3/commonplace/software/backupfunction.html


