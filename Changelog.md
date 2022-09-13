
# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a
Changelog](https://keepachangelog.com/en/1.0.0/), and this project
adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).
To adhere with semantic versioning, let's see if I can merge my backup
versioning with a GitHub REPO.

## [Unreleased]

  the release template, and current plans for DP

### Added

Search the **prof** family for members which belong here

### Changed

### Fixed

### Deprecated

### Security


## [0.4.a] TBD

A big hole I'm noticing, is the workflow needs to be tightened
up. Explicit dependencies in

+ dplib
+ dp_app -- make explicit dependencies on any library appearing in the
  header block
+ sourcing libraries in the header
+ timing of 
    - $ backup\_ver $(dp_version) 
	- $ git commit ...; git push

create function mismatches between updated external libraries, the
local, i.e. **dplib** and **dp_app**

A use for *dp_diff* compare the .prof copy of a function to it's
home library, and if a local library, the additional version copies,
immediate past and pending versions.

### Added

* *dp_binlib* finds the path location of the library in bin directory
* *dp_hint* on the abstracts, and repair functions
* *dp_wlhf* which library has the Function
* *dp_clear*  anticipates dp_restore
* *dp_{clear,restore,rmfunctions}*, repair functions to clean out the dot prof

### Changed

* move dp/src/* to dp/*, simplifies **install**, also git feature and
  compatible with **dfg** usage
* Workflow is now in OrgMode
* *dp_root*, *dp_version* are now assigned in *dp_init* by **setget**,
  and may be set by user from the command line.

### Fixed

* **dp** itself.   Remove a gratuitous **backup**, default copy in lib/dot.prof

### Deprecated

* **dp_qfile**  -- considerable performance win with new wlht

### Security

## [0.4.0] 2022-09-08

### Added

* *dp_app* FILE to complete DP application
* Workflow.md
* Versioning.md
* dp Management Functions: dp {compareall,cblock,functions,header,libraries}
  and dp {restore,rmfunctions}, deserving special notice for trimming the .prof

### Changed

* Move Changelog from shelf.html to Changelog.md
* **dp_install** accept a name, either user_input or ENVIRONMENT
  variable for the **dp_root**
* include **dp_funs** in dp_example

* **dp install** move README, Workflow, Versioning  to DP_ROOT 
* **dp all** -- where names are added or removed

Moved versions from ./ver/x.y.z to ../version/x.y.z

### Deprecated

* *dputillib, dplib* FILES -- absorbed in dp_app
* **dp_obsolete** function -- to render recent functions obsolete

### Fixed

* **dp_funs** leaked without arguments 

### Security


## [0.3.0] 2022-08-28

### Added

* audit feature to assure sufficient, dputillib anticipating dp_app
* function **util_fmlib**, awaits development utilities release
* sub-functions
** dp diff -- the difference between .prof and library function instance
** dp tolib,  *dp_wlhf* which library has the Function
** dp tolibrary -- writes dot prof functions to primary library

### Changed

* dp_abstracts complete, up to date
* properly install README from ./src,
* **dp_version** is now smart, default echo Version number
* **dp_root** has a default ENVIRONMENT Variable:  DP_ROOT, to locate installation

### Fixed

* dputillib audited for completeness, built during dp_install
* added README.md to SRC, install in parent

## [0.2.0] 2022-08-21

### Added

+ dp_version function names a version and points at this changelog

### Changed

+ move the source tree to dp/src, parallel with dp/bin and dp/lib, thus

### Removed

+ no longer need install locations, bin, lib in version tracking

## [0.1.0] 2022-08-20

### Added

* This CHANGELOG file to hopefully serve as an evolving example of
  standardized open source project CHANGELOG.

*  Outline of possible reasons

