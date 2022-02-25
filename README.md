# Sophia and Ahab

This is a novel I have been trying to write for roughly 15 years.
It is about a wizened old author, Ahab, and his apprentice Sophia.

## Building

This project can be compiled into a pdf with scons.
When the project is complete, there will be 10 modules with 10 variations each, to select which chapters you want to bind into your book, jut run:

```
scons --chapters=0000000000
```

Replace the string `0000000000` with whatever variation you prefer (for example `0123456789`).
All corresponding chapters can be found in the SConscript file for the build.

## Notes

1. Create a "noteblock" LaTeX object that will read in a paragraph, then annotate the paragraph with Tikz and point to a footnote. Something like \begin{noteblock} paragraph \end{noteblock}{footnotetext}
2. Allow for building with Fae.jl for fractal cover art?
3. subfiles package for multi-file input to compile one at a time

## License
Any code to render the text is licensed under the MIT license in LICENSE.md.

All of the writing in this repository is licensed under the [Creative Commons Attribution-NonCommercial-ShareAlike (CC BY-NC-SA) 4.0 International License](https://creativecommons.org/licenses/by-nc-sa/4.0/) with attribution to James Schloss (Leios).

<p>
<a href="http://creativecommons.org/licenses/by-nc-sa/4.0/" >
<img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/cc.svg?ref=chooser-v1"><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/by.svg?ref=chooser-v1"><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/nc.svg?ref=chooser-v1"><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/sa.svg?ref=chooser-v1">
</a>
</p>
