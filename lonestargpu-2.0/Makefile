TOPLEVEL := .
#APPS := bfs bh dmr mst pta sp sssp
APPS := bfs bh dmr mst pta nsp sssp
INPUT_URL := http://iss.ices.utexas.edu/projects/galois/downloads/lonestargpu2-inputs.tar.bz2
INPUT := lonestargpu2-inputs.tar.bz2

.PHONY: all clean inputs

all: $(APPS)

$(APPS):
	$(SETENV) make $(MAKE_ARGS) -C apps/$@
	$(SETENV) make $(MAKE_ARGS) -C apps/$@ variants

include apps/common.mk

inputs:
	@echo "Downloading inputs ..."
	@wget $(INPUT_URL) -O $(INPUT)
	@echo "Uncompressing inputs ..."
	@tar xvf $(INPUT)
	@rm $(INPUT)
	@echo "Inputs available at $(TOPLEVEL)/inputs/"

clean:
	for APP in $(APPS); do make -C apps/$$APP clean; done

