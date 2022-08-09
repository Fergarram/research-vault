What I came to realize is that my mental model of markdown has some weaknesses — it's not as rigid as I thought. This complicated my process but at the same time it showed me how rigid models depend on hard non-overlapping rules.

In my mental model, there's a high-level representation of markdown syntax which consists of the output it generates: headings 1 to 6, paragraphs, links, etc. I know that a heading 1 starts with a hash for example.  But when it came to the feature-level of rules, I found myself improvising or rather discovering the neighboring rules as I set myself to do so.

What this means is that I came up with neighboring rules via trial-and-error only to figure out there could be a ton. I could argue that the high-level representation is based on my direct experience of the output or the actual rendering of the output HTML — Everything is text, Headings are big and vary in size, links are blue and clickable, lists have indentation and bullet points, code has a colored background, etc.

I've been trying to map a visual representation (rendered HTML) into a symbolic representation with specific syntactical rules which I did not permit myself to be fully strict about (like a real parser would).

What I suspect is that we are always trying to figure out the low-level or "feature" details about our high-level models. Constantly re-evaluating them. This is where learning or genetic algorithms could play a role.

What I've also realized is that there's a million ways to solve the same problems. Using the specific cell types I developed and the neighboring rules I came up with are just one of many possible solutions. It's up to selection to find the most optimized one for the situation or world where it exists.

For example, I initially thought that some kind of memory would be needed to keep track of the heading level (1..6) considering that each cell can only access their direct neighbors. But then realized that it could also be solved by some kind of ray casting cell — if the right most `#` cell can raycast to the left asking something about them than it can infer something about itself.