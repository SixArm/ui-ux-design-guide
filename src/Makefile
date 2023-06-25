top = $(shell git rev-parse --show-toplevel)
key = $(shell basename ${top})

all: build.md ${key}.pdf

new: clean all

.PHONY: clean
clean:
	rm -f build.md ${key}.pdf

build.md:
	book-binder start.yml links.md build.md

${key}.pdf:
	pandoc-from-markdown-to-pdf build.md -o ${key}.pdf
