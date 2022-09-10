
Dot Prof
========
	
Dot Prof is a tool, a shell function library, built into a shell
application. I use it for initial development and function
maintenance.  It has grown out of my developing shell function
libraries.

Since aspects of function development are local to a specific directory, it
seemse useful to extend the concept of the  user's profile beyond the login
directory into local **.prof** files.

The documents here describe the programmer's workflow at two levels,
that of the developemen and maintenance task, as well as employing
change-control.  Other documents provide a manual page format, and
include a Changelo, which document brings with it a set of versioning
requirements.

It is worth saying the required rigor of the later steps in the
development cycle is well-supported by the the method here. Unit tests
are readily captured, and preserved in an evolving framework.

The user installs Dot Prof:

+
+
+
+

As delivered, the Dot Prof library, **dplib** supports the workflow
here.  The addtional features levied by the versioning procedures are
included in the Dot Prof App, **dp_app**.  That functionality comes
from two function library sources at present, a **backuplib** and a
generic utility library, **utillib**.  These are plannned as separate
REPOs to be similarly built and promulgated.

Workflow
--------

The workflow introduces 

+ how and why a .prof file will be used
+ the file format of a .prof
+ its routine use in an iterative manner
+ example(s) workflows
+ interaction with versioning requiremnets

Versioning
----------

Since this development has used **Semantic Versioning** the accompanying
**Changelog** was maintained with software checkpoints to validate
version to version changes.  This addition to the workflow separates
requirements for Changelog and Semantic Versioning features. The
resulting function library and enclosing App may be used without
reference to those practices.


Manual Page
-----------

The Dot Prof interface is thru functions in the **dplib**  which
are documented under the most often used **dp** function and 
with its family of sub-functions, as **dp** *subfunction* 


Changelog
---------

Little more need be said of the Changelog. It's meets
the requirements of **Semantic Versioning**, 


