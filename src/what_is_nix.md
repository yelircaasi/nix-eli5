# What Is Nix?

This is already a slightly tricky question, because Nix can mean multiple
things. On the one hand, it is a package manager. On the other hand, it is also
the programming language in which the package manager is written. And finally, NixOS
is the name of the operating system (a distribution or flavor of Linux) that is
built with, and according to the principles of, the Nix language and package manager.

So Nix is a package manager, Nix is a programming language, and NixOS is a
so-called distribution of Linux (an operating system).

A few words about NixOS at this point - it is indisputably Linux, GNU/Linux
to be precise. It is quite different from most other distributions of Linux
because its directory system is quite different, in ways which will soon become
clear, and for reasons which will also soon become clear. One exception is
Guix System, a related distribution of GNU/Linux that is built on the same
general principles, but using a different language (Guile Scheme, a dialect
of Lisp) and which does not allow any unfree software at all, unlike NixOS,
which allows users to opt in to unfree software.

So NixOS is a distribution of Linux that is quite different from most other
distributions, and it is built around the Nix package manager, which in turn
is built on the Nix programming language. What is the Nix language built on?
Theory and C++. Getting into the details of how Nix is implemented in C++
(or, by extension, how it might be implemented in any other Turing-complete
language) is a more advanced topic; to really understand Nix, it is more
important to understand the theory behind it and to see examples of its
practical usage, so we'll start with that.

Having said a few words about what Nix and NixOS are, I will use a simple
convention from now on: If it is ambiguous whether I mean the language or the
package manager, I will specify say "Nix [lang]" or "Nix [pm]". In case where
it is perfectly clear from the context or where it doesn't make a difference,
of course, I will just say Nix. And typically if I can just say "Nix", whatever
I say will apply to NixOS as well.

The next step in understanding Nix is to understand the background and
motivation behind why we might want such a thing, why it represents such a 
profound paradigm shift, and why it is (in my opinion and the opinion of many
other happy Nix users) such a nice thing to have.
