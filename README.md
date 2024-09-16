Appunti di Elettronica Digitale, corso tenuto all'università di Firenze dal professor Enrico Boni

Composti utilizzando [LunarVim](https://github.com/LunarVim/LunarVim), [pandoc](https://github.com/jgm/pandoc) e [tectonic](https://github.com/tectonic-typesetting/tectonic), per ottenere gli appunti in pdf.

Il comando che uso è:
```
pandoc -f markdown -t latex appunti.md -s -o appunti.tex -V lang=it --toc --top-level-division=chapter -N  && tectonic appunti.tex
```
