# SPARC Syntax for Sublime Text 2

Provides SPARC assembly language syntax highlighting, as well as various
snippets.

Though SPARC is fairly uncommon, it is still used as a teaching language
in some universities (including my own up until Fall 2013). Writing
SPARC without syntax highlighting is a horror that no mortal should have
to endure.

Please note that this file, `README.MD`, is a work in progress and is
*definitely* lacking in some places.

## Installation
### Downloading the files
##### SPARC will be added to Package Control once SPARC is complete.

Navigate to your Sublime Text 2 `Packages` directory in your terminal...

- OS X: `~/Library/Application\ Support/Sublime\ Text\ 2/Packages`
- Windows: `%APPDATA%/Sublime Text 2/Packages/`
- Linux: `~/.config/sublime-text-2/Packages/`

...and type the command:

	git clone git@github.com:ProtractorNinja/SPARC-sublime.git SPARC

To install manually, download these files to a folder called `SPARC` in
your Sublime Text 2 `Packages` directory (open sublime text 2 -> click
`preferences` -> click `browse packages`).

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

The syntax highlighting should be mostly straight forward, but I'd like
to point out an important distinction between certain opcodes: **those
opcodes that involve a delay slot are classified differently (and
therefore usually colored differently) than those that do not.**
Branching commands, jumping, and subroutine calls (the complete list is
in the included `sparc.tmLanguage` file) are all colored differently
than the others. `nop` also has its own syntax definition, and in most
color schemes should have its own color.

Regular machine registers (`%r0-31`, `%i0-7`, `%o0-7`, `%l0-7`, `%g0-7`)
all have their own colorations that differ from the strange and
mysterious `%lo`, `%hi`, `%fp`, and `%sp`, as well as any user- defined
macro registers (such as `%my_register` from `define(my_register, l0)`.
**Monokai does not color variables.**

## Snippets

The SPARC package provides 7 snippets for easier insertion of certain
code structures. They are listed below.

`main` creates a basic empty program template, with sections for code and
extra data.

`subr` inserts a basic non-leaf (i.e. with its own register window)
subroutine.

`while` you wait, `while` expands into a simple while loop structure!

`for` your convenience, `for` is like while, but with an iterator
register already included.

`arr` provides access (either for a `ld` or a `st`) to an
element in a single dimensional array, as long as the address of the
beginning of the array is already known.

`arr2d` might seem complicated, but it's just the same as `arr` except
that it works with a two-dimensional array instead.

`if` you want a conditional, `if` has got your back. Feel free to remove the "else" section (`if_not_condition: ...`) if you don't need an else.


## Screenshots