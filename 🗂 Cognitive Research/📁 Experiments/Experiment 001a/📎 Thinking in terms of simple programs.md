How can I make simple cell programs that can result in the behaviour I want?

I thought of a multi-layer CA implementation similar to what I have already implemented in code.

The first layer would be to determine which characters are `non-code` and which are `code`.

The second layer would determine which HTML element it represents:
- `<h1..6>`
- `<p>`
- `<pre>`
- `<ul>`
- `<ol>`

---

Activation Flow