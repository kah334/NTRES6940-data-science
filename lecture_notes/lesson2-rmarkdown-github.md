Lesson 2: RMarkdown and Github
================

<br>

## Readings

#### RMarkdown

Required:  
\- [Chapter 27 in Grolemund and Wickham’s R for Data
Science](https://r4ds.had.co.nz/r-markdown.html)  
\- Have a look at the [RMarkdown
website](https://rmarkdown.rstudio.com/lesson-1.html) including [this
video](https://rmarkdown.rstudio.com/authoring_quick_tour.html)

Additional resources:  
\- [RStudio’s R markdown
cheatsheet](http://www.rstudio.com/wp-content/uploads/2016/03/rmarkdown-cheatsheet-2.0.pdf)  
\- The [Rmd website](https://rmarkdown.rstudio.com/) has a fantastic
walk-through [tutorial](https://rmarkdown.rstudio.com/lesson-1.html)
that gives a great overview of R Markdown - Yihui’s [Rmd
book](https://bookdown.org/yihui/rmarkdown/) for lots more on R
Markdown.

<br>

#### GitHub

Required:  
\- [Chapter 1 in Jenny Bryan’s Happy Git with
R](https://happygitwithr.com/big-picture.html)

Additional resources:  
\- [Excuse me, do you have a moment to talk about version
control?](https://peerj.com/preprints/3159/) by Jenny Bryan  
\- [GitHub for Project
Management](https://openscapes.github.io/series/github-issues.html) by
Openscapes

<br>

## Class announcments

  - Course communication will primarily be through Slack. Please make
    sure to join our workspace to not miss announcements about
    scheduling changes etc.
  - Course website and readings - links posted on syllabus schedule
  - [Problem
    set 1](https://github.com/nt246/NTRES6940-data-science/blob/master/assignments/assignment_1.md)
    is due next Wednesday March 11
  - Remember office hours / hacky hour Friday 3-5 in Fernow 110
  - Sticky notes - get a set of green and red

<br>

## Learning objectives for today’s class

By the end of today’s class, students are expected to be able to:

  - Write documents in markdown on GitHub and RStudio, and render these
    documents to html and pdf with RStudio.
  - Choose whether html or pdf is an appropriate output
  - Style an Rmd document by editing the YAML header
  - Demonstrate at least two Rmd code chunk options
  - Make presentation slides using one of the R Markdown presentation
    formats.

<br>

**Acknowledgements**: Today’s lecture is adapted (with permission) from
the excellent [R for Excel
users](https://rstudio-conf-2020.github.io/r-for-excel/) course by Julia
Stewart Lowndes and Allison Horst.

<br>

## Introduction to RMarkdown

An RMarkdown file is a plain text file that allow us to write code and
text together, and when it is “knit”, the code will be evaluated and the
text formatted so that it creates a reproducible report or document that
is nice to read as a human.

This is really critical to reproducibility, and it also saves time. This
document will recreate your figures for you in the same document where
you are writing text. So no more doing analysis, saving a plot, pasting
that plot into Word, redoing the analysis, re-saving, re-pasting, etc.

This 1-minute video provides a great introduction to RMarkdown: [What is
RMarkdown?](https://vimeo.com/178485416).

Now let’s explore the RMarkdown format a bit ourselves to get started.

### Create an RMarkdown file

It’s super easy to get started with RMarkdown within RStudio. Let’s do
this together:

File -\> New File -\> RMarkdown… (or alternatively you can click the
green plus in the top left -\> RMarkdown).

Let’s title it “Testing” and write our name as author, then click OK
with the recommended Default Output Format, which is HTML.

<img src="../img/rstudio_new-rmd-doc-html.png" width="80%" />

OK, first off: by opening a file, we are seeing the 4th pane of the
RStudio console, which here is a text editor. This lets us dock and
organize our files within RStudio instead of having a bunch of different
windows open (but there are options to pop them out if that is what you
prefer).

Let’s have a look at this file — it’s not blank; there is some initial
text is already provided for you. Let’s have a high-level look through
of it:

  - The top part has the Title and Author we provided, as well as
    today’s date and the output type as an HTML document like we
    selected above.
  - There are white and grey sections. These are the 2 main languages
    that make up an RMarkdown file.
      - **Grey sections are R code**
      - **White sections are Markdown text**
  - There is black and blue text (we’ll ignore the green text for now).

<img src="../img/rmarkdown.png" width="80%" />

### Knit your RMarkdown file

Let’s go ahead and “Knit” by clicking the blue yarn at the top of the
RMarkdown file. It’s going to ask us to save first, I’ll name mine
“testing.Rmd”. Note that this is by default going to save this file in
your home directory `/~`. Since this is a testing document this is fine
to save here; we will get more organized about where we save files very
soon. Once you click Save, the knit process will be able to continue.

OK so how cool is this, we’ve just made an html file\! This is a single
webpage that we are viewing locally on our own computers. Knitting this
RMarkdown document has rendered — we also say formatted — both the
Markdown text (white) and the R code (grey), and the it also executed —
we also say ran — the R code.

Let’s have a look at them side-by-side:

<br>

<img src="../img/rmarkdown_side_by_side.png" width="80%" />

Let’s take a deeper look at these two files. So much of learning to code
is looking for patterns.

#### Activity

Introduce yourself to the person sitting next to you. Discuss what you
notice with these two files. Then we will have a brief share-out with
the group. (5 mins)

### Markdown text

Let’s look more deeply at the Markdown text. Markdown is a formatting
language for plain text, and there are only a handful of rules to know.

Notice the syntax for:

  - **headers** with `#` or `##`
  - **bold** with `**`

To see more of the rules, let’s look at RStudio’s built-in reference.
Let’s do this: Help \> Markdown Quick Reference

There are also good
[cheatsheets](https://github.com/adam-p/markdown-here/wiki/Markdown-Here-Cheatsheet)
available online.

<!---
#### Activity
1. In Markdown write some italic text, make a numbered list, and add a few subheaders.
 Use the Markdown Quick Reference (in the menu bar: Help > Markdown Quick Reference). 
1. Reknit your html file. 
--->

### R code

Let’s look at the R code that we see executed in our knitted document.

We see that:

  - `summary(cars)` produces a table with information about cars
  - `plot(pressure)` produces a plot with information about pressure

There are a couple of things going on here.

`summary()` and `plot()` are called **functions**; they are operations
and these ones come installed with R. We call functions installed with R
**base R functions**. This is similar to Excel’s functions and formulas.

`cars` and `pressure` are small datasets that come installed with R.

We’ll talk more about functions and data shortly.

### Code chunks

R code is written in code chunks, which are grey.
<!---There are two things to look at: R code chunks and code chunk options --->

Each of them start with 3 backticks and `{r label}` that signify there
will be R code following. Anything inside the brackets (`{ }`) is
instructions for RMarkdown about that code to run. For example:

  - the first chunk labeled “setup” says `include=FALSE`, and we don’t
    see it included in the HTML document.
  - the second chunk labeled “cars” has no additional instructions, and
    in the HTML document we see the code and the evaluation of that code
    (a summary table)
  - the third chunk labeled “pressure” says `echo=FALSE`, and in the
    HTML document we do not see the code echoed, we only see the plot
    when the code is executed.

> **Aside: Code chunk labels** It is possible to label your code chunks.
> This is to help us navigate between them and keep them organized. In
> our example Rmd, our three chunks say `r` as the language, and have a
> label (`setup`, `cars`, `pressure`).  
> Labels are optional, but will become powerful as you become a powerful
> R user. But if you label your code chunks, you must have unique
> labels. So while a third option for creating a new code chunk is to
> copy-paste-edit an existing one, you’ll have to remember to relabel it
> something unique. We will explore this more in a moment. Notice how
> the word `FALSE` is all capitals. Capitalization matters in R;
> `TRUE/FALSE` is something that R can interpret as a binary yes/no or
> 1/0.

There are many more options available that we will discuss as we get
more familiar with RMarkdown.

#### New code chunks

We can create a new chunk in your RMarkdown first in one of these ways:

  - click “Insert \> R” at the top of the editor pane (with the green
    plus and green box)
  - type it by hand: \`\`\`{r} \`\`\`

> **Aside**: doesn’t have to be only R, other languages supported. Let’s
> create a new code chunk at the end of our document.

Now, let’s write some code in R. Let’s say we want to see the summary of
the `pressure` data. I’m going to press enter to to add some extra
carriage returns because sometimes I find it more pleasant to look at my
code, and it helps in troubleshooting, which is often about identifying
typos. R lets you use as much whitespace as you would like.

``` r
summary(pressure)
```

We can knit this and see the summary of `pressure`. This is the same
data that we see with the plot just above.

> Troubleshooting: Did trying to knit your document produce an error?
> Start by looking at your code again. Do you have both open `(` and
> close `)` parentheses? Are your code chunk fences (\`\``) correct? ##
> R code in the Console So far we have been telling R to execute our
> code only when we knit the document, but we can also write code in the
> Console to interact with the live R process. The Console (bottom left
> pane of the RStudio IDE) is where you can interact with the R engine
> and run code directly. Let's type this in the
> Console:`summary(pressure)\` and hit enter. We see the pressure
> summary table returned; it is the same information that we saw in our
> knitted html document. By default, R will display (we also say
> “print”) the executed result in the Console

``` r
summary(pressure)
```

We can also do math as we can in Excel: type the following and press
enter.

``` r
8*22.3
```

### Error messages

When you code in R or any language, you will encounter errors. We will
discuss troubleshooting tips more deeply tomorrow in [Collaborating &
getting help](#collaboration); here we will just get a little
comfortable with them.

#### R error messages

**Error messages are your friends**.

What do they look like? I’ll demo typing in the Console
`summary(pressur)`

``` r
summary(pressur)
#> Error in summary(pressur): object 'pressur' not found
```

Error messages are R’s way of saying that it didn’t understand what you
said. This is like in English when we say “What?” or “Pardon?” And like
in spoken language, some error messages are more helpful than others.
Like if someone says “Sorry, could you repeat that last word” rather
than only “What?”

In this case, R is saying “I didn’t understand `pressur`”. R tracks the
datasets it has available as objects, as well as any additional objects
that you make. `pressur` is not among them, so it says that it is not
found.

The first step of becoming a proficient R user is to move past the
exasperation of “it’s not working\!” and **read the error message**.
Errors will be less frustrating with the mindset that **most likely the
problem is your typo or misuse**, and not that R is broken or hates you.
Read the error message to learn what is wrong.

#### RMarkdown error messages

Errors can also occur in RMarkdown. I said a moment ago that you label
your code chunks, they need to be unique. Let’s see what happens if not.
If I (re)name our `summary(pressure)` chunk to “pressure”, I will see an
error when you try to knit:

    processing file: testing.Rmd
    Error in parse_block(g[-1], g[1], params.src) : duplicate label 'cars'
    Calls: <Anonymous> ... process_file -> split_file -> lapply -> FUN -> parse_block
    Execution halted

There are two things to focus on here.

First: This error message starts out in a pretty cryptic way: I don’t
expect you to know what `parse_block(g[-1]...` means. But, expecting
that the error message is really trying to help me, I continue scanning
the message which allows me to identify the problem: `duplicate label
'cars'`.

Second: This error is in the “R Markdown” tab on the bottom left of the
RStudio IDE; it is not in the Console. That is because when RMarkdown is
knitted, it actually spins up an R workspace separately from what is
passed to the Console; this is one of the ways that R Markdown enables
reproducibility because it is a self-contained instance of R.

You can click back and forth between the Console and the R Markdown tab;
this is something to look out for as we continue. We will work in the
Console and R Markdown and will discuss strategies for where and how to
work as we go. Let’s click back to Console now.

### Running RMarkdown code chunks

So far we have written code in our RMarkdown file that is executed when
we knit the file. We have also written code directly in the Console that
is executed when we press enter/return. Additionally, we can write code
in an RMarkdown code chunk and execute it by sending it into the Console
(i.e. we can execute code without knitting the document).

How do we do it? There are several ways. Let’s do each of these with
`summary(pressure)`.

**First approach: send R code to the Console.** This approach involves
selecting (highlighting) the R code only (`summary(pressure)`), not any
of the backticks/fences from the code chunk. (If you see `Error: attempt
to use zero-length variable name` it is because you have accidentally
highlighted the backticks along with the R code. Try again (and don’t
forget that you can add spaces within the code chunk or make your
RStudio session bigger (View \> Zoom In)).

Do this by selecting code and then:

1.  copy-pasting into the Console and press enter/return.
2.  clicking ‘Run’ from RStudio IDE. This is available from:
    1.  the bar above the file (green arrow)
    2.  the menu bar: Code \> Run Selected Line(s)
    3.  keyboard shortcut: command-return

**Second approach: run full code chunk.** Since we are already grouping
relevant code together in chunks, it’s reasonable that we might want to
run it all together at once.

Do this by placing your curser within a code chunk and then:

1.  clicking the little black down arrow next to the Run green arrow and
    selecting Run Current Chunk. Notice there are also options to run
    all chunks, run all chunks above or below…

### Writing code in a file vs. Console

<!---TODO more --->

When should you write code in a file (.Rmd or .R script) and when should
you write it in the Console?

We write things in the file that are necessary for our analysis and that
we want to preserve for reproducibility; we will be doing this
throughout the workshop to give you a good sense of this. A file is also
a great way for you to take notes to yourself.

The Console is good for doing quick calculations like `8*22.3`, testing
functions, for calling help pages, for installing packages. We’ll
explore these things next.