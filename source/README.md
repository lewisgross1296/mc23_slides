This is a Beamer template set up to look pretty decent and have a
University of Wisconsin theme.  It is, of course, better than the
existing Powerpoint templates.

The easiest way to install this theme is to just dump the *.sty files
into the same directory as your tex source.

A minimal Beamer presentation using this template looks something like
the following:
```
\documentclass{beamer}
\usetheme{Wisconsin}
\begin{document}
%% Slides
\end{document}
```

The theme currently has two options:
  * nav          - This option includes a navigation bar in the
                   lower-right corner of each slide
  * white        - This option changes the color scheme to black-on-white
                   for projectors with poor color balance
  * nologo       - Suppress the crest in frame titles
  * compactlogo  - Compact title logo (takes less vertical space)

Options are specified as: `\usetheme[white]{Wisconsin}`

Other suggested packages:
* tikz (pgf, for diagrams)
* listings (for source code listings)
* fontspec (if using xetex)

Author: Tristan Ravitch (travitch@cs.wisc.edu)
Initial Release: June 2009
Public Domain

Extra
-----
Here is a very handy snippet of TeX to stick at
the beginning of your presentation (after \begin{document}):
```
\newcommand*{\alphabet}{ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz}
\newlength{\highlightheight}
\newlength{\highlightdepth}
\newlength{\highlightmargin}
\setlength{\highlightmargin}{2pt}
\settoheight{\highlightheight}{\alphabet}
\settodepth{\highlightdepth}{\alphabet}
\addtolength{\highlightheight}{\highlightmargin}
\addtolength{\highlightdepth}{\highlightmargin}
\addtolength{\highlightheight}{\highlightdepth}
\newcommand*{\Highlight}{\rlap{\textcolor{HighlightBackground}{\rule[-\highlightdepth]{\linewidth}{\highlightheight}}}}
```

HighlightBackground is defined by the Wisconsin theme.  This
snippet allows you to include source code listings in the
following way: `\lstinputlisting[language=C,moredelim={**[il][\Highlight]{@}}]{file.c}`

Note the moredelim option; with this option and the preceeding
declarations, prefixing a line in file.c will highlight the line.

Lewis Gross add-on July 2023:
-----------------
A Makefile has been provided that will compile this project from the command line. This is as simple as
running the command `make TARGET` from the `source` directory, where `TARGET` is the list of targets
(i.e. command blocks) to run. For example, to generate the PDF and cleanup the compilation, run `make all clean`.