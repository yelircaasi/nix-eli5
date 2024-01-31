# Desiderata for a Package Manager

At risk of sounding too didactic, it can be very helpful, before going on to
learn about Nix, to think about how you might go about trying to solve these
problems, or at least mitigate them.

## Avoid Duplication

Ideally, we would like to avoid unnecessary duplication of dependencies.
Even more importantly, we want to know what all dependencies of a project are,
so that we can get it right the first time - no trial-and-error. It would be
nice to have the different versions of the same package if we happen to need
both of them, and this is true whether we need them simultaneously of simply for
different projects.

## Declarative over Imperative / Procedural Package Management

Another thing that would be great is declarativeness. Usually we have to
install packages as we need them, one after the other, as we figure out we need 
them. The traditional  approach to dependency management is, to some degree, 
imperative - we can't  always just say **what** we want; we have to tell the
package manager how to do it. This is more true of some tools than others
(Poetry vs Pip, for example), but generally, we have to spell it out,
step-by-step, more than we would like to. apt or pacman, for example, will
often raise an error if a dependency is missing, rather than just installing it.
The best package managers are good at figuring out which dependencies are
required and doing it automatically, rather than requiring the user to
imperatively install dependencies. Declarativeness is nice - we say what and
the package manager figures out how.

To be fair, there are install scripts. A script is clearly imperative - it is,
after, just a sequence of instructions - by definition. At the same time, it is
a more declarative approach to imperativeness, since it records the steps all in
one place, in a reproducible manner. This, I believe, is why scripts are so 
popular. It's also why Ansible is such a powerful and popular approach to 
configuration management. But that doesn't that the scripting approach can't be
improved upon.

## Fine-Grained Control

While we're dreaming, we might also add a few more items to the wish list. It
would be nice to be able to specify different options when installing software.
A package manager powerful enough to provide fine-grained control would be nice.

## Pre-Built Packages

On the other hand, it would be tedious and in most cases undesirable to have to
specify everything. Moreover, having to build everything from source is also
rarely desirable to non-Gentoo users. So having the option of installing
pre-built packages where available and building where necessary would be the
best of both worlds. But we would need to be sure that pre-built binaries,
compressed files, etc. actually met the requirements.

## Garbage Collection

What about when packages build up and take up a lot of space on the hard drive,
but we're afraid to remove them because we don't know if something still needs
them? Of course, most package managers do support dependency graphs and can
sometimes provide information on what is still required by what, but in
practice, it is far from perfect, especially since in practice, not all
packages are managed just by one package manager. On Debian and its children,
for example, you might install most packages with apt, but some from source,
some through various programming languages, maybe npm or Cargo. It is not
uncommon to uninstall something you think is not longer needed, only to find
that removing the package broke something in unexpected ways.

You might try to be at least a bit *more* declarative about installing
packages. You might keep track of what exactly you installed and do your
best to roll back the state of your environment by tracing your steps and
trying to undo them. Some commands like `apt autoremove` are helpful
for this sort of thing. But having totally reliable garbage collection would be
nice. Try reading any moderately complex uninstall script, and you'll see why
this might be such a nice feature to have. On 'vanilla' Linux, programs can
install a lot of files and data in different places. `/usr/bin`, `/usr/share`,
`~/.cache`, `~/.local`, `~/.config`, `~/`, `~/etc`, and so on.

## Rollbacks

What about being able to go back to a previous state, like disk backups without
the hassle? How would that be possible? what if an installation fails and we are
left with chaos, wishing we could go back to a previous state when we knew
everything worked? Rollbacks would be another great feature to have. Most users
who install Arch Linux don't install it just once per machine. Often clean
re-installs become necessary.

## No Side Effects

While we're at it, what about when you install / uninstall one thing and it
completely borks something else? Sometimes even something seemingly unrelated.
Clearly side effects are not ideal. If we could install packages in such a way
that they 'left other packages alone', that would be great.

## Peaceful Co-Existence of Different Versions

We already mentioned it, and it's related to the point above, but there are 
often cases where would be desirable to
have different versions of the same package side-by side. If there is just one
available place for a package of a certain name, how is this even possible?
It isn't, not in the `$PATH`-searching approach, where the first executable
named, for example, `scala` found in any of the directories in the `$PATH`
environment variable is used, we just can't have another installed and
available. So clearly some innovation is needed - consider this a teaser.

## Conclusions

Ok, you're probably thinking this is all a bit contrived, that I'm just cherry-
picking features that I already know exist in Nix. That's a fair objection,
but I still believe this is a useful exercise, as it puts some of the features
of Nix into perspective, especially the trickier bits. As you can see, there
are a lot of perfectly reasonable requirements that traditional packagement
failed to meet, and understanding why and how prior systems failed is key to
understanding Nix and its design.
