LATEX = xelatex

comma:=,
empty:=
space:= $(empty) $(empty)

ifeq ($(OS),Windows_NT)
	RM = rm 
	FixPath = $(subst $(space),$(comma),$1)
else
	ifeq ($(shell uname), Linux)
		RM = rm -f 
		FixPath = $1
	endif
endif

cleanFiles = *.aux *.lof *.log *.lot *.out *.toc *.bbl *.blg
cleanCmd = $(call FixPath,$(cleanFiles))



.PHONY: clean cleanAll noBib updateFonts

all:
	$(LATEX) thesis
	bibtex thesis
	$(LATEX) thesis
	$(LATEX) thesis

noBib:
	$(LATEX) thesis

clean:
	$(RM) $(call FixPath,$(cleanFiles))

cleanAll:
	make clean
	rm *.pdf

updateFonts:
	initexmf --admin --mkmaps

print:
	$(info $$OS os [$(OS)])
	$(info $(cleanCmd))