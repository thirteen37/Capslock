%.json: %.yml
	yq eval '(.rules[].manipulators[].from.modifiers | select(has("mandatory")) | .mandatory) |= ([ .[] | select(. == "hyper") |= ["right_command", "right_control", "right_shift", "right_option"]] | flatten)' $< | \
	yq eval - -o=json > $@

compile: capslock.json

install: compile
	mkdir -p $$HOME/.config/karabiner/assets/complex_modifications/
	cp capslock.json $$HOME/.config/karabiner/assets/complex_modifications/

all:
	mkdir -p $$HOME/.config/karabiner/
	cp karabiner.json $$HOME/.config/karabiner/

.PHONY: compile,install,all
