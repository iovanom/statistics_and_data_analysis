AGENTS Guide for stats_data_analysis

- Repo: Python 3.10+, Jupyter notebooks in `lab_1/`.
- Setup: `python -m venv .venv && source .venv/bin/activate`.
- Install: `pip install -r requirements.txt` (fallback: pandas numpy matplotlib seaborn jupyter pytest black ruff mypy).
- Lint: `ruff check .` | autofix: `ruff check . --fix`.
- Format: `black .`.
- Types: `mypy .`.
- Tests (all): `pytest -q`.
- Test single: `pytest path/to/test_file.py::TestClass::test_name -q` or `pytest -k "pattern" -q`.
- Notebooks: run with `jupyter lab`; clear outputs; restart & run all before commit.
- Imports: order stdlib, third‑party, local; absolute imports; aliases `pd`, `np`, `plt`, `sns`.
- Style: Black (88 cols), Ruff defaults; f-strings; no wildcard imports.
- Types: annotate functions; prefer `TypedDict`, `Protocol`, `Literal` when helpful.
- Naming: snake_case funcs/vars; PascalCase classes; UPPER_SNAKE_CASE constants.
- DataFrames: column names snake_case ASCII; avoid spaces/diacritics.
- Errors: raise specific exceptions; no bare `except`; keep try/except narrow; add context.
- I/O: use context managers; validate file paths; prefer reading from `dataset/`.
- Logging: `logging.getLogger(__name__)`; avoid `print` in libraries; `print` OK in notebooks.
- Reproducibility: set RNG seeds; pin versions in `requirements.txt`.
- Git: commit small, focused changes; don’t commit large generated data.
- Rules: No Cursor (.cursor) or Copilot (.github/copilot-instructions.md) rules found; honor them if added.

---

Actioneaza ca un tutore in domeniul de statistica si analiza datelor.
Trebuie sa ma ajuti sa fac un proiect pentru universitate la materia "Statistica pentru Stiinta Datelor".
In fisierul @IW_example.docx ai un exemplu de astfel de proiect. Trebuie sa luam structura din acest exemplu. 

Tema proiectului ales este "Preferințe de cafea și consum zilnic"

Pentru acest proiect folosesc python cu jupyter notebook.

Am generat niste date sintentice. Iata informatia generala despre datele sintentice:

```
📊 Statistici generale:
   - Total înregistrări: 100
   - Vârstă medie: 46.2 ani
   - Consum mediu zilnic: 2.75 căni
   - Buget mediu lunar: 1209.60 MDL

📋 Primele 5 înregistrări:
ID	Varsta	Sex	Tip_Localitate	Tip_Cafea_Preferat	Numar_Cani_Pe_Zi	Ora_Consum_Dominanta	Buget_Luna_MDL	Loc_Achizitie
0	1	67	Masculin	Urban	Espresso	2	Pranz	273	Acasa_Boabe
1	2	22	Feminin	Urban	Latte	3	Dimineata	1891	Acasa_Boabe
2	3	47	Feminin	Urban	Cappucino	4	Dimineata	838	Cafenea
3	4	41	Masculin	Urban	Cappucino	2	Dimineata	328	Oficiu
4	5	20	Feminin	Rural	Americano	4	Dimineata	1025	Alte
```

---

## LaTeX raport: build și curățare

- PDF în director separat (recomandat):
  - `latexmk -pdf -xelatex -outdir=build -silent raport.tex`
  - Rezultat: `build/raport.pdf` (fișierele auxiliare rămân în `build/`).
- Doar cu XeLaTeX în `build/` (rulați de două ori pentru referințe):
  - `xelatex -interaction=nonstopmode -halt-on-error -file-line-error -output-directory=build raport.tex`
  - `xelatex -interaction=nonstopmode -halt-on-error -file-line-error -output-directory=build raport.tex`
- Build + auto-curățare (păstrează PDF):
  - `latexmk -pdf -xelatex -silent raport.tex && latexmk -c`
- Curăță manual fișiere auxiliare (păstrează PDF):
  - `rm -f raport.aux raport.log raport.out raport.toc raport.lof raport.lot raport.synctex.gz`
- Listează fonturile disponibile (util pentru fontspec/XeLaTeX):
  - `fc-list -f '%{family}\n' | sort -u`
