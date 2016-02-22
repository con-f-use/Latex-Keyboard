# Latex-Keyboard

Keyboad-Layout and instructions for quicker (La)TeXing

## Summary

With just a simple command it is possible to map any UTF-8 character in a LaTeX
document to just about every LaTeX command, as if the character was the actual
LaTeX command. While this is useful for allot of things, it is particularly
nice with a custom keyboard layout.

Here is an example LaTeX source before character mapping:

    f(x) = \int_{-\infty}^\infty \hat f(\xi)\ e^{2 \pi i \xi x}\,d\xi

And here the same source after:

    f(x) = ∫_{-∞}^∞ \hat f(ξ) e^{2πi ξ x} dξ

Not only is the second code more readable, but it is faster and easier to type,
if your keyboard layout looks like this:

![Custom keyboard layout for use with latex](layput.png)

For people that type a lot in LaTeX or have special Symbols of other languages
that they use allot, this might be nice.

## Usage

Simple put these lines before `\begin{document}` in your latex file:

   \usepackage[utf8]{inputenc}
   \input{/path/to/unicodedecl.tex}

Where you have to replace `/path/to/unicodedecl.tex` with the actual path to
the file of same name in this repository.

## Installing the custom layout

### Ubuntu 14.04

On Ubuntu, setting up the custom keyboard layout is as easy as running this
script:

    ./installCustomLayout.sh

All it does is make a backup of the relevant layout file and then overwrite the
"English (Macintosh)" layout with the custom layout shown in the picture above.
Layouts are cached as binary files `/var/lib/xkb/server-*.xkm`. This means that
the script has to run `dpkg-reconfigure xkb-data`. On other systems/versions,
one might not have to run that command or delete the cache files and reboot
to take effect.


### Customization

The only changes to the layout file are between lines 675 and 746 in
./installCustomLayout.sh`. They should be fairly self explanatory and the
structure clear. Change the individual characters to what ever you use most.

# Alternatives

    \documentclass{article}
    \usepackage[mathletters]{ucs}
    \usepackage[utf8x]{inputenc}

    \begin{document}
        The vorticity $ω$ is defined as $ω = ∇ × u$.
    \end{document}
