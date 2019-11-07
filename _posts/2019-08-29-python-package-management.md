---
layout: post
title: "Tame the Snake: Python Package Management"
subtitle: "Best practices for managing Python modules and virtual environment."
description: Modern solutions to untangling your Python modules and environments. Pipenv + pyenv + pipx = awesome.
permalink: python-package-management
image: /img/snake-charmer.jpg
tags: [python, environment, package, module, management, tools, developper]
redirect_from:
  - "/tame-the-snake"
  - "/tame-the-snake-python-project-management/"
published: true
---
In this post I describe the tools and workflow needed for a clean and simple Python development environment.
Messy dependencies, mixed module versions and unknown requirements are a thing of the past.
Learn to keep your development clean and free of conflicting and ambiguous versions.

# The Problem
Python is loved by many for its ecosystem. You can find a library or module package for nearly anything in [the Pypi repositories](https://pypi.org/).
Managing these libraries, packages and modules has historically been quite messy.

{% include image.html
            img="/img/python-environment.png"
            title="Famous XKCD comic lamenting the state of his Python environement."
            caption="XKCD on the frustration that is Python package management. Source: https://xkcd.com/1987/" %}

Different projects require different module and even different Python versions.
For a long while writing code in Python required hacked together tools to make pip behave cleanly when working on multiple projects.
Things tend to get even more messy when on a multi-user system such as on RnD servers.
Virtual environment management was not user-friendly 
Here I share my best practices for handling multiple projects with their own environments in Python.

The approach should provide the following:
- Ease-of-use: Simple creation of virtual environments that is cross-platform, without hacky installations for tools or barely documented scripts, and installs modules straight from Pypi pip or Github repos. Easy management of packages and dependencies.
- Install and use different Python versions: Many developers -myself included- have to work on Python 2 due to legacy code, but also want to use the latest-and-greatest in new projects. To keep the system clean, this requires a manager for Python interpreter versions
- Distinguish project environments vs. global tools: Separate project-based virtual environments from Python command-line tools.
- Document project requirements unambiguously: Use a clear and non-ambiguous dependency graph to avoid version conflicts. This is especially handy in setting up existing projects.

While a lot of ink has flowed on Python development tools, many older blog [posts](https://opensource.com/article/19/4/managing-python-packages) contain out-dated information:
[Pyenv-virtualenvwrapper](https://github.com/pyenv/pyenv-virtualenvwrapper) is often recommended.
But it has been overtaken by pipenv, which offers a cleaner installation and more user-friendly and powerful solution to environment and module management.
Many older post also do not tackle globally installed Python command-line tools which cause confusion with multiple concurrent Python versions.

# The Solution
Sadly, there is not one tool that integrates our desired requirements to a satisfactory level.
In vain of [the Unix philosophy](https://en.wikipedia.org/wiki/Unix_philosophy) -"Do One Thing and Do It Well"- we pick one tool to handle each aspect of our ideal workflow.

Pyenv, Pipenv, and Pipx meet and excede our requirements and are both mature and actively supported by the community.

- [Pyenv](https://github.com/pyenv/pyenv): Install different Python versions globally and locally.
- [Pipenv](https://pipenv.kennethreitz.org): Install module packages and creates environments for your projects. Recommended packaging tool by the official Python Packaging Authority
- [Pipx](https://github.com/pipxproject/pipx): Install and run Python applications such as command-line tools.

Don't feel bad if you are a long-time Python dev and have not heard of these.
Pipx and Pipenv are fairly recent additions (2018 and 2019 resp.) to the Python development toolset.

We will now go over each tool, provide installation and common-usage instructions.
Then I give an example of a typical workflow for new projects.

# Pyenv
Pyenv excells at managing Python versions.
It allows for:
- Setting directory-level local Python versions for projects
- Setting a system-wide Python version on a per-user basis.

It supports the default CPython interpreter as well as pypy, anaconda, jython, micropython, etc.

Pyenv excells at handling different Python versions, but don't be fooled by its name:
It is not a virtual environment manager. We have Pipenv for that.

Installation:
Pyenv installation is fairly easy and well-documented.
- Linux: to install pyenv use [the automated installer](https://github.com/pyenv/pyenv-installer) or follow [the manual installation instructions on Github](https://github.com/pyenv/pyenv#basic-github-checkout).
  ```
  curl -L https://github.com/pyenv/pyenv-installer/raw/master/bin/pyenv-installer | bash
  ```
  The installer will output some configuration code at the end that needs to be added to your shell’s rc file:
  ```
  #ensure the following is in your ~/.<SHELL>rc (.bashrc, .zshrc, .kshrc)export PATH="$HOME/.pyenv/bin:$PATH"
  eval "$(pyenv init -)"
  eval "$(pyenv virtualenv-init -)"
  export PYENV_ROOT="$HOME/.pyenv" # needed by pipenv
  ```
  Finally, refresh your shell:
  ```
  source ~/.<SHELL>rc
  ```
- Windows: Use [the Pyenv-win fork](https://github.com/pyenv-win/pyenv-win) and follow [the installation instructions](https://github.com/pyenv-win/pyenv-win#installation)
- macOS: [install via Homebrew](https://github.com/pyenv/pyenv#homebrew-on-macos)
  ```
  $ brew update
  $ brew install pyenv
  ```

Once pyenv is installed you should check out all Python interpreter versions that are at your fingertips:

```
pyenv install --list
```



# Pipenv

# Pipx

# New Project Workflow

# Existing Project Workflow

# Alternatives
- [Poetry](https://poetry.eustace.io/): Poetry is a snappier packaging and dependency manager to replace Pipenv. Unlike Pipenv, Poetry does not include Python interpreter versioning, is less widely used, and is not officially supported by [the Python Packaging Authority](https://www.pypa.io). Poetry however is [significantly faster](https://johnfraney.ca/posts/2019/03/06/pipenv-poetry-benchmarks-ergonomics/) when locking in dependencies and this translates to less waiting around when writing code. I will keep an eye on this promising project and follow up with an update after using it for a while.
- [Conda](https://docs.conda.io): I personally have very bad experiences using Conda to install data-science and deep learning frameworks. Many conda packages are broken and unmaintained. While pip is integrated into Conda, pipenv is the more flexible alternative. Conda is bloated compared to other tools, suffers from feature creep, and places itself outside of the Python ecosystem.