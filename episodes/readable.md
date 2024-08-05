---
title: 'Code readability'
teaching: 10
exercises: 2
---

:::::::::::::::::::::::::::::::::::::: questions 

- What is code readability?
- How do I make my code easier to interpret?
- How do I explain the purpose of my code?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Understand the common ways to make code easy to read
- Learn how to write code comments
- Learn to document variable types in Python and R

::::::::::::::::::::::::::::::::::::::::::::::::

It’s a common trope in the software engineering world that code is **read much more often than it is written**. It’s important that our code is **approachable** for new people to use with confidence, as they might want to review the code itself to understand what it does. Also, when you maintain your code, or come back to it in the future, you’ll be grateful for the effort you made in making it easy to interpret and follow its logic.

## Syntax highlighting

Many text editors use syntax highlighting to display parts of your source code using different colours or fonts to signify the meaning of each word or symbol.
For example, variable names may be given a bright blue colour, strings highighted in green, and numbers shown in a red font.

Let's take a look to see its benefits:

::: group-tab

### Python

Without syntax highlighting:

```output
def count_word_occurrences(filename, word_to_count):
  """
  This function counts the number of times a specific word appears in a text file.
  """
  word_count = 0
  # Read the file line by line
  with open(filename, "r") as text_file:
    for line in text_file:
        # Convert the line to lowercase for case-insensitive counting
        line = line.lower()
        words = line.split()

        # Count the occurrences of the word in the current line
        word_count += words.count(word_to_count)

  return word_count
```

With syntax highlighting:

```python
def count_word_occurrences(filename, word_to_count):
  """
  This function counts the number of times a specific word appears in a text file.
  """
  word_count = 0
  # Read the file line by line
  with open(filename, "r") as text_file:
    for line in text_file:
        # Convert the line to lowercase for case-insensitive counting
        line = line.lower()
        words = line.split()

        # Count the occurrences of the word in the current line
        word_count += words.count(word_to_count)

  return word_count
```

### R

Without syntax highlighting:

```default
#' Function to count word occurrences in a text file
count_word_occurrences <- function(filename, word_to_count) {
  text_file <- file(filename, "r")
  word_count <- 0
  
  # Read the file line by line using a loop
  for (line in readLines(text_file)) {
    # Convert the line to lowercase for case-insensitive counting
    line <- tolower(line)
    
    # Split the line into words
    words <- strsplit(line, split = " ")[[1]]  # Extract the first element (vector of words)
    
    # Count the occurrences of the word in the current line
    word_count <- word_count + sum(words == word_to_count)
  }
  close(text_file)
  return(word_count)
}

```

With syntax highlighting:

```R
# Function to count word occurrences in a text file
count_word_occurrences <- function(filename, word_to_count) {
  text_file <- file(filename, "r")
  word_count <- 0
  
  # Read the file line by line using a loop
  for (line in readLines(text_file)) {
    # Convert the line to lowercase for case-insensitive counting
    line <- tolower(line)
    
    # Split the line into words
    words <- strsplit(line, split = " ")[[1]]  # Extract the first element (vector of words)
    
    # Count the occurrences of the word in the current line
    word_count <- word_count + sum(words == word_to_count)
  }
  close(text_file)
  return(word_count)
}
```

:::

Which bit of code is easier to read? What a difference a splash of colour makes! I know which development environment I'd rather work in.

To work with our source code in a colourised way like this, use a text editor or IDE with a syntax highlighting feature such as Notepad++, VSCode, PyCharm, or RStudio.

## Meaningful names

Our code should convey as much **meaning** as possible to the user or developer that's trying to interpret it.

### Variable naming

Every variable has a *name* and a *value*.
For example, the code `x = 42` creates a variable named `x` that has the numerical value of four.
But what does `x` mean? Is it the number of swallows required to carry a coconut? In this case, we have no idea.

That's where **meaningful variable names** come in. Always try to name variables using a noun that describes its contents.
For example, in our case we'd use `laden_coconut_capacity = 42` which is much clearer.

### Function names

A function contains code that defines the performance of an **action**. As with variables, the name of a function should **describe its behaviour** so that the user of that code can anticipate what it will do when they run it.
A vague function name, such as `calc(a, b)` will be mysterious without any more explanation.
Name your functions using a **simple verb phrase** such as `calculate_area(width, height)` so it's easy to interpret their purpose.

::: group-tab

### Python

```python
def calculate_area(width, height):
    """
    Work out the surface area of a rectangle with the specified dimensions.
    """
    area = width * height
    return area
```

### R

```R
calculate_area <- function(width, height) {
  """
  Work out the surface area of a rectangle with the specified dimensions.
  """
  area <- width * height
  return(area)
}
```

:::

### Naming conventions

The communities of developers that use each programming language usually follow a conventional approach when naming objects in their code.

It's also a good idea not to use single-letter names such as `x` or `T` because it may not be clear to someone else what these represent. Also, avoid the common pitfall of naming a variable with the same name as an inbuilt function such as `sum()`.

::: group-tab

### Python

Classes use capitalised words

```python
class VectorSpace:
    pass
```

