# when you run `make` alone, run the `css` rule (at the
# bottom of this makefile)
all: css

# .PHONY is a special command, that allows you not to
# require physical files as the target (allowing us to
# use the `all` rule as the default target).
.PHONY: all

# replace all .less files with .css extension and cache
# the results in a variable called `css_files`
css_files := $(patsubst %.less, %.css, $(wildcard *.less))

css_files := $(filter-out scheme.css,$(css_files))
css_files := $(filter-out 1pxdeep.css,$(css_files))

# when a .css file is *not* up to date compared to the
# .less file, then make will run the the following commands:
# - echo the string "foo.less -> foo.css"
# - run the command `lessc -x --source-map foo.less foo.css`
%.css: %.less node_modules/bootstrap-less/ clean
	@echo "$< -> $@"
	lessc $< $@

node_modules/bootstrap-less/:
	npm install bootstrap-less

clean:
	rm -rf $(css_files)

css: $(css_files)
