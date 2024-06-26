---
title: "Why document code?"
teaching: 10
exercises: 2
---

:::::::::::::::::::::::::::::::::::::: questions

- What is software documentation?
- Why is documenting code useful for researchers?
- What does well-documented software look like?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Understand the basic purpose of this course
- Learn the motivation for learning to document software
- Be introduced to good software documentation practices

::::::::::::::::::::::::::::::::::::::::::::::::

## Introduction

No code is self-explanatory. It’s a tool we design, or, more often, a complex organism that develops as we use it, such as a library of functions used within a research team to perform certain kinds of analysis.

To explain our code we must write **software documentation**. These documents provide information about our  programs for everyone involved in its development, use, and future re-use. Documentation may consist of text, tips within a computer environment, and diagrams that guide the user in using a (potentially complex) software tool. It explained how the software works why it behaves the way it does.

## Why document software?

It’s a common occurrence to get a software package, whether it’s written by ourselves, a colleague, or someone else, that’s near-impossible to use because it’s unclear what each function or tool does. Maybe we look at the source code itself, but we can’t make head-nor-tail of it. Maybe the only person who can use this software is the person who wrote it—unless you wrote it and forgot what you were thinking when you did!

### Advantages of good documentation

There are many advantages to writing guidance to go along with your research software. Software documentation helps yourself and others to use it successfully in the future and read your code ensuring that its value is sustained.

Research outputs often depend upon the code used to generate them. Clarity and confidence are essential in using code to perform calculations, simulations, or data analysis. All kinds of research processes and analysis pipelines can be made more **reproducible** by providing clear context and instructions for using it.

There are many advantages to making your code more readable. Well-documented software is easier to maintain and has greater sustainability, which means it can continue to be used and modified for a longer period of time, despite changes in technology. If software is more reusable then it encourages others to use it for their research, increasing the number of citations of that software and its overall research impact.

Writing a useful software package that is well-documented and can be reused in the future means that your code could take on a life of its own, with benefits that extend beyond yourself to your collaborators and other researchers in the future.

In the long run, it can help you to develop your own software engineering practice by getting into the habit of reflecting on what the purpose of the software is and to articulate what each component or module is for.

## When should I write documentation?

Now! Start writing and sharing documentation for your reseach code from the beginning of your project. This might include design notes, diagrams, or the various kinds of software documentation we'll discuss in this module. The best practice for modern, collaborative research involving digital methods and tools is to document your processes *early and often*. Not only will writing notes about your code help other people to read and use that code, it will clarify your thought process as you design your system, focussing your work on the important parts of the task at hand.

Keep in touch with other developers and users of the research code and make a note of their feedback. Common questions and problems are a sign that there are issues that must be covered more clearly and in greater depth in the software documentation. Incorporate this feedback into the software documentation using the whichever method is most appropriate, following the guidance in this module.

## Examples

Here are some examples of some code to perform some geometry. The first example could be improved in terms of its documentation and readability, while the second one is much clearer. Which one would you prefer to use?

### Example of no documentation

Here's an example of some code that does... something. It's not clear what this code is for or why it was written.

::: group-tab

### Python

This is some research code that is contained in a Python function.

```python
def run(x):
  weird_num = 1.234
  return x * weird_num - angle**3 / (weird_num * 2)
```

### R

This is some research code that is contained in an R function.

```R
run <- function(x) {
  weird_num = 1.234
  return x * weird_num - angle**3 / (weird_num * 2)
}
```

:::

This is a function with a name that doesn't explain what the code will do. There are no comments or notes to explain what the author intended to achieve. The variable names don't clarify anything either: what does `x` mean in this context? Where would I go to find out more about `weird_num`? This is effectively a "magic" number that is arbitrarily stated but unexplained.

The logic of the calculation is also... rather cryptic.

Maybe the code works, maybe it doesn't (would you trust it?) but it could be made clearer and easier to maintain and modify in the future.

### Well-documented example

Now let's look at an example of best practices in documenting research software.

::: group-tab

### Python

This is a function written in the Python programming language that calculates a mathematical result, the details of which aren't relevant. This code has plenty of documentation to help us read and understand it.

```python
import math

def calculate_sine(angle: float) -> float:
  """
  Calculates the sine of an angle using the first four terms of the Taylor series.

  This function uses the first four terms of the Taylor series for sine to approximate
  the value. This is a simple and efficient method for most applications.

  Args:
      angle (float): The angle in radians.

  Returns:
      float: The sine of the angle (sin(angle)).
  """
  sin_value = angle

  # Iterate over the first four terms of the Taylor series for sine
  for i in range(1, 5):
    factorial = math.factorial(2 * i)
    sign = (-1) ** (i // 2)  # Alternate signs for sine terms

    # Add terms for sine
    sin_value += sign * (angle ** (2 * i)) / factorial

  return sin_value
```

### R

This is a function written in the R programming language that calculates a mathematical result, the details of which
aren't relevant. This code has plenty of documentation to help us read and understand it. R uses the
[roxygen2][roxygen2] package to build the docstrings into internal documentation and optionally external API documentation.

```R
#' Calculate the sine of an angle
#'
#' @description
#'
#' This function uses the first four terms of the Taylor series for sine to approximate
#' the value. This is a simple and efficient method for most applications.
#'
#' @param angle
#'
#' @returns The sine of the angle (sun(angle)).
calculate_sine <- function(angle) {
  sin_value <- angle

  # Loop for the first four terms
  for (i in 1:4) {
    factorial <- factorial(2 * i)
    sign <- (-1)^(i %% 2)  # Alternate signs with modulo (%)

    # Add terms for sine
    sin_value <- sin_value + sign * (angle^(2 * i)) / factorial
  }

  return(sin_value)
}
```

:::

This time, the function name is a verb that describes what the code will attempt to do. The description of the function is also written out clearly in a note for the user. There are comment lines (starting with `#`) that explain the mathematicalal method used. Each variable has a descriptive, human-readable name, making the code more intuitive to read. An existing library is used to calculate the factorial, which means we can look up the usage for the `factorial()` function elsewhere.

This approach means that our code is much easier to interpret, maintain, and make changes to in the future.

Of course, there may be some syntax in this example that is unfamiliar to you&mdash;but don't worry, we'll learn the basics in this course!

:::::: keypoints

 - **Reproducibility:** Well-documented software is easier for other researchers to understand and use with confidence. It enables them to **reproduce your results** to replicate research findings, enabling others to validate them and building trust in your research outputs.
 - **Collaboration:** Clear instructions enable other researchers to use and **collaborate** with your software and research projects.
 - **Knowledge transfer:** Your software package will be easier to maintain in the long term if others are able to learn about it and look after it after the original developers move on.

::::::

[roxygen2]: https://roxygen2.r-lib.org/index.html
