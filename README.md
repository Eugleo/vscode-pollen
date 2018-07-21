# Pollen for Visual Studio Code

This extension adds support for the [Pollen publishing system][1], including:

- Precision syntax highlighting with great scoping support for most of the Pollen markup and preprocessor formats (`.pm`, `.pp`, `.p`)
- Syntax highlighting for the special `pagetree` file
- Code snippets tailored to the filetype, such as `highlight` block for the markup files and `define` function for the preprocessor files
- Special syntax highlighting for `html.p` and `html.pp` files which combines the highlighting of both the html and the Pollen code
- Embedded syntax highlighting for the most common languages in builtin as well as custom `highlight`-type functions in the Pollen markup file

## Syntax highlighting

_The theme used in the screenshots is VSCode's Monokai Dimmed. The code smples are either mine, or taken from [this article][2]._

All common Pollen filetypes are supported; you can see how a sample `style.css.pp` looks like:



The extension also has special handling for the `html.p` and `html.pp` files, which are commonly used to provide a template for your content; notice the highlighted `doc` and `here` constants:



Last but not least, the extension adds syntax highlighting to the `highlight` function in the Pollen markup mode. The function is exported by `pollen/unstable/pygments`, but you can also define your own highlighting functions and it will work with those as well. Currently the extension recognizes the following programming languages:

- Racket
- Python
- Haskell
- Swift
- Javascript
- HTML
- CSS

Embedded LaTeX blocks get syntax highlighting as well, provided you use the recommended function/tag names `$` and `$$$`; that is, you embed LaTeX like this: `◊${\frac{1}{2}}`. 

This is an image showing an embedded python snippet:




If you are using `highlight.js` instead of `pygments` (or if you have your own highlighting function), be sure to name the tag as `highlight` or some string which has `"highlight"` in it; that is the rule the regexps are looking for. The language should then be supplied to the function as a pygments-style quoted symbol argument.

The syntax highlighting of the ebedded code depends on external syntax-highlighting extensions, so be sure to have those installed. Also note that the Racket syntax highlighting extensions for VS Code suck, but that's beyond the scope of this extension.

## Snippets

The extension adds general code snippets to all of the Pollen files, and also some specialized ones for concrete filetypes. The current list of snippets is:

- Insert the lozenge symbol
- Define a new variable
- Reference an existing variable
- Insert a tag with text body
- Insert a tag with text body and arguments
- Insert a highlight block (Pollen markup only)
- Insert a parent-level pagenode (Pagetree only)

## Pollen and Markdown

This extension does not support Pollen Markdown (`.pmd`), and I don't plan to add the support in the future, because I don't use Pollen Markdown. By the way, you shloudn't as well — the use of Pollen Markdown (and Markdown in general) is discouraged by the author of Pollen, Matthew Butterick. He makes some good points against Markdown in the Pollen docs [in the section 6.2][3]. If you _really_ need to use Markdown with Pollen and this extension, use the general preprocessor mode.

## Issues

If you need help with **Pollen**, check out the great [Pollen documentation][4], as well as some of the existing [Pollen projects & guides][5] (scroll to bottom).

If you encounter any problems with the **extension**, be sure to open an issue on this repo and I'll try to fix it as fast as possible.

Should you have any feature request or an idea how to improve this extension, please open an issue (or better, a PR). I'm not a great coder (or regexer, if you will), and don't have much experience with Pollen, so I might have messed up something.

[1]: https://docs.racket-lang.org/pollen/
[2]: https://unitscale.com/mb/technique/dual-typed-untyped-library.html
[3]: https://docs.racket-lang.org/pollen/second-tutorial.html
[4]: https://docs.racket-lang.org/pollen/quick-tour.html
[5]: https://docs.racket-lang.org/pollen/Getting_more_help.html