# SPARC Syntax for Sublime Text 2

This package provides SPARC assembly language syntax highlighting, as
well as a few code snippets.

Although SPARC is fairly uncommon in practice, it is still used as a
teaching language in some universities. Writing SPARC without syntax
highlighting is a horror that no mortal need endure.

Hilariously, my SPARC class was the final SPARC course my university
offered before switching to x86. I hope that other students find this
more useful than my classmates will.

## Installation

### Getting the files

The easiest way to install SPARC-sublime is via the package control
plugin... or will be, once my pull request is accepted. In the meantime,
follow the instructions below.

Navigate to your Sublime Text 2 `Packages` directory in your terminal...

- OS X: `~/Library/Application\ Support/Sublime\ Text\ 2/Packages`
- Windows: `%APPDATA%/Sublime Text 2/Packages/`
- Linux: `~/.config/sublime-text-2/Packages/`

...and paste (try middle click if you don't know the shortcut) the
command:

	git clone git@github.com:ProtractorNinja/SPARC-sublime.git SPARC

To install manually, download this archive into a folder called `SPARC`
in your Sublime Text 2 `Packages` directory (`Preferences -> Browse
Packages...`).

Make sure to restart Sublime Text 2 when you're finished.

### Setting SPARC as the default language

Other languages include the SPARC file extensions, `.s` and `.m`, in
their syntax definitions (R and Objective-C, respectively). To combat
this, I've included a `sparc.sublime-settings` file which *should*
change the auto-syntax preference to SPARC. If I have failed, then you
may make the change manually by opening an `.s` or `.m` file and
clicking  `View -> Syntax -> Open all with current extension as... ->
SPARC`.

## Syntax Notes 

The syntax highlighting should be mostly straightforward, but I'd like
to point out an important distinction between certain opcodes: **those
opcodes that involve a delay slot -- branching commands, jumping, and
subroutine calls -- are colored differently than those that do not.**
The complete list is located in `sparc.JSON-tmLanguage`, under
`constant.other.sparc`. `nop` should also have its own color, because
`nop` is special.

Regular machine registers (`%r0-31`, `%i0-7`, `%o0-7`, `%l0-7`, `%g0-7`)
all have their own colorations that differ from the strange and
mysterious `%lo`, `%hi`, `%fp`, and `%sp`. Everything else following a
`%` symbol (e.g. macro-defined registers such as `%my_register` from
`define(my_register, l0)`) has a distinctive color. **Monokai does not
color variables.**

## Snippets

The SPARC package provides 7 snippets for super simple insertion of
certain code structures. They are listed below.

`main` creates a basic empty program template, with sections for code and
extra data.

`subr` inserts a basic non-leaf subroutine that has its own register
window.

`while` you wait, `while` expands into a simple while loop structure!

`for` your convenience, `for` is like while, but with an iterator
register already included.

`arr` provides access (either for a `ld` or a `st`) to an
element in a single dimensional array, as long as the address of the
beginning of the array is already known.

`arr2d` might seem complicated, but it's just the same as `arr` except
that it works with a two-dimensional array instead.

`if` you want a conditional block, use `if`. Feel free to remove
the "else" section (`if_not_condition: ...`) if you don't need an else.


## Screenshots

Every shot features the beautiful and amazing (and free!) [Adobe Source
Code Pro][font] Light. It works wonders on zoomed-in displays.

Using [Timmfin's Monokai variation][t-git]: ![Monokai Timmfin][t-img]  
Using [Carl Calderon's Calydon Light][c-git]: ![Calydon Light][c-img]  
Using [Dayle Rees' Github scheme][r-git]: ![Dayle Rees' Github][r-img]  

[font]:  https://blogs.adobe.com/typblography/2012/09/source-code-pro.html
[t-git]: https://github.com/timmfin/monokai-timmfin
[t-img]: screenshots/sparc-monokai-timmfin.png
[c-git]: https://github.com/carlcalderon/sublime-color-schemes
[c-img]: screenshots/sparc-calydon-light.png
[r-git]: https://github.com/daylerees/colour-schemes
[r-img]: screenshots/sparc-dayle-rees-github.png