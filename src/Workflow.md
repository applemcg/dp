
Dot Prof Workflow
=================

Functions, *local* and non-local are entered in the .prof file, either
new, or copies of existing functions which may need to be modified..
In a source-controlled environment, the business here is to return
the all functions to their respective library, either a local one
under development or an existing library. 

Since this development uses **Semantic Versioning**, see the
accompanying **Changelog** for additional steps in the
workflow. Nothing in this workflow requires Changelog or Semantic
Versioning features. The function library and enclosing App may be
used without reference to those practices.

Format of the Dot Prof file
---------------------------

The .prof file will have four sections in the order here:

- the header, sourceing librarys
- function bodies, new and those being repaird
- a comment block in the **false && { ... }** 
- the execution steps, which may be themselves commented 

Executing the Dot Prof
----------------------

	dp   # or manually,
	source ./.prof
	
where the **dp** function also, one might say "gratuitiously" backs up a
changed .prof file.

Save .prof Functions in the Appropriate Library
-----------------------------------------------

Desination libs, local and non- are idenfied with this command which returns
function - library pairs.  A new function will not have a library name paired.

     do_whf $(fdp)
	
Identify library names, for many functions:

    do_whf $(fdp) | field 2 | sort -u # noting individual libraries

### Functions with a library

	 For any libraries with a function or more

    set -- $(do_whf $(fdp) | field 2 | sort -u)
	echo $# $*  # Number, Names
	: 
	libfuns $(do_whf $(fdp) | grep $1) field 1)
	shift # repeat if necessary

###	New functions

For new .prof functions (not yet in a library) using the family name, i.e. dp_

	libfuns $(do_whf $(fdp) | grep ^dp_ |  field 1)
	
For new utility functions, not for the local lib

    libfuns $(which {UTILIY}lib) {fun}a {other}b ...
	
For the default library -- functionlib, a function with no home:

    : reset the function - library table
    do_whf $(fdp)

	: funslib function ...
	:
	funslib $(do_whf $(fdp) | field 1);	
	
### 	



	
