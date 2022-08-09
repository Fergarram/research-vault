Thinking about what neighboring rules to use to detect links with `[some text goes here](a-url.com)` syntax requires a more thinking. It's unlike the basic border-based recognition. this requires some error correction it seems.

Here is what I mean. Let's say you're a cell and your value is `[` and your neighbors are ` [a` and you already know that you're part of a paragraph. This means you are likely part of a link. You're still not 100% sure since it's hard to see what's ahead. A link's text could be hundreds of characters long. 

What do you do? You assume you're a link until proven wrong.

This is where the concept of correction cells comes in. Within the condition/neighboring rule that colors the cell assuming it's part of a link, there is a counter condition that can turn the cell into a "correction cell". This would trigger a new type of overriding behaviour.

This makes me think more about general or universal cell taxonomy. This is probably what will stem from the work with experiments I'm doing here.