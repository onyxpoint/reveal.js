## Customization of Reveal.js

[Reveal.js](http://lab.hakim.se/reveal-js) is a simple HTML framework for creating beautiful and easy to do presentations in HTML5 developed by [Hakim El Hattab](https://github.com/hakimel) (thanks you very much, guy!, really good work!)

This project is a customization of [Reveal.js](http://lab.hakim.se/reveal-js) for my own purposes, right now creating presentations for online video courses made for [Tegnix learning platform](https://aula.tegnix.com.)

The original Github repository is [here](https://github.com/hakimel/reveal.js), go there for the original README file with an explanation of how to use it.

The following modifications are done:
* Added JQuery library
* Added some images under "images" directory: background for blue bar, "Tegnix":http://www.tegnix.com/ and "Creative Commons":http://creativecommons.org/ logo
* Simplified index.html file putting JavaScript code in separate files
* Paper.css is not used. Only pdf.css as printing style
* Used "sky" as theme. Modifications made in sky_custom.css and pdf_custom.css files

### Added header in all pages in PDF output

With Reveal.js there is no way of showing same content in every page (same header/footer, by example) when exporting to pdf. For solving it I have used some JQuery magic in the following way:

What I want is that the following HTML be added in every page. 

```html
<div class="topbar">
    <h1 class="titulo">' + titulo + '</h1><image class="logo" src="images/logo_tegnix.png">
</div>
```

This works in the navigator if we place it before the <code><section></code> labels, but for showing it in every PDF page we must repeat