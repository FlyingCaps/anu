# author: Pascal Bercher
#         pascal.bercher@anu.edu.au
#         https://cecs.anu.edu.au/people/pascal-bercher
# date: 27.11.2020
#

c = $(chapter)
1on1Mainfile = mainfile-1on1
4on1Mainfile = mainfile-4on1
1on1 = "\\def\\ChapterNumber{$(c)}\\input{$(1on1Mainfile)}"
4on1 = "\\def\\ChapterNumber{$(c)}\\input{$(4on1Mainfile)}"

# quick compilation: compile just once!
1on1: 1on1-quick
1on1-q: 1on1-quick
1on1-quick:
	pdflatex -jobname=$(1on1Mainfile)--chapter-$(c) $(1on1)

# time-consuming compilation: compile sufficiently often for references and label updates
1on1-all:
	pdflatex -jobname=$(1on1Mainfile)--chapter-$(c) $(1on1)
	biber $(1on1Mainfile)--chapter-$(c)
	pdflatex -jobname=$(1on1Mainfile)--chapter-$(c) $(1on1)
	pdflatex -jobname=$(1on1Mainfile)--chapter-$(c) $(1on1)

# quick compilation: compile just once!
4on1: 4on1-quick
4on1-q: 4on1-quick
4on1-quick:
	pdflatex -jobname=$(4on1Mainfile)--chapter-$(c) $(4on1)

# time-consuming compilation: compile sufficiently often for references and label updates
4on1-all:
	pdflatex -jobname=$(4on1Mainfile)--chapter-$(c) $(4on1)
	biber $(4on1Mainfile)--chapter-$(c)
	pdflatex -jobname=$(4on1Mainfile)--chapter-$(c) $(4on1)
	pdflatex -jobname=$(4on1Mainfile)--chapter-$(c) $(4on1)

# do everything! But quickly
all: all-quick
all-q: all-quick
all-quick: 1on1-quick 4on1-quick

# do everything! But sufficiently often
all-all: 1on1-all 4on1-all

clear: clean
clean:
	-rm -f *.aux *.log *.dvi *.ps *.nav *.out *.snm *.backup *.bak *.toc *~ *.bbl *.blg *.toc *.run.xml *-blx.bib *.bcf *.synctex.gz *.vrb *.pdfpc *.fls *.fdb_latexmk *.tce
