# Presentation

> Markdown is life !!

## Setup mdview - markdown rendered

```bash
sudo dnf install pandoc
sudo pip install grip

echo "mdview () { pandoc $1 | grip - -b }" >> ~/.bashrc
```

## Render markdown in command line

```bash
pandoc <file>.md | grip - -b

# If you installed mdview, just use
mdview <file>.md
```

