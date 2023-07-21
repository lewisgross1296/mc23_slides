# modified from Arielle's original
# https://github.com/opotowsky/dissertation/blob/main/presentation/Makefile
manuscript = mc2023_pres
references = mc2023_pres
latexopt = -halt-on-error -file-line-error -output-directory=build

all: pdf

# need biber to get references working properly
pdf: $(manuscript).tex
	mkdir -p build
	pdflatex $(latexopt) $(manuscript)
	biber build/$(references)
	pdflatex $(latexopt) $(manuscript)
	pdflatex $(latexopt) $(manuscript)
	cp build/$(manuscript).pdf .

diff:
	./diff.xsh --manuscript $(manuscript)-diff submitted

clean:
	rm -rf build

zip:
	zip paper.zip *.tex *.eps *.bib

.PHONY: all clean