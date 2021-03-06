CPSA: Crptographic Protocol Shapes Analyzer Version 3

The Cryptographic Protocol Shapes Analyzer (CPSA), is a software tool
designed to assist in the design and analysis of cryptographic
protocols.  A cryptographic protocol is a specific pattern of
interaction between principals.  TLS and IKE are some examples of
well-known cryptographic protocols.

CPSA attempts to enumerate all essentially different executions
possible for a cryptographic protocol.  We call them the shapes of the
protocol.  Naturally occurring protocols have only finitely many,
indeed very few shapes.  Authentication and secrecy properties are
easy to determine from them, as are attacks and anomalies.

For each input problem, the CPSA program is given some initial
behavior, and it discovers what shapes are compatible with it.
Normally, the initial behavior is from the point of view of one
participant.  The analysis reveals what the other participants must
have done, given the participant's view.

CPSA version 3 features support for Diffie-Hellman and state.  The
manual in <doc/cpsamanual.pdf> provides a comprehensive description of
the program.

CPSA: Cryptographic Protocol Shapes Analyzer

This program has been built and tested using Haskell Platform.
It is available from <http://haskell.org> or from an operating
system specific source.  The name of the Linux package is usually
haskell-platform.

If the Internet is available, install CPSA with:

$ cabal update
$ cabal install cpsa

Find the documentation directory by typing "cpsa -h" in a command
shell, and view index.html in a browser.

INSTALLING FROM A TARBALL

QUICK START (Linux)

: To build and install CPSA type:
$ make
$ make install

: To analyze a protocol you have put in prob.scm type:
$ cpsa -o prob.txt prob.scm
$ cpsagraph -o prob.xhtml prob.txt
$ firefox -remote "openFile(`pwd`/prob.xhtml)"

: Documentation and samples are in the directory given by
$ cpsa -h

: To view the user guide:
$ firefox -remote "openFile($HOME/share/cpsa-X.Y.Z/doc/cpsauser.html)"
: where X.Y.Z is the CPSA version number.

QUICK START (Mac)

: To build and install CPSA type:
$ make
$ make install

: To analyze a protocol you have put in prob.scm type:
$ cpsa -o prob.txt prob.scm
$ cpsagraph -o prob.xhtml prob.txt
$ open prob.xhtml

: Documentation and samples are in the directory given by
$ cpsa -h

: To view the user guide:
$ open $HOME/share/cpsa-X.Y.Z/doc/cpsauser.html
: where X.Y.Z is the CPSA version number.

QUICK START (Windows)

With Cygwin or MinGW, the installation is similar to the Linux
install.  The software has been tested on a Windows system on which
neither MinGW or Cygwin has been installed.  Install Haskell Platform
Core and then run:

C:\...> cabal update
C:\...> cabal install parallel
C:\...> cabal configure
C:\...> cabal build
C:\...> cabal install

Documentation and samples are in the directory given by
C:\...> cpsa -h

The installed programs can be run from the command prompt or via a
batch file.  Alternatively, copy doc/Make.hs into the directory
containing your CPSA problem statements, and load it into a Haskell
interpreter.  Read the source for usage instructions.

MAKEFILE

The file $HOME/share/cpsa-X.Y.Z/doc/cpsa.mk contains useful GNU Make
rules for inclusion, where X.Y.Z is CPSA version number.

Alternatively, copy the file Make.hs in the same directory into the
directory containing your CPSA problem statements.  The source file
has usage instructions.

PARALLELISM

CPSA is built so it can make use of multiple processors.  To make use
of more than one processor, start CPSA with a runtime flag that
specifies the number of processors to be used, such as "+RTS -N4
-RTS".  The GHC documentation describes the -N option in detail.

TEST SUITE

: To run the test suite type:
$ ./cpsatst

Tests with the .scm extension are expected to complete without error,
tests with the .lsp extension are expected to fail, and tests with the
.lisp extension are not run.  New users should read tst/README, and
then browse the files it suggests while reading CPSA documentation.

Don't develop your protocols in the tst directory.  The Makefile is
optimized for testing the cpsa program, not analyzing protocols.

ADDITIONAL PROGRAMS

The src directory of the source distributions includes programs
written in Scheme, Prolog, and Elisp for performing tasks.  Use them
as templates for your special purpose CPSA analysis and transformation
needs.  Also, when given the --json option, the CPSA pretty printer
cpsapp will transform CPSA S-expressions into JavaScript Object
Notation (JSON).

On Linux, the GHC runtime can request so much memory that thrashing
results.  The script in src/ghcmemlimit sets an environment variable
that limits memory to the amount of free and reclaimable memory on
your machine.

KNOWN BUGS

Variable separation in generalization fails to separate variables in
terms of the form (ltk a a).
