top = $(shell git rev-parse --show-toplevel)
key = $(shell basename ${top})

links=tmp/links.md
bound=tmp/bound.md
output=${top}/${key}.pdf
pandoc=pandoc-from-markdown-to-pdf

all: ${output}

.PHONY: clean
clean:
	rm -f "${links}" "${bound}" "${output}"

${output}:
	"${top}/bin/sync-topics"
	"${top}/bin/links" > "${links}"
	book-binder start.yml "${links}" "${bound}" "${top}/topics"
	${pandoc} "${bound}" -o "${output}"
