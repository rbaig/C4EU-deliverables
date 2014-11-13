ROOTFILE = D_5_4_3_report_on_pilots_on_fiber_deployment_c

LATEX = /usr/bin/latex
PDFLATEX = /usr/bin/pdflatex
BIBTEX = /usr/bin/bibtex
DVIPS = /usr/bin/dvips
PS2PDF = /usr/bin/dv2pdf
PEFVIEWER = /usr/bin/evince

PDFLATEX_CMD = $(PDFLATEX) --shell-escape -synctex=1 -interaction=nonstopmode -halt-on-error $(ROOTFILE).tex
LATEX_CMD = $(LATEX) $(ROOTFILE).tex
BIBTEX_CMD = $(BIBTEX) $(ROOTFILE)
DVIPS_CMD = $(DVIPS) -o $(ROOTFILE).ps -Ppdf -G0 -t a4 $(ROOTFILE).dvi
PS2PDF_CMD = ps2pdf -sPAPERSIZE=a4 -dPDFSETTINGS=/prepress -dEmbedAllFonts=true $(ROOTFILE).ps

#all:	clean bib pdf 
all:	clean pdf

pdf: 
###	latex $(ROOTFILE).tex
##	latex $(ROOTFILE).tex
#	$(LATEX_CMD)
#	#dvipdfm D_5_4_1_report_on_pilots_on_fiber_deployment_a.dvi
##	dvips -o $(ROOTFILE).ps -Ppdf -G0 -t a4 $(ROOTFILE).dvi
#	$(DVIPS_CMD)
##	ps2pdf -sPAPERSIZE=a4 -dPDFSETTINGS=/prepress -dEmbedAllFonts=true $(ROOTFILE).ps
#	$(PS2PDF_CMD)
#	evince $(ROOTFILE).pdf &

	$(PDFLATEX_CMD)
##	$(BIBTEX_CMD)
	$(PDFLATEX_CMD)
	$(PDFLATEX_CMD)

view:
	$(PEFVIEWER) $(ROOTFILE).pdf &


publish: pdf clean
#	s3cmd put --acl-public D_5_4_1_report_on_pilots_on_fiber_deployment_a.pdf s3://www.jaumebarcelo.info/projects/C4EU/
	cp $(ROOTFILE).pdf DELIVERED_VERSION/
	@echo ""
	@echo "Don't forget to git: pull commit push"
	@echo ""


bib:
#	latex D_5_4_1_report_on_pilots_on_fiber_deployment_a.tex
	$(LATEX_CMD)
#	bibtex D_5_4_1_report_on_pilots_on_fiber_deployment_a
	$(BIBTEX_CMD)
#	latex D_5_4_1_report_on_pilots_on_fiber_deployment_a.tex
	$(LATEX_CMD)

clean:
	rm -f $(ROOTFILE).aux $(ROOTFILE).log $(ROOTFILE).blg $(ROOTFILE).bbl $(ROOTFILE).out $(ROOTFILE).dvi $(ROOTFILE).ps $(ROOTFILE).lof $(ROOTFILE).lot $(ROOTFILE).toc $(ROOTFILE).synctex.gz diff* *~ 

cleanall: clean
	rm -f $(ROOTFILE).pdf

