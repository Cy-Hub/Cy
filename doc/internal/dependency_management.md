Staq Dependency Management
==========================

There is a central registry of all public Staq modules in github:
`git@github.com:deansher/staq-modules.git`.  If you want to make your module public, submit a pull
request to update this registry.  (Include a suggestion for how to verify that you own the domain
names used to construct the package names you are claiming.)

The directory structure of the registry corresponds to Staq package structure, except that each leaf
module `xyzzy` is represented by a file `xyzzy.txt`. The file for a module has four
whitespace-separated values on a single line with no other delimiters:

* the version-control system, which can currently only be git

* the URL of the repo containing the module

* the branch in that repo that contains the module

* the relative path of the module from the root of the repo, which should be the name of the
  directory that contains at least `node-out`, and `browser-out`, that preferably contains `src` and
  `README.md`, and that contains `contracts` if it does not contain `src`.  The root of the repo is
  represented by ".".

If you want to release your module (or selected versions of it) locally (including within an
organization), you can do this by creating a local directory tree that has the same structure as the
public module registry and by providing the path of this local directory tree to the Staq compiler
as --module-registry.  (This flag allows multiple local registry paths to be separated using the
same convention for `NODE_PATH`.)

For rapid iteration during development, Staq also maintains a file ~/.staq/module_repos.txt that
maps module names to the paths of local repo checkouts for those modules.  The Staq compiler updates
this file, but you can edit it by hand when necessary.  Each line simply contains a module name and
a local filesystem path (to the directory containing `node-out`, `browser-out`, etc.), separated by
whitespace with no additional delimeters.

The Staq compiler provides a `check-repo` command that is intended for use as a pre-commit hook,
and that verifies the following invariants on your repo:

* You cannot modify a previously committed output file.  (Instead, you can create a new version.)

* There must be a new output file for each modified source file.

* The version numbers of each source file and its corresponding contract file must match.

* If either the source file or the contract file are updated, then both must be updated
  at least with a new version number.

* Each new output file must have a version that corresponds to the current version of its source
  file, a `__staq_source_md5` that matches the source file, and a `__staq_contract_md5` that matches
  the contract file.

* You cannot delete a previously committed output file that is still the target of any
  version spec symbolic link.

* You cannot delete a previously committed version spec symbolic link except that after a new
  major or major.minor version has existed for one year, only the highest-numbered version
  spec symbolic link must be kept for older major versions or older major.minor versions.
  For example, if the highest version reached with major version number 1 was 1.2.97, then
  one year after version 2.0.0 is released, all version spec symbolic dependency links for
  major version number 1 *except* 1.2.97+.js can be deleted.

* Unless the current source for a module has a new major version number, the current contract must
  be a superset of the previous contract.

* Each module's current output files must meet the current contract.