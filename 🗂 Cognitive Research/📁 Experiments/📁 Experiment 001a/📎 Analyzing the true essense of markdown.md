I’m mapping the problem incorrectly - maybe I should try to solve the problem as for what it is: a parsing problem.

Or maybe I just need to change it to be word based and have very specific definitions of the elements needed to solve this problem like recursivity.

Answer the following:
* What's the strict formal definition of MD? as a parser would do
* What concepts are needed for that?
* How does this compare to the ambiguous approach based on words and other ideas?
* Which one is more flexible, useful, practical, resource heavy? How do they compare?

---

* The reading order is from `left` to `right` and `top` to `bottom`.
* Each `line` in a `text file` represents a unit for markdown.
* Each `line` represents an `HTML string`.
* Each `line` is made up of `characters`.
* There is a special type of characters that are `evaluated` when they appear in the first column of a `line`.
* There is a second type of special characters that represent an `HTML string` that are `evaluated` in `non-code lines`.
	* 2nd type of chars are `evaluated` to see if they are `non-code` or not.
* The `non-code` state needs to be determined first and based on the `borders`.

---

There are two questions we can ask: "Does this text looks like markdown?" and "Is this valid markdown?" This means there is a quick rough top-down look at it, a range of reach of each special feature/character, and a slow step-by-step read process.

The step-by-step process can feed an overall map or image. The top-down can also roughly contribute to that map.

For the top-down:
There is a sensation of closeness between perceived features. Consider the following example where we can perceive that the `*` special char being close to each other and thus recognizing that this could be a `bold` text.

```
------- ------- ------ -----
---- --- **----** ---- - ---
------- ------- ------ -----
```

In the same way, I'm guessing that there could be a similar approach to recognizing other attributes of the markdown problem such as the beginning and end (top-left to bottom-right corners). Acquiring valuable information in the first glance before spending resources reading line by line could be a huge performance optimization.

See [[🔩 Fast-thinking]].

I'm starting to feel like the relationship between a finite definition of markdown and the abstract ideas of reading text are starting to overlap. Meaning that my initial problem of not knowing if I should focus on the abstract or the finite is actually a false dichotomy.