---
title: Create Résumé/CV Using LaTex
---

## Why LaTex Resume?

#### Modularity
One of the main reasons I switch to LaTex from Word. It's modular so I can easily customize the module I need to tailor the position.

#### Complex formatting
It is just beautiful. A glimpse on any LaTex resume and you would know what I mean.

#### Easier to maintain
I can focus more on the content itself and no need to worry about format.

There're cons, of course. The learning curve is quite high, especially at the beginning as you need to setup everything correctly. However, once the setup is done, any changes take very minimal time compared to Microsoft Word.

## Install LaTex on Mac

I installed MacTex via `cask`. I know it's large (4GB) compared to BasicTex, but I've been testing it and turns out there's always some issue with BasicTex (e.g. cannot locate dependencies). Here is a [detailed comparison](https://sourabhbajaj.com/mac-setup/LaTeX/).

Install `cask` by Homebrew if you haven't.
```
brew install cask
```

Install MacTex.
```shell
brew cask install mactex
```

## Template

There're lots of resume template on [Overleaf](https://www.overleaf.com/). The template I'm using is based on [AltaCV](https://www.overleaf.com/latex/templates/altacv-template/trgqjpwnmtgv). Open as Template and then download the Source. You can edit and compile directly on Overleaf as well, but I prefer a local copy.

![Imgur](https://i.imgur.com/3JxGjcb.png)

## Customization

#### Colour
The color is in HTML colour code and can be changed in `main.tex`.
Here is the colour I use.
```
\definecolor{Teal}{HTML}{009688}
\definecolor{Darkteal}{HTML}{408F96}
\definecolor{SlateGrey}{HTML}{2E2E2E}
\definecolor{LightGrey}{HTML}{666666}
\colorlet{heading}{Teal}
\colorlet{accent}{Darkteal}
\colorlet{emphasis}{SlateGrey}
\colorlet{body}{LightGrey}
```

#### Section
There're many sections that I don't need, e.g. *A Day of My life*, *referees*. Simply searched the keyword and deleted `\cvsection{keyword}` and other related contents from `main.tex`.

#### Symbols

I found the symbols for email and address is a bit weird, so I changed them in `altacv.cls`.

Before
```
\NewInfoField{email}{\faAt}[mailto:]
\NewInfoField{mailaddress}{\faEnvelope}
```
After
```
\NewInfoField{email}{\faEnvelope}[mailto:]
\NewInfoField{mailaddress}{\faHome}
```

More LaTex web icons can be found in [here](http://texdoc.net/texmf-dist/doc/fonts/fontawesome/fontawesome.pdf).

The final result looks like this.
![Imgur](https://i.imgur.com/kWSrvDb.png)
