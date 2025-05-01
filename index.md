---
title: Home
layout: home
nav_order: 1
description: "Just the Docs is a responsive Jekyll theme with built-in search that is easily customizable and hosted on GitHub Pages."
permalink: /
---

### Welcome to the Holmes Lab at Rutgers University
{: .fs-9 }

The Holmes Lab is located in the Department of Psychiatry at Rutgers University. This is the internal documentation for our lab, including onboarding, resources and tutorials! 
{: .fs-6 .fw-300 }

[Looking for the Lab Website? Click here][Holmes Lab Website]{: .btn .fs-5 .mb-4 .mb-md-0 }

If you would like to add to this wiki, please follow these tutorials for how to add documentation: 
- [Using + Adding to this Wiki](docs/wiki/add-to-wiki.md): This gives an overview of the steps from downloading the repository, creating a new page and adding it to the site.
- [Structure of this Wiki](docs/wiki/structure.md): This gives an intro to the site infrastructure and of all the documents in the folder of the repository. It will help you understand how the filesystem is structured. This indicates how docs are stored. If you want to change something about style or layout, look here to see where to edit it. 
- [Using Markdown](docs/wiki/markdown.md): All docs are written in Markdown. Look here for how to style markdown text and add specific formatting/styles to your pages. 

---

#### Thank you to the contributors to the Holmes Lab documentation!

<ul class="list-style-none">
{% for contributor in site.github.contributors %}
  <li class="d-inline-block mr-1">
     <a href="{{ contributor.html_url }}"><img src="{{ contributor.avatar_url }}" width="32" height="32" alt="{{ contributor.login }}"></a>
  </li>
{% endfor %}
</ul>

----

[^1]: The [source file for this page] uses all three markup languages.

[Jekyll]: https://jekyllrb.com
[Markdown]: https://daringfireball.net/projects/markdown/
[Liquid]: https://github.com/Shopify/liquid/wiki
[Front matter]: https://jekyllrb.com/docs/front-matter/
[Jekyll configuration]: https://jekyllrb.com/docs/configuration/
[source file for this page]: https://github.com/just-the-docs/just-the-docs/blob/main/index.md
[Just the Docs Template]: https://just-the-docs.github.io/just-the-docs-template/
[Just the Docs]: https://just-the-docs.com
[Just the Docs repo]: https://github.com/just-the-docs/just-the-docs
[Just the Docs README]: https://github.com/just-the-docs/just-the-docs/blob/main/README.md
[GitHub Pages]: https://pages.github.com/
[Template README]: https://github.com/just-the-docs/just-the-docs-template/blob/main/README.md
[GitHub Pages / Actions workflow]: https://github.blog/changelog/2022-07-27-github-pages-custom-github-actions-workflows-beta/
[use the template]: https://github.com/just-the-docs/just-the-docs-template/generate
[Holmes Lab Website]: https://holmeslab.rutgers.edu/
[Holmes Lab repo]: https://github.com/HolmesLab/holmeslab 
