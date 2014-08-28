# -*- Mode:Makefile -*-

# $Id: Makefile,v 0.1 2008/02/07 17:57:00 $

#commands
#standard latex aufruf, ACHTUNG: erzeugt keine links im pdf... daher pdflatex
#nehmen!
LATEX		=latex
#pdflatex verarbeitet keine vektorgrafiken, ermoeglicht so z.B. kein
#pstricks..., das ginge mit dvips aus den von latex erzeugten dvi-files, aber da
#ist das link-problem...
PDFLATEX	=pdflatex
#makeindex fuer glossar usw... ACHTUNG: mit package nomencl
#MAKEINDEX	=makeindex -s nomencl.ist
#bibtex fuer literaturangaben
BIBTEX		=bibtex
#latexmk integriert den bibtex-aufruf, kann allerdings makeindex moeglicherweise
#nicht mit dem nomencl-package anwenden
LATEXMK		=latexmk
RM			=del

PROJECT = main
#bachelorarbeit_lsi.tex
INFILE = $(PROJECT:=.tex)
TEMPFILES = *.aux *.bak
LOGFILES = *.blg *.ilg *.log
WORKFILES = *.bbl *.nlo *.nls *.out *.thm *.lof *.lot *.toc *.lol
OUTFILES = *.dvi *.ps

default:	ma clean
#.PHONY:		realclean clean ma

fast:
	$(PDFLATEX) $(PROJECT)
	
ma:
	@echo "1st latex run..."
	$(LATEX) -interaction batchmode $(PROJECT)
	@echo "bibtex run..."
	$(BIBTEX) $(PROJECT)
	@echo "2nd latex run..."
	$(LATEX) -interaction batchmode $(PROJECT)
	@echo "3rd latex run... (pdflatex)"
	$(LATEX) -interaction batchmode -shell-escape $(PROJECT)
#	dvipdfm $(PROJECT).dvi
	@echo "complete... output: " $(PROJECT).pdf

make debug:
	@echo "1st latex run..."
	$(LATEX) $(PROJECT)
	@echo "makeindex run..."
#	makeindex bachelorarbeit_lsi.nlo -s nomencl.ist -o bachelorarbeit_lsi.nls
#	$(MAKEINDEX) $(PROJECT).nlo -o $(PROJECT).nls
	@echo "bibtex run..."
	$(BIBTEX) $(PROJECT)
	@echo "2nd latex run..."
	$(LATEX) $(PROJECT)
	@echo "3rd latex run... (pdflatex)"
	$(LATEX) -shell-escape $(PROJECT)
#	dvipdfm $(PROJECT).dvi
	@echo "complete... output: " $(PROJECT).pdf

clean::
	$(RM) $(TEMPFILES) $(WORKFILES) $(OUTFILES) $(LOGFILES)

# default real cleanup target
realclean::
	$(RM) $(TEMPFILES) $(LOGFILES) $(WORKFILES) $(OUTFILES)

# $Id: Makefile,v 0.1 2008/02/07 17:57:00 $
