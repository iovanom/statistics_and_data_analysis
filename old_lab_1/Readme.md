# Laboratorul Nr. 1

Proiect: Statistica pentru Știința Datelor — „Preferințe de cafea și consum zilnic”.

## LaTeX — build rapid

- PDF în director separat (recomandat):
  - `latexmk -pdf -xelatex -outdir=build -silent raport.tex`
  - Rezultat: `build/raport.pdf` (auxiliarele rămân în `build/`).
- Doar cu XeLaTeX în `build/` (rulați de două ori):
  - `xelatex -interaction=nonstopmode -halt-on-error -file-line-error -output-directory=build raport.tex`
  - `xelatex -interaction=nonstopmode -halt-on-error -file-line-error -output-directory=build raport.tex`
- Build + auto-curățare (păstrează PDF):
  - `latexmk -pdf -xelatex -silent raport.tex && latexmk -c`
- Curățare manuală (păstrează PDF):
  - `rm -f raport.aux raport.log raport.out raport.toc raport.lof raport.lot raport.synctex.gz`
- Listează fonturile instalate (util pentru fontspec):
  - `fc-list -f '%{family}\n' | sort -u`

## Date
- Fișier: `dataset/date_cafea_consum.csv`
- Notebook generare: `generare_date.ipynb`
