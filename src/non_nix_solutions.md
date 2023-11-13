# Non-Nix Solutions

Most programming languages have built-in package managers, or packages managers
that are at least closely associated with and developed for the language.
In the world of Linux, package managers and package repositories are among the
most important differences between distributions. 

Some programming languages or tools also provide "virtual environments" (as
in the case of Python) or similar, to isolate dependencies in one project from
the dependencies used in other projects or globally on the system.

There are also other approaches. One of the most popular is containerization,
similar to virtual machines (simulating another computer via software, and
working within this 'virtual' computer or virtual machine), but more
lightweight. Basically, it shares CPU resources with the global system, but
the filepath hierarchy is separate and access to the global system must be
explicitly granted.

These approaches have their benefits, but they are still far from ideal.
Containers are still fairly heavy, as they require installing nearly everything
needed for a program to run inside the container. Images (the disk snapshot
of a container) can be several or even tens of GB large. And this still leaves
the possibility of dependency conflicts or dependencies that are not fully,
specified, requiring a tedious process of trial-and-error to find and install
missing dependencies.

Similarly, virtual environments require a lot of duplication of code, and
external dependencies (system libraries, drivers, headers in the case of
languages like C/C++, etc.) are not installed inside the virtual library. Then
there is also the case of dependency resolution. Again, in the case of Python -
a popular and relatively simple programming language with notoriously
problematic package  and environment management - there are tools like Poetry
for dependency resolution and virtual environment management, which do improve
the situation, but even so, dependency resolution may fail.

So what to do?
