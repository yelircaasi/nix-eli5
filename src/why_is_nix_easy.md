# Interlude 2 - Why is Nix easy?

Having just talked about why Nix is hard, it's only fair to ask on the other hand why Nix is easy.
Here are a few things that come to mind:

* **bizarrely easy rollbacks** - nearly impossible to really bork your system (i.e., you'd have to try). This is 
  because if something goes wrong, you can simply reboot and select the last (or any previous)
  "generation" where everything was stable and working just fine. Then, rather than losing months
  or even years'  worth of accumulated experience and configuration, you just lose whatever changes 
  you made since the last time you ran `nixos-rebuild switch` (same goes for `home-manager switch`).
* **wonderful community** - perhaps surprising for a functional language, which sometimes have a 
  reputation for having elitist, snobbish, unwelcoming communities compared to some wonderfully 
  welcoming and helpful communities like (in my experience) the Julia, Raku, or Rust
  communities. In my experience, NixOS communities, channels, and fora - both official and unofficial - have more in common with the latter. Much like with Rust, NixOS tends to inspire a certain kind of mostly-benign fanaticism, and this has the wonderful side-effect of willingness - often even eagerness - to help new beginners.
* **availability of software** - Nixpkgs is the best software repository out there. I'm asserting this
  without evidence, but take a look at [repology.org](https://repology.org/) - it's impressive.
  And maybe the best part is related to the next point - if something is missing, you can still
  use it in the same way (and with the same functionality and advantages) by writing your own
  expression for it, and you can add it to Nixpkgs using basic Git and Github.
* **extensibility** - once you have reached a certain level of proficiency (and yes, that is easier said
  than done, but it is doable), the possibilities are limitless. Nix is extremely powerful and 
  allows fine-grained control over small details. If you want to change the way something is built,
  you can do that in Nix. If you want to have the same configuration for all of your devices, but 
  with certain differences, you can do that. If you want to write your own functions to control
  how Nix configures your favorite software, you can do that.
* **everything all in one place** - coming from other Linux distros (with the exception of Guix System, 
  which is a GNU-y and LISP-y spinoff of NixOS), it feels like a luxury to be able to declare and configure everything all in one folder that is tracked by Git. This means backups are trivially easy - built-in, in fact. And you don't need to look through a dozen locations to find where a given app is getting its configuration from. Having a clean overview of your system is priceless.