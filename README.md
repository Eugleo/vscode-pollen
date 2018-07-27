# Pollen for Visual Studio Code

This extension adds support for the [Pollen publishing system][1], including:

- High quality syntax highlighting with great scoping support for most of the Pollen Markup and preprocessor formats (`.pm`, `.pp`, `.p`)
- Syntax highlighting for the special `pagetree` file
- Code snippets tailored to the filetype, such as `highlight` block for the markup files and `define` function for the preprocessor files
- Special syntax highlighting for `html.p` and `html.pp` files which combines the highlighting of both the `html` and the `pollen` code
- Embedded code syntax highlighting both for builtin as well as custom `highlight`-type functions

This extension adds syntax highlighting for Pollen constructs _only_, and thus depends on external Racket highlighting packages in some cases.
We highly recommed our users to use this extension alongside the [Racket for VS Code](https://marketplace.visualstudio.com/items?itemName=karyfoundation.racket) package — its Racket highlighting support is one of the best you can find.

## Syntax highlighting

_The theme used in the screenshots is customized One Dark Pro. The code samples are taken from [this article][2]._

All common Pollen filetypes are supported; you can see how a sample `style.css.pp` looks like:

![Pollen Preprocessor syntax highlighting](https://raw.githubusercontent.com/Eugleo/vscode-pollen/master/images/pollen-preprocessor.png)

The extension also has special handling for the `html.p` and `html.pp` files, which are commonly used to provide a rendering template for the content:

![Pollen Template syntax highlighting](https://raw.githubusercontent.com/Eugleo/vscode-pollen/master/images/pollen-template.png)

The extension naturally also supports Pollen Markup; the highlighting is mostly similar to the preprocessor files, but has one extra feature:
the embedded code (not necessarilly Racket code) in the `highlight` function is highlighted based on the embedded language semantics. Currently the extension recognizes the following programming languages:

- Racket
- Python
- Haskell
- Swift
- Javascript
- HTML
- CSS

Embedded LaTeX blocks get syntax highlighting as well, provided you use the recommended function/tag names `$` and `$$`; that is, you embed LaTeX like this: `◊${\frac{1}{2}}`.

This is an image showcasing the embedded language highlighting (Racket code):

![Pollen Markup syntax highlighting](https://raw.githubusercontent.com/Eugleo/vscode-pollen/master/images/pollen-markup.png)

### Defining own highlight functions/tags

The `highlight` function is exported by `pollen/unstable/pygments`. If you are using `highlight.js` instead of `pygments` (or if you have your own highlighting function), be sure to name the tag/function as `highlight` or some string which has `"highlight"` in it; that is the rule the regexps in the Pollen Markup grammar are looking for. The embedded language should then be supplied to the function as a pygments-style quoted symbol argument. You can see one such function in the screenshot above.

The syntax highlighting of the embedded code depends on external syntax-highlighting extensions, so be sure to have those installed.

## Snippets

The extension adds general code snippets to all of the Pollen files, and also some specialized ones for concrete filetypes. The current list of snippets is:

- Insert the lozenge symbol
- Define a new variable
- Reference an existing variable
- Insert a tag with text body
- Insert a tag with text body and arguments
- Insert a highlight block (Pollen Markup only)
- Insert a parent-level pagenode (Pagetree only)

## Pollen and Markdown

This extension does not support Pollen Markdown (`.pmd`), and I don't plan to add the support in the future, because the use of Pollen Markdown (and Markdown in general) is discouraged by the author of Pollen, Matthew Butterick. If you _really_ need to use Markdown with Pollen and this extension, use the general preprocessor mode.

## Issues

If you need help with **Pollen**, check out the great [Pollen documentation][4], as well as some of the existing [Pollen projects & guides][5] (scroll to bottom).

If you encounter any problems with the **extension**, be sure to open an issue on this repo and I'll try to fix it as fast as possible.

Should you have any feature request or an idea how to improve this extension, please open an issue (or better, a PR). I'm not a great coder (or regexer, if you will), and don't have much experience with Pollen, so I might have messed up something.

[1]: https://docs.racket-lang.org/pollen/
[2]: https://unitscale.com/mb/technique/dual-typed-untyped-library.html
[4]: https://docs.racket-lang.org/pollen/quick-tour.html
[5]: https://docs.racket-lang.org/pollen/Getting_more_help.html