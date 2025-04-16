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
