# Problems with Package Management

First, a word about terminology - a more precise term may be "software
deployment". But for an entry-level explanation of Nix, the important thing
is just to pick a term and be clear about what it means. So when I say "package
management", I'm also referring to software deployment, software dependency
management, and so on. Basically, we're talking about using software that
depends on other software, whether it be in development or deployment.

So for the very big picture: Software usually depends on other software. In
theory, it is possible to write everything from scratch if you are
both [exremely talented and extremely insane](https://en.wikipedia.org/wiki/Terry_A._Davis).
In practice, it is much nicer to 'stand on the shoulders of giants' and not
'reinvent the wheel', using instead software that has already been written.

Good software, in some ways, is like a living organism. New versions are
released from time to time, sometimes to add features, sometimes to fix bugs
and to patch security vulnerabilities, and sometimes just to improve code
quality. It is generally a good idea to keep up-to-date on software, but in,
practice, some projects are better than others at keeping their dependencies
up-to-date. If we're unlucky, this can lead to dependency conflicts, where
our project has dependencies which we'll call A and B, and A depends on a
different, older version of B. Under "vanilla" Linux, we can't have two 
versions of the package installed. We may have to use an older version of A, or
maybe "vendor" one of the packages, copying it into our codebase and maintaining
it as our own, which of course is extra work we'd probably prefer to avoid. 
Obviously, waiting for B to be updated is also far from ideal.

It's also possible for A and B to each depend on a third package, C, but require
different versions of it, once again requiring some suboptimal and frustrating
solution.

There is another common problem - packages with unclear dependencies.
In some cases, these dependencies are unknown or unrecognized because
they are *usually* present on a Linux system. But if they are missing, the
project may fail to build or run. Anyone who has tried to install packages on
a fresh install of Ubuntu or Debian has probably encountered this, for example.
Usually the fix is simple - you search the error and find a Stack Overflow 
answer explaining which packages you need to install in order for the packages 
to build or run. Still, this kind of approach to software installation is
mildly irritating and clearly suboptimal. Sometimes, the problem is not so
simple and developers can waste hours trying to figure out exactly which
dependencies are missing.

Finally, another example of something about the status quo that we might want
to improve upon - getting programs configured right is a fine art, and 
"dotfiles" (configuration files) are very important to users who want programs
to look or behave a certain way. Configurations are an important part of the
software, and managing configurations on multiple devices can be tedious.
This can also be problematic when developers are working on the same project.
The "it works on my machine" trope has become a meme precisely because
differences between local environments can be so difficult to track down and
to manage.

These are just a few examples to illustrate why installing software, and 
developing software that depends on other software, is not always as 
straightforward a process as one might assume or hope. So what to do? And what
do people do?
