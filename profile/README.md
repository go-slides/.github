<p align="center"><img src="https://raw.githubusercontent.com/go-slides/brand/main/social/go-slides.png" alt="go-slides" width="720"></p>

# go-slides

🌐 **[Website](https://go-slides.github.io)** · 📚 **[Documentation](https://go-slides.github.io/docs/)**

**Marp-compatible slide decks in pure Go (CGO=0), with Go templates and slide kinds.**

`slides` reads the Markdown that [Marp](https://marp.app) reads — `---`
between slides, global, local and spot directives, `![bg]` backgrounds,
fragmented lists, header, footer and pagination, speaker notes,
`<style scoped>`, the default, gaia and uncover themes — and adds two things
Marp does not have:

- **Go `text/template` interpolation** in the deck: `{{ .title }}` from the
  front matter's `data:`, a `{{ range }}` that generates slides,
  `{{ page }}` / `{{ total }}`, `include`. Code blocks are left alone by
  default, so a slide about templates can show one.
- **Slide kinds**: `kind: title` names a preset of local directives — header,
  footer, pagination, class, background — defined in the front matter's
  `kinds:` or in a shared kinds file, with `title`, `section`, `content` and
  `blank` built in. A slide says what it is instead of repeating how it looks.

```markdown
---
marp: true
paginate: true
data:
  talk: Pure Go slides
  topics: [Why, How, Next]
---

<!-- _kind: title -->
# {{ .talk }}

---

# Agenda

{{ range .topics }}- {{ . }}
{{ end }}
```

> **Status: in development, nothing released yet.** The first release targets
> HTML output and `slides expand` (a deck with its templates and kinds
> resolved, as plain Marp Markdown). **Planned**, not built: PNG/JPEG through
> go-webengine, PDF through go-pdfkit, PPTX through go-ooxml, math through
> go-tex, code highlighting through go-rouge — no headless Chrome, unlike
> marp-cli.

## Repositories

| Repo | What it is |
|------|------------|
| [**slides**](https://github.com/go-slides/slides) | the `slides` command and its library: the Marp-compatible parser and renderer, template interpolation and slide kinds |
| [**docs**](https://github.com/go-slides/docs) | the documentation site (Hugo + Hextra), served at [/docs/](https://go-slides.github.io/docs/) |
| [**go-slides.github.io**](https://github.com/go-slides/go-slides.github.io) | the landing page (Hugo) |
| [**brand**](https://github.com/go-slides/brand) | logo, icons and social images |

go-slides belongs to the document family of the go-* ecosystem, with
[go-richdoc](https://github.com/go-richdoc), [go-ooxml](https://github.com/go-ooxml),
[go-tex](https://github.com/go-tex) and [go-docutils](https://github.com/go-docutils).
