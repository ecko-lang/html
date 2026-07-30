# HTML - Ecko Std Lib Package

A tolerant HTML parser for [Ecko](https://ecko.sh), written in Ecko. Parse a
page into a node tree, strip it to text (great for feeding web content to
`ai`), or find elements.

## Install

```bash
ecko get github.com/ecko-lang/html
```

## Usage

```ecko
import html

doc = html.parse("<article><h1>Hi</h1><p>Body <b>text</b></p></article>")

html.text(doc)             # "HiBody text"  - all tags stripped
html.find(doc, "p")        # [ <p> node, ... ]  (all descendants)
html.attr(node, "href")    # attribute value, or null
```

A node is a map: elements are `{ tag, attrs, children }`, text is
`{ tag: "#text", text }`, and the root is `{ tag: "#root", ... }`.

## API

| Function | Description |
|---|---|
| `parse(src)` | Parse HTML into a `#root` node tree |
| `text(node)` | All descendant text concatenated, tags stripped |
| `find(node, tag)` | Every descendant element with that tag (case-insensitive) |
| `attr(node, name)` | An attribute's value, or `null` |

## Notes

- Tolerant: void elements (`br`, `img`, …), self-closing tags, comments, and
  doctypes are all handled; malformed markup is parsed forgivingly rather than
  rejected.
- Tag names are lower-cased; attribute names too.
- This is a pragmatic parser, not a full HTML5 tree-construction algorithm
  (no implicit tag closing beyond nesting).

## Testing

```bash
ecko test tests/
```

## License

MIT - see [LICENSE](LICENSE).
