New new thoughts:

I don't think it's worth using GA on this specfic markdown problem since the possible connections between neighboring cells are quite big. A reasonable approach would be to use GA for the primitives with which something such as markdown is allowed to exist if that makes sense.

---

New thoughts:

What if this experiment is actually about finding a way to train cells with GAs? What I mean is, if I take the approach of simple programs and well defined limits/boundaries, is it possible for the GA to arrive to the right neighboring rules under supervised training?

---

## Objective

Use a genetic algorithm to find the neighboring rules that make [[🔬 Experiment 001a - Parsing Markdown with Cellular Automata]] correctly highlight markdown elements.

## Thoughts

The layers between the raw markdown layer and the block layer in Experiment 001 are currently using hard-coded tokens values such as `TK_HEAD_SINGLE` which represents a heading 1 token. But the rules by which a GA arrives to might not require such token. This means that the middle layers would have to benefit from a dynamic space that can be filled by them, although this is too vague and might not be possible to implement. Alternatively, maybe setting some middle layer generic abstraction options might make sense, such as a `HEADING_1_PREFIX` which, in the training data, would be linked to the corresponding characters and block. To make this easier, the neighborhood could be increased to any number below the work-buffer provided in the program.

Just as in the previous experiment, I think there could be many solutions to this problem, finding the right one depends on predefined constraints and technical limitations.


## Training Data

Training data will be a markdown buffer with marked blocks.

```
# Heading

Paragraph text goes here

* list
* list

```

So this would result in:
```
Line 1 -> Heading 1 (B1)
Line 2 -> Empty (B1)
Line 3 -> Paragraph Line (B2)
Line 4 -> Paragraph Line (B2)
Line 5 -> Paragraph Line (B2)
Line 6 -> List item (B3)
Line 7 -> List item (B3)
```

I'm sure there can be a more complete approach that covers all of markdown features, but this is the minimal experiment requirements.

---

Vault Relationships:

- [[🧩 Runtime Modeling]]