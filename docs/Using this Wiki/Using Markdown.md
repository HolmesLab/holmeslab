---
title: Text in Markdown
parent: Using this Wiki
nav_enabled: true 
---

# Using Markdown

Date: April 15, 2025 7:27 PM

## Text

### Headings and sizes:

```bash
### This is title text!
{: .fs-9 }

This is specially formatted text.
{: .fs-6 .fw-300 }

This is non-formatted text.

# Heading 1
## Heading 2
### Heading 3
#### Heading 4
##### Heading 5
###### Heading 6
This is unformatted text under the header.
```

### Styles

![Screenshot 2025-04-15 at 8.13.01 PM.png](Using%20Markdown%201d6cf00eb936801ab4b3d070df2b21c6/Screenshot_2025-04-15_at_8.13.01_PM.png)

```bash
Text can be **bold**, _italic_, or ~~strikethrough~~.
`Also code`
```

```bash
> Quoted / indented text
```

Text can be **bold**, *italic*, or ~~strikethrough~~.

`Also code`

> Quoted / indented text
> 

```bash
{: .new-title }
> Green Callout 
>
> text in here
```

<aside>

**GREEN CALLOUT**

text in here

</aside>

```bash
{: .warning }
> Red Callout
> text in here
```

<aside>

**RED CALLOUT**

text in here

</aside>

### Links

Links can be made like this

```bash
[Text on the page][https://holmeslab.rutgers.edu/]
```

[Text on the page](https://holmeslab.rutgers.edu/)

Or like this, if the site is used often:

```bash
[Text on the page][Holmes Lab website]

[Another instance of text][Holmes Lab website]

...

[Holmes Lab website][https://holmeslab.rutgers.edu/]
```

[Text on the page](https://holmeslab.rutgers.edu/)

[Another instance of text on the page](https://holmeslab.rutgers.edu/)

---

## Table of Contents

Insert this line of code into your page and it will generate a table of contents based on the headings which appear in that file, unless the heading has {: .no_toc .text-delta } beneath it.

```bash
1. {:toc}
```

To make a nice table of contents, this format is recommended

```bash

---
### Table of Contents
1. TOC
{:toc}
---
```

![Screenshot 2025-04-15 at 8.00.58 PM.png](Using%20Markdown%201d6cf00eb936801ab4b3d070df2b21c6/Screenshot_2025-04-15_at_8.00.58_PM.png)

---

## Special Formatting

### Tables and Dividers

You can make a table like this

```bash

| name        | head two          | three |
|:-------------|:------------------|:------|
| ok           | good swedish fish | nice  |
| out of stock | good and plenty   | nice  |
| ok           | good `oreos`      | hmm   |
```

| name | head two  | three |
| --- | --- | --- |
| ok | good swedish fish | nice |
| out of stock | good and plenty | nice |
| ok | good `oreos`  | hmm |

You can create a divider like this 

---

---

```bash
* * * #or
---
```

### Bullet points

Normal bullets

```markdown
*   Item foo
*   Item bar
*   Item baz
*   Item zip
```

- Item foo
- Item bar
- Item baz
- Item zip

Ordered list

```bash
1.  Item one
1.  Item two
Even with text between it
1.  Item three
1.  Item four
```

1. Item one
2. Item two

Even with text between it

1. Item three
2. Item four

Nested list

```bash

- level 1 item
  - level 2 item
  - level 2 item
    - level 3 item
    - level 3 item
```

- level 1 item
    - level 2 item
    - level 2 item
        - level 3 item
        - level 3 item

Collapsed sections

```markdown
<details markdown="block">
<summary>Shopping list (click me!)</summary>
* Apples
* Oranges
* Milk
</details>

```

- Shopping list (click me!)
    - Apples
    - Oranges
    - Milk

### Images

```bash
![](../../path/to/image.jpg)
```

### Labels

```markdown
### Labels

Label type 1
{: .label }

blue
{: .label .label-blue }
green
{: .label .label-green }
purple
{: .label .label-purple }
yellow
{: .label .label-yellow }
red
{: .label .label-red }

**bold**
{: .label }
*italic*
{: .label }
***bold + italic***
{: .label }
```

![Screenshot 2025-04-15 at 7.55.22 PM.png](Using%20Markdown%201d6cf00eb936801ab4b3d070df2b21c6/Screenshot_2025-04-15_at_7.55.22_PM.png)

### Diagrams/Flow charts

```bash
```mermaid
graph TD;
    accTitle: the diamond pattern
    accDescr: a graph with four nodes: A points to B and C, while B and C both point to D
    A-->B;
    A-->C;
    B-->D;
    C-->D;
```
```

![Screenshot 2025-04-15 at 7.56.47 PM.png](Using%20Markdown%201d6cf00eb936801ab4b3d070df2b21c6/Screenshot_2025-04-15_at_7.56.47_PM.png)

### Buttons

```markdown
[View it on GitHub][<link>]{: .btn .fs-5 .mb-4 .mb-md-0 }

```

![Screenshot 2025-04-15 at 8.08.00 PM.png](Using%20Markdown%201d6cf00eb936801ab4b3d070df2b21c6/Screenshot_2025-04-15_at_8.08.00_PM.png)

---

## Color Schemes

Just the Docs supports two color schemes: light (default), and dark.
To enable a color scheme, set the `color_scheme` parameter in your site's `_config.yml` file:

```bash
# Color scheme currently only supports "dark", "light"/nil (default), or a custom scheme that you define
color_scheme: nil
```

Or, you can have a button on the page which switches between dark and light

```bash
```yaml
# Color scheme supports "light" (default) and "dark"
color_scheme: dark
```

<button class="btn js-toggle-dark-mode">Preview dark color scheme</button>

<script>
const toggleDarkMode = document.querySelector('.js-toggle-dark-mode');

jtd.addEvent(toggleDarkMode, 'click', function(){
  if (jtd.getTheme() === 'dark') {
    jtd.setTheme('light');
    toggleDarkMode.textContent = 'Light';
  } else {
    jtd.setTheme('dark');
    toggleDarkMode.textContent = 'Dark';
  }
});
</script>
```