Variables use lower case with underscores

```python
my_user_name = "Joe"
```

Constants are named using upper case with underscores

```python
NEGATIVE_ONE = -1
```

 the [Naming Conventions](https://peps.python.org/pep-0008/#naming-conventions) section of <acronym title="Python Enhancement Proposals">PEP</acronym> 8.

### R

Classes use capitalised words

```R
setClass("VectorSpace", representation = character())
```

Variables use lower case with underscores

```R
my_user_name <- "Joe"
```

Constants are named using upper case with underscores

```R
NEGATIVE_ONE <- -1
```

For more information about this aspect of coding style, please read the [Tidyverse Style Guide](https://style.tidyverse.org/).

:::

Although these rules aren't strict, because your code will still run without error, it does help clarify your intentions by describing what type of variable or object is being referred to. Whatever you do, please try to follow a consistent style with your collaborators to avoid confusion.

## Comments

Code **comments** allow us to annotate any part of our software with a human-readable description of the expected behaviour of the code or our general intentions to aid the reader in their interpretation. Start writing these as soon as you begin development work, as they'll capture your thought process while the knowledge is fresh in your mind, avoiding the risk of forgetting important details.

To add comments to your code, use the `#` symbol at the start of a new line, like so:

::: group-tab

### Python

```python
# Add three to my age
age = 21
age =+ 3
```

### R

```R
# Add three to my age
age <- 21
age = age + 3
```

:::

It's best practice to use a very concise style when writing code comments. I recommend using active tense verbs.

## Type hints

Type hints display the expected *type* of each object in your code. They are a kind of "documentation as code" that annotate the code that's already there, rather than being written as separate documentation. While they don't change the way the software works, they can help to improve code clarity and may be used to catch errors early in the development process.

### Type hints for variables

When reading source code, it can be useful to know the type of each variable so we get an idea of what possible values they might contain as they move through the system.

::: group-tab

### Python

In the Python programming language, we can tell the user what type of data we expect each variable to contain by using the syntax below. This colon means that the `age` variable should contain a value with the integer type, `int`.

```python
age: int = 21
```

For more information, please see the [typing section](https://docs.python.org/3/library/typing.html) of the Python Documentation and the [Type hints cheat sheet](https://mypy.readthedocs.io/en/stable/cheat_sheet_py3.html) in the mypy documentation.

### R

There is no type hinting feature in base R, although some packages are available that enable this. Here, the `L` symbol at the end of the number tells the R interpreter that this is an integer data type that should only contain whole numbers.

```R
# Integer
age <- 21L
```

:::

Using type hints will make sure your code much easier to read and provide helpful documentation for others, and yourself in the future.

### Function argument type hints

They can also be used to label the input and output types of functions.  They are not strictly enforced, but act as a guide to the reader.

::: group-tab

### Python

Below is the source code for a simple Python function that calculates the sum of two numbers. I've labelled each of the function arguments `a` and `b` with variable annotations that let you know that the expected inputs are whole numbers because `int` is short for the *integer* type. The result of this mathematical operation is also expected to be an integer, so the return type is labelled with the arrow syntax on the first line of the function declaration as `-> int`.

```python
def add(a: int, b: int) -> int:
    """Add two numbers"""
    return a + b
```

### R

Below is the source code for a simple R function that calculates the sum of two numbers.

In R, there is no inbuilt functionality for annotating the expected types of variable arguments, but this can be done with the [roxygen2](https://roxygen2.r-lib.org/) library. The code block below shows a docstring (which we covered earlier in the course) that labels the types of the inputs and output of the function.

```R
#' @title Add two numbers
#' @param a integer
#' @param b integer
#' @return integer
add <- function(a, b) {
  if (is.numeric(a) && is.numeric(b)) {
    return(a + b)
  } else {
    return(paste(a, b, sep = ""))
  }
}
```

:::

::::::::::::::::::::::::::::::::::::: challenge

### Type hints quiz

What do you expect to happen when the following code runs?

```python
add(42, 1)
```

What about this code?

```python
add(42.5, 1e5)
```

Will an error occur when we use strings as the input arguments?

```python
add('cheese', 'cake')
```

:::::::::::::::: solution

None of these code examples will cause an error because type hints are just passive labels that document our code. They don't enforce any type checking or rules that are asserted when the code is executed. This means that, while type hints are very useful for *static analysis* of code, where we learn something about a piece of software without running it.

:::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::

This is just a brief introduction to code annotation. For the keen coder, there are many more features and tools available to make your software easier for other people to understand and use.

It will take some time and effort to write these labels, but it will pay off in the long run to think about variables tapes and make it easier to interpret how the code will behave as it operates. It's best practice to use an integrated development environment (IDE) that will check your type hints and inform you if it detects a problem with your source code.

::::::::::::::::::::::::::::::::::::: keypoints 

- Try to inject as much *meaning* into your source code as possible by naming things clearly and succintly.
- Use comments to explain your rationale&mdash;even if the code seems obvious to you know, think of the future benefits!
- Label functions and variables with *type hints* to tell the user what data types are expected.

::::::::::::::::::::::::::::::::::::::::::::::::
