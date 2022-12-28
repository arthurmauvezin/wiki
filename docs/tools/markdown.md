# GitHub Markdown Cheatsheet

## [Basics](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
Style | Sign | Example
--- | --- | ---
Header 1 | `#` | 
Header 2 | `##` | 
Header 6 | `######` |
Bold | `**` | **Bold**
Italic | `*` | *Italic*
Strikethrough | `~~` | ~~Strikethrough~~
Subscript | `<sub></sub>` | <sub>Subscript</sub>
Superscript | `<sup></sup>` | <sup>Subscript</sup>
Quote | `>` | 
Inline code | ` `` ` | `Inline code`
Multiline code | ` ```type ``` ` | ```bash Multine code  ```
Color | `#0969DA` 
Links | `[Link](https://www.google.com)` | [Link](https://www.google.com)
Relative links | `[Link to other file](docs/other-file.md#title1)` | [Link to other file](./tools/markdown/#basics)
Images | `![Alt text](https://url-of-image.com "image title")`
Bullet list | `- / * / +` | * test
Ordered list | `1. 2. 3.`
Nested list | `  *`
Task list | `[ ] / [x]` 
Emoji | `:emojicode:` | :smile:
Comment | `<!-- Comment -->`
Escape | `\`

## Images
### Image with alt & title
```markdown
![Alt text](/path/to/img.jpg "image title")
```
### `left` alignment
```markdown
<img align="left" width="100" height="100" src="http://www.fillmurray.com/100/100">
```
### `right` alignment
```markdown
<img align="right" width="100" height="100" src="http://www.fillmurray.com/100/100">
```
### `center` alignment example
```markdown
<p align="center">
  <img width="460" height="300" src="http://www.fillmurray.com/460/300">
</p>
```

## Ligth/Dark mode
See [the following article](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#specifying-the-theme-an-image-is-shown-to)
```markdown
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://user-images.githubusercontent.com/25423296/163456776-7f95b81a-f1ed-45f7-b7ab-8fa810d529fa.png">
  <source media="(prefers-color-scheme: light)" srcset="https://user-images.githubusercontent.com/25423296/163456779-a8556205-d0a5-45e2-ac17-42d089e3c3f8.png">
  <img alt="Shows an illustrated sun in light mode and a moon with stars in dark mode." src="https://user-images.githubusercontent.com/25423296/163456779-a8556205-d0a5-45e2-ac17-42d089e3c3f8.png">
</picture>
```

## Collapsible sections
```markdown
<details>
<summary>To make sure markdown is rendered correctly in the collapsed section...</summary>

 1. Put an **empty line** after the `<summary>` block.
 2. *Insert your markdown syntax*
 3. Put an **empty line** before the `</details>` tag
 
</details>
```

## Warning and notes
```markdown
> **Note**
> This is a note

> **Warning**
> This is a warning
```

## Badges
```markdown
<div align="center">

[![CI](https://github.com/fastify/fastify/workflows/ci/badge.svg)](https://github.com/fastify/fastify/actions/workflows/ci.yml)

</div>
```

## File tree output
````markdown
```graphql
./src/* 
  ├─ src/assets - # Minified images, fonts, icon files
  ├─ src/components - # Individual smaller components
  └─ src/utils - # Utility functions used in various places./src/* 
```
````