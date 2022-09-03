
Dot Prof
========
	
Dot Prof is a tool, shell function library, builit into a shell
application. It is used for initial development, and appropriately in
maintenance.  Since it was born to develop shell function libraries,
its use in other language environments is an un-performed experiment,
as yet.

Since some facets of the programming environment are local, the
opening concept is extending the user's profile beyond the login
profile into local **.prof** files

These documents describe the programmer's workflow at two levels, also
provide a manual page format, and include a Changelog. This latter
document brings with it a set or versioning requirements. 

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


