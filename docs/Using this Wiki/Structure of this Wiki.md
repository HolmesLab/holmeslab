---
title: Structure of this Wiki
parent: Using this Wiki
has_nav: true
nav_order: 2
---

# Structure of this Wiki

Date: April 15, 2025 8:51 PM

## Site Infrastructure:

This site is a Jekyll site, so the bones of it are based off of Jekyll functionality. [Jekyll documentation](https://jekyllrb.com/docs) can give insight into things like [pages structure](https://jekyllrb.com/docs/pages/), how to change page layouts, [front matter](https://jekyllrb.com/docs/front-matter/), etc. 

Jekyll is a format which is meant to be readable, so it mostly uses Markdown, which is plain text with some readable style formatting. however there are some more ~coding~ style bits. For example, how to reference variables, other pages, etc. Here is a [Jekyll cheat sheet](https://cloudcannon.com/cheat-sheets/jekyll/) for how to reference various data types within markdown pages using Jekyll. More tutorials can be found [on Cloud Cannon](https://cloudcannon.com/tutorials/)

The theme of this site is [just-the-docs](github.com/just-the-docs/just-the-docs). This is a common Jekyll theme, and created the template for the styles, layouts, header/footers, etc. Essentially everything in the _includes, _layouts and _sass files were started from base files from [just-the-docs](github.com/just-the-docs/just-the-docs). If you’re interested in making your own Jekyll site with a different theme, there are many themes available at [jekyllthemes.org,](http://jekyllthemes.org/) [jekyllthemes.io](https://jekyllthemes.io/), [GitHub.com #jekyll-theme repos](https://github.com/topics/jekyll-theme), and [jamstackthemes.dev](https://jamstackthemes.dev/ssg/jekyll/). 

## **Site Structure**

### **Pages & Navigation**

The docs which appear in the left hand navigation are ***any .md files which start with***:

```bash
---
title: <any title> 
	#This is the title which will appear on the nav bar
	#This doesn't have to match any content within the file
	#But is the label which is the 'parent' field for any nested pages
nav_order: 1 
	#This is the order they'll appear in the nav bar, lowest=first
nav_enabled: true 
	#default to true
	#if false the page will still be in the nav bar,
	# but the nav bar won't be *visible* on that page
parent: <any title>
	# if this references an existing 'title' field, the doc will be 
	# located as a nested doc under that doc in the nav bar
---
```

If two parents have the same `title`, but different grandparents, you can set their `grand_parent` titles to distinguish between their parents. The `grand_parent` title needs to be the same as the `parent` of the `parent`.

```bash
--
title: T
parent: S
grand_parent: X
---
```

```bash
--
title: T
parent: S
grand_parent: Y
---
```

Table of Contents

X
├──S
│   └── T
Y
├──S
│   └── T



### Config File

The _config.yml file controls everything which is site-universal. For example, the color scheme, header and footer, and 

### Header and Footer

These are set in the _config.yml file, because they span every page. 
*Note: any changes to _config.yml file won’t be seen until you restart the server (if hosting locally)*

- The logo (on the upper left) is set here:
    
    ```bash
    # Set a path/url to a logo that will be displayed instead of the title
    logo: "/assets/images/logo_circle.png"
    ```
    
- The link (on the upper right) to our repository + text is set here:
    
    ```bash
    # Aux links for the upper right navigation
    aux_links:
      "This Repository on Github":
        - "https://github.com/HolmesLab/holmeslab"
    ```
    
- This enables that the navigation bar is always seen
    
    ```bash
    # Enable or disable the side/mobile menu globally
    nav_enabled: true
    ```
    
- This adds external links into the navigation bar
    
    ```bash
    # External navigation links
    nav_external_links:
      - title: Holmes Lab Website
        url: https://holmeslab.rutgers.edu/ 
    ```
    
- This sets footer content
    
    ```bash
    # Footer content
    # appears at the bottom of every page's main content
    
    # Back to top link
    back_to_top: true
    back_to_top_text: "Back to top"
    
    footer_content: 'Copyright &copy; 2025 Avram Holmes. Distributed by an <a href="https://github.com/just-the-docs/just-the-docs/tree/main/LICENSE.txt">MIT license.</a> <a href="https://www.netlify.com/">This site is powered by Netlify.</a>'
    ```
    

### Folders & Files — Legend

```bash
holmeslab #Repo name + site name, so makes our link HolmesLab.github.io/holmeslab
├── 404.html # Shows up when a link points to non-existent page
├── Gemfile # This has info for what jekyll file you're using and versioning
├── Gemfile.lock # This is versioning, automatically created by updating Gemfile
├── README.md # This will show up on the front page of the repo
├── _config.yml # This controls site-wide aspects of jekyll formatting

## THIS is likely the only folder you'll change. The docs folder contains all the pages. 

# all navigation in the site (defined by each file's frontmatter) should be reflected in the folder structure, for readability and organization
# all folders need an index.html which will be the 'homepage' for that section
# the 'title' field of the index.html front matter will be what files within that section reference as 'parent'
│   ├── docs
│   │   ├── Folder # folder titles/naming = for readability, isn't relevant to site filepaths or links
│   │   │   ├── Subfolder
│   │   │   │   └── index.html # index.html means the homepage for a certain section
│   │   │   │   └── page.html # this means the site URL will be holmeslab.github.io/docs/page
│   │   ├── Lab Space at CAHBIR
│   │   │   ├── CAHBIR E-Mailing List SOP
│   │   │   │   └── index.html
│   │   │   │   └── page.html
│   │   │   ├── pictures_folder 
│   │   │   │   ├── Screenshot1.png # images in index.html or page.html
│   │   │   │   ├── Screenshot2.png
│   │   │	# The name of the file with images will be referenced directly by pages, so be careful changing the name of any folders because then those references in files will also need to be changed
│   ├── favicon.ico # This is the icon which goes at the tab header on browsers
│   ├── index.html # This is the home page of the website
│   ├── robots.txt
│   └── sitemap.xml

# This folder is css for specific website items/parts, anything you see which is dynamic (aka not the website layout). Only change these if you're familiar with css coding or if you have a specific small change you need to do.
├── _includes
│   ├── components
│   │   ├── aux_nav.html 
│   │   ├── breadcrumbs.html
│   │   ├── children_nav.html
│   │   ├── footer.html
│   │   ├── header.html
│   │   ├── mermaid.html
│   │   ├── nav
│   │   │   ├── children.html
│   │   │   ├── links.html
│   │   │   ├── pages.html
│   │   │   └── sorted.html
│   │   ├── search_footer.html
│   │   ├── search_header.html
│   │   ├── sidebar.html
│   │   └── site_nav.html
│   ├── css 
│   │   ├── activation.scss.liquid
│   │   ├── callouts.scss.liquid
│   │   ├── custom.scss.liquid
│   │   └── just-the-docs.scss.liquid
│   ├── favicon.html # This is the code which assigns favicon.ico file to be image which is on the tab
│   ├── fix_linenos.html 
│   ├── footer_custom.html
│   ├── head.html
│   ├── head_custom.html
│   ├── header_custom.html
│   ├── icons
│   │   ├── code_copy.html
│   │   ├── document.html
│   │   ├── expand.html
│   │   ├── external_link.html
│   │   ├── icons.html
│   │   ├── link.html
│   │   ├── menu.html
│   │   └── search.html
│   ├── js
│   │   └── custom.js
│   ├── lunr
│   │   ├── custom-data.json
│   │   └── custom-index.js
│   ├── mermaid_config.js
│   ├── nav_footer_custom.html
│   ├── search_placeholder_custom.html
│   ├── title.html
│   ├── toc_heading_custom.html
│   └── vendor
│       └── anchor_headings.html

# This folder is html for website layout templates. You can create new templates and put them in here, and then assign pages to that template by putting `layout:template_name.html` into the front matter
# Currently all pages default to minimal.html
# You can alter the default page layout in the config file -- BUT this will change the layout of ALL pages which don't have a layout specified, so be careful!

├── _layouts
│   ├── about.html
│   ├── default.html
│   ├── home.html
│   ├── minimal.html
│   ├── page.html
│   ├── post.html
│   ├── table_wrappers.html
│   └── vendor
│       └── compress.html

# This is is the scss code for all teh things on the page which can be input by the user in the markdown files. For example, buttons, table of contents, typography, color scheme, etc.
# 
├── _sass
│   ├── base.scss
│   ├── buttons.scss # Can change button formatting or add new buttons
│   ├── code.scss
│   ├── color_schemes # Can change color_scheme style or add color_scheme
│   │   ├── dark.scss
│   │   ├── legacy_light.scss
│   │   └── light.scss
│   ├── content.scss
│   ├── custom
│   │   ├── custom.scss
│   │   └── setup.scss
│   ├── labels.scss # Can change button formatting or add new buttons
│   ├── layout.scss
│   ├── modules.scss
│   ├── navigation.scss
│   ├── print.scss
│   ├── search.scss # Can change search formatting or add new buttons
│   ├── skiptomain.scss # Can change 'skip to main' formatting
│   ├── support
│   │   ├── _variables.scss
│   │   ├── mixins
│   │   │   ├── _buttons.scss
│   │   │   ├── _layout.scss
│   │   │   ├── _typography.scss
│   │   │   └── mixins.scss
│   │   └── support.scss
│   ├── tables.scss # Can change table formatting
│   ├── typography.scss
│   ├── utilities
│   │   ├── _colors.scss
│   │   ├── _layout.scss
│   │   ├── _lists.scss
│   │   ├── _spacing.scss
│   │   ├── _typography.scss
│   │   └── utilities.scss
│   └── vendor
│       ├── OneDarkJekyll
│       │   ├── LICENSE
│       │   └── syntax.scss
│       ├── OneLightJekyll
│       │   ├── LICENSE
│       │   └── syntax.scss
│       └── normalize.scss
│           ├── README.md
│           └── normalize.scss

# This is the place where media for the site is stored, including images, javascript and css themes. 
├── _site
│   ├── 404.html
│   ├── LICENSE
│   ├── assets
│   │   ├── css
│   │   │   ├── just-the-docs-dark.css
│   │   │   ├── just-the-docs-default.css
│   │   │   ├── just-the-docs-head-nav.css
│   │   │   ├── just-the-docs-light.css
│   │   │   └── style.css
│   │   ├── images
│   │   │   ├── android-chrome-192x192.png
│   │   │   ├── android-chrome-512x512.png
│   │   │   ├── apple-touch-icon.png
│   │   │   ├── favicon-16x16.png
│   │   │   ├── favicon-32x32.png
│   │   │   ├── favicon.ico
│   │   │   ├── large-image.jpg
│   │   │   ├── logo_circle.png
│   │   │   ├── logo_department.png
│   │   │   └── small-image.jpg
│   │   └── js
│   │       ├── just-the-docs.js
│   │       ├── search-data.json
│   │       └── vendor
│   │           └── lunr.min.js

```