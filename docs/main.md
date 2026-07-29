# html

## `parse(src)`

Parse an HTML document into a node tree. The root is a `#root` node whose
children are the top-level elements. Tolerant of unclosed void elements.

## `text(node)`

text(node) -> all descendant text concatenated, tags stripped.

## `find(node, tag)`

find(node, tag) -> every descendant element with that tag (case-insensitive).

## `attr(node, name)`

attr(node, name) -> the attribute value, or null.
