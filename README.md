Appunti di Elettronica Digitale, corso tenuto all'università di Firenze dal professor Enrico Boni

Composti utilizzando [LunarVim](https://github.com/LunarVim/LunarVim), [pandoc](https://github.com/jgm/pandoc) e [tectonic](https://github.com/tectonic-typesetting/tectonic), per ottenere gli appunti in pdf.

Il comando che uso è:
```
pandoc -f markdown -t latex appunti.md -s -o appunti.tex -V lang=it  --top-level-division=chapter -N  && tectonic appunti.tex
```
Altre configurazioni specifiche sono inserite nell'[header](https://pandoc.org/MANUAL.html#extension-yaml_metadata_block), scritto in linguaggio [Yaml](https://yaml.org/).

Le parti in appunti.pdf evidenziate di giallo sono miei interrogativi, saranno poi rimossi.
