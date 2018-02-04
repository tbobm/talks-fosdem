# Vis Editor

author: Marc Andre Tanner

> Combining modal editing with structural regular expressions

ref: editor lineage from wikipedia

## Demonstration

---

## Modal Editing

---

## The vi(m) Grammer by Example

> d2i{

`[count] operator [count] (motion | text-object)`

## Structural Regex

Rob Pike, 1987

### By example

- search and replae:
    x/Emacs/ c/vi/

- indent:
    x/^/ i/\t/

- deindent:
    x/^\t/d

- nested loops:
    x/lua/ x/1/ c/L/

- Guard:
    x/\w+/ g/^i$/ c/I/

- Group:
    x/Emacs / { /i/v/ d a/i/  }

sam(1) Commands

Text commands:
- a/text/
- i/text/

Loops:
- x/regex/
- y/regex/
- g/regex/
- v/regex/

### Multiple Selections

- core primtiives
- Cursos are singleton selections
- Encourage a more interactive workflow than macros

### Selections: Creation

- :x/regex/ and :y/regex
- <C-K> h
