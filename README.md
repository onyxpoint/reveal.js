## Customization of Reveal.js

[Reveal.js](http://lab.hakim.se/reveal-js) is a simple HTML framework for creating beautiful and easy to do presentations in HTML5 developed by [Hakim El Hattab](https://github.com/hakimel) (thanks you very much, guy!, really good work!)

This project is a customization of [Reveal.js](http://lab.hakim.se/reveal-js) for my own purposes, right now creating presentations for online video courses made for [Tegnix learning platform](https://aula.tegnix.com.).

**You can see a [live demo of this code here](http://www.ciges.net/revealjs_demo) and the result of exporting to [PDF format here](http://github.com/Ciges/reveal.js/blob/master/PDF_export/presentation.pdf?raw=true)**.

Also, you can read [here](http://www.ciges.net/presentaciones-buenas-bonitas-y-baratas-y-facilitas-en-html5-con-revealjs) a post (in Spanish) at my web explaining what Reveal.js is, how to use it and why this fork has been developed.

The original Github repository is [here](https://github.com/hakimel/reveal.js), go there for the original README file with an explanation of how to use it.

The following modifications are done:
* Added JQuery library
* Added some images under "images" directory: background for blue bar, [Tegnix](http://www.tegnix.com) and [Creative Commons](http://creativecommons.org) logo
* Added some jquery code to allow inserting a header in all pages when exporting to pdf
* Simplified index.html file putting JavaScript code in separate files
* Paper.css is not used. Only pdf.css as printing style
* Used "sky" as theme. Modifications made in sky_custom.css and pdf_custom.css files

### Added header in all pages in PDF output

With Reveal.js there is no way of showing same content in every page (same header/footer, by example) when exporting to pdf. For solving it I have used some JQuery magic in the following way:

What I want is that the following HTML be added in every page. 

```html
<div class="topbar">
    <h1 class="titulo">Title text</h1><image class="logo" src="images/logo_tegnix.png">
</div>
```

This works in the navigator if we place it before the `<section>` labels, but for showing it in every PDF page we must repeat the HTML fragment in every section.

So I used the following JQuery code to avoid repeating:
* if we want to get the PDF output (**the URL contains `?print-pdf`**) insert automatically *in every slide*, after `<section>`
* if shown in a navigator, insert *only once* after `<div class="reveal">`

```javascript
var html_barra = '<div class="topbar"><h1 class="titulo">' + titulo + 
'</h1><image class="logo" src="images/logo_tegnix.png"></div>';
if ( window.location.search.match( /print-pdf/gi ) ) {
    $('section').append(html_barra);
}
else {
    $('div.reveal').append(html_barra);
}
```

Note that `titulo` is the variable name for title text.

### PDF exporting

For exporting to PDF with reveal.js we must:
* Open the presentation with *Google Chrome* adding `?print-pdf` to the URL
* Press `CTRL + p` to launch the Chrome print dialog and save as a PDF file (with no margins)

Et voila! You can see the [PDF presentation here](https://github.com/Ciges/reveal.js/blob/master/PDF_export/presentation.pdf?raw=true).

