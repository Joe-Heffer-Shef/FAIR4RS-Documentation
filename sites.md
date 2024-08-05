---
title: 'Documentation sites'
teaching: 10
exercises: 2
---

:::::::::::::::::::::::::::::::::::::: questions 

- What is a documentation website for research software?
- How do I generate a website containing a user guide to my code?
- What should my documentation site contain?
- How do I publish my software documentation on the internet?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Learn about documentation websites for software packages.
- Gain basic familiarity with some common website generation tools.
- Understand the basics of structuring a documentation website.
- Be able to set up a static site deployment workflow.

::::::::::::::::::::::::::::::::::::::::::::::::

## Introduction

A documentation website is a user guide and reference manual for a library of research code. Up to now, we've looked at ways to put helpful notes in our code, but now we'll learn how to write a longer, more complete guide to the research tools you create.

A documentation site bring all your user guidance into one place. This kind of resource may be prepared for research software and will usually contain an introduction, installation instructions, a user guide, troubleshooting tips, and an in-depth reference section.

To get an idea of this, here are some links documentation websites for widely-used data analysis and research software packages:

- [pandas](https://pandas.pydata.org/docs/) is a data processing library for the Python programming language.
- [ggplot2](https://ggplot2.tidyverse.org/index.html) is a plotting package for the R statistical language.
- [scikit-learn](https://scikit-learn.org/stable/user_guide.html) is a machine learning library for the Python programming language.

### Advantages

There are many advantages to building a documentation site to provide a information-rich resource for researchers who use your code at institutions all around the world. These sites can work as hubs for collaboration, sharing the latest updates, and encouraging people to take up your system and get involved in improving it. The effort of setting one up will be rewarded in the long run because you will have created a valuable asset that will foster collaboration and knowledge sharing in your research community.

A key foundation stone of modern digital research practices is the ability to replicate results by reproducing analysis workflows.  Clear, thorough documentation of the research code ensures that researchers can repeat processes and verify results and other people's outputs.

Documementation sites are really useful for introducing new users to your software. It makes it much easier and faster for new users to get started using your software to boost their research. It's one of the most effective ways to create a user base that has a sophisticated understanding of the research code, which is essential for them to adapt it to the complex problems that often raise in research contexts.

They're also a valuable resource for your existing user base, enabling them to look up reference material or search the manual to find new capabilities they weren't aware of before. This will increase the potential for your software to accellerate the productivity of other research teams and boost scientific progress.

### When to use one

Although the advantages are numerous, not all software packages require a comprehensive documentation website. However, for any code project that is growing in the number of collaborators, users, and technicala complexity, consider coordinating the team to write one as soon as possible to help the project grow in a healthy manner.

### Writing style

Strive to use everyday, jargon-free language. It helps to set an approachable tone that encourages others to use the software and get involved with the project. This will en sure that the code is accesible to the widest possible layers of the research community and foster collaboration.

Always consider the target audience of your documentation, because your user base may be unaware of some of the unstated assumptions and technical backgroud knowledge that you take for granted.

## Contents

Documentation pages contain comphrehensive information about a particular piece of research software. Think of it like a user manual for your car or an instruction guide for building a piece of furniature.

### Research context

For research software, it may be important to explain the theoretical background or statistical methods that are used and explain the domain-specific assumptions that were made when the code was designed and written. It's good practice to provide a concise summary of the relevent concepts and link to external sources such as papers, books, and other websites for users to take a deeper dive into the principles and algorithms used.

### Installation instructions

This section provides a detailed walkthrough of the steps required to install the package onto their computer, with details that are specific to their operating system.

### Tutorials

It can be very useful to include an in-depth "Getting Started" guide that provides step-by-step instructions to introduce a new user to your software package. It might guide the user through each aspect of the tool's functionality and features so they're able to become familiar with it in a more approachable way.

A series of code examples to demonstrate how to use the software in different contexts can be very useful for users to get off the ground in implementing common research workflows to achieve their specific goals.

### User reference

If you have written functions that are intended to be use in other reseachers' code, then an on-depth explaination of these procedures is essential reference material. In the world of software engineering, these detailed appendices are called <acronym title="Application Programming Interfaces">API</acronym> references, which list each function and describe how the arguments may be used to control how the code works. This content may be automatically generated from the documentation strings.

### Troubleshooting

As issues come up with your research code, and are eventually resolved and clarified, make a note of the causes of these troubles and make them available to the entire user base in your documentation site. This will help users to identify and fix common misunderstandings and technical problems they may run into when utilising your code.

This prevents a situation where potential solutions to common issues do exist, but are scattered around the internet are the exclusive knowledge of a few individuals and are hard to find.

### FAQs

An appendix containing frequently asked questions (FAQs) is very useful to save yourself time in responding to common queries from the users of your code.

## Tools

There are various tools available to build documentation sites for your research software.

### GitHub Wiki

If you are publishing your code on GitHub, which is a web service that hosts costs repositories, then one of the easiest ways to create a documentation site is to use the wiki feature on that platform. This is a great way to write detailed, structured documents containing long-form content that describes aspects of your software. What's more, it's available alongside your code so your documentation and software are located in one place.

As with readme files, the text that appears on GitHub is [formatted using Markdown syntax](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github).

#### Getting started

To create a wiki, which is a simple, easy-to-edit web site, go to the main page of your code repository on GitHub and click on the Wiki button on the top menu. For a detailed walkthrough of this process, please read [adding or editing wiki pages](https://docs.github.com/en/communities/documenting-your-project-with-wikis/adding-or-editing-wiki-pages) on the GitHub documentation.

::: callout

For more information about the wiki feature on GitHub, see [Documenting your project with wikis](https://docs.github.com/en/communities/documenting-your-project-with-wikis) on the GitHub documentation.

:::

### Sphinx

[Sphinx](https://www.sphinx-doc.org/) is a tool for building documentation websites that is commonly used amongst developers of Python packages, although it's also compatible with other programming languages. It doesn't currently support packages written using the R statistical language.

Sphinx is a documentation generator tool takes plain text files that use a markup syntax (such as reStructuredText or Markdown) for formatting the content of your documentation site and transforms them into various output formats, ready to be published on the internet. It has a number of useful features, but in this module we'll learn the basics to document our research code.

::: callout

For a more in-depth guide, please see [Build your first project](https://www.sphinx-doc.org/en/master/tutorial/) in the Sphinx documentation.

:::

#### Getting started

Let's use Sphinx to create a documentation site for our Python code.

##### Installing Sphinx

Navigate to the root folder of your code project. Create a virtual environment using [venv](https://docs.python.org/3/library/venv.html) which is a separate area in which to install the Sphinx package.

```bash
python -m venv .venv
```

This will create a subdirectory that contains the packages we'll need to complete the exercises in this section.

Run the activation script to enable the virtual environment. The specific command needed to activate the virtual environment depends on the operating system you are using.

::: group-tab

### Windows

```bash
.venv\Scripts\activate
```

### Linux

```bash
source .venv/bin/activate
```

### macOS

```bash
source .venv/bin/activate
```

Use the Python package manager [pip](https://pip.pypa.io/en/stable/) to [install Sphinx](https://www.sphinx-doc.org/en/master/usage/installation.html).

```bash
pip install sphinx
```

:::

##### Start a new Sphinx project

Sphinx includes a command to set up a new project called [sphinx-quickstart](https://www.sphinx-doc.org/en/master/man/sphinx-quickstart.html). Navigate to your project's root folder and run the following command. 

```bash
sphinx-quickstart docs --no-sep --ext-autodoc
```

This will initialise the configuration files for a new Sphinx site in a subdirectory called `docs/` and prompt you to enter the following options:

* Project name: Birdsong Identifier
* Author name(s): Bill Oddie
* Project release []: 1.0

::: callout

To find out more about the Sphinx configuration files, please read their guide to [defining document structure](https://www.sphinx-doc.org/en/master/usage/quickstart.html#defining-document-structure) on the Sphinx documentation.

:::

#### Building the site

In this context, building means taking our collection of Sphinx files and converting them into the source code files that define a website. Sphinx will create HyperText Markup Language (HTML) files, which is the markup language for pages that display in a web browser commonly used on the internet.

To build our site, we run the [sphinx-build](https://www.sphinx-doc.org/en/master/man/sphinx-build.html) command using the `-M` option to select HTML syntax as the output format.

```bash
sphinx-build -M html docs docs/_build
```

Sphinx will load our files from the `docs/` directory and output the built HTML files in the `docs/_build` directory.

The file `docs/_build/html/index.html` contains the home page of your new documentation site! Open that file to view your handiwork.

![The Sphinx homepage for our documentation site](fig/sphinx-build-screenshot.png "Sphinx")

#### Autodoc

It can be useful to automatically populate our documentation sites by converting our [documentation strings](docstrings.md) into formatted text. We can achieve this using the [autodoc](https://www.sphinx-doc.org/en/master/usage/extensions/autodoc.html) plugin for Sphinx.

##### Configuring Autodoc

Let's set up the options for `autodoc`.

If you struggle with these steps, please refer to the [template project](https://github.com/Joe-Heffer-Shef/oddsong).

Add the following lines to `docs/conf.py`

```python
# Our Python code may be imported from the parent directory
import os
import sys
sys.path.insert(0, os.path.abspath('..'))
```

This ensures that Sphinx can access our Python code.

Next, edit `docs/index.rst` and add the following lines:

```rst
.. automodule:: oddsong.song
    :members:
```

Now, when we build our site, Sphinx will scan the contents of the `oddsong` Python module and automatically generate a useful reference guide to our functions.

```bash
sphinx-build -M html docs docs/_build
```

The result looks something like this:

![Python documentation string rendered as HTML](fig/oddsong-autodoc.png "A Python function documentation string")

::::::::::::::::::::::::::::::::::::: challenge

## Automatically generated content

Try using `autodoc`.

:::::::::::::::: solution

TODO

:::::::::::::::::::::::::
:::::::::::::::::::::::::::::::::::::::::::::::

### Documentation sites for R packages

It's also possible to generate a documentation site to accompany R packages that you create. 
For more information about this, please refer to the book *R Packages* by Hadley Wickham, which
has a chapter on [documentation websites](https://r-pkgs.org/website.html).

## Publishing

Now that you've started writing your documentation website, there are various ways to upload it to the internet so that others can read it.

There are several hosting services that can be used to publish your documentation site, such as [GitHub Pages](https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages) and [Read the Docs](https://about.readthedocs.com/).

The detailed of setting up the deployment of your site to these platforms is beyond the scope of this course.

::::::::::::::::::::::::::::::::::::: keypoints 

- Structured documentation websites are very useful for users to learn to use all kinds of digital systems, ensuring its successful adoption by the wider research community.
- Documentation sites contain comprehensive installation instructions, user guides, and troubleshooting tips.
- There are several libraries that may be used to generate documentation sites.
- Documentation websites may be deployed to a hosting platform.

::::::::::::::::::::::::::::::::::::::::::::::::
