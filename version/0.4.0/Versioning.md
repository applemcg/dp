
Dot Prof Versioning
===================

Since this development uses **Semantic Versioning**, see the
accompanying **Changelog** for additional steps in the
workflow. This part of the workflow assumes both a github REPO
and using Semantic Versioning with a Changelog.

Read the **Workflow** instructions before proceeding here.

Format of the Dot Prof file
---------------------------

The .prof file will have four sections in the order here:

- the execution steps, which may be themselves commented 

Executing the Dot Prof
----------------------

	dp   # or manually,
	source ./.prof
	
where the **dp** function also, one might say "gratuitously" backs up a
changed .prof file.

Save .prof Functions in the Appropriate Library
-----------------------------------------------

Libraries are either local (under development) or non-local (existing
libraries on the PATH) are identified with this command which returns
function - library pairs.  A new function will not have a paired
library name.

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

    libfuns $(which {UTILITY}lib) {fun}a {other}b ...
	
For the default library -- functionlib, a function with no home:

    : reset the function - library table
    do_whf $(fdp)

	: funslib function ...
	:
	funslib $(do_whf $(fdp) | field 1);	
	
Execution Steps
---------------

This is why the Dot Prof workflow is useful.   The objective is to
unit test the functions under development.   

Here is a sample of the **comment** and **execution** blocks from
a recent .prof.   The comment block, shielded by the **false** command
has copies of recent statements from the **execution** block

    # ------------------------------------------- COMMENT BLOCK	--
    false &&
    {
        dp_utilities | tee $(dp_utillib)
        dp_install
        which dputillib

        ls -lisart .prof $(find . -type f | usefulfiles)
        set -- fun_peek; $1 .prof  $1
        dp_diff ; comment missing args
        # lib_tidy ./dplib
        # def compare_all_lib
    
        #  ------------- this is where other maintenance utilities are invoked,	--
        #
        # 1). "compare_all_lib" doesn't belong here, it's now part of the process,
    }
    # --------------------------------------------- EXECUTION BLOCK	--	
        # compare_all_lib
        # funslib $( do_whf $(fdp)| field 1)
        # 
        # backup_ver $(dp_version)
        dp_version backup_ver 
        # ver_diff .ver/0.{2,3}.0
        dp_install
		
The **execution** block may also have comments and likely have one or
more executable statements.  For example, if "compare_all_lib" needs to
be executed, simply delete the shell comment sharp (#).   This is where
the functions may be unit tested.


Versioning
----------

Not imposed by the DP tools, but use of **git** in a **Semantic Versioning**
environment.   Co-ordinating git versions with the Semantic Version is not
terribly challenging, but with the implementation I use, it may be necessary
to return some functions to the Dot Prof for re-work before the current 
version may be closed.

See an adjacent **Versioning** paper.

