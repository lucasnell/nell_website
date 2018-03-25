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

#### Important notes:

- Only make changes inside the `_build` folder!
    Edits to the parent `nell_website` directory files will probably disappear the next
    time someone builds the site.
- Although I have "Commit your changes" as a single step, you really should do this 
    multiple times, especially if you're making significant changes.
- I recommend using RStudio to change content because it provides useful 
    highlighting for `Rmd` and `md` files.

#### Steps:

1. Pull changes from the GitHub repo to your local repo.†
    - In GitKraken:
        1. Select the `nell_website` repo
        2. Click the button that says "Pull"
            (it should at the top, very near the middle)
    - If using the command line:
        1. `cd` to the `nell_website` directory
        2. Run `git pull`
2. Open `/nell_website/_build/nell_website.Rproj` in RStudio.
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
7. Pull the GitHub repo changes to the website builder from DoIT.
    1. Login at https://linux3.dwh.doit.wisc.edu:8443/login_up.php
    2. Click the button that says "Pull Updates" (it should be towards the middle of 
        the page, right next to the GitHub repo's name)


† This is done in case someone else has made changes to the repo since you last pulled
from it.
Without you pulling before making your own changes, your changes might conflict
with theirs.


## Home page

> File to edit: `/nell_website/_build/content/_index.md`

Simply change the text as you see fit.

## People page

#### Current people

> File to edit: `/nell_website/_build/content/people/current.md`

This section uses a shortcodes to insert people's information in a specific way
formatting-wise. To add a new person, start with the following form:

```
{{% person name="<NAME>" image="/img/<name_lowercase>.jpg" email_user="<USERNAME>" email_domain="<DOMAIN_NAME>" %}}

<RESEARCH_INTERESTS>

{{% /person %}}
```

where...

* `<NAME>`: Full name (e.g., "John Doe").
* `<name_lowercase>`: Lowercase name with spaces replaced with underscores 
    (e.g., "john_doe"). *This should coincide with the filename of the image stored in
    the `/static/img/` folder.* Obviously change the trailing `.jpg` if the file has
    a different extension.
* `<USERNAME>`: Email username (e.g., "jdoe47").
* `<DOMAIN_NAME>`: Email domain name (e.g., "wisc.edu").
* `<RESEARCH_INTERESTS>`: Research interests (e.g., "I like math.").

Other options include:

* `title`: Title (e.g., "Distinguished Professor of Improbable Maths").
* `office`: Office number (e.g., "999 Birge Hall").
* `website`: Website (e.g., "http://iheartbugs.com"). Be sure to include the "http://"!
* `phone`: Phone number (e.g., "(999) 867-5309").
* `cv`: CV link (e.g., "Doe_CV.pdf"). For this example, the CV is located directly in 
    the `/static/` folder.
* `twitter`: Twitter handle (e.g., "JohnDoeTweets48"). Do not include the @.
* `scholar`: Link to Google Scholar page
    (e.g., "https://scholar.google.com/citations?user=D847cGsAAAAJ&hl=en").
* `github`: GitHub user name (e.g., "JohnDoeCoder390").

Each of these is inserted the same as name, image, etc.


#### Alumni

> File to edit: `/nell_website/_build/content/people/alumni.md`

These people were inserted into either the grad student or post doc list with more
recent people at the top.




## Photos page

> File to edit: `/nell_website/_build/content/photos/_index.md`

Each entry is inserted using a shortcode, with the following format: 

```
{{% photo "/img/photos_page/<IMAGE_NAME>" %}}
<CAPTION>
{{% /photo %}}
```

where...

* `<IMAGE_NAME>`: The file name of the image being inserted (e.g., "retreat17.jpg"). 
    It should be located in the `/static/img/photos_page/` folder for consistency.
* `<CAPTION>`: Caption for the image (e.g., "Lab retreat 2017").



## Prospective students page

> File to edit: `/nell_website/_build/content/prospective_students.Rmd`

Simply change the text as you see fit.




## Publications page

> File to edit: `/nell_website/_build/content/publications.md`

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
`/nell_website/_build/content/publications/_index.md` file.



## Research page

> File to edit: `/nell_website/_build/content/research/<FILE_NAME>.Rmd`

To create a new sub-section here, you have to add a new R markdown file with a name of
your choosing.
(In general, I'd recommend against spaces and capitalization in these names.)
The new file's yaml header should contain the "image", "title", and "weight" arguments.
The "weight" argument dictates where that sub-section will appear in the Research page,
with low numbers being at the top of the page.

To edit current files, just change the text in the relevant R markdown file how you 
see fit.

To add a table of contents to this page, make `toc = true` in the yaml header of the
`/nell_website/_build/content/research/_index.md` file.








# Installing `blogdown` and Hugo

At the time of writing this, the `blogdown` package isn't on CRAN, which means you can't
install it using `install.packages` in R.
You can run the following to install `blogdown` (plus the useful `devtools` package).

```r
if (!requireNamespace("devtools")) install.packages("devtools")
devtools::install_github("rstudio/blogdown")
```

Hugo is the actual site generator that `blogdown` uses. You need to install this using
the following code:

```r
blogdown::install_hugo()
```

(If these instructions don't work, check the `blogdown` website
[here](https://bookdown.org/yihui/blogdown).)


# Setting up GitHub with DoIT

*You should only have to do this once*

Login at https://linux3.dwh.doit.wisc.edu:8443/login_up.php.

The DoIT side of the instructions is 
[here](https://docs.plesk.com/en-US/onyx/customer-guide/git-support/using-remote-git-hosting.75848/).

The instructions for using an SSH key on GitHub are 
[here](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/).



