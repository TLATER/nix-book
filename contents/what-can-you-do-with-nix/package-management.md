# Package management

While there are many things that Nix can help with, it is ultimately a package manager at heart.
This chapter will cover how one uses Nix for this purpose, as well as some of the unique features Nix has over other package managers.

<!-- Maybe the following paragraphs should go into an earlier chapter, but I think the content should be covered -->
For those unfamiliar with the concept, for Linux distributions pieces of software are typically packaged up as "packages", which you are expected to tell your computer to install with the help of a package manager.
For end users, this is similar to how "app stores" function on mobile phones - and distinct from how software is usually installed on something like Microsoft Windows, where programs are typically downloaded from the internet and executed directly.

Unlike mobile phones, on a typical Linux distribution packages are prepared by your distribution's maintainers, not the application's developers.
These maintainers put a lot of effort into making sure packages work together and don't change their behavior unexpectedly while staying up-to-date with security-related bug fixes.

<!-- Are NixOS-specific topics in-scope? -->
> NixOS <!-- can we have a flake icon here?-->: NixOS in particular is quite different from other distributions, so while you may find pre-built software on the internet, such software will often not work on NixOS without some additional work.
> This additional work will be covered in another section of this book, but take away that you can save yourself a lot of work by using packages others have already prepared for NixOS.


<!-- Previous-chapter-paragraphs end -->

Nix enables two distinct styles of package management that each have their own trade-offs. These are:

<!-- Maybe this is too much detail for the prelude, but I think giving readers some context so that they know what they are getting into for the other parts is helpful. -->

---

**Imperative package management**

<!-- I think this is a nice bit of fluff for non-native English readers. -->
[Imperative][imperative-definition] here means that we are instructing the computer to do something - we are giving it a command.

In this style, we type out installation commands in a terminal, and the computer in response downloads and installs packages.

The benefit is that this is a quite natural way of interacting with a computer - after all, when we want some software, we want to tell it to just do so.
It is also how other package managers generally work, so will feel second-nature to a long-time Linux user.

The downside is that we lack a conveniently accessible record of which packages are installed - while we can also ask the computer what is installed, there will be no note of why it is installed.

**Declarative package management**

[Declarative][declarative-definition] here means that we instead write down everything we want the computer to do.

In this style, we write a list of packages that we want to be installed on a computer.
We *still* make an imperative command, but rather than doing so for each package, and letting the computer manage the list, we command the computer to install our list (and remove all software that is not in it anymore).

While this may seem like a pointless distinction, we are now keeping track of the software we are installing in a list in a text file.
This means we can comment on why we want each piece of software, and even keep different versions of the list around so that we can easily go back to a previous version if we need to.

The downside is that we now need to keep track of this list, which is a bit more work.

---

Which style you prefer is up to you, however sticking to this rule of thumb may help avoid issues down the line:

- If you use NixOS, prefer declarative package management.
- If you use Nix without NixOS, prefer imperative package management.

Mixing the approaches on one system can lead to hard-to-debug problems much later, when you have already long forgotten that you made a choice.

If you are not fond of rules like this without explanation, don't worry - the later parts of this chapter will provide you with some reasoning for it.

<!-- Sub-chapter links here, so that we have a good chance of the reader reading the caveats. -->

<!-- Can probably find a better online dictionary? Is linking to dictionary definitions even appropriate? -->
<!-- Got confirmation from an English major that, yes, this is probably a good resource to link to for someone learning English. I'll take that as gospel ;) -->
[imperative-definition]: https://www.merriam-webster.com/dictionary/imperative
[declarative-definition]: https://www.merriam-webster.com/dictionary/declarative
