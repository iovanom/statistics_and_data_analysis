PDFENGINE = xelatex
DOC = main

all:
	latexmk -pdf -pdflatex="$(PDFENGINE) -interaction=nonstopmode -shell-escape -file-line-error %O %S" $(DOC).tex

watch:
	latexmk -pvc -pdf -pdflatex="$(PDFENGINE) -interaction=nonstopmode --shell-escape -file-line-error %O %S" $(DOC).tex

clean:
	latexmk -C
