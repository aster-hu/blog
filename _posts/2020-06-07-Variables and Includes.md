---
title: Variables and Includes
---

## Variables

There're five types of global variables. Details can be viewed on the [official website](https://jekyllrb.com/docs/variables/).

- site
- page
- layout
- content
- paginator


## Includes

Includes is used for extracting common components on the website, e.g. header, footer.
Use the format for variable in includes:

```
{ % include header.html %}                #use header.html layout
{ % include header.html color="blue" %}   #color is customized in the page layout
```

Access the variable can be:
```
<h1 style="color: {{ include.color }}">{{ site.title }}</h1>
```
