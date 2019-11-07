---
layout: post
title: "Python Package Management: Tame The Snake"
subtitle: "Best practices for managing Python modules and environment."
description: Modern solutions to untangling your Python modules and environments. Pipenv + pyenv + pipx = awesome.
permalink: python-package-management
image: /img/python-environment.png
tags: [python, environment, package, module, management, tools, developper]
published: true
---
In this post I describe the tools needed for a clean and manageable Python development environment. Messy dependencies, mixed module versions and unknown requirements are a thing of the past.

# The problem
Python is loved by many for its ecosystem. You can find a library or module package for nearly anything in [the Pypi repositories](https://pypi.org/). Managing these libraries, packages and modules has historically been quite messy. 

{% include image.html
            img="/img/python-environment.png"
            title="Famous XKCD comic lamenting the state of his Python environement."
            caption="XKCD on the frustration that is Python package management. Source: https://xkcd.com/1987/" %}

For a long while writing code in Python required hacked together tools to make pip behave.
I decided they share my best practices for handling multiple projects with their own environments in Python.

Different projects require different module and even different Python versions.
Things get even more messy when on a multi-user system such as RnD servers.

My approach should provides the following:
- Ease-of-use: Cross-platform, no hacky installations for tools or barely documented scripts, modules installed straight from Pypi pip or Github repos.
- Clean global system-level environment: Avoid conflict in Python and module versions.
- Unambiguous project requirements: Clear and non-ambiguous dependency graph using Pipenv.

While a lot of ink has flowed on Python development tools, many older blog [posts](https://opensource.com/article/19/4/managing-python-packages) contain irrelevant information:
- [Pyenv-virtualenvwrapper](https://github.com/pyenv/pyenv-virtualenvwrapper) has been overtaken by pipenv, which offers a clean and powerful solution to library module management.
- or they do not tackle globally installed Python command-line tools which cause confusion with multiple concurrent python versions.

# The solution
The following tools are

- [Pyenv](https://github.com/pyenv/pyenv): Handles installation of different python versions.
- Pipenv: Recommended by the Python foundation
- Pipx: 

# pyenv
To complicate things, there are multiple ways of installing Python too:

- Preinstallation by the OS 😔
- Using a package manager like brew or apt 😕
- Using the binaries from www.python.org 😫
- Using pyenv—easy way to install and manage Python installations 😎


# Alternatives
- [Poetry](https://poetry.eustace.io/): Poetry is a snappier packaging and dependency manager to replace Pipenv. Unlike Pipenv, Poetry does not include Python interpreter versioning, is less widely used, and is not officially supported by [the Python Packaging Authority](https://www.pypa.io). Poetry however is [significantly faster](https://johnfraney.ca/posts/2019/03/06/pipenv-poetry-benchmarks-ergonomics/) when locking in dependencies and this translates to less waiting around when writing code. I will keep an eye on this promising project and follow up with an update after using it for a while.
- [Conda](https://docs.conda.io): I personally have very bad experiences using Conda to install data-science and deep learning frameworks. Many conda packages are broken and unmaintained. While pip is integrated into Conda, pipenv is the more flexible alternative. Conda is bloated compared to other tools, suffers from feature creep, and places itself outside of the Python ecosystem.