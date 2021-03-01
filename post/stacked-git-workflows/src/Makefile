REPOSPEC = \
	branched_workflow/repo1.json \
	branched_workflow/repo2.json \
	branched_workflow/repo3.json \
	branched_workflow/repo4.json \
	branched_workflow/repo5.json \
	branched_workflow/repo6.json \
	stacked_workflow/repo1.json \
	stacked_workflow/repo2.json \
	stacked_workflow/repo3.json \
	stacked_workflow/repo4.json \
	stacked_workflow/repo5.json

REPO = $(REPOSPEC:.json=.repo)
REPOSVG = $(REPOSPEC:.json=.svg)
REPODOT = $(REPOSPEC:.json=.dot)


%.repo: %.json
	git synth -r $@ $<

%.dot: %.repo
	git -C $< dot -m --rankdir=RL -g branch > $@ || { rm -f $@; exit 1; }

%.svg: %.dot
	dot -T svg -o $@ $<

all: $(REPOSVG) $(REPODOT)

clean:
	rm -rf $(REPO)
	rm -f $(REPOSVG) $(REPODOT)
