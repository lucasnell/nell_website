# `nell_website` contents

This file outlines the file and folder contents present in this repository.

# Top-level objects

### Top-level folders

*Note*: folders starting with `.` are hidden in the Finder. To see them, you can `cd` to
the repository's folder in the Terminal and run the following command: `ls -lha`.

```
.
├── .git
├── archetypes
├── content
├── layouts
├── public
├── static
└── themes
```

**Folder descriptions:**

* `.git`: Folder containing the git repository data. This won't show up on GitHub or
    in Finder, but it is present in the top-level folder.
* `archetypes`: Documents to define default yaml parameters for different types of
    documents. The yaml is the top part of the document delimited by a line with 
    `+++` or `---` that contains document-level options.
* `content`: All the website's non-style, text content. See [below](#content-objects) 
    for more information.
* `layouts`: HTML files defining styles for the different document types.
    See [below](#layouts-objects)  for more information.
* `public`: On GitHub, this folder shows up as a link to another GitHub repo, while on the
    computer it is a folder full of files. It is a submodule contained within this repo,
    and it contains the files that are present on the website.
    See that repo's `README.md` file for how to use it.
* `static`: Files that should always be present for the website. This includes images,
    pdfs, and style (e.g., css) files. See [below](#static-objects)  for more information.
* `themes`: Folder containing the single theme used for this site. There should only 
    be one sub-folder within this folder (`kube`), which contains the theme's style
    files.


### Top-level files

*Note*: files starting with `.` are hidden in the Finder. To see them, you can `cd` to
the repository's folder in the Terminal and run the following command: `ls -lha`.

```
.
├── .Rprofile
├── .gitignore
├── .gitmodules
├── README.md
├── config.toml
├── index.Rmd
└── nell_website.Rproj
```

**File descriptions:**

* `.Rprofile`: Sets options for blogdown that R loads at startup.
* `.gitignore`: Describes files to ignore in git.
* `.gitmodules`: Information on any submodules. This repo currently only has the 
    `public` submodule.
* `README.md`: This file.
* `config.toml`: Sets site-level options, such as author, theme, and title.
* `index.Rmd`: Sets default output to `blogdown:::blogdown_site`, which is necessary for
    building the site. This file shouldn't need edited.
* `nell_website.Rproj`: Options that are useful if you edit this repo in RStudio.






# Content objects


```
.
├── .gitignore
├── _index.md
├── cv.md
├── posts
│   ├── ...
│   └── _index.md
├── publications.md
└── research
    └── _index.md
```

* `.gitignore`: Files for git to ignore. The html files blogdown creates in this folder
    are not necessary to keep in the repo, so I've included this file here to ignore
    html files just in this folder.
* `_index.md`: Text and yaml options for the home page.
* `cv.md`: Page with the CV embedded in it.
* `posts`: Posts page content.
    - `...`: Content for each post.
    - `_index.md`: yaml options.
* `publications.md`: All content for the Publications page.
* `research`: Content for Research page.
    - `_index.md`: yaml options.





# Layouts objects


```
.
├── 404.html
├── _defaults
│   ├── baseof.html
│   └── single.html
├── index.html
├── partials
│   ├── favicon.html
│   ├── footer.html
│   ├── header.html
│   ├── people
│   │   └── single.html
│   ├── research
│   │   └── single.html
│   └── toc.html
├── section
│   ├── people.html
│   ├── photos.html
│   └── research.html
└── shortcodes
    ├── person.html
    ├── photo.html
    └── publication_section.html
```



* `404.html`: Page that shows up when you try to access a path that doesn't exist, the 
  "404 Error" page.
* `_defaults`: Default layouts for pages with no specified document type.
    - `baseof.html`: Base html for all default files (perhaps all files, I'm not sure).
      I have not edited this file at all.
    - `single.html`: Default layout for pages with no specified document type.
* `index.html`: Layout for home page.
* `partials`: Files that specify the layout for part of a page.
    - `favicon.html`: The favicon, or the small image that appears on the browser tab 
        next to the site title.
    - `footer.html`: Footer layout. This is empty and not used any most/all of the
        layouts.
    - `header.html`: Header layout. This contains the banner and navigation menu.
    - `people`: Layout for individual sub-sections of People page.
        + `single.html`: Defines layout described above.
    - `research`: Layout for individual sub-sections of Research page.
        + `single.html`: Defines layout described above.
    - `toc.html`: Table of contents layout.
* `section`: Layouts for specially designed pages.
    - `people.html`: People page. This is the overall layout, not just for one
        sub-section.
    - `photos.html`: Photos page.
    - `research.html`: Research page. This is the overall layout, not just for one
        sub-section.
* `shortcodes`: Custom [Hugo shortcodes](https://gohugo.io/extras/shortcodes/) designed
    for this site.
    - `person.html`: An individual person's entry on the People page.
    - `photo.html`: A single photo on the Photos page.
    - `publication_section.html`: A publication section on the Publications page.




# Static objects

*Note*: Although not shown, all folders below contain sub-folders and/or files.
These are not shown because they aren't necessary to explain individually.

```
.
├── Ives_CV.pdf
├── css
├── font-awesome
├── fonts
├── icon
└── img
```

* `Ives_CV.pdf`: Tony's current CV.
* `css`: Style files used throughout website.
* `fonts`: Current empty, but can contain more fonts.
* `icon`: Image used for the website favicon. This is this image you see on the browser 
    tab next to the site title.
* `img`: Images used for banner, research page, post page, and photos page.
* `pdfs`: PDFs of Biosphere and Natural History articles.
* `posts`: Images used in the `functionalr` post.

