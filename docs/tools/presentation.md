# Presentation

> Markdown is life !!

## List
* [Asciinema](https://asciinema.org/)
* Pandoc
* [Diagrams as code](https://github.com/mingrammer/diagrams)

## Render markdown in browser

### From VIM
Install [Markdown preview plugin](https://github.com/iamcco/markdown-preview.vim)

```bash
# Usage in vim
:MarkdownPreview
```

### From command line
```bash
pandoc <file>.md | grip - -b

# If you installed mdview, just use
mdview <file>.md
```

## Setup Markdown editor and viewer

[Python markdown editor](https://github.com/ncornette/Python-Markdown-Editor/) is a great tool when only having python on a computer or if you want simple markdwon edition.

The best part is it integrates a VIM editor.
