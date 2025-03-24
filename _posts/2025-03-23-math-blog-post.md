---
title: Math Typesetting in Md and Jekyll
categories:
- Math
- WebDev
feature_image: "https://picsum.photos/2560/600?image=872"
---

This page outlines usefull tips for configuring typesetting for math for my website.

Testing some math

I added the following to a new include file `math-config.html`

``` html
<!-- MathJax for LaTeX support -->
<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
<script>
    window.MathJax = {
      tex: {
        inlineMath: [['$', '$'], ['\\(', '\\)']],
        displayMath: [['$$', '$$'], ['\\[', '\\]']],
        processEscapes: true
      },
      svg: {
      fontCache: 'global',
      scale: {%raw%}{{ include.size }}{%endraw%},  // Make equations 100% larger
      },
      chtml: {
        scale: {%raw%}{{ include.size}}{%endraw%},
        matchFontHeight: false,
        mtextFont: 'serif',
        minScale: .8
    }
    };
  </script>
```
Then I make sure to `{%raw%}{%include math-config...%}{%endraw%}` this file on any pages with math (added to my default page)


Now we can do standard latex like:

Integrals:
```
$\int_0^1 f(x) dx$
```
$\int_0^1 f(x) dx$

Fractions: 
```
$\frac{x}{y}$
```
$\frac{x}{y}$

Symbols: 
```
$u_t = \lambda\sigma+Du_{xx}$
```
$u_t = \lambda\sigma+Du_{xx}$