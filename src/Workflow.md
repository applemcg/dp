
Dot Prof Workflow
=================

Functions, *local* and non-local are entered in the .prof file, either
new, or copies of existing functions which may need to be modified..
In a source-controlled environment, the business here is to return
the all functions to their respective library, either a local one
under development or an existing library. 

Since this development uses **Semantic Versioning**, see the
accompanying **Changelog** for additional steps in the workflow. This
workflow separates requirements Changelog or Semantic Versioning
features. The resulting function library and enclosing App may be used
without reference to those practices.

Format of the Dot Prof file
---------------------------

The .prof file will have four sections in the order here:

- a header which may source libraries and perform initialization
- function bodies, new and those being repaired
- comments in a block wrappend in **false && { ... }** 
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

Example Update
--------------

A list of steps for the next release. This assumes the versioning in use here.

1. qf **dp_version**; update to x.\(N+1\).a, read it into .prof
1. edit Changelog, to reflect version, making space for Unreleased
1. comment, ordered list "just a number", successive "1"s make sense
1. pick a function to add to .prof.  lets add **dp_app**, 0.4.x
  1. most affected function, **dp_install**, start there.
  1. idiom:   qf *functionname*, in editor, read .qf into buffer
  1. test dp_install here in the .prof
1. another function, dp_all
1. test
1. git ls-files, git status
1. no NEED to fix compare_all_lib
1. add **fun_asapp** to **dp**, test



Versioning
----------

Not imposed by the DP tools, but use of **git** in a **Semantic Versioning**
environment.   Co-ordinating git versions with the Semantic Version is not
terribly challenging, but with the implementation I use, it may be necessary
to return some functions to the Dot Prof for re-work before the current 
version may be closed.

See an adjacent **Versioning** paper.

Functions
---------


1. qf

    qf () 
    { 
        : named show Quick Function ...;
        : date: 2019-08-11;
        : date: 2021-08-28;
        declare -f ${*:-qf} | tee .qf
    }

1. code\_tomd

    code\_tomd () 
    { 
        : prepare Functions for including in a Markdown;
        : date: 2022-08-29;
        declare -f $* | fourspaces | tee .qf | show_tmpclip
    }

