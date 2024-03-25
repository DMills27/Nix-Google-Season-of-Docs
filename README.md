# GSoD 2024 - Improving and Enchancing the Nix Documentation.

# Introduction

[Nix](https://nix.dev/) is an open source build system that simplifies software management using a functional package management system. It ensures dependency management, facilitates easy deployment across platforms, and enables rollbacks to previous versions. It is the basis of an ecosystem of exceptionally powerful tools – including Nixpkgs, the [largest, most up-to-date software repository in the world](https://repology.org/repositories/graphs). The [Nix ecosystem](https://ossinsight.io/analyze/NixOS/nixpkgs#overview) is on an exponential growth trajectory in terms of user adoption and development activity at the periphery. Moreover, the public [Nix binary cache](http://cache.nixos.org/) provides operational software artefacts from more than a decade back, some of which cannot be obtained otherwise any more.

Nix has the potential to become a default in the software development tool stack, by drastically reducing the time required to start working on software development projects – written in any language – and the cost of maintaining and sharing build setups and development environments. However, much of this potential is unrealised due to obscure documentation that presents a significant hurdle for new, and even some experienced, users to overcome.

# Our Project's problem

The Nix's documentation in its current state [leaves much to be desired](https://www.reddit.com/r/NixOS/comments/1b9jrzt/why_is_the_nix_documentation_so_bad/). There have been a number of efforts from [invested individuals](https://ianthehenry.com/posts/how-to-learn-nix/) as well as larger scale initiatives such as those [here](https://www.youtube.com/watch?v=0nbwejLyF4Q) and [here](https://zero-to-nix.com/) to improve the state of Nix's documentation with varying degrees of success. The issues are mainfold owing to the fact that Nix is already more than two decades old, and started out as a research project that made discovering the base definitions and concepts inaccessible to a wider audience, and more recently, due to the aforementioned exponential growth trajectory for development activity. 

On one hand, the documentation lacks exhaustive examples and cogent explainations for many of its rudimentary concepts and tools. On the other, the documentation does not keep apace with the development of new features. The former is the more pertinent of the two since it doesn't provide a solid foundation for new users to become productive with the Nix ecosystem in a short amount of time, and thus hinders them from graduating to more advanced concepts easily. 


# Project Scope

The scope of this project is to create official documenation that addresses some of the most prominent pain points in the Nix documentation for newcomers, namely understanding how to use its elementary features and commonly used tools in the Nix ecosystem, in addition to, developing a more organic way to produce documentation that keeps up with the size and scope of the Nix ecosystem. We use a multipronged approach,  using the insights from [previous attempts and feedback](https://discourse.nixos.org/t/usability-studies/21404)  to refine the processes and use-cases through: 


- Writing tutorials and guides detailing how to use the basic Nix concepts and tools.
- Improvements to the technical infrastructure related to documentation.
- Enchancing and developing tooling to ensure that new documentation remains relevant as it increases in complexity and scope.


# Measuring the Project's Success

Ideally, we consider the metrics for success to be an overall increase in the activity on the documentation website and decrease in the number of documentation related issues on Github, which we will measure through:

- An increase in the number of visitors on the documentation website which can be determined via Google Analytics.
- A decrease in the number of GitHub issues and pull requests concerning the documentation measured through [Git Insights](https://gitinsights.io/) on a weekly and/or monthly basis.
- An uptick in the number of users visiting the documentation website from referral traffic which can again be determined through Google Analytics.


# Timeline

| Dates   |      Action Items      |
|:----------:|:-------------|
| May |  Orientation | 
| June-October | Begin working on documenting |
|November| Project completion and final report due|

This timeline, especially within the May-July period, is not strict and has some room for unforeseen circumstances that may arise. However, it is expected that  all the requiste tasks will be complete within the intervals posted and everything will be completed by the November deadline.

# Budget

| Item   |      Amount      |  Running total | Notes |
|:----------:|:-------------:|:------:|:------- |
| Technical Writers |  9000 | 9000 | A sum of 3000 would be allocated for 3 Technical Writers|
| Volunteer Stipend |    1000   |   10000 | |

Additional information:

- The NixOS Foundation was selected for Google Summer of Code (GSoC) in 2024.

# Ideas List

Here are a few ideas we'd like to implement in the coming months.

## Improving the Base Nix Documentation

On a rudimentary level, the Nix documentation lacks detailed information about how to use some of its basic functionalities and tools associated with it, and would benefit from the inclusion of documentation that provides:

- An expansive overview of various features and functionalities that a user new to the Nix ecosystem would find useful, such as how to debug builds or the basics of the module system, which are detailed in this [issue](https://github.com/NixOS/nix.dev/issues/572).
- Guides and recipes for the most common Nix use cases, such as package scaffolding with `nix-init` and automatic environments with `direnv`. This is discussed in greater length in this [issue](https://github.com/NixOS/nix.dev/issues/908).
- The Nix manpages would benefit from being properly exposed, such as on the official [Nix  documentation website](https://nix.dev/), so that they can be directly linked to. Manpages can (and are) build with Nix, but no one has done any work to properly expose those built manpages. Currently, whenever someone wants to link to a manpage, they have to [add a link](https://github.com/NixOS/nixpkgs/blob/master/doc/manpage-urls.json) first, and then use [special syntax](https://github.com/NixOS/nixpkgs/blob/master/doc/README.md#roles) to link it. However, looking at the list of links, they go all over the place. Thus, exposing them on the documentation website would provide a better interface than using the command line to read pre-existing documentation while also being less onerous to sift through.  Arch Linux, for example, has a page for manpages of packages in their repositories: https://man.archlinux.org/man/passwd.5. Something similar can be done for Nix possibly with a stable/unstable distinction in the URL.


**Skills Required**: The ideal candidate should have some familiarity with Nix and a strong willingness to further expand their knowledge of Nix. Additionally, they need to be comfortable with using Git/Github and be able to write code in a scripting language.

**Contact details**: Send at least two technical writing samples to dominic@palisadoes.org with the heading Nix GSoD - <your name\>

## Tooling for supporting documentation writing and maintainership  

The inclusion of proper tooling can make documentation more stable and maintainable. A common gripe among developers is the frustration felt from running a code sample from the documentation and then finding out it that doesn't work. This problem can be ameliorated, in our context, by:
- Integrating a [Nix doctester](https://github.com/mobusoperandi/eelco) which can be used to test various examples on the [nix.dev](https://nix.dev/) site. Some examples are more complex, however, and require the tool to be further refined. The scope of work is thus to first integrate the tool on the nix.dev site and then see if additional work can be done to further improve the tool for more complex examples. 

- Integrating a recently developed [internal link checker](https://github.com/NixOS/nixpkgs/pull/298665) that would provide much needed support to the documentation website by ensuring consistency among any hyperlinks on the documentation website, helping to avert [link rot](https://en.wikipedia.org/wiki/Link_rot).   

**Skills Required**: The ideal candidate should have some familiarity with Nix and a strong willingness to further expand their knowledge of Nix. Additionally, they need to be comfortable with using Git/Github and be able to write code Rust as well as a scripting language.

**Contact details**: Send at least two technical writing samples to dominic@palisadoes.org with the heading Nix GSoD - <your name\>

 ## Interactive Nix Guides



**Skills Required**: The ideal candidate should have some familiarity with Nix and a strong willingness to further expand their knowledge of Nix. Additionally, they need to be comfortable with using Git/Github and be able to write code in a scripting language.

**Contact details**: Send at least two technical writing samples to dominic@palisadoes.org with the heading Nix GSoD - <your name\>

## Revising  the Standard Environment, Build Helpers, and library reference chapters in the Nixpkgs manual

**Skills Required**: The ideal candidate should have some familiarity with Nix and a strong willingness to further expand their knowledge of Nix. Additionally, they need to be comfortable with using Git/Github and be able to write code in a scripting language.

**Contact details**: Send at least two technical writing samples to dominic@palisadoes.org with the heading Nix GSoD - <your name\>

# Resources

The following are resources that are useful to newcomers, as well as more experienced users, to the Nix ecosystem:

- [Nix from Nothing playlist](https://www.youtube.com/playlist?list=PLCy0xwW0SDSSt2VJKx3MsXRuVvcFUO6Sw): A three part video series more geared towards newcomers to the Nix ecosystem. If you're unfamiliar with the Nix language and package manager, this is provides brief but excellent starting point for delving into  Nix.

- [Nix Hour playlist](https://www.youtube.com/playlist?list=PLyzwHTVJlRc8yjlx4VR4LU5A5O44og9in): A playlist with a weekly format that goes through various, and often more obscure, concepts in the Nix package manager, Nix language and the Nix operating system.

