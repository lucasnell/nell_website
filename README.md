`nell_website`
========

Code for Lucas Nell's website
--------

This repo contains
(1) the code necessary to build the static html website using Hugo through the R 
package `blogdown`
and
(2) the static html website that is sent to the web hosting service.

If you're looking to make some changes to the website and seeking instruction, you 
should start with the ["Overall procedure"](#overall-procedure) section below.

See [the contents file](CONTENTS.md) for details on this repo's contents.


## Table of Contents
* [Content definitions](#content-definitions)
    - [`md` vs `Rmd` files](#md-vs-rmd-files)
    - [yaml headers](#yaml-headers)
    - [`.gitignore` files](#gitignore-files)
    - [Shortcodes](#shortcodes)
* [Adding or changing content](#adding-or-changing-content)
    - [Overall procedure](#overall-procedure)
    - [Home page](#home-page)
    - [People page](#people-page)
    - [Photos page](#photos-page)
    - [Prospective students page](#prospective-students-page)
    - [Publications page](#publications-page)
    - [Research page](#research-page)
*  [Installing blogdown and Hugo](#installing-blogdown-and-hugo)


# Content definitions

### `md` vs `Rmd` files

Some functionality, like shortcodes (see below), are not easy to implement in R markdown
(`.Rmd` extension) files so were converted to regular markdown files (`.md` extension).
For this reason, you should not change these file extensions.

### yaml headers

These are headers delimited with lines consisting of either `+++` or `---` for `md` or 
`Rmd` files, respectively.
They contain document-level options, such as date, author, title, and description.
Here's an example for a `md` file:

```
+++
title = "Publications"
menu = "main"
weight = 3
url = "/publications/"
toc = false
+++
```

### `.gitignore` files

These files, as you might've guessed, are to tell git to ignore file(s).
You shouldn't need to change these unless you add a file to the folder on your computer
that you don't want on GitHub.

### Shortcodes

I used [shortcodes](https://gohugo.io/extras/shortcodes/) in some sections to force 
a style without having to put html inside `Rmd` or `md` files.
They start with `{{% shortcode_name %}}` and end in `{{% /shortcode_name %}}`.
Everything between these tags is considered part of the shortcode and its formatting is
adjusted accordingly.
They can also have named arguments that are included in the opening tag like so:
`{{% shortcode_name arg_name="arg_value" %}}`.

The People, Publications, and Photos sections use shortcodes.





# Adding or changing content

## Overall procedure

#### Important note:

- Only make changes inside the `content` folder!

#### Steps:

1. Pull changes from the GitHub repo to your local repo.†
    - In GitKraken:
        1. Select the `nell_website` repo
        2. Click the button that says "Pull"
            (it should at the top, very near the middle)
    - If using the command line:
        1. `cd` to the `nell_website` directory
        2. Run `git pull`
2. Open `/nell_website/nell_website.Rproj` in RStudio.
3. Make your changes (see the next sections for how to make changes for each page).
4. Build the website.
    1. Run `blogdown::serve_site()` in R
    2. Preview it now by going to `127.0.0.1:4321` in a web browser
    3. When it looks good, stop the `blogdown::serve_site()` function by hitting escape
        or by clicking the stop button above the console in RStudio
5. Commit your changes to the local git repository (the one on your computer).
    - In GitKraken:
        1. Select the `nell_website` repo
        2. Enter a summary of your changes in the "Summary" box in the bottom-right corner
            (if you need to add more information, you should use the "Description" box)
        3. Then click "Commit changes to X files" where X can change
    - In the terminal:
        1. `cd` to the `nell_website` directory
        2. To "stage" all file changes, run `git add .` (the trailing period is
            necessary). To stage changes to only some files, replace `.` above
            with a list of all the files you want to stage separated by spaces.
        3. Then `git commit -am "<message>"`, where `<message>` is a brief summary of
            the changes you made.
6. Push the changes from your local git repo to your GitHub repo.
    - In GitKraken:
        1. Select the `nell_website` repo
        2. Click the tab that says "Push" (it should at the top, very near the middle)
    - In the terminal:
        1. `cd` to the `nell_website` directory
        2. Run `git push`
7. Netlify should automatically update the website once pushed to GitHub.


† This is done in case someone else has made changes to the repo since you last pulled
from it.
Without you pulling before making your own changes, your changes might conflict
with theirs.


## Home page

> File to edit: `/nell_website/content/_index.md`

Simply change the text as you see fit.


## Publications page

> File to edit: `/nell_website/content/publications.md`

For any additional publication sections, they should follow the following form:

```
{{% publication_section %}}
# <SECTION_NAME>

* <PUBLICATION_1>
* <PUBLICATION_2>
...
* <PUBLICATION_N>

{{% /publication_section %}}
```

where...

* `<SECTION_NAME>`: The publication section's name (e.g., "Population dynamics of 
    magical creatures").
* `<PUBLICATION_X>`: Reference for publication `X` (e.g., "Ives, A. R., and R. Hagrid.
    1984. The collapse of cycles in the dynamics of North American unicorn populations.
    Ecology 59: 1039-1052.")

To add a table of contents to this page, make `toc = true` in the yaml header of the
`/nell_website/content/publications/_index.md` file.



## Research page

> File to edit: `/nell_website/content/research/<FILE_NAME>.Rmd`

To create a new sub-section here, you have to add a new R markdown file with a name of
your choosing.
(In general, I'd recommend against spaces and capitalization in these names.)
The new file's yaml header should contain the "image", "title", and "weight" arguments.
The "weight" argument dictates where that sub-section will appear in the Research page,
with low numbers being at the top of the page.

To edit current files, just change the text in the relevant R markdown file how you 
see fit.

To add a table of contents to this page, make `toc = true` in the yaml header of the
`/nell_website/content/research/_index.md` file.








# Installing `blogdown` and Hugo

You can run the following to install `blogdown` and Hugo.
(Hugo is the actual site generator that `blogdown` uses.)

```r
install.packages("blogdown")
blogdown::install_hugo()
```

(If these instructions don't work, check the `blogdown` website
[here](https://bookdown.org/yihui/blogdown).)


