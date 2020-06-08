---
title: Change Site's Theme
---

I chose [Lanyon](https://github.com/poole/lanyon) as my theme.

## Install Theme

Follow this [quick guide](https://github.com/poole/poole#usage).

If there's any error message when running the server, double check if all dependencies has been installed.

```
bundle install
```

## Customize Theme Color

I'm using Cyan color schemes that ship with Lanyon, but I customized the default color into a deeper cyan color `#408F96`.

To change it, go to `/public/css/lanyon.css` and search `cyan`.

Replace the code

```html
.theme-base-0c .sidebar,
.theme-base-0c .sidebar-toggle:active,
.theme-base-0c #sidebar-checkbox:checked ~ .sidebar-toggle {
  background-color: #408F96;
}
.theme-base-0c .container a,
.theme-base-0c .sidebar-toggle,
.theme-base-0c .related-posts li a:hover {
  color: #009688;
}
```
